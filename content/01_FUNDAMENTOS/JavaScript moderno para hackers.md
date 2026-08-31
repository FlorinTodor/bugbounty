---
tags: [fundamentos]
---
# JavaScript moderno para hackers

Las SPAs (React/Vue/Angular) meten toda su lógica en **bundles JS**. Leerlos es una de las
habilidades más rentables y donde tu perfil de programador + IA brilla.

## Qué buscas en los bundles
- **Endpoints de API** ocultos (rutas que el frontend llama pero no ves navegando).
- **Rutas de admin / features internas** referenciadas en el router.
- **Secretos**: claves API, tokens, IDs de terceros, endpoints de staging.
- **Feature flags** y lógica condicional que revela funciones ocultas.
- **Sinks de DOM XSS**: `innerHTML`, `eval`, `document.write`, `dangerouslySetInnerHTML`.

## Cómo
1. `katana -jc` / `getJS` para recolectar todos los `.js`.
2. **Source maps** (`.js.map`): si están, reconstruyes el código fuente original. Búscalos.
3. `linkfinder` para extraer endpoints; **+ un LLM** para digerir el bundle entero
   (ver [[IA para cazar]] y [[Biblioteca de prompts]]).
4. Beautifica (`js-beautify`) lo minificado antes de leer.

## Tu ventaja
Sabes leer JS/TS de verdad. Donde otros corren un script y se pierden, tú **entiendes** el router,
el estado y las llamadas. Combínalo con IA para escalar a muchos bundles.

Enlaces: [[Recon - superficie de ataque]] · [[IA para cazar]] · [[Prototype pollution]]
