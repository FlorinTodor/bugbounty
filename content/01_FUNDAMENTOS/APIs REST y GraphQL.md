---
tags: [fundamentos]
---
# APIs REST y GraphQL

El grueso de las apps modernas son un frontend + una API. **La API es donde están los bugs.**

## REST
- Verbos (GET/POST/PUT/PATCH/DELETE): prueba todos en cada endpoint.
- Versionado: `/v1` suele quedar sin los fixes de `/v2`. Busca versiones viejas.
- Descubrimiento: `/swagger`, `/openapi.json`, `/api-docs`, endpoints en los bundles JS.
- IDOR y mass assignment son endémicos en REST → [[Broken Access Control e IDOR]].

## GraphQL
- **Introspección**: si está abierta, te da el esquema completo (`__schema`). Úsala para mapear todo.
- **Batching**: mandar muchas queries en una → brute-force saltándose rate limits.
- IDOR en nodos por ID, autorización por campo (unos campos protegidos, otros no).
- Herramientas: GraphQL Raider (Burp), graphql-voyager, InQL.
- Endpoint típico: `/graphql`, `/api/graphql`.

## Autenticación de APIs
- Bearer tokens / JWT ([[OAuth, OIDC, SAML y JWT]]), API keys en cabeceras, claves en el JS.
- Rate limiting ausente en endpoints sensibles (login, OTP, export).

Enlaces: [[Broken Access Control e IDOR]] · [[Inyecciones SQL y NoSQL]] · [[JavaScript moderno para hackers]]
