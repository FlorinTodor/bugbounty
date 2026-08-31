---
tags: [vulnerabilidad]
clase: SSRF
estado: 🔴 pendiente
owasp: A10:2021
paga_bien: ⭐⭐⭐
---
# SSRF (Server-Side Request Forgery)

> Haces que **el servidor** haga peticiones por ti. En cloud, esto suele escalar a robo de
> credenciales de IAM → acceso a toda la infraestructura. De ahí que pague tan bien.

## Qué es
Un input controla una URL/host que el servidor va a solicitar. Rediriges esa petición a sitios
internos que tú no alcanzas desde fuera.

## Dónde aparece
Cualquier función que haga que el servidor busque algo por ti:
- "Importar desde URL", "avatar por URL", webhooks, callbacks, generación de PDF/thumbnails,
  validadores de URL, proxies, integraciones, previsualizadores de enlaces, `xmlrpc`, parsers que
  resuelven entidades externas (relación con XXE).

## Objetivos internos
- **Metadata cloud**: `http://169.254.169.254/latest/meta-data/` (AWS), equivalentes GCP/Azure.
  → credenciales temporales de IAM. **Máximo impacto.**
- Servicios internos: `http://localhost:puerto`, `http://10.x`, `http://192.168.x`.
- Panel de admin interno, bases de datos, Redis, Elasticsearch expuestos en localhost.

## Técnicas y bypass
- Blind SSRF: usa **Burp Collaborator / interactsh** para ver la petición saliente OOB.
- Bypass de filtros: IPs en decimal/octal/hex, `[::]`, DNS rebinding, redirects (tu servidor
  responde 302 a `169.254.169.254`), `@` en la URL, dominios que resuelven a IP interna.
- Protocolos: `file://`, `gopher://`, `dict://` según el cliente HTTP.

## Impacto
Blind SSRF sin más → Medium. SSRF a metadata cloud con robo de credenciales → **Critical**.

## Labs de PortSwigger
- [ ] SSRF (módulo completo)

## ⚠️ Legal
No pivotes por la red interna aunque puedas. Demuestra el SSRF y para. Ver [[Reglas del juego - legalidad y scope]].

## Mis notas de caza
- 

Enlaces: [[Checklist maestro]] · [[Subdomain takeover y errores de cloud]]
