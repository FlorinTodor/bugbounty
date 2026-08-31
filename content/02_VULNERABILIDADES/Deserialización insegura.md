---
tags: [vulnerabilidad]
clase: Deserialization
estado: 🔴 pendiente
paga_bien: ⭐⭐⭐
---
# Deserialización insegura

> Esqueleto. Complétalo **con tus palabras** al hacer los labs. Estructura completa en
> `_plantillas/Plantilla - Vulnerabilidad`.

## Qué es
Deserializar datos no confiables → ejecución de código. **Muy relevante para tu nicho de IA**: pickle, joblib, torch.load, PyYAML \`yaml.load\`, y en otros stacks Java (ysoserial), PHP (\`__wakeup\`), .NET, Node. En librerías de ML es casi RCE directa al cargar un modelo/dataset malicioso.

## Labs de PortSwigger (fuente principal)
- [ ] Insecure deserialization (módulo)

## Recursos
- PayloadsAllTheThings (categoría correspondiente) — payloads reales.
- HackTricks — técnicas y bypass.

## Mis notas de caza
- 

Enlaces: [[Nicho - seguridad de IA y ML]] · [[SSTI e inyección de plantillas]]
