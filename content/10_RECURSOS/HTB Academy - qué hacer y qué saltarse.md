---
tags: [recursos, htb, plan]
---
# HTB Academy - qué hacer y qué saltarse

> [!important] Regla de oro
> Tu material nº1 sigue siendo **PortSwigger Web Security Academy (gratis)**. HTB Academy aporta
> **estructura, temas que PortSwigger no cubre, entorno guiado y el camino a los certs**.
> Si una tarde tienes que elegir: PortSwigger gana para bug bounty puro.
> El error caro con HTB no es pagar la mensualidad: es **hacer los paths enteros y en serie**.

**Actualizado 2026-09-01** con los dos paths que vas a empezar. Nota de nomenclatura: el antiguo
job role path *"Bug Bounty Hunter"* ahora se llama **Web Penetration Tester** (sigue preparando el
**CBBH**), y el módulo *"Attacking Web Applications with Ffuf"* ahora se llama **Web Fuzzing**.

---

## PATH 17 — Web Penetration Tester (→ CBBH)

`https://academy.hackthebox.com/app/paths/17/details` · 20 módulos · 279 secciones · nivel Medium

### Veredicto: **no lo hagas entero. Cherry-pick.**

Los ~11 primeros módulos son tu base de máquinas HTB, que **ya tienes**. Pagar 150-200 h por
reaprender XSS y SQLi básico es el peor uso posible de tus tardes.

**Excepción:** si vas a por el **CBBH** como línea de CV (prácticas, primer empleo), el examen
exige el path → entonces sí, entero. Pero para *cazar* no necesitas el cert.

### Sáltate o pasa en diagonal (ya lo sabes)
Web Requests · Introduction to Web Applications · Cross-Site Scripting (XSS) ·
SQL Injection Fundamentals · SQLMap Essentials · Command Injections · File Upload Attacks ·
File Inclusion · Login Brute Forcing · JavaScript Deobfuscation

Si alguno te incomoda, hazle solo el **Skills Assessment**. Si lo pasas, salta el módulo entero.

### Los 8 que sí valen, en este orden

| # | Módulo | Por qué | Nota del vault |
|---|---|---|---|
| 1 | **Server-side Attacks** | SSRF + SSTI. Gap directo tuyo, y el SSRF es de los que mejor pagan | [[SSRF]] · [[SSTI e inyección de plantillas]] |
| 2 | **Web Attacks** | IDOR, HTTP verb tampering, XXE. El núcleo del access control | [[Broken Access Control e IDOR]] |
| 3 | **API Attacks** | APIs REST en producción, no CTF | [[APIs REST y GraphQL]] |
| 4 | **Attacking GraphQL** | Introspección, batching, autorización por resolver | [[APIs REST y GraphQL]] |
| 5 | **Broken Authentication** | Base para el módulo de auth avanzada de más abajo | [[Autenticación y toma de cuentas]] |
| 6 | **Information Gathering - Web Edition** + **Web Fuzzing** | Recon web; alimenta tu pipeline | [[Recon - superficie de ataque]] |
| 7 | **Attacking Common Applications** | WordPress, Jenkins, Tomcat, Splunk. Pan de cada día en scopes amplios | [[Metodología de caza]] |
| 8 | **Bug Bounty Hunting Process** | Corto. Marco de reporte y comunicación | [[Cómo escribir un buen report]] |

Los **dos primeros son los de mayor ROI hoy**. Empieza por ahí.

---

## PATH 405 — AI Red Teamer (→ COAE)

`https://academy.hackthebox.com/app/paths/405/details` · 12 módulos · 230 secciones · nivel Hard
Hecho **con Google**, alineado con su framework SAIF. Cert asociada: **HTB Certified Offensive AI
Expert (COAE)** — examen práctico de 7 días con informe.

### Veredicto: **es tu path, pero no todo él sirve para bounties, y no va después: va en paralelo.**

Es exactamente [[Nicho - seguridad de IA y ML]]. Tu TFG (agentes LLM, RAG, Neo4j) te pone por
delante de casi todo el mundo aquí — y esa ventaja **caduca**: cada mes hay más gente formada.

### Módulo a módulo

| Módulo | Secc. | Valor para **cazar** |
|---|---|---|
| Fundamentals of AI | 24 | ⏭️ **Sáltalo.** Ya lo sabes por el TFG |
| Applications of AI in InfoSec | 25 | ⏭️ En diagonal. Es ML *para* seguridad, no seguridad *de* la IA |
| Introduction to Red Teaming AI | 11 | ✅ Corto y da el marco. Hazlo primero |
| **Prompt Injection Attacks** | 12 | 🔥 **Alto.** Directa e indirecta, jailbreaks, casos reales |
| **LLM Output Attacks** | 14 | 🔥 **Alto.** Es XSS/SSRF/SQLi *a través* de la salida del modelo → tu base clásica aplicada. Probablemente el módulo más rentable del path |
| **Attacking AI - Application and System** | 14 | 🔥 **Alto.** La app *alrededor* del modelo: deserialización, cadena de suministro, agentes con herramientas. Es lo de **huntr** |
| AI Data Attacks | 25 | 🟡 Medio. Envenenamiento de datos; aparece, pero menos |
| AI Privacy | 21 | 🟡 Medio. Extracción de datos de entrenamiento, membership inference |
| AI Evasion - Foundations | 12 | 🔻 **Bajo para bounty.** Adversarial ML académico |
| AI Evasion - First-Order Attacks | 23 | 🔻 Bajo. Gradientes, perturbaciones |
| AI Evasion - Sparsity Attacks | 28 | 🔻 Bajo. 63 secciones entre los tres y casi ningún programa paga por esto |
| AI Defense | 21 | 🟡 Medio. Útil si acabas trabajando en el lado defensivo |

**Traducción:** de 230 secciones, las que convierten en dinero son ~**40** (los tres 🔥).
Eso son dos o tres semanas de tardes, no medio año.

Los AI Evasion sí valen para el **COAE**, para red team interno y para el CV. Déjalos para después,
con calma, si decides ir a por la cert.

> [!tip] Y no necesitas nada de esto para empezar en huntr
> Gran parte de lo que se reporta ahí es **appsec clásico sobre repos de ML**: deserialización de
> pickles, path traversal en cargadores de modelos, RCE en frameworks. Eso ya lo puedes hacer hoy
> con tu nivel + Python. Ver [[Nicho - seguridad de IA y ML]] y [[Deserialización insegura]].

---

## Módulos fuera de esos dos paths que sí te convienen

Esto es donde HTB **suma de verdad sobre PortSwigger**, y no está en el path 17. Coincide con el
**Bloque C** de [[Ruta de aprendizaje]].

| Módulo | Dif. | Secc. | Qué cubre | Nota del vault |
|---|---|---|---|---|
| **Attacking Authentication Mechanisms** | Medium | 20 | JWT (algorithm confusion, secretos débiles), OAuth (robo de token, CSRF en el flujo), SAML (signature wrapping/exclusion) | [[OAuth, OIDC, SAML y JWT]] |
| **HTTP Attacks** | Hard | 18 | CRLF injection, response splitting, request smuggling (CL.TE / TE.TE / TE.CL), HTTP/2 downgrading | [[HTTP request smuggling]] |
| **Abusing HTTP Misconfigurations** | Hard | 20 | Web cache poisoning, Host header attacks, password reset poisoning, session puzzling | [[Web cache poisoning y deception]] |
| **Whitebox Attacks** | Hard | 15 | Prototype pollution, race conditions, timing attacks, type juggling en PHP — **desde el código fuente** | [[Prototype pollution]] · [[Race conditions]] |
| **Modern Web Exploitation Techniques** | Hard | 18 | DNS rebinding y bypass de filtros SSRF, vulns de **segundo orden** (IDOR/LFI/cmdi almacenados), ataques a **WebSockets** (CSWH) | [[SSRF]] · [[Broken Access Control e IDOR]] |
| **Introduction to / Advanced Deserialization Attacks** | Hard | — | Deserialización en varios lenguajes. **Directamente rentable en huntr** | [[Deserialización insegura]] |
| **Session Security** | Medium | — | Fijación, hijacking, CSRF, gestión de sesión | [[CSRF y CORS]] |
| **Introduction to NoSQL Injection** | Medium | — | Mongo y compañía | [[Inyecciones SQL y NoSQL]] |
| **Blind SQL Injection** / **Advanced SQL Injections** | Hard | — | Subir de tu nivel actual a ciega y out-of-band | [[Inyecciones SQL y NoSQL]] |
| **Advanced XSS and CSRF Exploitation** | Medium | — | Encadenar XSS a impacto real | [[XSS moderno]] |

> [!note] Honestidad sobre el solapamiento
> Smuggling, cache poisoning, prototype pollution y race conditions los inventó/documentó
> PortSwigger y **sus labs son mejores**. Lo que HTB añade de verdad es: el ángulo **whitebox**
> (leer el código y encontrarlo, que es tu punto fuerte), **WebSockets**, **segundo orden**,
> **session puzzling**, **type juggling** y **SAML**. Ese es el motivo real para tocarlos aquí.

---

## Qué saltarse sin remordimiento

- ❌ Todo lo de **Active Directory**, Windows interno, pivoting, C2, post-explotación. Es CPTS/OSCP,
  no bug bounty.
- ❌ Fundamentos de **Linux/redes** — ya los dominas, tienes vault propio.
- ❌ Los tres **AI Evasion** *por ahora* (63 secciones que no cazan bugs).
- ❌ **Máquinas de HTB** (el HTB "normal", no Academy): máximo 1 al mes por diversión.
- ❌ Cualquier módulo que empieces "por completar el path". Ve por **objetivos**.

---

## Orden concreto de arranque

El plan de "path 17 entero → cazar → path 405 entero" son ~510 secciones **antes de tocar tu ventaja
diferencial**. Esto es lo mismo en un tercio del tiempo:

**Semanas 1-3 — el ROI inmediato**
- [ ] HTB: **Server-side Attacks**
- [ ] HTB: **Web Attacks**
- [ ] PortSwigger: *Access control* completo (incluidos los Expert) → [[Broken Access Control e IDOR]]
- [ ] Crear cuentas de plataforma y fichar 1 programa VDP en `09_BITACORA/Targets`

**Semanas 3-6 — APIs + entrar en el nicho ya**
- [ ] HTB: **API Attacks** + **Attacking GraphQL**
- [ ] HTB: **Introduction to Red Teaming AI** (corto) → **Prompt Injection Attacks** → **LLM Output Attacks**
- [ ] PortSwigger: *Web LLM attacks* (gratis, 2-3 tardes)
- [ ] **1 tarde/semana de caza real**, sin excepciones

**Semanas 6-10 — la app alrededor del modelo**
- [ ] HTB: **Attacking AI - Application and System**
- [ ] Elegir 2 repos de huntr que conozcas (LangChain, Gradio, MLflow…) y revisar código buscando
      `pickle.load`, `yaml.load`, `eval`, `subprocess`, `torch.load`, rutas construidas con input
- [ ] HTB: **Attacking Authentication Mechanisms** + PortSwigger OAuth/JWT

**Semanas 10+ — Bloque C y decisión de cert**
- [ ] HTB: **Whitebox Attacks**, **Modern Web Exploitation Techniques**, **HTTP Attacks**,
      **Abusing HTTP Misconfigurations**, **Deserialization**
- [ ] Decidir: ¿**CBBH** (path 17 entero) o **COAE** (path 405 entero)? Si el objetivo es dinero por
      bounties, **ninguno de los dos es necesario**. Si es CV/empleo, el que apunte al trabajo que
      quieras. Ver [[Certificaciones - cuáles valen la pena]]

> [!warning] La regla que más te va a costar cumplir
> **No hay un umbral de conocimiento que "desbloquea" cazar.** Se aprende cazando. Si a la semana 6
> no has enviado un report, el plan ha fallado, por muchos módulos que lleves verdes.

Enlaces: [[Ruta de aprendizaje]] · [[Certificaciones - cuáles valen la pena]] ·
[[Nicho - seguridad de IA y ML]] · [[MOC - Vulnerabilidades]] · [[Enlaces]]
