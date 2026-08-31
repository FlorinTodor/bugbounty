---
tags: [reportes, imprescindible]
---
# Cómo escribir un buen report

> El report **es el producto que vendes.** El mismo bug, bien o mal escrito, es la diferencia entre
> un bounty pagado y un "N/A - no impact". Muchos cazadores buenos cobran poco por escribir fatal.

## Estructura estándar (funciona en todas las plataformas)

### 1. Título
Claro, específico, con impacto. Formato: **[Tipo] en [ubicación] permite [impacto]**.
- ✅ `IDOR en /api/v1/invoices/{id} permite leer facturas de cualquier usuario`
- ❌ `Vulnerabilidad grave` / `Encontré un bug`

### 2. Resumen (2-3 frases)
Qué es, dónde, y por qué le importa a la empresa. El triager decide en estas líneas si te toma en serio.

### 3. Severidad + CVSS
Da tu **vector CVSS 3.1** razonado. No infles: un triager detecta el inflado y te penaliza.
Consulta la **VRT de Bugcrowd** para saber cómo clasifican ellos. Ver [[Severidad y CVSS]].

### 4. Pasos de reproducción
**Lo más importante.** Numerados, exactos, reproducibles por alguien que no conoce la app:
1. Inicia sesión como Usuario A (`bb1@...`). Ve a X.
2. Captura la petición `GET /api/...`. Copia tu `id`.
3. Inicia sesión como Usuario B. Repite con el `id` de A.
4. Observa que la respuesta contiene los datos de A.

Incluye **peticiones/respuestas HTTP completas** (redacta tokens y PII), capturas, y si ayuda un
vídeo corto. Un curl o un Repeater que reproduzca el bug vale oro.

### 5. Impacto
Traduce a **negocio**, no a jerga: *"cualquier usuario autenticado puede leer las facturas
—con nombre, dirección e importe— de todos los demás clientes"*. Concreto y verificable, sin drama.

### 6. Remediación
Una recomendación breve y correcta. Demuestra que entiendes el problema y agiliza el fix (y a veces
sube la valoración): *"validar en el servidor que el `invoice.owner_id == session.user_id`"*.

## Reglas de oro

1. **Un report = un bug.** No metas cinco cosas en uno.
2. **Reprodúcelo tú antes de enviar.** Con cuentas limpias, desde cero. Ver [[Límites y riesgos de la IA]].
3. **No exageres el impacto.** Es la forma más rápida de perder credibilidad con un programa.
4. **Redacta claro y sobrio.** Sin "hola espero que estés bien", sin relleno, sin amenazas de
   divulgación. Profesional y directo.
5. **Evidencia mínima suficiente.** Demuestra el bug, no acumules datos de usuarios (legal + ética).
6. **Antes de enviar**: ¿está en scope? ¿es duplicado obvio? ¿es un Informative disfrazado?

## Cómo ayuda la IA aquí (bien usada)
La IA **redacta el borrador** a partir de los pasos que **tú ya reprodujiste**, estima el CVSS y
mejora la redacción. Tú verificas cada afirmación técnica. Prompt en [[Biblioteca de prompts]].
Nunca al revés: la IA no descubre ni confirma el bug.

## Qué NO reportar (te baja la reputación)
Ver la lista de Informatives en [[Triage - qué esperar de la respuesta]]. Regla rápida: si no
puedes describir un **atacante, una acción y una víctima concretos**, probablemente es Informative.

Enlaces: [[Severidad y CVSS]] · [[Triage - qué esperar de la respuesta]] · [[Plantilla - Report]]
