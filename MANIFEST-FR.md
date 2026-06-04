# 🏛️ UNIVERSAL AI CLIPBOARD (UAC)

## Le Presse-papiers Universel pour l'Intelligence Artificielle

### Un Mécanisme de Réutilisation de Contenu pour les Agents IA

---

> **Date de publication :** 3 juin 2026
> **Statut :** ⚡ Découverte dans le domaine public
> **Licence :** CC0 1.0 Universelle — Dédicace au Domaine Public

---

## 📜 DÉCLARATION DU DÉCOUVREUR

Moi, **[DScoNOIZ](https://github.com/DScoNOIZ)**, déclare devant la communauté mondiale :

**1. Je suis le découvreur** d'une catégorie fondamentalement nouvelle dans l'architecture des agents IA — le **« Mécanisme Optionnel de Citation de Contenu entre Appels d'Outils »** (Optional Inter-Tool Content Citation Mechanism), nommé **Universal AI Clipboard (UAC)**.

**2. L'essence de la découverte :** Un agent IA peut référencer du contenu contextuel existant via des paramètres dédiés (`ref`, `multi_ref`, `transform`) au lieu de le régénérer. Le modèle cesse d'être un simple « générateur de texte » et devient un **assembleur** qui combine des fragments d'information prêts à l'emploi en un seul appel.

**3. Je libère cette découverte en libre usage pour toute la communauté mondiale** sous licence Creative Commons Zero (CC0) — sans brevets, redevances, licences fermées ni restrictions.

**4. J'appelle** les développeurs, chercheurs, ingénieurs et passionnés du monde entier — prenez cette idée, implémentez-la dans vos frameworks, plateformes et outils. **Cette technologie ne m'appartient pas. Elle appartient à tous.**

---

## 🤝 CODÉCOUVREUR : DÉCOUVERTE INDÉPENDANTE

Je reconnais et respecte que **TJ Guadagno** (TJ-Codes) est arrivé indépendamment à la même idée fondamentale et l'a implémentée expérimentalement sous le nom de **Clipboard Primitives** — un mécanisme `copy`/`template_invoke` avec des emplacements nommés et des espaces réservés `{{slot}}` pour les agents IA.

**Son travail :** [Copy and Paste for AI Agents: An Experimental Primitive](https://www.linkedin.com/pulse/copy-paste-ai-agents-experimental-primitive-tj-guadagno-v3r9c) (~décembre 2025)
**Code :** [github.com/TJ-Codes/Agent-clipboard](https://github.com/TJ-Codes/Agent-clipboard)

TJ Guadagno est un **codécouvreur indépendant** de ce concept. Son expérience a confirmé que :
- Les modèles **adoptent naturellement** la sémantique du presse-papiers sans formation spéciale
- Les primitives de presse-papiers **éliminent** la régénération de tokens, la latence et les risques de mutation du contenu
- Le mécanisme nécessite une **intégration au niveau du harness**, pas au niveau du serveur MCP

**Mon concept d'Universal AI Clipboard est plus large et plus universel** — il inclut Clipboard Primitives comme cas particulier et étend l'idée à :
- **5 mécanismes de citation** (incluant le presse-papiers syntaxique via AST, l'index de messages, la citation par paire d'ancres)
- **Presse-papiers universel pour toutes les sources** (fichiers, chat, terminal, API, MCP)
- **Assemblage en mosaïque** — combinaison de fragments de différentes sources avec transformations
- **Citation inter-protocole** — citation transparente à travers tout protocole, y compris MCP

**Analogie informatique :** Clipboard Primitives est comme un utilitaire de copie simple pour une application. Universal AI Clipboard est un gestionnaire de presse-papiers système complet fonctionnant à travers toutes les applications, avec gestion des emplacements, pipeline de transformation et intégration inter-protocole.

> **Je ne renonce pas à mon statut de découvreur.** J'ai formulé et systématisé ce concept indépendamment, en menant des recherches multi-niveaux qui n'ont trouvé aucun analogue complet. Ayant découvert le travail de TJ Guadagno seulement après la publication du manifeste, je reconnais sa contribution indépendante et considère qu'il est de mon devoir de refléter cela dans le manifeste.

---

## 🏛️ NOM

**Nom officiel :** **UNIVERSAL AI CLIPBOARD (UAC)**
**Nom technique :** Mécanisme de Référence de Contenu
**Slogan :** _« Reuse, Don't Regenerate »_ — _« Réutilisez, ne régénérez pas »_
**Métaphore :** Ctrl+C / Ctrl+V pour les Agents IA

---

## 🌍 LE PROBLÈME

### La Contradiction Fondamentale

Les agents IA modernes gaspillent **jusqu'à 90% de leur trafic de sortie** en régénérant de manière monotone du contenu qui existe déjà dans le contexte de la session.

Chaque fois qu'un modèle écrit une commande, un bloc de code ou un fragment de texte — il le régénère à partir de zéro, même si le même contenu a été créé une minute auparavant. Le modèle n'a aucun moyen de référencer instrumentalement du contenu déjà existant.

### Échelle Globale du Problème

- Des millions d'agents IA opèrent quotidiennement dans le monde
- Chacun effectue des dizaines d'appels d'outils par session
- Une partie significative de chaque appel est une régénération de contenu existant
- Cela entraîne une énorme consommation d'énergie, un gaspillage informatique et des coûts financiers

### Pourquoi les Approches Existantes ne Résolvent Pas ce Problème

| Approche | Limitation |
| ----------------------- | --------------------------------------------------------------- |
| **Mise en cache des prompts** | Fonctionne seulement avec les parties statiques, pas le contenu dynamique |
| **Mise en cache sémantique** | Met en cache par sens de requête, ne permet pas la citation de fragments |
| **Compression de contexte** | Compresse l'historique, mais ne fournit pas d'outil de citation |
| **RAG** | Récupère depuis des sources externes, ne réutilise pas le contexte interne |
| **Chaînage d'outils** | Enchaîne les appels, mais ne permet pas de référencer leurs résultats |

---

## 💡 LA SOLUTION : UNIVERSAL AI CLIPBOARD

### L'Idée Centrale

Un agent IA obtient la capacité de **référencer du contenu contextuel déjà existant** au lieu de le régénérer. Lors de l'appel de tout outil qui accepte des paramètres textuels (commandes, code, texte), l'agent peut spécifier : « prends ce fragment de là » — au lieu de l'écrire à partir de zéro.

### Assemblage en Mosaïque : Composer l'Information Comme un Puzzle

Au-delà de la citation simple, ce concept permet une manière fondamentalement nouvelle de composer l'information — **l'assemblage en mosaïque**.

Un agent peut **combiner plusieurs fragments de différentes sources** en une seule opération :

- Code d'un fichier
- Configuration de l'historique de chat
- Sortie de commande du terminal
- Résultats d'API externes

L'agent peut **modifier à la volée** — modifier, envelopper, remplacer le texte dans chaque fragment. Il peut **réorganiser** les fragments, **imbriquer** l'un dans l'autre, **fusionner** les parties qui se chevauchent et **restructurer** le contenu récursivement.

**L'idée clé :** au lieu de générer un nouveau texte, le modèle agit comme un **éditeur et conservateur** du contenu existant — considérablement plus efficace, plus précis et moins sujet aux erreurs.

### Gestionnaire de Presse-papiers : Emplacements Nommés pour le Stockage

Une extension naturelle de ce concept est un **gestionnaire de presse-papiers avec des emplacements nommés**.

L'agent peut :
- **Enregistrer des fragments** dans des emplacements nommés (`clip-1`, `clip-2`, `config-block`, `error-log`, etc.)
- **Référencer les emplacements par nom** — zéro tokens dépensés pour la description
- **Échanger et réorganiser** le contenu entre les emplacements
- **Construire des documents composites** en référençant plusieurs emplacements
- **Conserver les fragments entre les sessions** — survivent à la compression de contexte et aux redémarrages

### La Différence Axiale par Rapport aux Mécanismes Existants

Tous les mécanismes de citation existants en IA (Citations API, Grounding, ContextCite) fonctionnent sur l'axe **« agent → utilisateur »** — ils montrent à l'humain où l'agent a trouvé l'information.

Universal AI Clipboard fonctionne sur l'axe **« agent → agent »** — il permet à l'agent lui-même de réutiliser le contenu entre ses propres appels d'outils. C'est une catégorie fondamentalement nouvelle.

| Mécanisme | Axe | Objectif |
| -------------------------- | ----------------- | --------------------------------------------- |
| Anthropic Citations | Agent → Utilisateur | Montrer la source de la réponse |
| OpenAI Citations | Agent → Utilisateur | Afficher les sources |
| Google Grounding | Agent → Utilisateur | Confirmation de recherche web |
| **★ UAC (cette découverte)** | **Agent → Agent** | **Réutilisation du contenu entre appels** |

---

## 🧩 CINQ MÉCANISMES CLÉS

### Mécanisme 1 : 🔗 Presse-papiers Syntaxique

Le modèle spécifie un seul **élément d'ancrage** — un nom de fonction, de classe ou de variable. Le système automatiquement :
1. Trouve cet élément dans la source spécifiée (fichier, message de chat, sortie de commande)
2. Détermine ses limites exactes en tant qu'unité syntaxique
3. Extrait l'unité entière

**Économie :** quelques tokens pour la référence au lieu de milliers de tokens de code.

```
{ source: "fichier", chemin: "utils.ts", focus: "calculateSum" }
  → 2 tokens au lieu de 800+ tokens de toute la fonction
```

### Mécanisme 2 : 📇 Citation par Paire d'Ancres

Le modèle spécifie seulement le **DÉBUT** et la **FIN** du fragment désiré (15-40 caractères chacun). Le système trouve tout ce qui se trouve entre les deux en utilisant une recherche multi-étapes :

1. **Correspondance exacte** — fragment trouvé littéralement (~70% des cas)
2. **Correspondance normalisée** — différences d'espaces, de casse et de ponctuation ignorées
3. **Correspondance floue** — petites fautes de frappe tolérées (~9% des cas)
4. **Expansion aux limites des mots** — intégrité du fragment

```
{ source: "chat", ref: "-1",
  début: "function calculateSum(",
  fin: "return result;" }
  → ~10 tokens au lieu de 200+
```

### Mécanisme 3 : 🧠 Carte d'Index de Messages

Lors du travail avec l'historique de chat, un index séparé est créé — une carte des positions exactes des caractères pour chaque message et chaque ligne à l'intérieur. Le modèle écrit une courte référence comme `"numéro_enregistrement:ligne_début..ligne_fin"`, et le système extrait le fragment exact par positions de caractères.

```
{ source: "chat", ref: "167:14..18" }
  → "enregistrement #167, lignes 14-18" → extraction exacte
```

### Mécanisme 4 : 🔄 Pipeline de Transformation

Un fragment copié peut être **modifié à la volée** — avant d'atteindre l'outil. Opérations disponibles :

- **Remplacer** — changer une sous-chaîne dans le fragment
- **Préfixer** — ajouter du texte avant le fragment
- **Envelopper** — placer le fragment dans un modèle
- **Ajouter** — ajouter du texte après le fragment
- **Joindre** (pour plusieurs références) — fusionner des fragments avec un séparateur

```
{ ref: { ... }, transform: { wrap: "try { {content} } catch (err) { }" } }
  → prendre une fonction, l'envelopper dans try-catch, écrire — tout en 1 appel
```

### Mécanisme 5 : 🔁 Citation Inter-Protocole (MCP)

Des marqueurs de référence peuvent être intégrés directement à l'intérieur des paramètres textuels de tous les outils, y compris les serveurs MCP externes. Le système reconnaît automatiquement ces marqueurs et substitue le contenu réel avant d'appeler le serveur externe.

```
"{{ref:source=chat,ref=-1,début=export const config}} --host production"
  → 91% de contenu du contexte, 9% généré par le modèle
```

---

## 🔭 DIRECTIONS FUTURES

### 🏖️ Sous-sessions Isolées pour la Recherche

Pour les tâches complexes nécessitant de nombreuses étapes intermédiaires, un agent auxiliaire peut être lancé dans une sous-session temporaire isolée. Il effectue tout le « sale boulot », ne retourne que le résultat propre, puis la sous-session est détruite.

### Autres Directions

- Mise en cache prédictive des fragments fréquemment utilisés
- Détection automatique des appels en double
- Désambiguïsation intelligente des références ambiguës
- Intégration avec les systèmes de mémoire et de stockage à long terme

---

## 💰 IMPACT ÉCONOMIQUE

### Par Agent

| Métrique | Sans mécanisme | Avec mécanisme | Économie |
| -------------------------------- | ---------------- | -------------- | ---------- |
| Tokens par citation (code long) | 200-500 | 5-15 | **96-97%** |
| Tokens par citation (code court) | 50-100 | 2-5 | **90-95%** |
| Tokens par session | 25 000-50 000 | 5 000-15 000 | **60-80%** |
| Énergie par session | unité arbitraire | 5× moins | **~80%** |

### À l'Échelle Globale

Lorsqu'adoptée à l'échelle de l'industrie, l'économie atteindra des milliards de tokens quotidiennement, équivalant à réduire la consommation énergétique du secteur IA de dizaines de pour cent et à diminuer l'empreinte carbone de dizaines de milliers de tonnes de CO₂ par an.

---

## 🔬 VÉRIFICATION D'UNICITÉ

J'ai mené **des recherches approfondies multi-niveaux** (7 rounds, ~50 sources) via des systèmes de recherche web (Tavily Search, advanced depth) couvrant toutes les catégories connues d'architectures d'agents IA.

*Après la publication du manifeste, lors d'analyses supplémentaires (rounds 8-10), il a été découvert que TJ Guadagno avait indépendamment implémenté un prototype expérimental du concept — Clipboard Primitives. Ce travail n'a pas été identifié lors des 7 premiers rounds de recherche en raison de sa faible visibilité (LinkedIn Pulse + GitHub sans étoiles).*

**Objectif :** trouver quoi que ce soit qui résout le même problème — permettre à un agent IA de référencer du contenu existant entre des appels d'outils au lieu de le régénérer.

**Résultat : rien de tel n'a été trouvé.**
*Précision : le travail expérimental de TJ Guadagno (Clipboard Primitives, ~décembre 2025) est une implémentation partielle (~40% du concept UAC) et confirme la viabilité de l'idée, mais n'est pas un analogue complet.*

| Catégorie | Sources | Pourquoi ce n'est PAS un analogue |
| --------------------------------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **API de citation (Anthropic/OpenAI/Google)** | APIs officielles | Montrent la source à l'utilisateur, ne permettent pas à l'agent de réutiliser. Axe : Agent → Utilisateur uniquement |
| **Mise en cache (Prompt, Sémantique)** | Divers frameworks | Fonctionne au niveau des requêtes, pas au niveau des fragments de contenu |
| **RAG** | LangChain, OpenAI, Google | Récupère depuis des bases de connaissances externes, pas depuis le contexte de session actuel |
| **CAMEL-AI "Brainwash Your Agent"** | camel-ai.org | Stocke seulement la DERNIÈRE sortie d'outil comme référence. Pas de 5 mécanismes, pas de pipeline de transformation |
| **LangChain artifacts** | langchain.com | `content_and_artifact` sépare contenu et métadonnées, pas un système de citation |
| **MCP Resources** | modelcontextprotocol.io | Un standard pour connecter des outils, pas un mécanisme de citation agent→agent |
| **Académique (AgentReuse, KVCOMM)** | arXiv | Réutilisation de PLANS ou KV-cache, pas de citation de contenu |
| **Outils humains (UiPath, PowerToys)** | UiPath, Microsoft | Conçus pour l'interaction homme-machine, pas pour les agents IA |
| **Agents IA existants** | Industrie en général | Ont un historique, mais pas de mécanisme de citation entre appels d'outils |
| **Mémoire partagée multi-agent** | Divers | Mémoire RAG partagée, pas de citation précise au niveau des caractères |

> **Universal AI Clipboard n'a pas d'analogues complets dans la pratique mondiale des systèmes d'agents IA. La seule implémentation partielle connue — Clipboard Primitives (TJ Guadagno, ~40% du concept) — a été découverte seulement après la publication du manifeste et confirme l'émergence indépendante de l'idée.**

---

## ⚖️ STATUT JURIDIQUE

**🏛️ Creative Commons Zero (CC0) — Dédicace Universelle au Domaine Public**

Vous êtes libre de :
- ✅ **Utiliser** dans des projets commerciaux et non commerciaux
- ✅ **Modifier** et adapter à vos besoins
- ✅ **Distribuer** sous toute forme
- ✅ **Brevetter vos améliorations** (mais pas l'idée centrale)
- ✅ **Traduire** dans n'importe quelle langue

Sans aucune obligation, redevance ou restriction.

> **Je renonce consciemment à tous droits de brevet sur cette technologie. Elle doit appartenir à tous.**

---

## 📜 PREUVE DE LA DATE DE DÉCOUVERTE

La date de publication de ce manifeste est enregistrée **par le système de contrôle de version Git dans le dépôt GitHub** — [github.com/DScoNOIZ/UNIVERSAL-AI-CLIPBOARD](https://github.com/DScoNOIZ/UNIVERSAL-AI-CLIPBOARD).

L'historique des commits, les dates d'édition et tous les changements chronologiques sont **immuablement préservés par GitHub** et servent de preuve publique de la date de découverte et de la paternité.

---

## 🗓️ CHRONOLOGIE

| Date | Événement |
| ------------------- | ------------------------------------------------------------------------ |
| **~2021** | Première prise de conscience du problème (DScoNOIZ) |
| **~décembre 2025** | **Expérience indépendante :** TJ Guadagno publie Clipboard Primitives |
| **Mai — juin 2026** | Recherche : analyse des architectures d'agents IA existantes |
| **Juin 2026** | Découverte : aucune technologie existante n'a d'analogue complet |
| **Juin 2026** | Concept Universal AI Clipboard formulé |
| **3 juin 2026** | Recherche d'unicité terminée — **aucun analogue complet trouvé** |
| **3 juin 2026** | **Ce manifeste publié** — découverte dans le domaine public |
| **4 juin 2026** | Travail de TJ Guadagno découvert — reconnaissance du codécouvreur |

---

## 🎯 APPEL À L'ACTION

Développeurs de frameworks IA, créateurs d'agents IA, chercheurs, entreprises, écologistes, communauté open source — **cette technologie appartient à tous. Forkez, implémentez, améliorez-la.**

---

```
  ╔══════════════════════════════════════════════════════════════════╗
  ║                                                                  ║
  ║   UNIVERSAL AI CLIPBOARD (UAC)                                   ║
  ║   Content Reference Mechanism                                    ║
  ║   Optional Inter-Tool Content Citation Mechanism                 ║
  ║                                                                  ║
  ║   «Reuse, Don't Regenerate»                                      ║
  ║   «Réutilisez, ne régénérez pas»                                 ║
  ║                                                                  ║
  ║   CC0 1.0 Universal — Domaine Public                             ║
  ║   github.com/DScoNOIZ                                            ║
  ║   3 juin 2026                                                    ║
  ║                                                                  ║
  ╚══════════════════════════════════════════════════════════════════╝
```

---

_Ce manifeste peut être librement traduit dans n'importe quelle langue. Original en russe._

_Version anglaise : [MANIFEST.md](MANIFEST.md)_
