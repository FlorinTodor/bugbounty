---
tags: [ia, estudio]
---
# IA para estudiar

## Lo que funciona de verdad

### 1. El profesor socrático (el mejor uso, con diferencia)
Después de cada lab de PortSwigger, **explícale la solución a la IA como si le enseñaras** y pídele
que te haga preguntas y detecte agujeros en tu razonamiento.

> *"Acabo de resolver el lab X. Mi explicación de por qué funciona es: [tu explicación].
> No me des la respuesta correcta todavía: hazme 5 preguntas que revelen si de verdad lo entiendo
> o si estoy repitiendo pasos memorizados."*

Esto ataca el problema nº1 de los labs: **completarlos sin entenderlos**.

### 2. Traducir teoría a "cómo se ve en producción"
Los labs son limpios; la realidad es sucia.

> *"Este es el lab de web cache poisoning. En una aplicación real detrás de Cloudflare,
> ¿qué señales concretas vería en las respuestas HTTP que me hicieran sospechar? Dame 8 señales
> observables, no teoría."*

### 3. Generar tarjetas de repaso espaciado
Pídele que convierta tus notas en preguntas/respuestas para Anki. Los payloads y las cabeceras
se olvidan; el repaso espaciado los fija.

> *"Convierte esta nota en 15 tarjetas Anki en formato CSV (pregunta;respuesta). Que las preguntas
> sean de aplicación, no de definición: 'qué cabecera probarías si...' en vez de 'qué es...'."*

### 4. Explicar código y tecnologías desconocidas
Te vas a topar con Ruby on Rails, .NET, Spring, gRPC, protobuf, WebSockets… Pídele un resumen
**orientado a seguridad**: dónde están los sinks típicos de ese stack, qué configuraciones fallan.

### 5. Deconstruir writeups
Los writeups buenos dan el resultado, no el proceso.

> *"Aquí tienes un writeup. Reconstruye el **proceso mental**: ¿qué observación disparó cada
> hipótesis? ¿Qué habría probado antes y le habría fallado? Dame la lista de decisiones, no de pasos."*

### 6. Simulacros
> *"Haz de aplicación web vulnerable. Descríbeme respuestas HTTP y yo te digo qué pruebo.
> Tú respondes lo que devolvería el servidor. No me digas si voy bien hasta que lo pida."*

## Lo que NO funciona

- ❌ **Pedirle que te resuelva el lab.** Aprendes cero. Si estás atascado >45 min, pide una *pista*
  ("dame la siguiente pregunta que debería hacerme", no "dame la solución").
- ❌ **Pedirle payloads de memoria.** Se los inventa y no verás por qué fallan. Usa PayloadsAllTheThings.
- ❌ **Pedirle "enséñame hacking"** en abstracto. Sin un lab delante no fija nada.
- ❌ Fiarte de datos concretos: versiones, CVEs, números de puerto, sintaxis exacta. **Verifica siempre.**

## Rutina de estudio con IA (encaja en [[Rutina semanal]])

1. **Antes** de la sesión: 5 min. *"Recuérdame los 6 conceptos clave de [tema] en forma de preguntas."*
2. **Durante**: la IA solo para desatascar conceptos, nunca para dar la solución.
3. **Después**: 10 min. Le explicas lo aprendido → te interroga → escribes la nota en el vault.
   **Escribes tú la nota.** Si la escribe la IA, no la recordarás.

> [!tip] Este vault como copiloto
> Claude Code puede leer este vault entero. Prueba: *"Lee mi Checklist maestro y mis notas de
> Broken Access Control. ¿Qué técnicas de las que existen no tengo apuntadas?"*

Enlaces: [[IA para cazar]] · [[Biblioteca de prompts]] · [[Ruta de aprendizaje]]
