---
tags: [metodologia, checklist]
---
# Checklist maestro

Lo que pruebas sistemáticamente. **Este es un documento vivo**: cada bug o técnica nueva que
aprendas cazando, añádela aquí. Empieza siendo mío; en un año será tuyo y ese será su valor.

> Uso: no lo corras entero cada sesión. Elige **una sección** como objetivo de la sesión
> (ver [[Metodología de caza]]).

## Por cada endpoint con un ID / referencia a objeto
- [ ] Cambiar el ID por el de mi 2ª cuenta → ¿accedo? (**IDOR** → [[Broken Access Control e IDOR]])
- [ ] IDs no numéricos: UUID predecible, base64 de un email, hash de algo adivinable
- [ ] Cambiar método HTTP (GET→POST, PUT, DELETE, PATCH)
- [ ] Quitar/cambiar el parámetro de tenant/organización
- [ ] Acceder al endpoint sin sesión / con sesión de rol inferior

## Autenticación y sesión
- [ ] Reset de contraseña: token predecible, sin caducidad, reutilizable, host header injection
- [ ] 2FA: se puede saltar, brute-force del código, race condition en la verificación
- [ ] Registro: enumerar usuarios por mensajes distintos, saltarse verificación de email
- [ ] JWT: `alg:none`, firma no verificada, secreto débil, `kid` injection ([[OAuth, OIDC, SAML y JWT]])
- [ ] Cookies de sesión: no rotan al login, no expiran al logout, atributos flojos
- [ ] OAuth: `redirect_uri` abierto, `state` ausente (CSRF), robo de `code`

## Access control / privilegios
- [ ] Función de admin accesible con rol normal (forzar la ruta que vi en el JS)
- [ ] Escalada horizontal (otro usuario) y vertical (más permisos)
- [ ] Parámetros ocultos tipo `role=admin`, `isAdmin=true`, `debug=1`
- [ ] Mass assignment: mandar campos extra en el JSON que no están en el formulario

## Entradas / inyecciones
- [ ] Todo campo reflejado → **XSS** (contexto: HTML, atributo, JS, URL) → [[XSS moderno]]
- [ ] Todo campo que va a BD → **SQLi/NoSQLi** (blind, time-based) → [[Inyecciones SQL y NoSQL]]
- [ ] Campos en plantillas/emails → **SSTI** → [[SSTI e inyección de plantillas]]
- [ ] Parsers de XML → **XXE** → (base en tu vault viejo)
- [ ] Campos que se usan en comandos/paths → **command injection / path traversal**

## Peticiones que salen del servidor (SSRF)
- [ ] Cualquier campo "URL", "webhook", "callback", "importar desde", "avatar por URL"
- [ ] ¿Llega a metadata cloud? (`169.254.169.254`) → [[SSRF]]
- [ ] Blind SSRF con Burp Collaborator / interactsh

## Subida de ficheros
- [ ] Tipo/extensión: doble extensión, content-type falso, `.svg` con XSS, polyglots
- [ ] Path traversal en el nombre → sobrescribir ficheros
- [ ] ¿El fichero acaba en un dominio con ejecución? → RCE

## Lógica de negocio
- [ ] Precios/cantidades negativas o manipuladas en el carrito
- [ ] Reutilizar cupones, saltarse pasos de un flujo, repetir acciones de un solo uso
- [ ] Race conditions en acciones con límite (transferencias, invitaciones, votos) → [[Race conditions]]
- [ ] Saltarse límites de plan (free→features de pago)

## Cabeceras / infraestructura
- [ ] Web cache poisoning (cabeceras no keyed) → [[Web cache poisoning y deception]]
- [ ] Request smuggling (CL.TE / TE.CL) → [[HTTP request smuggling]]
- [ ] CORS mal configurado (`Origin` reflejado + credentials) → [[CSRF y CORS]]

## APIs
- [ ] GraphQL: introspección abierta, batching para brute-force, IDOR en nodos
- [ ] REST: versiones antiguas (`/v1` sin los fixes de `/v2`), verbos no contemplados
- [ ] Rate limiting ausente en endpoints sensibles

## Nicho IA (si el target lo tiene)
- [ ] Chatbot: prompt injection directa e indirecta, fuga de system prompt
- [ ] ¿El agente tiene herramientas? → excessive agency → [[Nicho - seguridad de IA y ML]]
- [ ] RAG multi-tenant: ¿me devuelve datos de otro usuario?

## Siempre
- [ ] Leer los bundles JS enteros (con IA) → endpoints y secretos ocultos
- [ ] Revisar `robots.txt`, `sitemap.xml`, `.well-known/`, `/swagger`, `/.git/`
- [ ] Anotar cada **anomalía** aunque no sepa explotarla aún

Enlaces: [[Metodología de caza]] · [[MOC - Vulnerabilidades]]
