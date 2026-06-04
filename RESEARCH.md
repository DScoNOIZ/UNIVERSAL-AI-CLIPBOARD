# 🔬 RESEARCH: Universal AI Clipboard (UAC) — Full Investigation History

## 10 Rounds of Deep Search Across 100+ Sources

**Author:** DScoNOIZ  
**Date:** June 4, 2026  
**Objective:** Find any existing system that allows an AI agent to reference existing content between tool calls instead of regenerating it (model-driven content citation).

---

## Executive Summary

After **10 rounds of deep research** (~100 sources) across academic papers (arXiv), production frameworks (LangChain, Anthropic, Google ADK, CAMEL-AI), MCP ecosystem, GitHub repositories, and AI conferences — **no complete analogue of UAC was found.**

The closest known work is **Clipboard Primitives** by TJ Guadagno (~Dec 2025), an experimental prototype implementing ~40% of the UAC concept (named slots + `{{slot}}` placeholders). All other systems (IBM Memory Pointer, AWS Strands, LangChain Deep Agents, Claude Code, CAMEL-AI) address the same problem (token waste) through **runtime-driven mechanisms** (automatic offloading, caches, wrappers) — fundamentally different from UAC's **model-driven citation** approach.

---

## Round 1: General AI Agent Content Reuse (May 2026)

**Query:** AI agent tool call content reuse context citation mechanism reference existing context

**Sources:** ~15 (Anthropic, MIT, Firecrawl, Weaviate, arXiv, LinkedIn, various blogs)

**Key findings:**
- **Anthropic Context Engineering** (2025): compaction, structured note-taking, sub-agent architectures — all **runtime-driven**
- **ContextCite (MIT CSAIL)**: identifies which parts of context the model used — **Agent→User axis**
- **Context Compaction** (Redis, Arize AI): offloading, summarization, sliding window — **runtime-driven**

**Verdict:** No model-driven citation found.

---

## Round 2: FIM / Fill-in-the-Middle Connections (May 2026)

**Query:** AI agent fill-in-middle FIM content reuse citation mechanism between tool calls

**Sources:** ~15 (arXiv, LinkedIn, Medium, GitHub)

**Key findings:**
- **FIM** is a training technique (reordering prefix/suffix/middle for infilling) — unrelated to UAC
- **AgentReuse** (arXiv 2512.21309): reuses execution **plans**, not content
- **Tool Calling** patterns: 6-step agentic loop, no content citation

**Verdict:** No connection to FIM. No model-driven citation found.

---

## Round 3: CAMEL-AI and Tool Output Caching (May 2026)

**Query:** AI agent context compaction delta tool result caching CAMEL-AI "Brainwash Your Agent"

**Sources:** ~15 (CAMEL-AI blog, Redis, Arize AI, LinkedIn, various blogs)

**Key findings:**
- **CAMEL-AI Tool Output Caching**: stores only the LAST tool output as ID + short preview outside context
- **Was reverted** due to information loss and performance degradation
- Only caches tool outputs, not arbitrary content
- **Runtime-driven** (automatic, transparent to model)

**Verdict:** Partial functional overlap (~5%), but architecturally different (runtime vs model-driven).

---

## Round 4: Model-Driven Citation Search (June 2026)

**Query:** "model-driven" "content reuse" AI agent "ref" mechanism between tool calls cite fragment

**Sources:** ~15 (arXiv, various blogs, GitHub)

**Key findings:**
- **IBM Memory Pointer Pattern** (arXiv 2511.22729, 2025): "shifting from raw data to memory pointers"
  - Tool outputs → runtime memory → pointer → context
  - 16,000x reduction (20M → 1,234 tokens)
  - **BUT:** pointer created by tool **wrapper**, not by model. Model doesn't manage pointers.
- **Anthropic** "Writing effective tools for agents": evaluation-driven tool design, no citation

**Verdict:** IBM Memory Pointer is the closest conceptual analogue (~70% on concept level), but uses **wrapper-driven** approach, not model-driven.

---

## Round 5: Clipboard Manager / Named Slots (June 2026)

**Query:** AI agent clipboard manager named content slots reuse across tools model assembler not generator

**Sources:** ~15 (arXiv, GitHub, various blogs)

**Key findings:**
- **Amazon Payload Referencing** (arXiv 2412.05449, 2024): supervisor agent references payloads by ID — but only for inter-agent communication
- **Microsoft PlugMem** (2026): transforms interaction history into reusable knowledge units
- **Mem0**, **Letta**, various memory frameworks — all about memory, not content citation

**Verdict:** No clipboard-like mechanism for AI agents found.

---

## Round 6: Tool Output Reuse Systems (June 2026)

**Query:** "tool output" "reuse" "reference" OR "pointer" AI agent framework "instead of regenerating"

**Sources:** ~15 (arXiv, AWS, Microsoft, various blogs)

**Key findings:**
- **AWS Strands Agents SDK** (2026): `agent.state` + `ToolContext` — tools write large data, return pointer string
  - **BUT:** pointer written by **tool code**, not by model
  - Model calls tools normally, unaware of pointer mechanism
- **LangChain Deep Agents** (2026): auto-offloading when >20K tokens → file path + preview
  - **BUT:** automatic, transparent to model
- **Claude Code**: non-destructive pruning of tool results, 2KB previews
  - **BUT:** runtime-driven, model-unaware

**Verdict:** All production systems use runtime-driven approaches. No model-driven citation found.

---

## Round 7: Cross-Protocol / MCP Citation (June 2026)

**Query:** "cross-protocol citation" OR "MCP injection" OR "{{ref}}" AI agent content reference

**Sources:** ~15 (MCP docs, Microsoft, MIT Tech Review, various)

**Key findings:**
- **MCP (Model Context Protocol)**: standard for connecting tools, NOT a citation mechanism
- **A2A (Agent-to-Agent)**: inter-agent communication, NOT content citation
- **MCP injection security** research: about prompt injection, not content reuse

**Verdict:** No cross-protocol citation mechanism exists.

---

## Round 8: Deep Search — Clipboard Primitives Discovery (June 4, 2026)

**Query:** TJ Guadagno "Agent-clipboard" GitHub copy paste AI agents experimental primitive

**Sources:** ~5 (LinkedIn, GitHub)

**Key findings:**
- **Clipboard Primitives** by **TJ Guadagno** (TJ-Codes) — **THE CLOSEST KNOWN WORK**
  - Published ~December 2025 on LinkedIn Pulse
  - GitHub: [TJ-Codes/Agent-clipboard](https://github.com/TJ-Codes/Agent-clipboard) (3 commits, no stars)
  - Two tools: `copy` (extracts into named slots) + `template_invoke` (executes with `{{slot}}` placeholders)
  - 9 functional tests against Claude
  - **Key finding:** "The agent didn't need to be taught clipboard semantics"
  - **Limitations:** tool results only, no transform pipeline, no MCP injection, no AST clipboard
  - Author states: "This cannot be implemented as a standalone MCP server"

**Coverage of UAC features:** ~40%

---

## Round 9: Academic Verification (June 4, 2026)

**Query:** "LLM generates reference" OR "LLM generates pointer" AI agent tool call "instead of generating"

**Sources:** ~15 (arXiv, SEMANTIC SCHOLAR, various)

**Key findings:**
- arXiv 2605.06635: cited but not verified — about citation accuracy in LLM responses (Agent→User)
- arXiv 2512.21309: AgentReuse — plan reuse, not content
- arXiv 2603.22862: tool evolution — test-time tool generation, not content citation
- arXiv 2601.06007: prompt caching evaluation
- arXiv 2504.07830: MOSAIC — social AI simulation, unrelated

**Verdict:** Zero academic papers describe model-driven content citation between tool calls.

---

## Round 10: Final Exhaustive Search (June 4, 2026)

**Query combinations:**
- "syntactic clipboard" OR "AST block" AI agent content extraction
- "content reference mechanism" AI agent "reuse existing"
- "mosaic assembly" OR "multi_ref" AI agent
- Various GitHub searches, LinkedIn, conference talks

**Sources:** ~10+

**Key findings:**
- **ast-grep**: AST-based code search — exists, but not for AI agent clipboard
- **code-chunk**: AST-aware code chunking for RAG — unrelated
- **PowerToys Advanced Paste**: clipboard for humans with AI — not for agents
- **UiPath Clipboard AI**: for human automation — not for agents

**Verdict confirmed:** UAC has no complete analogue in any existing system.

---

## Summary Table

| Round | Focus | Key Finding |
|:-----:|-------|-------------|
| 1 | General reuse | All systems runtime-driven |
| 2 | FIM connection | No connection to UAC |
| 3 | CAMEL-AI | ~5% partial, runtime-driven |
| 4 | Model-driven citation | IBM Memory Pointer ~70% concept, but wrapper-driven |
| 5 | Clipboard/named slots | Nothing found |
| 6 | Tool output reuse | Strands, LangChain, Claude Code — runtime only |
| 7 | MCP citation | No cross-protocol citation exists |
| 8 | **Deep search** | **TJ Guadagno's Clipboard Primitives ~40% — closest match** |
| 9 | Academic papers | Zero academic works describe this |
| 10 | Exhaustive final | Final confirmation: no complete analogue exists |

---

## Conclusion

**Universal AI Clipboard is a new category in AI agent architecture.** The only known partial implementation — Clipboard Primitives (TJ Guadagno, ~40% of the concept) — was discovered experimentally after the initial 7 research rounds due to its low visibility.

No production framework, academic paper, or open-source project implements model-driven content citation where:
1. The model writes `ref` parameters instead of generating content
2. The content can come from any source (files, chat, terminal, API, MCP)
3. Multiple fragments can be assembled with transformations (mosaic assembly)
4. Citation works cross-protocol through MCP injection
5. A universal clipboard manager with named slots exists for the model
