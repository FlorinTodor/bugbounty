---
tags: [vulnerabilidad]
clase: Auth/Tokens
estado: 🔴 pendiente
paga_bien: ⭐⭐
---
# OAuth, OIDC, SAML y JWT

> Esqueleto. Complétalo **con tus palabras** al hacer los labs. Estructura completa en
> `_plantillas/Plantilla - Vulnerabilidad`.

## Qué es
Los protocolos de identidad federada y sus tokens. JWT: \`alg:none\`, firma no verificada, secreto débil (bruteforce), \`kid\`/\`jku\` injection. OAuth: \`redirect_uri\` abierto, falta de \`state\` (CSRF), robo de \`code\`. SAML: firma no validada, XML wrapping. ATO potente si fallan.

## Labs de PortSwigger (fuente principal)
- [ ] OAuth authentication (módulo)
- [ ] JWT attacks (módulo)

## Recursos
- PayloadsAllTheThings (categoría correspondiente) — payloads reales.
- HackTricks — técnicas y bypass.

## Mis notas de caza
- 

Enlaces: [[Autenticación y toma de cuentas]] · [[Checklist maestro]]
