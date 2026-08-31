---
tags: [fundamentos]
---
# Sesiones, cookies y el modelo de origen

El modelo de seguridad del navegador. Entenderlo es la base de XSS, CSRF, CORS y ATO.

## Conceptos clave
- **Same-Origin Policy (SOP)**: qué puede leer un origen de otro. La regla que todo lo demás relaja.
- **Cookies**: atributos `Secure`, `HttpOnly`, `SameSite` (Strict/Lax/None), `Domain`, `Path`.
  Qué protege cada uno y qué bug habilita su ausencia.
- **CORS**: cómo se relaja la SOP. Mal configurado = fuga de datos ([[CSRF y CORS]]).
- **postMessage**: comunicación entre orígenes; origen no validado → XSS/robo de datos.
- **Tokens de sesión vs JWT**: dónde se guardan (cookie vs localStorage) y qué implica para XSS/CSRF.
- **Service workers, storage, iframes/sandbox**: superficie extra en SPAs.

## Preguntas que te haces ante cualquier app
- ¿Cómo mantiene la sesión? ¿Cookie o token en storage?
- ¿La cookie es `HttpOnly`+`SameSite`? → condiciona si un XSS roba sesión y si el CSRF es viable.
- ¿Hay CORS? ¿Refleja el `Origin`? ¿Con credenciales?

Enlaces: [[XSS moderno]] · [[CSRF y CORS]] · [[OAuth, OIDC, SAML y JWT]]
