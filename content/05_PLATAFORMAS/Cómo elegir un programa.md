---
tags: [plataformas, metodologia]
---
# Cómo elegir un programa

> **El 50% de tu resultado se decide aquí, antes de lanzar una sola petición.**
> Elegir mal un programa es garantizarte 40 horas de duplicados.

## Criterios de selección (para alguien que empieza)

### ✅ Busca

| Señal | Por qué |
|---|---|
| **Programa lanzado hace poco** (< 3 meses) | Nadie lo ha peinado todavía. La mejor señal de todas |
| **Scope amplio o wildcard** (`*.empresa.com`) | Más superficie = más sitios donde nadie ha mirado |
| **Aplicación con lógica de negocio rica** (marketplace, SaaS multi-tenant, banca, sanidad, educación) | Roles, permisos, planes → IDOR y fallos de lógica a punta pala |
| **Empresa mediana / no tecnológica** | Menos madurez de seguridad que Google |
| **Tiempo de respuesta bueno** (`< 1 semana` en las estadísticas) | Un programa que tarda 6 meses te quema |
| **VDP de empresa grande** | Sin pago, pero **muy poca competencia** y triage real. Ideal para tus 3 primeros meses |
| **Registro abierto con roles** (free / pro / admin de organización) | Puedes crear tú mismo las cuentas para probar access control |
| **Que puedas usarla de verdad** como usuario | Los bugs de lógica salen de entender el producto |

### ❌ Evita al principio

| Señal | Por qué |
|---|---|
| Google, Meta, Apple, PayPal, Shopify… | Miles de cazadores a tiempo completo llevan años ahí |
| Scope de un solo dominio pequeño y estático | Nada que buscar; ya lo miraron todos |
| Programas con muchos "N/A" en sus estadísticas | Triage hostil |
| "Solo aceptamos Critical/High" con pagos ridículos | Trabajarás gratis |
| Todo lo interesante en **out of scope** | Léelo antes: a veces el scope real es 3 URLs |
| Web3 / smart contracts | Otro stack entero. No ahora |

## Procedimiento concreto (30-45 min por candidato)

1. **Filtra** en la plataforma por fecha de lanzamiento y por scope wildcard.
2. **Lee el brief entero.** Anota: scope, exclusiones, rate limits, requisito de User-Agent, tabla de pagos.
3. **Regístrate como usuario** en la aplicación. Usa 2 cuentas (`+bb1@`, `+bb2@` con Gmail).
4. **Úsala 20 minutos como usuario normal** con Burp en segundo plano grabando. Sin atacar nada.
5. Pregúntate: *¿entiendo qué vende esta empresa y quién puede ver qué?* Si no, es mala elección.
6. Rellena `_plantillas/Plantilla - Target` en `09_BITACORA/Targets` y decide: **entro o descarto**.

## Regla de la profundidad

> Es mejor **un target durante 3 meses** que 30 targets durante un día cada uno.

Los bugs fáciles de un target caen en las primeras 4 horas — y ya los encontró otro. Los que pagan
aparecen en la hora 20, cuando entiendes el modelo de permisos mejor que sus desarrolladores.

## Cuándo abandonar un target

- 15-20 h sin una sola anomalía interesante (no bug: **anomalía**).
- El programa te ha cerrado 3 reports razonables como N/A sin explicación.
- Han rediseñado la app y tu mapa ya no vale (a veces esto es lo contrario: **oportunidad**, un
  rediseño reciente es oro).

Enlaces: [[Comparativa de plataformas]] · [[Metodología de caza]] · [[Plantilla - Target]]
