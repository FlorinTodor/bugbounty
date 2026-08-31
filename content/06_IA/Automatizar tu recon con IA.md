---
tags: [ia, recon, automatizacion]
---
# Automatizar tu recon con IA

**Aquí está tu ventaja real sobre el cazador medio.** Sabes programar (Python + TS, TFG con
pipelines y agentes). La mayoría de cazadores copian scripts ajenos; tú puedes construir el tuyo.

> No se trata de "correr un escáner". Se trata de un **pipeline de monitorización continua** que te
> avisa cuando un target cambia — nuevo subdominio, nuevo endpoint en un bundle JS, nueva
> funcionalidad. **El primero que ve el cambio se lleva el bug.**

## Arquitectura mínima (empieza simple, mes 2-3)

```
[cron diario]
   └─> subfinder/amass  ──> subdominios nuevos ─┐
   └─> httpx            ──> vivos + tecnologías  │
   └─> descarga de JS   ──> diff de bundles      ├─> [LLM resume qué cambió]
   └─> nuclei (suave)   ──> findings conocidos   │        └─> notificación (Telegram)
                                                  ┘
```

Todo esto se guarda en `09_BITACORA/Targets/<target>/`.

## Dónde entra la IA (y dónde NO)

| Tarea | Herramienta clásica | Papel de la IA |
|---|---|---|
| Enumerar subdominios | subfinder, amass, chaos | ninguno |
| Detectar vivos/tech | httpx | ninguno |
| Fuzzing de rutas | ffuf, feroxbuster | **generar wordlists contextuales** ("esta app es de logística en español, dame 200 rutas probables") |
| Analizar bundles JS | linkfinder, JS scripts | **leer y extraer endpoints/secretos** — aquí brilla |
| Diff de cambios | git diff sobre snapshots | **resumir en lenguaje humano qué cambió y si es interesante** |
| Priorizar findings | — | **triage: "de estos 40 hallazgos de nuclei, cuáles merecen mi atención y por qué"** |
| Escribir el propio código del pipeline | — | **Claude Code te lo escribe y mantiene** |

## Proyecto guiado (constrúyelo con Claude Code)

1. **v0 (una tarde):** script que toma un dominio, corre subfinder+httpx y guarda `hosts.txt`.
2. **v1:** añade descarga de bundles JS y un `diff` contra la ejecución anterior.
3. **v2:** el diff se lo pasas a un LLM: *"resume qué endpoints/parámetros/secretos nuevos aparecen"*.
4. **v3:** notificación a tu Telegram cuando hay algo nuevo.
5. **v4:** cron diario en un VPS barato. Ya tienes monitorización continua de tus targets.

> Pídeselo a Claude Code paso a paso. Tú entiendes cada pieza (por eso funcionará y podrás
> arreglarlo cuando se rompa). Guarda el código en un repo privado tuyo.

## Reglas para no meterte en líos

- **Rate limiting suave.** Un recon agresivo puede tumbar un servicio pequeño = posible delito
  (ver [[Reglas del juego - legalidad y scope]]). Respeta los límites del programa.
- **Solo scope.** Tu automatización debe tener una **allowlist** de dominios del programa. Un bug
  en tu script que escanee fuera de scope es tu responsabilidad.
- **No subas a la IA** datos sensibles del target (ver [[Límites y riesgos de la IA]]).
- Herramientas: **ProjectDiscovery** (subfinder, httpx, nuclei, katana, chaos) es el stack estándar,
  gratis y en Go. Empieza por ahí antes de reinventar nada.

## Idea avanzada (para tu nicho)
Un agente que **vigile releases de librerías de ML** (huntr scope) y, cuando salga una versión,
haga `diff` del código y le pida a un LLM que señale sinks nuevos. Eso es aprovechar de verdad tu
perfil de [[Nicho - seguridad de IA y ML]].

Enlaces: [[Recon - superficie de ataque]] · [[Stack de herramientas]] · [[Nicho - seguridad de IA y ML]]
