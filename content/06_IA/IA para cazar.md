---
tags: [ia, caza]
---
# IA para cazar

Dónde aporta la IA **durante** una sesión de caza real. Ordenado por retorno.

## 1. Leer JavaScript por ti (altísimo retorno)
Las SPAs modernas descargan megas de JS. Ahí dentro hay endpoints ocultos, claves, rutas de admin,
feature flags. Leerlo a mano es inviable.

- Descargas los bundles (`.js`) y los pasas por un LLM: *"Extrae de este JS todos los endpoints de
  API, parámetros, rutas que sugieran funciones de admin/interno, y cualquier secreto o clave.
  Devuélvelo como tabla."*
- Con **Claude Code** puedes automatizarlo sobre una carpeta entera de bundles.
- Ojo: en ficheros enormes, trocea. Y **verifica** cada endpoint que te dé (a veces alucina rutas).

## 2. Entender una respuesta o tecnología rara al vuelo
Te encuentras un token JWT raro, una respuesta GraphQL enorme, un blob serializado de .NET
(`__VIEWSTATE`), un protobuf. Pégalo y pide: *"¿qué es esto, qué framework lo genera, y qué debería
probar contra ello desde el punto de vista de seguridad?"*

## 3. Generar variaciones de payload contextualizadas
No para inventar payloads (eso es PayloadsAllTheThings), sino para **adaptarlos**:
*"Este WAF bloquea `<script>`. Dame 15 variantes de mi payload de XSS que evadan filtros que
bloqueen esa cadena, explicando la técnica de cada una."* → tú entiendes cada una antes de usarla.

## 4. Mapear el modelo de permisos
Le describes los roles y endpoints que has visto y pides una **matriz de acceso esperada** vs.
**qué probar para romperla**. Esto acelera la caza de IDOR/BAC, que es lo que más paga.
Ver [[Broken Access Control e IDOR]].

## 5. Analizar código fuente (targets open source y de IA)
Para huntr y programas con código público: le das el repo (Claude Code lo lee entero) y pides:
*"Encuentra sinks peligrosos: deserialización, ejecución de comandos, path traversal, SSRF,
SQL construido por concatenación. Dame fichero:línea y por qué es sospechoso."* Ver [[Nicho - seguridad de IA y ML]].

## 6. El MCP de Burp (integración directa)
Con el **MCP Server** oficial de Burp, el LLM ve tu historial de proxy y puede sugerir sobre
peticiones reales tuyas. Útil para *"revisa estas 30 peticiones y dime cuáles tienen identificadores
numéricos que valdría la pena manipular"*.

## Lo que la IA NO hace cazando

- ❌ **No decide qué target vale la pena.** Eso es criterio y contexto de negocio (tuyo).
- ❌ **No confirma un bug.** Confirmar = reproducir tú, con dos cuentas, viendo el impacto real.
  La IA diciendo "esto es vulnerable" no es evidencia de nada.
- ❌ **No encuentra fallos de lógica de negocio.** No conoce las reglas del negocio; tú sí.
- ❌ **No sustituye entender la app.** Un IDOR lo ves porque entendiste que ese `orderId` no debería
  ser accesible. La IA no sabe eso.

## Flujo realista de una sesión con IA de copiloto

1. Tú: recon y navegación. **Entiendes** la app. (IA fuera)
2. IA: te digiere los bundles JS y te saca el mapa de endpoints. (delegado)
3. Tú: eliges dónde atacar según lo que entendiste. (criterio)
4. IA: te ayuda a adaptar payloads y a entender respuestas raras. (soporte)
5. Tú: reproduces, confirmas impacto, capturas evidencia. (insustituible)
6. IA: te redacta el borrador del report; tú lo verificas y corriges. Ver [[Cómo escribir un buen report]].

Enlaces: [[Automatizar tu recon con IA]] · [[Límites y riesgos de la IA]] · [[Biblioteca de prompts]]
