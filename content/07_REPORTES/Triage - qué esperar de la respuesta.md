---
tags: [reportes, triage]
---
# Triage - qué esperar de la respuesta

Los estados que verás y qué significan. Entenderlos evita que te frustres o discutas mal.

| Estado | Qué significa | Qué haces |
|---|---|---|
| **New / Pending** | En cola | Esperar. No mandes 5 mensajes |
| **Triaged / Accepted** | Confirmado, validado. **¡Bien!** | Esperar a la recompensa/fix |
| **Duplicate** | Otro lo reportó antes | Normal, sobre todo al principio. No discutas salvo que el "original" sea claramente distinto |
| **Informative** | Válido pero sin impacto suficiente para pagar | Aprende de por qué. Demasiados bajan tu reputación |
| **N/A (Not Applicable)** | No lo consideran vuln / fuera de scope | Si crees que se equivocan, argumenta **una vez**, con datos, sin drama |
| **Resolved** | Arreglado | Puede que autoricen divulgación |
| **Spam** | Report malo/ruido | Evítalo a toda costa: penaliza fuerte |

## Por qué te van a cerrar reports al principio (y cómo evitarlo)
- **Duplicate**: elegiste un target muy peinado. → programas nuevos/pequeños ([[Cómo elegir un programa]]).
- **Informative**: reportaste "best practice" sin impacto. → lista de abajo.
- **N/A**: fuera de scope o no reprodujeron. → pasos de reproducción impecables ([[Cómo escribir un buen report]]).

## Lista negra de Informatives (NO los reportes)
- Falta de cabeceras (`X-Frame-Options`, CSP, HSTS) sin explotación demostrada.
- `SPF/DMARC` mal configurado sin PoC de spoofing con impacto.
- Autocompletado en formularios, falta de rate limit sin impacto concreto.
- Versión de software / banner expuesto sin CVE explotable demostrado.
- Clickjacking en páginas sin acción sensible.
- Self-XSS, CSRF en logout, open redirect sin cadena a algo mayor.
- Salida de `nuclei`/scanner sin verificación ni impacto.
- "Robots.txt revela rutas", "cookie sin flag" sin demostrar consecuencia.

## Buenas prácticas con el programa
- Sé **profesional y paciente**. Los triagers hablan entre ellos y con los programas.
- Si discrepas, aporta **evidencia nueva**, no insistencia.
- **Nunca amenaces** con divulgar. Es la vía rápida al ban y a problemas legales
  ([[Reglas del juego - legalidad y scope]]).
- Un buen historial (pocos reports, alta validez) te abre los **privados**, donde está el dinero.

Enlaces: [[Cómo escribir un buen report]] · [[Severidad y CVSS]] · [[Comparativa de plataformas]]
