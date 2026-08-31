---
tags: [vulnerabilidad]
clase: SSTI
estado: 🔴 pendiente
paga_bien: ⭐⭐
---
# SSTI e inyección de plantillas

> Esqueleto. Complétalo **con tus palabras** al hacer los labs. Estructura completa en
> `_plantillas/Plantilla - Vulnerabilidad`.

## Qué es
Inyección en motores de plantillas del servidor (Jinja2, Twig, Freemarker, Velocity...). Input que llega a la plantilla se evalúa → desde fuga de datos hasta **RCE**. Zonas típicas: emails personalizados, generación de documentos, campos "nombre" reflejados en plantillas. Detectar el motor primero (\`{{7*7}}\`, \`${7*7}\`...).

## Labs de PortSwigger (fuente principal)
- [ ] Server-side template injection (módulo)

## Recursos
- PayloadsAllTheThings (categoría correspondiente) — payloads reales.
- HackTricks — técnicas y bypass.

## Mis notas de caza
- 

Enlaces: [[Deserialización insegura]] · [[Checklist maestro]]
