# 📐 SPECIFICATION: Universal AI Clipboard (UAC) — Technical Reference

**Version:** 1.0 (June 2026)  
**License:** CC0 1.0 Universal (Public Domain)  
**Status:** ⚡ Specification — not yet implemented

---

## 1. Core Concept

UAC defines a **Content Reference Mechanism** that allows AI agents to cite existing content from any source instead of regenerating it. The model acts as an assembler, composing solutions from ready-made fragments.

### 1.1 Key Principles

1. **Model-Driven:** The model consciously decides when to reference content and writes `ref` parameters
2. **Universal Sources:** Any content in the agent's accessible context (files, chat, terminal, API, MCP)
3. **Byte-Identical Transfer:** Content bypasses LLM generation entirely — no mutation, no hallucination
4. **Composable:** Fragments can be combined, transformed, and assembled (mosaic assembly)
5. **Cross-Protocol:** Works with any tool interface, including MCP, REST, SDKs

---

## 2. Reference Parameters

### 2.1 Single Reference (`ref`)

```json
{
  "ref": {
    "source": "file|chat|terminal|api|mcp|clipboard",
    "path": "path/to/source",           // file path, chat ID, etc.
    "focus": "functionName",            // for syntactic clipboard (Mechanism 1)
    "start": "first 15-40 chars",       // for anchor pair (Mechanism 2)
    "end": "last 15-40 chars",          // for anchor pair (Mechanism 2)
    "ref": "167:14..18",                // for message index (Mechanism 3)
    "clip": "clip-1"                    // for clipboard slot
  }
}
```

### 2.2 Multi-Reference (`multi_ref`)

```json
{
  "multi_ref": [
    { "source": "file", "path": "handlers.ts", "start": "async function validate(", "end": "}" },
    { "source": "file", "path": "handlers.ts", "start": "async function process(", "end": "}" }
  ],
  "transform": {
    "join": "\n\n",
    "prepend": "// --- Handlers ---\n"
  }
}
```

### 2.3 Inline Reference (`{{ref:...}}`)

For embedding directly inside any tool parameter:

```
"{{ref:source=chat,ref=-1,start=export const config}} --host production"
```

---

## 3. Five Citation Mechanisms

### Mechanism 1: 🔗 Syntactic Clipboard (AST-Based)

Model specifies a **syntactic anchor** (function name, class name, variable name). System:
1. Parses the source code into an AST
2. Locates the anchor element
3. Determines precise syntactic boundaries
4. Extracts the complete syntactic unit

**Use case:** Citing a function from a file without regenerating its code.

```
{ source: "file", path: "utils.ts", focus: "calculateSum" }
  → 2 tokens instead of 800+ tokens of the entire function
```

**Resolution algorithm:**
1. Read source file → parse into AST (using Tree-sitter or equivalent)
2. Find node matching `focus` name at the top level
3. Walk up to the enclosing declaration node (function, class, variable)
4. Extract source text from start to end of that node
5. Return extracted text

### Mechanism 2: 📇 Anchor Pair Citation

Model specifies **START** and **END** markers (15-40 characters each). System finds everything between them.

```
{ source: "chat", ref: "-1",
  start: "function calculateSum(",
  end: "return result;" }
  → ~10 tokens instead of 200+
```

**Resolution algorithm (multi-stage):**
1. **Exact match** — literal string search for both anchors (~70% success)
2. **Normalized match** — whitespace/case/punctuation normalization (~20%)
3. **Fuzzy match** — Levenshtein distance ≤ 2 (~9%)
4. **Word boundary expansion** — expand to nearest word boundaries
5. Validate: extract must contain start anchor before end anchor
6. Return text between anchors, excluding anchor markers

### Mechanism 3: 🧠 Message Index Map

System maintains an index of exact character positions for each message in chat history.

```
{ source: "chat", ref: "167:14..18" }
  → "record #167, lines 14-18" → exact extraction
```

**Index structure:**
```
message_index = {
  167: {
    lines: [
      { start: 0, end: 42 },        // line 1
      { start: 43, end: 156 },       // line 14 (target start)
      ...
      { start: 892, end: 924 }       // line 18 (target end)
    ],
    total_chars: 1042
  }
}
```

**Advantage:** model sees only ~5 tokens for the reference, never the index itself. Achieves 100% precision.

### Mechanism 4: 🔄 Transform Pipeline

Copied fragment can be modified on-the-fly before tool dispatch.

**Available operations:**

| Operation | Parameter | Description | Example |
|-----------|-----------|-------------|---------|
| `replace` | `{from, to}` | Replace substring | `{from: "var", to: "let"}` |
| `prepend` | `string` | Add before fragment | `"// Auto-generated\n"` |
| `wrap` | `string` | Place in template | `"try { {content} } catch (e) {}"` |
| `append` | `string` | Add after fragment | `" --verbose"` |
| `join` | `string` | Merge fragments (with multi_ref) | `"\n\n"` |

**All operations applied in a single tool call:**
```
{
  ref: { source: "file", path: "utils.ts", focus: "parseConfig" },
  transform: {
    wrap: "function safeParseConfig(path) {\n  try {\n    {content}\n  } catch (e) {\n    return null;\n  }\n}"
  }
}
```

### Mechanism 5: 🔁 Cross-Protocol Citation (MCP Injection)

Reference markers embedded inside any tool's text parameters. System resolves before external call.

```
"{{ref:source=chat,ref=-1,start=export const config}} --host production"
```

**Resolution:**
1. Tool call generated by model contains `{{ref:...}}` marker
2. Harness intercepts tool call before dispatch
3. Resolves `{{ref:...}}` to actual content
4. Substitutes content in-place, preserving surrounding text
5. Dispatches fully resolved tool call to external system

**Advantage:** Works with ANY tool interface (MCP, REST APIs, SDKs) without schema changes.

---

## 4. Clipboard Manager: Named Slots

### 4.1 Slot Operations

| Operation | Description |
|-----------|-------------|
| `save` | Save content to named slot (`slot.save("config-block", content)`) |
| `load` | Load content from named slot (`slot.load("config-block")`) |
| `delete` | Remove named slot |
| `list` | List all available slots |
| `swap` | Swap content between two slots |

### 4.2 Slot Properties

- **Scope:** Session-wide (persists across context compaction)
- **Naming:** User-defined (`clip-1`, `config-block`, `error-log`, etc.)
- **Cost:** Zero tokens for storage and retrieval
- **Content:** Any text content of any length
- **Persistence:** Can survive session restarts when backed by persistent storage

### 4.3 Example Workflow

```
Step 1: tool_read → "export const API_URL = 'https://...'" 
        slot.save("api-config", result)

Step 2: tool_write with {{ref:clip=api-config}}
        → System substitutes the actual config
        → 0 tokens spent on regeneration
```

---

## 5. Mosaic Assembly

The model can combine multiple fragments from different sources in a single operation:

```json
{
  "multi_ref": [
    { "source": "file", "path": "types.ts", "focus": "UserConfig" },
    { "source": "chat", "ref": "42:1..10" },
    { "source": "clipboard", "clip": "helpers" }
  ],
  "transform": {
    "join": "\n\n",
    "prepend": "// --- Compiled Module ---\n",
    "append": "\n// End of module"
  }
}
```

**Result:** A new file composed from 3 different sources, assembled with formatting — in 1 tool call.

---

## 6. Refutation of Common Objections

### 6.1 ❌ "This is just caching"

**Response:** Caching is **automatic** and **runtime-driven**. UAC is **model-driven**. The model consciously decides what to reference. It's the difference between a cache that stores web pages automatically and a user who bookmarks specific pages.

### 6.2 ❌ "IBM Memory Pointer already does this"

**Response:** IBM Memory Pointer uses **wrappers** to create pointers without the model's knowledge. UAC requires the **model itself** to decide and write references. The pointer in IBM is a tool wrapper's output; the ref in UAC is the model's own intentional parameter.

### 6.3 ❌ "Context compaction is the same thing"

**Response:** Context compaction (LangChain, Claude Code, etc.) automatically removes/compresses old data. It's like an OS swapping memory pages. UAC is like having the program code use pointers intentionally.

### 6.4 ❌ "References will cause cascading hallucinations"

**Response:** This confuses runtime-driven caching (where model doesn't know data is missing) with model-driven citation (where model intentionally references content). In UAC, content is transferred **byte-for-byte** — it never passes through LLM generation. Copy-paste doesn't cause hallucinations in humans, and it won't in AI agents.

### 6.5 ❌ "Clipboard Primitives already exists"

**Response:** Clipboard Primitives implements ~40% of UAC's concept (named slots + `{{slot}}` placeholders). UAC extends this with 5 citation mechanisms, universal sources, transform pipeline, mosaic assembly, and cross-protocol citation. TJ Guadagno is recognized as an independent co-discoverer.

---

## 7. Implementation Considerations

### 7.1 Harness-Level Integration Required

The `{{ref:...}}` resolution and `multi_ref` assembly must happen at the **harness layer** — after the model generates the tool call but before content flows through to the tool. This cannot be implemented as a standalone MCP server because the LLM would regenerate content before the MCP tool receives it.

### 7.2 Source Discovery

The model needs a way to discover available content:
- File system: explicit paths
- Chat history: message index
- Terminal: command output IDs
- Clipboard: named slot listing
- MCP: schema-available content

### 7.3 Error Handling

| Failure | Behavior |
|---------|----------|
| Source not found | Return error, model falls back to generation |
| Anchor mismatch | Try next match stage (exact → normalized → fuzzy) |
| Ambiguous reference | Return options, model selects |
| Transform syntax error | Return error with guidance |

---

## 8. Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | June 3, 2026 | Original specification |
| 1.1 | June 4, 2026 | Added Clipboard Primitives comparison; refined distinction from IBM Memory Pointer; added objections section |
