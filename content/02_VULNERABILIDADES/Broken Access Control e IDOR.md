---
tags: [vulnerabilidad]
clase: Broken Access Control
estado: 🔴 pendiente
owasp: A01:2021
paga_bien: ⭐⭐⭐ (la nº1)
---
# Broken Access Control e IDOR

> **La clase que más dinero mueve en bug bounty** y la que ninguna herramienta encuentra bien,
> porque depende de **entender quién debería poder ver qué**. Tu prioridad nº1.

## Qué es
El servidor no comprueba (o comprueba mal) que el usuario tiene permiso para la acción/recurso.
- **IDOR** (Insecure Direct Object Reference): cambias un identificador y accedes a algo ajeno.
- **Escalada horizontal**: acceder a datos de *otro usuario del mismo nivel*.
- **Escalada vertical**: hacer cosas de un rol superior (admin) siendo usuario normal.

## Por qué existe
El desarrollador confía en que el frontend "no muestra" el botón, pero el endpoint sigue ahí.
Autorización comprobada en el cliente, no en el servidor.

## Cómo lo pruebo (procedimiento con 2 cuentas)
1. Crea **cuenta A** y **cuenta B**. Haz una acción en A que genere un recurso con ID.
2. Captura la petición en Burp. Manda al Repeater.
3. Repite la petición **con la sesión de B** pero el **ID de A**. ¿Accedes? → IDOR.
4. Variantes del identificador:
   - Numérico: +1/-1, IDs adivinables.
   - UUID/hash: ¿es predecible? ¿es base64 de un email/id?
   - Cambia el objeto pero no el tenant, o el tenant pero no el objeto.
5. **Autorize** (extensión Burp): configura la sesión de B como "low-priv" y navega con A;
   te marca automáticamente cada endpoint donde B accede a algo de A. Imprescindible.
6. Escalada vertical: fuerza rutas/acciones de admin que viste en el JS con tu sesión normal.

## Dónde mirar
- Cualquier `id`, `user_id`, `account_id`, `order_id`, `file_id`, `uuid` en URL, body o cabecera.
- Endpoints de export/download (`/invoice/123.pdf`).
- APIs REST y **GraphQL** (nodos por ID).
- Parámetros de tenant/organización en SaaS multi-tenant.
- Mass assignment: añade `"role":"admin"`, `"isAdmin":true`, `"userId":<otro>` al JSON.

## Técnicas de bypass
- Cambiar método HTTP (GET↔POST↔PUT↔DELETE).
- Añadir/quitar extensión (`.json`), añadir parámetros duplicados.
- Wrappers de URL: `/user/2` bloqueado pero `/user/2/` o `/user/%32` no.
- Force browsing a rutas de admin.

## Impacto (para el report)
"Cualquier usuario autenticado puede leer/modificar los datos de cualquier otro usuario" →
normalmente **High/Critical**. Concreta qué datos y qué acción.

## Labs de PortSwigger (hazlos TODOS)
- [ ] Access control vulnerabilities (módulo completo, ~13 labs)
- [ ] Los de IDOR y los de escalada vertical/horizontal

## ⚠️ Legal
Al probar IDOR tocarás datos de "otro usuario" = **tu cuenta B**, no usuarios reales. Si por error
ves datos de un usuario real, para, captura mínimo, redacta. Ver [[Reglas del juego - legalidad y scope]].

## Mis notas de caza
- 

Enlaces: [[Checklist maestro]] · [[Fallos de lógica de negocio]] · [[APIs REST y GraphQL]]
