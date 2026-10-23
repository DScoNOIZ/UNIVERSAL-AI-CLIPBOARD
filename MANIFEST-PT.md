# 🏛️ UNIVERSAL AI CLIPBOARD (UAC)

## A Área de Transferência Universal para Inteligência Artificial

### Um Mecanismo de Reutilização de Conteúdo para Agentes de IA

---

> **Data de publicação:** 3 de junho de 2026
> **Status:** ⚡ Descoberta liberada em domínio público
> **Licença:** CC0 1.0 Dedicacão Universal ao Domínio Público

---

## 📜 DECLARAÇÃO DO DESCOBRIDOR

Eu, **[DScoNOIZ](https://github.com/DScoNOIZ)**, declaro diante da comunidade global:

**1. Sou o descobridor** de uma categoria fundamentalmente nova na arquitetura de agentes de IA — o **«Mecanismo Opcional de Citação de Conteúdo entre Ferramentas»** (Optional Inter-Tool Content Citation Mechanism), nomeado por mim como **Universal AI Clipboard (UAC)**.

**2. A essência da descoberta:** Um agente de IA pode referenciar conteúdo contextual já existente por meio de parâmetros dedicados (`ref`, `multi_ref`, `transform`) em vez de regenerá-lo. O modelo deixa de ser apenas um «gerador de texto» e se torna um **montador** que combina fragmentos de informação prontos em uma única chamada.

**3. Eu libero esta descoberta para o uso livre de toda a comunidade global** sob a licença Creative Commons Zero (CC0) — sem patentes, royalties, licenças fechadas ou restrições.

**4. Eu convoco** desenvolvedores, pesquisadores, engenheiros e entusiastas do mundo inteiro — peguem esta ideia, implementem-na em seus frameworks, plataformas e ferramentas. **Esta tecnologia não me pertence. Ela pertence a todos.**

---

## 🤝 CO-DESCOBRIDOR: DESCOBERTA INDEPENDENTE

Eu reconheço e respeito o fato de que **TJ Guadagno** (TJ-Codes) chegou de forma independente à mesma ideia fundamental e a implementou experimentalmente como **Clipboard Primitives** — um mecanismo `copy`/`template_invoke` com slots nomeados e placeholders `{{slot}}` para agentes de IA.

**Trabalho dele:** [Copy and Paste for AI Agents: An Experimental Primitive](https://www.linkedin.com/pulse/copy-paste-ai-agents-experimental-primitive-tj-guadagno-v3r9c) (~dezembro de 2025)
**Código:** [github.com/TJ-Codes/Agent-clipboard](https://github.com/TJ-Codes/Agent-clipboard)

TJ Guadagno é um **co-descobridor independente** deste conceito. Seu experimento confirmou que:
- Modelos **adotam naturalmente** a semântica de área de transferência, sem treinamento especial
- Primitivas de área de transferência **eliminam** regeneração de tokens, latência e riscos de mutação de conteúdo
- O mecanismo exige integração **no nível do harness**, não no nível do servidor MCP

**Meu conceito de Universal AI Clipboard é mais amplo e mais universal** — ele inclui Clipboard Primitives como caso particular e estende a ideia para:
- **5 mecanismos de citação** (incluindo área de transferência sintática via AST, índice de mensagens, citação por par de âncoras)
- **Área de transferência universal para qualquer fonte** (arquivos, chat, terminal, API, MCP)
- **Montagem em Mosaico** — combinar fragmentos de diferentes fontes com transformações
- **Citação entre Protocolos** — citação transparente através de qualquer protocolo, incluindo MCP

**Analogia de computador:** Clipboard Primitives é como um utilitário simples de copiar para um único aplicativo. Universal AI Clipboard é um gerenciador de área de transferência completo a nível de sistema, funcionando entre todos os aplicativos, com gerenciamento de slots, pipeline de transformação e integração entre protocolos.

> **Eu não renuncio ao meu status de descobridor.** Formulei e sistematizei este conceito de forma independente, conduzindo uma pesquisa em múltiplas rodadas que não encontrou análogos completos. Tendo tomado conhecimento do trabalho de TJ Guadagno apenas após publicar o manifesto, reconheço sua contribuição independente e considero meu dever refleti-la no manifesto.
---

## 🏛️ NOME

**Nome oficial:** **UNIVERSAL AI CLIPBOARD (UAC)**
**Nome técnico:** Mecanismo de Referência de Conteúdo (Content Reference Mechanism)
**Lema:** _«Reuse, Don't Regenerate»_ — _«Reutilize, não regenere»_
**Metáfora:** Ctrl+C / Ctrl+V para Agentes de IA

---

## 🌍 O PROBLEMA

### A Contradição Fundamental

Agentes de IA modernos desperdiçam **até 90% do seu tráfego de saída** regenerando de forma monótona conteúdo que já existe no contexto da sessão.

Cada vez que um modelo escreve um comando, um bloco de código ou um fragmento de texto — ele o regenera do zero, mesmo que o mesmo conteúdo tenha sido criado um minuto atrás. O modelo não tem como referenciar de forma instrumental um conteúdo já existente.

### Escala Global do Problema

- Milhões de agentes de IA operam diariamente no mundo todo
- Cada um executa dezenas de chamadas de ferramenta por sessão
- Uma parte significativa de cada chamada é regeneração de conteúdo existente
- Isso leva a um enorme consumo de energia, desperdício computacional e custos financeiros

### Por que as Abordagens Existentes Não Resolvem Isso

| Abordagem                | Limitação                                                       |
| ----------------------- | --------------------------------------------------------------- |
| **Cache de Prompt**      | Funciona apenas com partes estáticas, não com conteúdo dinâmico |
| **Cache Semântico**    | Faz cache pelo significado da consulta, não permite citação de fragmentos |
| **Compressão de Contexto** | Comprime o histórico, mas não fornece uma ferramenta de citação |
| **RAG**                 | Recupera de fontes externas, não reutiliza o contexto interno |
| **Encadeamento de Ferramentas**       | Encadeia chamadas, não permite referenciar seus resultados  |

---

## 💡 A SOLUÇÃO: UNIVERSAL AI CLIPBOARD

### A Ideia Central

Um agente de IA ganha a capacidade de **referenciar conteúdo contextual já existente** em vez de regenerá-lo. Ao chamar qualquer ferramenta que aceite parâmetros de texto (comandos, código, texto), o agente pode especificar: «pegue este fragmento dali» — em vez de escrevê-lo do zero.

### Montagem em Mosaico: Compondo Informação como um Quebra-Cabeça

Além da citação simples um-para-um, este conceito permite uma forma fundamentalmente nova de compor informação — **a montagem em mosaico**.

Um agente pode **combinar múltiplos fragmentos de diferentes fontes** em uma única operação:

- Código de um arquivo
- Configuração do histórico de chat
- Saída de comando do terminal
- Resultados de APIs externas

O agente pode **editar em tempo real** — modificar, envolver, substituir texto dentro de cada fragmento. Ele pode **reordenar** fragmentos, **aninhar** um dentro do outro, **mesclar** pedaços sobrepostos e **reestruturar** conteúdo recursivamente. Isso cria a capacidade de montar textos compostos, documentos ou blocos de código a partir de peças espalhadas — como um mosaiquista organizando ladrilhos coloridos em uma figura completa.

**A percepção-chave:** em vez de gerar texto novo, o modelo atua como **editor e curador** de conteúdo existente — muito mais eficiente, mais preciso e menos propenso a erros.

### Gerenciador de Área de Transferência: Slots Nomeados para Armazenamento Persistente

Uma extensão deste conceito é um **gerenciador de área de transferência com slots nomeados** — semelhante a ter múltiplas áreas de transferência ou um gerenciador de buffers de texto.

O agente pode:

- **Salvar fragmentos** em slots nomeados (`clip-1`, `clip-2`, `config-block`, `error-log`, etc.)
- **Referenciar slots** pelo nome em vez de pelo conteúdo — zero tokens gastos com descrição
- **Trocar e reorganizar** conteúdo entre slots
- **Construir documentos compostos** referenciando vários slots em sequência
- **Fazer fragmentos persistirem entre sessões** — fragmentos salvos sobrevivem à compactação do contexto e a reinícios de sessão

Isso transforma o fluxo de trabalho do agente de IA em algo análogo a um desenvolvedor humano trabalhando com múltiplos gerenciadores de área de transferência, buffers de texto e blocos de rascunho — mas totalmente automatizado e com custo zero de tokens para operações de armazenamento.

### A Diferença Axial dos Mecanismos Existentes

Todos os mecanismos de citação existentes em IA (Citations API, Grounding, ContextCite) operam no eixo **«agente → usuário»** — mostram aos humanos onde o agente obteve a informação.

Universal AI Clipboard opera no eixo **«agente → agente»** — permite que o próprio agente reutilize conteúdo entre suas chamadas de ferramenta. Esta é uma categoria fundamentalmente nova.

| Mecanismo                  | Eixo              | Propósito                           |
| -------------------------- | ----------------- | --------------------------------- |
| Anthropic Citations        | Agente → Usuário      | Mostrar a fonte da resposta             |
| OpenAI Citations           | Agente → Usuário      | Exibir fontes                   |
| Google Grounding           | Agente → Usuário      | Confirmação de busca na web           |
| **★ UAC (esta descoberta)** | **Agente → Agente** | **Reutilizar conteúdo entre chamadas** |

---

## 🧩 CINCO MECANISMOS CENTRAIS

### Mecanismo 1: 🔗 Área de Transferência Sintática

O modelo especifica apenas um **elemento âncora** — um nome de função, nome de classe ou variável. O sistema faz isso automaticamente:

1. Localiza este elemento na fonte especificada (arquivo, mensagem de chat, saída de comando)
2. Determina seus limites exatos como unidade sintática
3. Extrai a unidade inteira

**Economia:** alguns tokens pela referência em vez de milhares de tokens de código.

```
{ source: "file", path: "utils.ts", focus: "calculateSum" }
  → 2 tokens em vez de 800+ tokens de toda a função
```

---

### Mecanismo 2: 📇 Citação por Par de Âncoras

O modelo especifica apenas o **INÍCIO** e o **FIM** do fragmento desejado (15-40 caracteres cada). O sistema encontra tudo entre eles usando busca em múltiplos estágios:

1. **Correspondência exata** — fragmento encontrado literalmente (~70% dos casos)
2. **Correspondência normalizada** — diferenças de espaços, maiúsculas/minúsculas e pontuação ignoradas
3. **Correspondência aproximada** — pequenos erros de digitação tolerados (~9% dos casos)
4. **Expansão por limites de palavra** — integridade do fragmento

**Economia:** ~10 tokens por citação em vez de 200+.

```
{ source: "chat", ref: "-1",
  start: "function calculateSum(",
  end: "return result;" }
  → ~10 tokens em vez de 200+
```

---

### Mecanismo 3: 🧠 Mapa de Índice de Mensagens

Ao trabalhar com o histórico de chat, é criado um índice separado — um mapa de posições exatas de caracteres para cada mensagem e cada linha dentro dela. O modelo escreve uma referência curta como `"record_number:start_line..end_line"`, e o sistema extrai o fragmento exato pelas posições de caracteres.

**Vantagem-chave:** o modelo nunca vê o índice em si — apenas uma referência curta (~5 tokens), mas alcança 100% de precisão de extração.

```
{ source: "chat", ref: "167:14..18" }
  → "registro #167, linhas 14-18" → extração exata por posição de caracteres
```

---

### Mecanismo 4: 🔄 Pipeline de Transformação

Um fragmento copiado pode ser **modificado em tempo real** — antes de chegar à ferramenta. Operações disponíveis:

- **Substituir** — alterar uma substring dentro do fragmento
- **Adicionar antes** — inserir texto antes do fragmento
- **Envolver** — colocar o fragmento em um template
- **Adicionar depois** — acrescentar texto após o fragmento
- **Juntar** (para múltiplas referências) — mesclar fragmentos com um separador

Todas as operações são aplicadas em uma única chamada de ferramenta.

```
{ ref: { ... }, transform: { wrap: "try { {content} } catch (err) { }" } }
  → pegar uma função, envolvê-la em try-catch e escrever — tudo em 1 chamada
```

---

### Mecanismo 5: 🔁 Citação entre Protocolos (MCP)

Marcadores de referência podem ser embutidos diretamente dentro dos parâmetros de texto de quaisquer ferramentas, incluindo servidores MCP externos. O sistema reconhece automaticamente esses marcadores e substitui o conteúdo real antes de chamar o servidor externo.

**Resultado:** todos os componentes do ecossistema trocam dados por meio de um mecanismo de referência unificado, sem precisar mudar nada nos schemas dos servidores externos.

```
"{{ref:source=chat,ref=-1,start=export const config}} --host example.com"
  → 91% do conteúdo vem do contexto, 9% gerado pelo modelo
```

---

## 🔭 DIREÇÕES FUTURAS

As seguintes ideias são extensões naturais do conceito e podem ser implementadas no futuro:

### 🏖️ Sub-sessões Isoladas para Pesquisa

Para tarefas complexas que exigem muitas etapas intermediárias (exploração de codebase, leitura de logs, execução de testes), um agente auxiliar pode ser lançado em uma sub-sessão temporária isolada. Ele realiza todo o «trabalho sujo», retorna apenas o resultado limpo e, em seguida, a sub-sessão é destruída. O agente principal permanece focado na tarefa principal.

### Outras Direções

- Cache preditivo de fragmentos usados com frequência
- Detecção automática de chamadas duplicadas
- Desambiguação inteligente de referências ambíguas
- Integração com sistemas de memória e armazenamento de longo prazo

---

## 💰 IMPACTO ECONÔMICO

### Por Agente

| Métrica                           | Sem mecanismo | Com mecanismo | Economia    |
| -------------------------------- | ----------------- | -------------- | ---------- |
| Tokens por citação (código longo)  | 200-500           | 5-15           | **96-97%** |
| Tokens por citação (código curto) | 50-100            | 2-5            | **90-95%** |
| Tokens por sessão               | 25,000-50,000     | 5,000-15,000   | **60-80%** |
| Energia por sessão               | unidade arbitrária    | 5x menos        | **~80%**   |

### Escala Global

Quando adotada por toda a indústria, a economia chegará a bilhões de tokens por dia, o equivalente a reduzir o consumo de energia do setor de IA em dezenas de por cento e cortar a pegada de carbono em dezenas de milhares de toneladas de CO₂ por ano.

> **Universal AI Clipboard não é apenas uma inovação tecnológica — é uma solução de significância ecológica.**

---

## 🔬 VERIFICAÇÃO DE UNICIDADE

Conduzi uma **pesquisa profunda extensa em múltiplas rodadas** (7 rodadas, ~50 fontes) por meio de sistemas de busca na web (Tavily Search, profundidade avançada), cobrindo todas as categorias conhecidas de arquiteturas de agentes de IA:

*Após a publicação do manifesto, em análises adicionais (rodadas 8-10), descobriu-se que TJ Guadagno implementou de forma independente um protótipo experimental do conceito — Clipboard Primitives. Este trabalho não foi identificado nas primeiras 7 rodadas de busca devido à sua baixa visibilidade (LinkedIn Pulse + GitHub sem estrelas).*

- Área de transferência de agente de IA: copiar-colar entre chamadas de ferramenta
- Mecanismos de citação de conteúdo para agentes de IA
- Tecnologias de copiar-colar com custo zero de tokens
- Todas as APIs de citação conhecidas (Anthropic, OpenAI, Google, xAI, Azure)
- Reutilização e cache de saídas de chamadas de ferramenta (CAMEL-AI, LangChain artifacts)
- Protocolo MCP e compartilhamento de conteúdo entre protocolos
- Artigos acadêmicos (AgentReuse, KVCOMM, sistemas multi-agente)
- Utilitários de área de transferência para humanos (UiPath Clipboard AI, PowerToys Advanced Paste)
- Sistemas de compartilhamento de memória para arquiteturas multi-agente
- Discussões no GitHub, documentação de frameworks (LangChain, CrewAI, AutoGen, Mastra)

**Objetivo:** encontrar qualquer coisa que resolva o mesmo problema — permitir que um agente de IA referencie conteúdo existente entre chamadas de ferramenta em vez de regenerá-lo.

**Resultado: nada desse tipo foi encontrado.**
*Esclarecimento: o trabalho experimental de TJ Guadagno (Clipboard Primitives, ~dezembro de 2025) é uma implementação parcial (~40% do conceito da UAC) e confirma a viabilidade da ideia, mas não é um análogo completo.*

| Categoria                                    | Fontes                   | Por que NÃO é um análogo                                                                                                             |
| ------------------------------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **APIs de Citação (Anthropic/OpenAI/Google)** | APIs oficiais             | Mostram a fonte ao usuário, não permitem ao agente reutilizar conteúdo. Eixo: Agente → Usuário apenas                                                  |
| **Cache (Prompt, Semântico)**              | Vários frameworks        | Funciona no nível da requisição, não no nível do fragmento de conteúdo                                                                            |
| **RAG**                                     | LangChain, OpenAI, Google | Recupera de bases de conhecimento externas, não do contexto atual da sessão                                                         |
| **CAMEL-AI "Brainwash Your Agent"**         | camel-ai.org              | Armazena apenas a ÚLTIMA saída de ferramenta como referência + uma prévia curta. Sem os 5 mecanismos, sem pipeline de transformação, sem multi_ref, sem injeção MCP |
| **LangChain artifacts**                     | langchain.com             | `content_and_artifact` separa o conteúdo dos metadados, não é um sistema de citação. Sem referenciamento entre chamadas                                 |
| **Recursos MCP**                           | modelcontextprotocol.io   | Um padrão para conectar ferramentas, não um mecanismo de citação de agente para agente                                                             |
| **Acadêmico (AgentReuse, KVCOMM)**           | arXiv                     | Reutilização de PLANOS de execução ou KV-cache, não citação de conteúdo entre chamadas de ferramenta                                                         |
| **Ferramentas para humanos (UiPath, PowerToys)**         | UiPath, Microsoft         | Projetadas para interação humano-computador, não para agentes de IA                                                                            |
| **Agentes de IA existentes**                      | Indústria             | Possuem histórico, mas nenhum mecanismo de citação entre chamadas de ferramenta                                                                            |
| **Compartilhamento de memória multi-agente**              | Vários                   | Memória RAG compartilhada, não citação precisa em nível de caracteres                                                                               |

### Comparação com o parcial mais próximo (CAMEL-AI)

| Característica                                   | UAC      | Cache do CAMEL-AI | Diferença |
| ----------------------------------------- | -------- | ---------------- | ---------- |
| 🔗 Área de Transferência Sintática (blocos AST)       | ✅       | ❌               | Somente UAC   |
| 📇 Citação por Par de Âncoras                   | ✅       | ❌               | Somente UAC   |
| 🧠 Mapa de Índice de Mensagens                      | ✅       | ❌               | Somente UAC   |
| 🔄 Pipeline de Transformação                     | ✅       | ❌               | Somente UAC   |
| 🔁 Citação entre Protocolos (MCP)          | ✅       | ❌               | Somente UAC   |
| 🧩 Montagem em Mosaico (multi-fonte)         | ✅       | ❌               | Somente UAC   |
| 📋 Gerenciador de Área de Transferência (slots nomeados)        | ✅       | ❌               | Somente UAC   |
| {{ref:...}} Injeção Inline              | ✅       | ❌               | Somente UAC   |
| Cache da saída de ferramenta (referência + prévia) | ✅       | ✅               | Ambos       |
| Cobertura das funcionalidades da UAC                  | **100%** | **~5%**          | —          |

> **Universal AI Clipboard não tem análogos completos na prática dos sistemas de agentes de IA no mundo inteiro. Esta é uma tecnologia pioneira criando uma nova categoria. A única implementação parcial conhecida — Clipboard Primitives (TJ Guadagno, ~40% do conceito) — foi descoberta apenas após a publicação do manifesto e confirma o surgimento independente da ideia entre diferentes pesquisadores.**

---

## 📖 EXEMPLOS DE USO

### Exemplo 1: Reexecutar um comando com parâmetros extras

Um agente executou um comando de teste; a saída mostrou um erro. Para reexecutar com flags de debug, o agente não reescreve o comando — ele o referencia e adiciona flags:

```
{ ref: { source: "terminal", id: "cmd-xxx", start: "npx vitest" },
  transform: { append: " --verbose --timeout=30000" } }
  → resultado: "npx vitest run --verbose --timeout=30000"
```

### Exemplo 2: Montar várias funções em um arquivo

Um agente lê um arquivo com várias funções e, em seguida, cria um novo arquivo montando as funções necessárias por meio de referências:

```
{ multi_ref: [
    { source: "file", path: "handlers.ts", start: "async function validate(", end: "}" },
    { source: "file", path: "handlers.ts", start: "async function process(", end: "}" },
    { source: "file", path: "handlers.ts", start: "async function respond(", end: "}" }
  ],
  transform: { join: "\n\n", prepend: "// --- Handlers ---\n" } }
  → três funções mescladas em um arquivo em 1 chamada
```

### Exemplo 3: Substituição de configuração via MCP

Um agente usa uma ferramenta MCP externa, passando uma referência à configuração do chat em seus argumentos:

```
"{{ref:source=chat,ref=-1,start=export const config}} --host production"
  → configuração do chat substituída na requisição MCP
```

---

## ⚖️ STATUS LEGAL

**🏛️ Creative Commons Zero (CC0) — Dedicação Universal ao Domínio Público**

Você é livre para:

- ✅ **Usar** em projetos comerciais e não comerciais
- ✅ **Modificar** e adaptar para suas necessidades
- ✅ **Distribuir** em qualquer forma
- ✅ **Patentear suas melhorias** (mas não a ideia central)
- ✅ **Traduzir** para qualquer idioma

Sem nenhuma obrigação, royalties ou restrições.

> **Eu renuncio conscientemente a todos os direitos de patente sobre esta tecnologia. Ela deve pertencer a todos.**

---

## 📜 PROVA DA DATA DE DESCOBERTA

A data de publicação deste manifesto está registrada **pelo sistema de controle de versões Git no repositório do GitHub** — [github.com/DScoNOIZ/UNIVERSAL-AI-CLIPBOARD](https://github.com/DScoNOIZ/UNIVERSAL-AI-CLIPBOARD).

O histórico de commits, as datas de edição e todas as mudanças cronológicas são **preservados de forma imutável pelo GitHub** e servem como prova pública da data de descoberta e da autoria. A tecnologia do Git torna isso praticamente impossível de falsificar.

---

## 🗓️ CRONOLOGIA

| Data                | Evento                                                                    |
| ------------------- | ------------------------------------------------------------------------ |
| **~2021**         | Primeira percepção do problema (DScoNOIZ): pensamento «o modelo não deveria regenerar o que já viu»                                         |
| **~dezembro de 2025** | **Experimento independente:** TJ Guadagno publica Clipboard Primitives — `copy`/`template_invoke` com slots nomeados e placeholders `{{slot}}`     |
| **Maio – junho de 2026** | Pesquisa: análise das arquiteturas de agentes de IA existentes                                                                                             |
| **junho de 2026**       | Descoberta: nenhuma tecnologia existente possui um análogo completo                                                                                        |
| **junho de 2026**       | Conceito de Universal AI Clipboard formulado                                                                                                        |
| **3 de junho de 2026**    | Pesquisa de unicidade concluída — **nenhum análogo completo encontrado**                                                                                   |
| **3 de junho de 2026**    | **Este manifesto publicado** — descoberta liberada em domínio público                                                                          |
| **4 de junho de 2026**    | Trabalho de TJ Guadagno descoberto — reconhecimento do co-descobridor independente                                                                       |

---

## 🎯 CHAMADO À AÇÃO

### Desenvolvedores de Frameworks de IA

Integrem o mecanismo de Referência de Conteúdo em suas ferramentas. Ofereçam aos seus usuários economia instantânea de tokens sem alterar o código deles.

### Criadores de Agentes de IA

Adicionem a citação opcional entre chamadas de ferramenta. Seus agentes se tornarão ordens de grandeza mais eficientes.

### Pesquisadores

Façam a tecnologia avançar: aprimorem os algoritmos de busca, implementem cache preditivo, desenvolvam novos cenários.

### Negócios

Adotem o Universal AI Clipboard em suas soluções de IA. Reduzam custos operacionais em dezenas de por cento.

### Ambientalistas

Usem a UAC como uma ferramenta para reduzir a pegada de carbono da infraestrutura de IA.

### Comunidade Open Source

Fork, implementem, melhorem. **Esta tecnologia pertence a todos.**

---

## 🏛️ PALAVRA FINAL

Eu descobri o **Universal AI Clipboard** — um mecanismo que permite aos agentes de IA reutilizar conteúdo em vez de regenerá-lo.

Isto não é apenas uma otimização. É uma **mudança de paradigma**: o modelo deixa de ser um «gerador de texto» e se torna um **montador** que constrói soluções a partir de fragmentos prontos.

**Assim como Ctrl+C / Ctrl+V mudaram o mundo dos computadores, o Universal AI Clipboard mudará o mundo dos agentes de IA.**

Eu entrego esta ideia à humanidade. Desenvolvam-na. Aprimorem-na. Implementem-na.

**Que os agentes de IA parem de reescrever a mesma coisa repetidamente.**
**Que eles comecem a montar mosaicos.**

---

```
  ╔══════════════════════════════════════════════════════════════════╗
  ║                                                                  ║
  ║   UNIVERSAL AI CLIPBOARD (UAC)                                   ║
  ║   Mecanismo de Referência de Conteúdo                             ║
  ║   Mecanismo Opcional de Citação de Conteúdo entre Ferramentas      ║
  ║                                                                  ║
  ║   «Reutilize, não regenere»                                      ║
  ║                                                                  ║
  ║   CC0 1.0 Universal — Domínio Público                             ║
  ║   github.com/DScoNOIZ                                            ║
  ║   3 de junho de 2026                                              ║
  ║                                                                  ║
  ╚══════════════════════════════════════════════════════════════════╝
```

---

_Este manifesto pode ser traduzido livremente para qualquer idioma. Original em russo._

_Versão em russo: [MANIFEST-RU.md](MANIFEST-RU.md)_
