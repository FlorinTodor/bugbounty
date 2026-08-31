---
tags: [inicio, expectativas]
---
# La verdad incómoda sobre el bug bounty

Lee esto antes de gastar un euro. No es para desanimarte: es para que **no abandones en el mes 2**,
que es cuando abandona casi todo el mundo, por expectativas mal puestas.

## 1. La distribución de ingresos es brutal

En cualquier plataforma, un puñado de cazadores se lleva la mayoría del dinero. La mediana de un
cazador registrado es **0 €**. La mayoría de la gente que se registra nunca reporta nada válido.

No es porque sean tontos: es porque tratan el bug bounty como un CTF. En un CTF hay un bug puesto
ahí para ti. En bug bounty, **ya han pasado 500 personas antes que tú** por ese endpoint.

## 2. Tu primer bounty tardará entre 3 y 9 meses

Con tu base (programación + fundamentos), realista: **4-6 meses** de tardes constantes hasta el
primer pago. Antes de eso tendrás: N/A, Informative, Duplicate, y silencio. Es normal.

## 3. Lo que decide tu resultado, por orden de importancia

1. **Elegir bien el programa y el target** (50%) — ver [[Cómo elegir un programa]].
2. **Ir en profundidad en pocos targets** en vez de escanear muchos (25%).
3. **Conocer bien 3-4 clases de bug** en vez de 20 a medias (15%).
4. Herramientas y automatización (10%). Sí, solo un 10%. Nadie paga por correr `nuclei`.

## 4. Lo que NO funciona (y lo verás recomendado por todas partes)

- Correr un scanner masivo sobre 10.000 subdominios. Todo lo que encuentre es duplicado.
- Reportar cosas de "best practice": falta de cabecera `X-Frame-Options`, `SPF` mal puesto,
  autocompletado en el login, versión de servidor expuesta. Eso es **Informative**, y acumular
  Informatives te baja la reputación y te cierra puertas a programas privados.
- Cazar solo XSS reflejado en programas grandes y públicos. Es el bug más buscado por todos.
- Mandar un report generado por IA sin verificar. Ver [[Límites y riesgos de la IA]].

## 5. Lo que sí funciona para alguien que empieza

- **Empezar por VDPs** (programas sin pago) y programas pequeños/nuevos: menos competencia,
  triage más humano, y te construyen reputación para que te inviten a los privados, que es
  donde está el dinero de verdad.
- Elegir un solo target y volverte **la persona que más sabe del mundo de esa aplicación**.
  Registrarte, usarla como usuario normal, entender el negocio. De ahí salen los IDOR y los
  fallos de lógica que un escáner no ve nunca.
- Especializarte en algo raro. Ver [[Nicho - seguridad de IA y ML]].

## 6. Cuánto tiempo hace falta

"Por las tardes" es suficiente **si es constante**. 10-12 h/semana sostenidas durante un año baten
a 40 h/semana durante mes y medio. Ver [[Rutina semanal]].

## 7. Riesgo real de quemarse

El bucle *"4 horas buscando → nada → frustración"* es el que mata. Antídotos:
- Mide **horas de práctica y notas escritas**, no bounties. Las bitácoras de [[Bitácora]] existen
  para que veas progreso aunque no haya dinero.
- Alterna: días de estudio (labs con solución garantizada, dopamina asegurada) y días de caza.
- Ten un objetivo que no dependa del azar: *"este mes domino access control"*, no *"este mes cobro"*.

---
Siguiente: [[Ruta de aprendizaje]]
