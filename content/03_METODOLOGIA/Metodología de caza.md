---
tags: [metodologia, moc]
---
# Metodología de caza

Qué haces, en orden, cuando te sientas a cazar. Basado en cómo trabajan los cazadores que viven de
esto, adaptado a alguien que empieza y prioriza **profundidad sobre amplitud**.

## Las 5 fases

### 1. Selección (una vez por target, no cada sesión)
→ [[Cómo elegir un programa]]. Result: un target fichado en `09_BITACORA/Targets`.

### 2. Recon y mapeo (primeras 2-4 sesiones de un target)
→ [[Recon - superficie de ataque]]. Objetivo: **un mapa** de subdominios, tecnologías, endpoints,
roles y flujos. No buscas bugs aún: construyes el terreno.

### 3. Comprensión del negocio (lo que casi nadie hace = donde están tus bugs)
- Regístrate, crea 2 cuentas, paga si hay plan gratis con trial.
- Dibuja: **qué roles hay**, **qué recurso pertenece a quién**, **qué flujos multi-paso existen**
  (checkout, invitaciones, transferencias, cambios de plan).
- Pregúntate constantemente: *"¿qué NO debería poder hacer yo aquí?"* → esa lista es tu plan de ataque.

### 4. Caza dirigida (el grueso de las sesiones)
Un objetivo por sesión, del [[Checklist maestro]]. Ejemplos de objetivo de sesión:
- "Hoy solo access control en el módulo de facturación."
- "Hoy solo el flujo de reset de contraseña."
- "Hoy solo el chatbot de IA y sus herramientas."
Timeboxing de 45 min por hipótesis (ver [[Rutina semanal]]).

### 5. Confirmación y report
Reproduces con 2 cuentas, capturas evidencia mínima, mides impacto real, y escribes.
→ [[Cómo escribir un buen report]].

## El bucle mental (lo que distingue a un cazador de un escáner)

```
OBSERVAR  → veo algo (un parámetro id, una respuesta rara, un rol, un flujo)
HIPÓTESIS → "¿y si este id lo puedo cambiar por el de otro usuario?"
PROBAR    → lo pruebo con mi 2ª cuenta, mínimamente
OBSERVAR  → ¿qué devolvió? ¿coincide con mi hipótesis?
   └─> anomalía → profundizo
   └─> nada     → siguiente hipótesis, anoto la descartada
```

**El activo no son los bugs: son las anomalías.** Anota cada respuesta rara aunque no sepas
explotarla. Muchos bugs son 3 anomalías que encajan una semana después.

## Dónde mirar primero (mapa de calor de dónde salen los bounties)

1. **Funciones nuevas / recién lanzadas** — código con prisa, nadie las auditó.
2. **Todo lo que tenga un ID en la URL o el body** — candidato a IDOR.
3. **Flujos con dinero o permisos** — checkout, upgrades, invitaciones, roles de organización.
4. **Importar/exportar/subir** — ficheros, URLs (SSRF), parsers (XXE), plantillas (SSTI).
5. **Integraciones y webhooks** — SSRF, secretos, confianza mal puesta.
6. **Zonas "de admin" que asoman en el JS** aunque no deberías ver.
7. **APIs sin documentar** que descubres en los bundles.
8. **Cualquier chatbot/IA** — ver [[Nicho - seguridad de IA y ML]].

## Anti-patrones

- ❌ Lanzar nuclei/escáner y reportar lo que salga → duplicados garantizados.
- ❌ Saltar de target en target buscando fruta fácil → ya la cogieron.
- ❌ Buscar "un XSS" en abstracto → busca romper **una regla concreta del negocio**.
- ❌ No anotar → repites trabajo y pierdes las anomalías.

Enlaces: [[Recon - superficie de ataque]] · [[Checklist maestro]] · [[Bitácora]] · [[Cómo escribir un buen report]]
