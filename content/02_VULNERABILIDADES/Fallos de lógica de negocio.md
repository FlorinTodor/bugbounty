---
tags: [vulnerabilidad]
clase: Business Logic
estado: 🔴 pendiente
owasp: A04:2021
paga_bien: ⭐⭐⭐
---
# Fallos de lógica de negocio

> La segunda clase más rentable, y **la más segura frente a la competencia**: no la encuentra
> ningún escáner porque no hay "payload". Requiere entender el negocio, que es justo lo que tú
> puedes hacer mejor que una herramienta.

## Qué es
Explotar el **flujo previsto** de la aplicación de formas que los diseñadores no anticiparon. No
rompes la sintaxis; rompes las **reglas de negocio**.

## Ejemplos clásicos
- Precio/cantidad **negativos** o manipulados en el carrito → te pagan a ti.
- **Saltarse pasos** de un flujo multi-paso (ir directo al paso 4 sin pagar en el 3).
- **Reutilizar** algo de un solo uso: cupón, token de invitación, código de referido.
- **Condiciones de carrera** en límites (retirar dinero 2 veces a la vez) → [[Race conditions]].
- Saltarse **límites de plan** (usar features de pago siendo free).
- Manipular la **moneda** o el **redondeo**.
- Registro/invitación que te da un rol que no deberías (te invitan como "viewer", te haces "admin").

## Cómo se cazan
1. **Entiende el negocio primero.** ¿Qué gana dinero? ¿Qué límites hay? ¿Qué pasos tiene cada flujo?
2. Por cada regla, pregúntate: *"¿qué pasa si la salto, la repito, la hago al revés, o mando un
   valor imposible?"*
3. Mapea flujos multi-paso en Burp y prueba a **saltar, reordenar o repetir** peticiones.
4. Prueba valores límite: 0, negativos, enormes, decimales, otra moneda, otro tipo.

## Impacto
Suele ser **directo y grave** (pérdida económica, acceso indebido) → paga bien porque el negocio
lo entiende sin explicaciones técnicas.

## Labs de PortSwigger
- [ ] Business logic vulnerabilities (módulo completo)

## Mis notas de caza
- 

Enlaces: [[Metodología de caza]] · [[Broken Access Control e IDOR]] · [[Race conditions]]
