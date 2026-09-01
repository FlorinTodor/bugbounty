# `custom/`

Ficheros que se copian **encima** de lo que genera Quartz, después de `npx quartz build`.
Van aquí y no dentro de `quartz/` para que un `npx quartz update` no se los lleve por delante.

## `404.html`

El 404 de Quartz ("Esta página es privada o no existe") no se parecía en nada al del portafolio.
Este es el mismo diseño que `florintodor.dev`, con los destinos cambiados por los del vault.

- **Origen del CSS**: está incrustado en un `<style>` y sale de `Portafolio/dist/_astro/_slug_.*.css`,
  que es el `src/styles/global.css` ya compilado. Se incrusta en vez de enlazarlo porque Astro le
  pone un hash al nombre y cambia en cada build del portafolio.
- **Si rediseñas el portafolio**, este 404 se queda con el estilo viejo. Para refrescarlo: reconstruye
  el portafolio (`npm run build`) y sustituye el bloque `<style>` por el contenido del nuevo
  `dist/_astro/_slug_.*.css`.
- Es español solo, a diferencia del 404 del portafolio (que es bilingüe porque sirve también a `/en/`).
  Aquí no hace falta: el vault es todo en español.
