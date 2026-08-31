---
tags: [plataformas, nicho, ia]
---
# Nicho - seguridad de IA y ML

**Esta es tu ventaja competitiva.** Casi nadie en bug bounty sabe de LLMs, RAG, grafos y pipelines
de ML a nivel de ingeniería. Tú sí, por el TFG. Y casi nadie que sabe de ML sabe de seguridad web.

## Los tres frentes

### 1. Vulnerabilidades **en librerías de ML** (código clásico, target moderno)
Plataforma: **huntr.com** (Protect AI). Bounties por CVEs en proyectos como Gradio, MLflow, LangChain,
Ray, ComfyUI, Label Studio, etc.
Lo que se encuentra ahí es **web clásica en herramientas mal escritas**:
- Path traversal y **arbitrary file read/write** en interfaces de subida de datasets.
- **Deserialización insegura**: pickle, joblib, `torch.load`, YAML → RCE casi directa.
- **SSRF** al cargar modelos/datasets desde URL.
- **RCE** por evaluación de código en pipelines "configurables".
- Auth ausente en dashboards de MLOps expuestos.
- **Model file poisoning** (un `.pkl` o `.gguf` malicioso que ejecuta código al cargarse).

> Encaja perfecto: es Python, es open source (puedes **leer el código**, no adivinar), y tu
> experiencia montando `Ciber-AsesorIA` te dice dónde miran poco estos proyectos.

### 2. **Seguridad de aplicaciones con LLM** (el nuevo OWASP)
Los programas de bug bounty empiezan a incluir "nuestro chatbot" en el scope. Temas:
- **Prompt injection** directa e indirecta (a través de un documento, una web, un email que el agente lee).
- **Fuga de system prompt** y de datos de otros usuarios en RAG multi-tenant.
- **Excessive agency**: el agente tiene herramientas (envía correos, ejecuta SQL, llama APIs) y le
  convences de usarlas mal. **Aquí es donde está la severidad real**, no en hacerle decir tacos.
- **RAG poisoning**: envenenar la fuente que el agente indexa.
- Referencias: **OWASP Top 10 for LLM Applications** y el módulo de *Web LLM attacks* de PortSwigger
  (gratis, y muy bueno).

### 3. Programas específicos
- **0din** (Mozilla) — bounty de GenAI.
- Programas propios de **Anthropic, OpenAI, Google DeepMind** para seguridad de modelos y de producto.
- Cualquier empresa que haya metido un "asistente IA" en su producto este año: **superficie nueva,
  código escrito con prisa, nadie la ha auditado**.

## Cómo entrar (plan concreto)

1. **Mes 3-4**: haz el módulo *Web LLM attacks* de PortSwigger (2-3 tardes). Es gratis y corto.
2. Lee el **OWASP Top 10 for LLM Apps** y haz una nota por cada ítem en `02_VULNERABILIDADES`.
3. **Mes 4-5**: elige 2 proyectos de huntr que ya conozcas (LangChain, Gradio, MLflow…), clónalos
   y haz **revisión de código** buscando sinks: `pickle.load`, `yaml.load`, `eval`, `subprocess`,
   `os.path.join` con input de usuario, `requests.get(url_usuario)`.
4. En cada target web que caces, **si tiene un chatbot, es prioridad**: mira qué herramientas
   tiene detrás y si el contexto mezcla datos de varios usuarios.

## Por qué esto es más rentable para ti que competir en XSS

- En XSS reflejado compites con 5.000 personas y herramientas automatizadas.
- En "deserialización en un framework de MLOps" compites con **20 personas en el mundo**, y la
  mitad no sabe leer Python bien.

Enlaces: [[Comparativa de plataformas]] · [[MOC - IA en bug bounty]] · [[Deserialización insegura]]
