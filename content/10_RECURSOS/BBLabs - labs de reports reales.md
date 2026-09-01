---
tags: [recursos, plataforma-estudio]
---
# BBLabs - labs de reports reales

`https://bblabs.es` · de **Gorka "El Bochi"** (cazador en activo, no una empresa). En español.

## Qué es y por qué encaja contigo
Labs que **reconstruyen reports reales ya pagados** de HackerOne, Bugcrowd e Intigriti (~50-60 labs,
descargables con Docker, con writeup y el contexto del report original). Cubre el hueco que
**PortSwigger no cubre**: PortSwigger te enseña la técnica en un lab diseñado para que el bug exista;
BBLabs te enseña **cómo se veía ese bug dentro de una app real y cuánto pagó**. Ese salto
("sé hacer XSS en el lab pero no encuentro nada en un target") es el muro donde se atasca casi todo
el mundo — y donde vas a estar tú en el mes 2.

## Lo gratis (míralo ya)
- **Academy** — 16 categorías con cheatsheets y payloads. Úsala como **referencia de payloads**, no
  como material de estudio (para eso está PortSwigger, más profundo). Vale para el "no me acuerdo de
  la sintaxis exacta".
- **Roadmap** — míralo pero **no lo sigas**: ya tienes [[Ruta de aprendizaje]], hecha para tu punto
  de partida. El suyo es genérico y te haría repetir fundamentos que ya tienes.
- **Blog** — guías y noticias.

## Lo de pago (PRO+)
7,99 €/mes (o 74,99 €/año, o 149,99 € lifetime). Barato y cancelable. Incluye todos los labs,
entornos, writeups y Discord privado.

## Cuándo pagar y cómo usarlo
**No ahora.** Ya vas a pagar HTB Academy y tu enemigo nº1 es la dispersión: tres plataformas a la
vez = ninguna a fondo. Págalo **a partir del mes 2-3**, cuando ya hayas hecho el bloque de Access
Control en PortSwigger, y úsalo así:

> **El lab de BBLabs es el examen de la clase de vuln que acabas de estudiar.**
> PortSwigger (aprendes) → BBLabs (validas sobre un caso real) → lo apuntas en tu nota de esa vuln.

Labs que van directos a tus huecos: **IDOR / broken access control**, **lógica de negocio**
(payment bypass, abuso de flujo), **race conditions**, **OAuth/JWT bypass** y
**[[Mass assignment]]**.

> [!note] BBLabs vs HTB Academy, honestamente
> Para **cazar** (no para el CV), BBLabs le gana a HTB Academy: más realista y un tercio del precio.
> HTB gana solo si vas a por el **CBBH** o el **COAE**. Ver [[HTB Academy - qué hacer y qué saltarse]]
> y [[Certificaciones - cuáles valen la pena]].

## El aviso sobre sus vídeos de YouTube
Sus vídeos son buenos para **descubrir temas** y malísimos para **retener**. Ver a alguien encontrar
un bug produce la sensación de haber aprendido sin haber aprendido nada; el trabajo real es la hora
que pasas atascado tú solo. Regla: **un vídeo → una nota escrita con tus palabras** en
`02_VULNERABILIDADES`, o no cuenta como estudio. Ver [[IA para estudiar]] (mismo principio).

## Y algo gratis que vale más que todo esto
Los reports **disclosed** de HackerOne. Es de donde salen los labs de BBLabs. Leer 3-4 reports
reales por semana no cuesta un euro y es lo que más te acerca a encontrar el primero.

Enlaces: [[Enlaces]] · [[Comparativa de plataformas]] · [[HTB Academy - qué hacer y qué saltarse]] · [[Ruta de aprendizaje]]
