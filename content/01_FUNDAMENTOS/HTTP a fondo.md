---
tags: [fundamentos]
---
# HTTP a fondo

El detalle que importa para bugs (no el repaso básico).

## Puntos donde viven los bugs
- **Cabecera `Host`**: password reset poisoning, routing, virtual host. ¿Qué pasa si la cambio?
- **`Content-Length` vs `Transfer-Encoding`**: base del request smuggling ([[HTTP request smuggling]]).
- **Cabeceras no incluidas en la clave de caché** (`X-Forwarded-Host`, `X-Forwarded-For`...):
  base del cache poisoning ([[Web cache poisoning y deception]]). Descúbrelas con Param Miner.
- **Métodos HTTP**: muchos endpoints aceptan PUT/DELETE/PATCH sin control. Prueba todos.
- **Codificaciones**: URL-encoding doble, unicode, normalización de rutas → bypass de filtros/WAF.
- **HTTP/2 y HTTP/1.1**: diferencias de parsing que habilitan smuggling moderno.
- **Redirecciones y `Location`**: open redirect, y cadenas hacia SSRF/OAuth theft.
- **Cabeceras de seguridad** (CSP, HSTS, CORS): entender qué protegen para saber cuándo su ausencia
  es explotable (y cuándo es solo Informative → [[Triage - qué esperar de la respuesta]]).

## Práctica
- Intercepta una app real en Burp y **lee** peticiones y respuestas enteras, cabecera por cabecera.
- Módulo *Information disclosure* de PortSwigger como calentamiento.

Enlaces: [[Sesiones, cookies y el modelo de origen]] · [[HTTP request smuggling]]
