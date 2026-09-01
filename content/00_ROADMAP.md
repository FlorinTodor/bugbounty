---
tags: [roadmap, moc, inicio]
aliases:
  - "🗺️ ROADMAP — por dónde ir con todo"
  - "ROADMAP"
  - "Roadmap maestro"
---
# 🗺️ ROADMAP — por dónde ir con todo

> [!important] Qué es esta nota
> El **mapa maestro**. [[Ruta de aprendizaje]] es el plan de *estudio*; esto es el plano de *todo a
> la vez*: en qué orden tocar **PortSwigger, HTB Academy, BBLabs y la caza real**, sin dispersarte.
> Si algún día no sabes qué hacer esta tarde, vuelve aquí. Léelo una vez entero y luego ve por fases.

## La regla que ordena todo lo demás

Tienes cuatro fuentes. No compiten, tienen **cada una su papel**:

| Fuente | Para qué sirve | Cuándo |
|---|---|---|
| **PortSwigger** (gratis) | **Aprender** la técnica a fondo | Siempre. Es el eje |
| **BBLabs** (7,99 €/mes) | **Validar** la técnica sobre un caso real | Mes 2-3 en adelante |
| **HTB Academy** (susc. estudiante) | **Temas que PortSwigger no cubre** + camino a cert | Cherry-pick, no entero |
| **Caza real** (gratis) | Lo único que importa | 1 tarde/semana desde la semana 6 |

> **El circuito de una clase de bug:** PortSwigger (aprendes) → BBLabs o HTB (validas en caso real) →
> **lo escribes en tu nota** de `02_VULNERABILIDADES` con tus palabras → lo pruebas en un target.
> Si te saltas el paso de escribir, no lo has aprendido. Ver [[IA para estudiar]].

---

## Las 5 fases (visión de un vistazo)

```
FASE 0  Montaje            sem 1        entorno + cuentas + leer legal
   │
FASE 1  HTTP y web moderna sem 1-3      el nivel de detalle donde viven los bugs
   │
FASE 2  Clases que pagan   sem 3-20     ← el grueso. Bloques A → B → C
   │                                      (aquí entran BBLabs y los módulos de HTB)
FASE 3  Caza real          sem 6+  ─────┐  EN PARALELO, no después
   │                                    │  1 tarde/semana pase lo que pase
FASE 4  Profesionalizar    mes 6-12  ◄──┘  nicho IA, recon propio, cert, privados
```

Detalle de cada fase, con entregables y checklist: **[[Ruta de aprendizaje]]**.

---

## Qué hacer en cada fase, con TODAS las fuentes

### FASE 0 — Montaje · semana 1
- [ ] [[Reglas del juego - legalidad y scope]] entero. **Innegociable.**
- [ ] [[Instalación del entorno]] (Burp, Firefox dedicado, extensiones, Go, recon).
- [ ] Crear cuentas: HackerOne, Bugcrowd, Intigriti, YesWeHack ([[Comparativa de plataformas]]).
- [ ] Mira **gratis** la Academy y el Roadmap de [[BBLabs - labs de reports reales]] (no lo sigas, solo ojéalo).
- [ ] Leer [[La verdad incómoda sobre el bug bounty]] y montar [[Rutina semanal]].

### FASE 1 — HTTP y web moderna · sem 1-3
- **PortSwigger**: módulo *Information disclosure* (calentamiento).
- **Vault**: [[HTTP a fondo]] · [[Sesiones, cookies y el modelo de origen]] · [[APIs REST y GraphQL]] · [[JavaScript moderno para hackers]].
- Todavía NO pagues HTB ni BBLabs.

### FASE 2 — Las clases que pagan · sem 3-20 (el grueso)
Aquí es donde se juntan las fuentes. Por bloques de [[MOC - Vulnerabilidades]]:

**Bloque A — el dinero (sem 3-9)** · aquí ya pagas BBLabs
- [[Broken Access Control e IDOR]] · [[Fallos de lógica de negocio]] · [[Autenticación y toma de cuentas]] · [[SSRF]] · [[Mass assignment]]
- **HTB** (cherry-pick): *Server-side Attacks* (SSRF/SSTI) y *Web Attacks* (IDOR/XXE). Los 2 de mayor ROI.
- **BBLabs**: el lab de IDOR / lógica / mass assignment como *examen* de cada tema.

**Bloque B — el volumen (sem 9-14)**
- [[XSS moderno]] · [[Inyecciones SQL y NoSQL]] · [[Subida de ficheros y path traversal]] · [[CSRF y CORS]] · [[Exposición de información y secretos]]
- **HTB**: *API Attacks* + *Attacking GraphQL* (tu especialización de APIs).

**Bloque C — lo que te diferencia (sem 14-20)** · aquí HTB suma más que en A/B
- [[OAuth, OIDC, SAML y JWT]] · [[Race conditions]] · [[Web cache poisoning y deception]] · [[HTTP request smuggling]] · [[Prototype pollution]] · [[SSTI e inyección de plantillas]] · [[Deserialización insegura]] · [[Subdomain takeover y errores de cloud]]
- **HTB (módulos sueltos, fuera del path 17)**: *Attacking Authentication Mechanisms*, *HTTP Attacks*, *Abusing HTTP Misconfigurations*, *Whitebox Attacks*, *Modern Web Exploitation Techniques*. Ver [[HTB Academy - qué hacer y qué saltarse]].

### FASE 3 — Caza real · desde la semana 6, EN PARALELO
- [[Recon - superficie de ataque]] · [[Metodología de caza]] · [[Checklist maestro]].
- Fichar 1 programa VDP en `09_BITACORA/Targets` y enviar el **primer report** (aunque sea Informative).
- **Semana 6 con un report enviado no es negociable.** Es el único hito que no depende de cuántos módulos lleves.

### FASE 4 — Profesionalizar · mes 6-12
- **Nicho IA**, empezado ya (no esperes aquí): los 3 módulos rentables del path *AI Red Teamer* de HTB (Prompt Injection, LLM Output, Attacking AI - App & System) + *Web LLM attacks* de PortSwigger. Ver [[Nicho - seguridad de IA y ML]].
- Recon propio continuo ([[Automatizar tu recon con IA]]), programas privados por invitación.
- **Cert opcional**: CBBH (path 17 entero) o COAE (path 405 entero). Para *cazar*, ninguna hace falta. Ver [[Certificaciones - cuáles valen la pena]].

---

## El calendario de gasto (para no pagar de más)

| Cuándo | Qué pagas | Por qué |
|---|---|---|
| Mes 1-2 | **Nada** (0 €) | PortSwigger es gratis y es el eje. Empieza hoy |
| Mes 2-3 | **BBLabs** 7,99 €/mes | Cuando ya tengas Access Control de PortSwigger, para validar en casos reales |
| Mes 3-4 | **HTB Academy** (susc. estudiante) | Solo para los módulos cherry-pick y el nicho IA |
| Mes 6-9 | Examen de cert (opcional) | Solo si quieres el CV, no para cazar |

Regla de oro del gasto: **nunca tres plataformas a la vez a medias**. Una a fondo > tres de pasada.

---

## Los 3 errores que te van a tentar (y que este roadmap evita)

1. **Hacer los paths de HTB enteros y en serie.** No: cherry-pick. Ver [[HTB Academy - qué hacer y qué saltarse]].
2. **Esperar a "saber suficiente" para cazar.** No hay umbral. Se aprende cazando: semana 6, report enviado.
3. **Confundir ver vídeos con estudiar.** Un vídeo → una nota escrita, o no cuenta. Ver [[BBLabs - labs de reports reales]].

---

## Hitos (de [[Ruta de aprendizaje]])

| Mes | Hito |
|---|---|
| 1 | Entorno + 50 labs PortSwigger + cuentas |
| 2 | Bloque A empezado + 1er target + 1er report |
| 4 | Bloque A y B completos + 3 targets trabajados |
| 6 | Primera resolución válida (Triaged) |
| 9 | Primer bounty + recon propio funcionando |
| 12 | Programa privado, o primer bug en el nicho de IA |

---

Siguiente paso concreto: abre **[[EMPIEZA AQUÍ]]** y lee las 5 notas en orden. Luego vuelve a la Fase 0.
