# 🏛️ UNIVERSAL AI CLIPBOARD (UAC)

## El Portapapeles Universal para la Inteligencia Artificial

### Un Mecanismo de Reutilización de Contenido para Agentes de IA

---

> **Fecha de publicación:** 3 de junio de 2026
> **Estado:** ⚡ Descubrimiento en dominio público
> **Licencia:** CC0 1.0 Dedicación Universal al Dominio Público

---

## 📜 DECLARACIÓN DEL DESCUBRIDOR

Yo, **[DScoNOIZ](https://github.com/DScoNOIZ)**, declaro ante la comunidad global:

**1. Soy el descubridor** de una categoría fundamentalmente nueva en la arquitectura de agentes de IA — el **«Mecanismo Opcional de Citación de Contenido entre Llamadas a Herramientas»** (Optional Inter-Tool Content Citation Mechanism), denominado **Universal AI Clipboard (UAC)**.

**2. La esencia del descubrimiento:** Un agente de IA puede referenciar contenido contextual existente mediante parámetros dedicados (`ref`, `multi_ref`, `transform`) en lugar de regenerarlo. El modelo deja de ser solo un «generador de texto» y se convierte en un **ensamblador** que combina fragmentos de información listos en una sola llamada.

**3. Libero este descubrimiento para uso gratuito de toda la comunidad global** bajo licencia Creative Commons Zero (CC0) — sin patentes, regalías, licencias cerradas ni restricciones.

**4. Hago un llamado** a desarrolladores, investigadores, ingenieros y entusiastas de todo el mundo — tomen esta idea, impleméntenla en sus frameworks, plataformas y herramientas. **Esta tecnología no me pertenece. Pertenece a todos.**

---

## 🤝 CODESCUBRIDOR: DESCUBRIMIENTO INDEPENDIENTE

Reconozco y respeto que **TJ Guadagno** (TJ-Codes) llegó independientemente a la misma idea fundamental y la implementó experimentalmente como **Clipboard Primitives** — un mecanismo `copy`/`template_invoke` con slots nombrados y marcadores `{{slot}}` para agentes de IA.

**Su trabajo:** [Copy and Paste for AI Agents: An Experimental Primitive](https://www.linkedin.com/pulse/copy-paste-ai-agents-experimental-primitive-tj-guadagno-v3r9c) (~diciembre 2025)
**Código:** [github.com/TJ-Codes/Agent-clipboard](https://github.com/TJ-Codes/Agent-clipboard)

TJ Guadagno es un **codescubridor independiente** de este concepto. Su experimento confirmó que:
- Los modelos **adoptan naturalmente** la semántica del portapapeles sin entrenamiento especial
- Las primitivas de portapapeles **eliminan** la regeneración de tokens, la latencia y los riesgos de mutación de contenido
- El mecanismo requiere **integración a nivel de harness**, no a nivel de servidor MCP

**Mi concepto de Universal AI Clipboard es más amplio y universal** — incluye Clipboard Primitives como un caso especial y extiende la idea a:
- **5 mecanismos de citación** (incluyendo portapapeles sintáctico vía AST, índice de mensajes, citación por par de anclas)
- **Portapapeles universal para cualquier fuente** (archivos, chat, terminal, API, MCP)
- **Ensamblaje de mosaico** — combinación de fragmentos de diferentes fuentes con transformaciones
- **Citación entre protocolos** — citación fluida a través de cualquier protocolo, incluyendo MCP

**Analogía informática:** Clipboard Primitives es como una utilidad de copia simple para una aplicación. Universal AI Clipboard es un gestor de portapapeles completo de todo el sistema, con gestión de slots, pipeline de transformación e integración entre protocolos.

> **No renuncio a mi estatus como descubridor.** Formulé y sistematicé este concepto independientemente, realizando investigaciones multi-ronda que no encontraron análogos completos. Habiendo conocido el trabajo de TJ Guadagno solo después de publicar el manifiesto, reconozco su contribución independiente y considero mi deber reflejar esto en el manifiesto.

---

## 🏛️ NOMBRE

**Nombre oficial:** **UNIVERSAL AI CLIPBOARD (UAC)**
**Nombre técnico:** Mecanismo de Referencia de Contenido
**Lema:** _«Reuse, Don't Regenerate»_ — _«Reutiliza, no regeneres»_
**Metáfora:** Ctrl+C / Ctrl+V para Agentes de IA

---

## 🌍 EL PROBLEMA

### La Contradicción Fundamental

Los agentes de IA modernos desperdician **hasta el 90% de su tráfico de salida** regenerando monótonamente contenido que ya existe en el contexto de la sesión.

Cada vez que un modelo escribe un comando, un bloque de código o un fragmento de texto — lo regenera desde cero, incluso si el mismo contenido fue creado hace un minuto. El modelo no tiene forma de referenciar instrumentalmente el contenido ya existente.

### Escala Global del Problema

- Millones de agentes de IA operan diariamente en todo el mundo
- Cada uno realiza docenas de llamadas a herramientas por sesión
- Una parte significativa de cada llamada es regeneración de contenido existente
- Esto genera un enorme consumo de energía, desperdicio computacional y costos financieros

### Por Qué los Enfoques Existentes No Resuelven Esto

| Enfoque | Limitación |
| ----------------------- | --------------------------------------------------------------- |
| **Caché de prompts** | Funciona solo con partes estáticas, no con contenido dinámico |
| **Caché semántico** | Almacena por significado de consulta, no permite citar fragmentos |
| **Compresión de contexto** | Comprime el historial, pero no proporciona una herramienta de citación |
| **RAG** | Recupera de fuentes externas, no reutiliza el contexto interno |
| **Encadenamiento de herramientas** | Conecta llamadas, pero no permite referenciar sus resultados |

---

## 💡 LA SOLUCIÓN: UNIVERSAL AI CLIPBOARD

### La Idea Central

Un agente de IA obtiene la capacidad de **referenciar contenido contextual ya existente** en lugar de regenerarlo. Al llamar a cualquier herramienta que acepte parámetros de texto (comandos, código, texto), el agente puede especificar: «toma este fragmento de allí» — en lugar de escribirlo desde cero.

### Ensamblaje de Mosaico: Componer Información como un Rompecabezas

Más allá de la citación simple uno a uno, este concepto permite una forma fundamentalmente nueva de componer información — **ensamblaje de mosaico**.

Un agente puede **combinar múltiples fragmentos de diferentes fuentes** en una sola operación:

- Código de un archivo
- Configuración del historial de chat
- Salida de comandos del terminal
- Resultados de APIs externas

El agente puede **editar sobre la marcha** — modificar, envolver, reemplazar texto dentro de cada fragmento. Puede **reordenar** fragmentos, **anidar** uno dentro de otro, **fusionar** partes superpuestas y **reestructurar** contenido recursivamente.

**La idea clave:** en lugar de generar nuevo texto, el modelo actúa como un **editor y curador** del contenido existente — mucho más eficiente, preciso y con menos errores.

### Gestor de Portapapeles: Slots Nombrados para Almacenamiento

Una extensión natural de este concepto es un **gestor de portapapeles con slots nombrados**.

El agente puede:
- **Guardar fragmentos** en slots con nombre (`clip-1`, `clip-2`, `config-block`, `error-log`, etc.)
- **Referenciar slots por nombre** — cero tokens gastados en descripción
- **Intercambiar y reorganizar** contenido entre slots
- **Construir documentos compuestos** referenciando múltiples slots
- **Persistir fragmentos entre sesiones** — sobreviven a la compresión de contexto y reinicios

### Diferencia Axial con Mecanismos Existentes

Todos los mecanismos de citación existentes en IA (Citations API, Grounding, ContextCite) operan en el eje **«agente → usuario»** — muestran al humano dónde el agente obtuvo la información.

Universal AI Clipboard opera en el eje **«agente → agente»** — permite al propio agente reutilizar contenido entre sus propias llamadas a herramientas. Esta es una categoría fundamentalmente nueva.

| Mecanismo | Eje | Propósito |
| -------------------------- | ----------------- | --------------------------------- |
| Anthropic Citations | Agente → Usuario | Mostrar fuente de respuesta |
| OpenAI Citations | Agente → Usuario | Mostrar fuentes |
| Google Grounding | Agente → Usuario | Confirmación de búsqueda web |
| **★ UAC (este descubrimiento)** | **Agente → Agente** | **Reutilizar contenido entre llamadas** |

---

## 🧩 CINCO MECANISMOS CLAVE

### Mecanismo 1: 🔗 Portapapeles Sintáctico

El modelo especifica solo un **elemento ancla** — un nombre de función, clase o variable. El sistema automáticamente:
1. Encuentra este elemento en la fuente especificada (archivo, mensaje de chat, salida de comando)
2. Determina sus límites exactos como unidad sintáctica
3. Extrae la unidad completa

**Ahorro:** unos pocos tokens para la referencia en lugar de miles de tokens de código.

```
{ source: "file", path: "utils.ts", focus: "calculateSum" }
  → 2 tokens en lugar de 800+ tokens de toda la función
```

### Mecanismo 2: 📇 Citación por Par de Anclas

El modelo especifica solo el **INICIO** y el **FIN** del fragmento deseado (15-40 caracteres cada uno). El sistema encuentra todo lo intermedio mediante búsqueda multietapa:

1. **Coincidencia exacta** — fragmento encontrado literalmente (~70% de los casos)
2. **Coincidencia normalizada** — diferencias de espacios, mayúsculas y puntuación ignoradas
3. **Coincidencia difusa** — pequeños errores tipográficos tolerados (~9% de los casos)
4. **Expansión a límites de palabras** — integridad del fragmento

```
{ source: "chat", ref: "-1",
  inicio: "function calculateSum(",
  fin: "return result;" }
  → ~10 tokens en lugar de 200+
```

### Mecanismo 3: 🧠 Mapa de Índice de Mensajes

Al trabajar con el historial de chat, se crea un índice separado — un mapa de posiciones exactas de caracteres para cada mensaje y cada línea dentro de él. El modelo escribe una referencia corta como `"número_registro:línea_inicio..línea_fin"`, y el sistema extrae el fragmento exacto por posiciones de caracteres.

```
{ source: "chat", ref: "167:14..18" }
  → "registro #167, líneas 14-18" → extracción exacta
```

### Mecanismo 4: 🔄 Tubería de Transformación

Un fragmento copiado puede **modificarse sobre la marcha** — antes de llegar a la herramienta. Operaciones disponibles:

- **Reemplazar** — cambiar una subcadena dentro del fragmento
- **Anteponer** — añadir texto antes del fragmento
- **Envolver** — colocar el fragmento en una plantilla
- **Añadir** — añadir texto después del fragmento
- **Unir** (para múltiples referencias) — fusionar fragmentos con un separador

```
{ ref: { ... }, transform: { wrap: "try { {content} } catch (err) { }" } }
  → tomar función, envolver en try-catch, escribir — todo en 1 llamada
```

### Mecanismo 5: 🔁 Citación entre Protocolos (MCP)

Los marcadores de referencia pueden incrustarse directamente dentro de los parámetros de texto de cualquier herramienta, incluidos servidores MCP externos. El sistema reconoce automáticamente estos marcadores y sustituye el contenido real antes de llamar al servidor externo.

```
"{{ref:source=chat,ref=-1,inicio=export const config}} --host production"
  → 91% de contenido del contexto, 9% generado por el modelo
```

---

## 🔭 DIRECCIONES FUTURAS

### 🏖️ Subsesiones Aisladas para Investigación

Para tareas complejas que requieren muchos pasos intermedios, se puede lanzar un agente auxiliar en una subsesión temporal aislada. Realiza todo el «trabajo sucio», devuelve solo el resultado limpio, y luego la subsesión se destruye.

### Otras Direcciones

- Caché predictivo de fragmentos usados frecuentemente
- Detección automática de llamadas duplicadas
- Desambiguación inteligente de referencias ambiguas
- Integración con sistemas de memoria y almacenamiento a largo plazo

---

## 💰 IMPACTO ECONÓMICO

### Por Agente

| Métrica | Sin mecanismo | Con mecanismo | Ahorro |
| -------------------------------- | ---------------- | -------------- | ---------- |
| Tokens por cita (código largo) | 200-500 | 5-15 | **96-97%** |
| Tokens por cita (código corto) | 50-100 | 2-5 | **90-95%** |
| Tokens por sesión | 25,000-50,000 | 5,000-15,000 | **60-80%** |
| Energía por sesión | unidad arbitraria | 5 veces menos | **~80%** |

### A Escala Global

Cuando se adopte en toda la industria, el ahorro alcanzará miles de millones de tokens diariamente, equivalente a reducir el consumo energético del sector IA en decenas de porcentaje y reducir la huella de carbono en decenas de miles de toneladas de CO₂ al año.

---

## 🔬 VERIFICACIÓN DE UNICIDAD

Realicé **investigaciones profundas multi-ronda** (7 rondas, ~50 fuentes) a través de sistemas de búsqueda web (Tavily Search, profundidad avanzada) cubriendo todas las categorías conocidas de arquitecturas de agentes de IA.

*Después de publicar el manifiesto, en análisis adicionales (rondas 8-10), se descubrió que TJ Guadagno implementó independientemente un prototipo experimental del concepto — Clipboard Primitives. Este trabajo no fue identificado en las primeras 7 rondas de búsqueda debido a su baja visibilidad (LinkedIn Pulse + GitHub sin estrellas).*

**Objetivo:** encontrar algo que resuelva el mismo problema — permitir a un agente de IA referenciar contenido existente entre llamadas a herramientas en lugar de regenerarlo.

**Resultado: no se encontró nada similar.**
*Aclaración: el trabajo experimental de TJ Guadagno (Clipboard Primitives, ~diciembre 2025) es una implementación parcial (~40% del concepto UAC) y confirma la viabilidad de la idea, pero no es un análogo completo.*

| Categoría | Fuentes | Por qué NO es un análogo |
| --------------------------------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **APIs de citación (Anthropic/OpenAI/Google)** | APIs oficiales | Muestran la fuente al usuario, no permiten al agente reutilizar. Eje: Agente → Usuario solo |
| **Caché (Prompt, Semántico)** | Varios frameworks | Funciona a nivel de solicitudes, no a nivel de fragmentos de contenido |
| **RAG** | LangChain, OpenAI, Google | Recupera de bases de conocimiento externas, no del contexto de sesión actual |
| **CAMEL-AI "Brainwash Your Agent"** | camel-ai.org | Almacena solo la ÚLTIMA salida de herramienta. No tiene 5 mecanismos, ni pipeline de transformación |
| **LangChain artifacts** | langchain.com | `content_and_artifact` separa contenido y metadatos, no es un sistema de citación |
| **MCP Resources** | modelcontextprotocol.io | Un estándar para conectar herramientas, no un mecanismo de citación agente→agente |
| **Académico (AgentReuse, KVCOMM)** | arXiv | Reutilización de PLANES o KV-cache, no citación de contenido |
| **Herramientas humanas (UiPath, PowerToys)** | UiPath, Microsoft | Diseñadas para interacción humano-computadora, no para agentes de IA |
| **Agentes IA existentes** | Industria en general | Tienen historial, pero no mecanismo de citación entre llamadas |
| **Memoria compartida multi-agente** | Varios | Memoria RAG compartida, no citación precisa a nivel de caracteres |

> **Universal AI Clipboard no tiene análogos completos en la práctica mundial de sistemas de agentes de IA. La única implementación parcial conocida — Clipboard Primitives (TJ Guadagno, ~40% del concepto) — fue descubierta solo después de la publicación del manifiesto.**

---

## ⚖️ ESTADO LEGAL

**🏛️ Creative Commons Zero (CC0) — Dedicación Universal al Dominio Público**

Usted es libre de:
- ✅ **Usar** en proyectos comerciales y no comerciales
- ✅ **Modificar** y adaptar a sus necesidades
- ✅ **Distribuir** en cualquier forma
- ✅ **Patentar sus mejoras** (pero no la idea central)
- ✅ **Traducir** a cualquier idioma

Sin obligaciones, regalías ni restricciones.

> **Renuncio conscientemente a todos los derechos de patente sobre esta tecnología. Debe pertenecer a todos.**

---

## 📜 PRUEBA DE FECHA DE DESCUBRIMIENTO

La fecha de publicación de este manifiesto está registrada **por el sistema de control de versiones Git en el repositorio de GitHub** — [github.com/DScoNOIZ/UNIVERSAL-AI-CLIPBOARD](https://github.com/DScoNOIZ/UNIVERSAL-AI-CLIPBOARD).

El historial de commits, fechas de edición y todos los cambios cronológicos están **inmutablemente preservados por GitHub** y sirven como prueba pública de la fecha de descubrimiento y autoría.

---

## 🗓️ CRONOLOGÍA

| Fecha | Evento |
| ------------------- | ------------------------------------------------------------------------ |
| **~2021** | Primera conciencia del problema (DScoNOIZ) |
| **~diciembre 2025** | **Experimento independiente:** TJ Guadagno publica Clipboard Primitives |
| **Mayo — junio 2026** | Investigación: análisis de arquitecturas de agentes IA existentes |
| **Junio 2026** | Descubrimiento: ninguna tecnología existente tiene un análogo completo |
| **Junio 2026** | Concepto Universal AI Clipboard formulado |
| **3 de junio 2026** | Investigación de unicidad completada — **no se encontraron análogos completos** |
| **3 de junio 2026** | **Este manifiesto publicado** — descubrimiento en dominio público |
| **4 de junio 2026** | Trabajo de TJ Guadagno descubierto — reconocimiento del codescubridor |

---

## 🎯 LLAMADO A LA ACCIÓN

Desarrolladores de frameworks de IA, creadores de agentes, investigadores, empresas, ecologistas, comunidad de código abierto — **esta tecnología pertenece a todos. Bifurquen, implementen, mejoren.**

---

```
  ╔══════════════════════════════════════════════════════════════════╗
  ║                                                                  ║
  ║   UNIVERSAL AI CLIPBOARD (UAC)                                   ║
  ║   Content Reference Mechanism                                    ║
  ║   Optional Inter-Tool Content Citation Mechanism                 ║
  ║                                                                  ║
  ║   «Reuse, Don't Regenerate»                                      ║
  ║   «Reutiliza, no regeneres»                                      ║
  ║                                                                  ║
  ║   CC0 1.0 Universal — Dominio Público                            ║
  ║   github.com/DScoNOIZ                                            ║
  ║   3 de junio de 2026                                             ║
  ║                                                                  ║
  ╚══════════════════════════════════════════════════════════════════╝
```

---

_Este manifiesto puede ser traducido libremente a cualquier idioma. Original en ruso._

_Versión en inglés: [MANIFEST.md](MANIFEST.md)_
