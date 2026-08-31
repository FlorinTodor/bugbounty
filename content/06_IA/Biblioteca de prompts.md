---
tags: [ia, prompts]
---
# Biblioteca de prompts

Prompts concretos y copiables. Adáptalos. Recuerda [[Límites y riesgos de la IA]]: **verifica todo**
y no pegues datos reales de usuarios ni de programas privados.

## Estudio

**Profesor socrático (post-lab)**
> Acabo de resolver el lab "[nombre]" de PortSwigger. Mi explicación de por qué la vulnerabilidad
> existe y por qué el exploit funciona es: [tu explicación]. No me corrijas todavía. Hazme 5
> preguntas que distingan si lo entiendo de verdad o si repito pasos memorizados. Luego valoras.

**Teoría → producción**
> Tema: [vuln]. En una aplicación real (no un lab limpio), dame 8 señales OBSERVABLES en el tráfico
> HTTP que me harían sospechar de esta vulnerabilidad. Solo señales concretas, nada de teoría.

**Generar Anki**
> Convierte esta nota en 15 tarjetas Anki, formato CSV `pregunta;respuesta`. Preguntas de
> aplicación ("qué probarías si...") no de definición. Nota: [pega la nota].

## Recon / caza

**Analizar bundle JS**
> Este es un bundle JS de una web (autorizada, bug bounty). Extrae en una tabla: (1) todos los
> endpoints de API y su método probable, (2) parámetros que acepten, (3) rutas que sugieran
> funciones de admin/internas, (4) posibles secretos o claves. No inventes rutas: si no estás
> seguro, márcalo como "inferido". [pega el JS]

**Entender un blob raro**
> ¿Qué es esto, qué tecnología/framework lo genera, y qué debería probar contra ello desde
> seguridad? [pega token/viewstate/protobuf/respuesta]

**Matriz de acceso (para IDOR/BAC)**
> App con estos roles: [lista]. Estos endpoints observados: [lista]. Construye la matriz de acceso
> ESPERADA (qué rol debería poder hacer qué) y, en otra columna, qué prueba concreta haría para
> verificar si esa restricción se puede romper. Ver [[Broken Access Control e IDOR]].

**Evadir un filtro (entendiendo)**
> Un filtro bloquea la cadena "[x]" en mi payload de [tipo]. Dame 12 variantes que podrían evadirlo,
> y para CADA una explica la técnica de evasión. No quiero solo payloads, quiero entender por qué.

**Wordlist contextual**
> Genera una wordlist de 200 rutas/parámetros probables para una app de [sector] en [idioma] que
> hace [función]. Una por línea, sin explicaciones.

## Análisis de código (open source / nicho IA)

**Buscar sinks**
> Revisa este código buscando sinks peligrosos: deserialización (pickle/yaml/torch.load),
> ejecución de comandos, path traversal, SSRF, SQL por concatenación, eval. Para cada uno: ruta,
> línea, por qué es sospechoso, y qué input de usuario llegaría hasta ahí. [pega código o carpeta]

## Reporte

**Borrador de report (tú lo verificas)**
> Redacta un borrador de report de bug bounty con esta estructura: Título, Resumen, Severidad+CVSS
> propuesta, Pasos de reproducción numerados, Impacto de negocio, Remediación. Bug: [descripción y
> pasos que YO ya reproduje]. Tono profesional y conciso. NO exageres el impacto. Marca con [VERIFICAR]
> cualquier afirmación técnica que debería comprobar. Ver [[Cómo escribir un buen report]].

**Estimar CVSS**
> Dame el vector CVSS 3.1 razonado para este bug y explica cada métrica. Bug: [descripción]. Si una
> métrica depende de contexto que no te he dado, pídemelo en vez de asumir.

## Meta (usando este vault)

**Auditar mis notas**
> Lee mi [[Checklist maestro]] y mi nota [[X]]. ¿Qué técnicas conocidas de esta clase de vuln NO
> tengo apuntadas? Dame solo las que faltan, con una línea de qué son.

Enlaces: [[MOC - IA en bug bounty]] · [[IA para estudiar]] · [[IA para cazar]]
