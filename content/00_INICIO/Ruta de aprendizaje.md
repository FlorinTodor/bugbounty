---
tags: [inicio, roadmap]
---
# Ruta de aprendizaje

Plan de 12 meses, diseñado **para tu punto de partida concreto** (tu punto de partida),
asumiendo ~10-12 h/semana por las tardes.

> [!important] Decisión de gasto (léela antes de pagar nada)
> **PortSwigger Web Security Academy es gratis y es el mejor material del mundo para bug bounty web.**
> ~250 labs, escritos por la gente que hace Burp y que descubrió el request smuggling moderno.
> **Ese es tu material principal.** HTB Academy es un complemento útil (estructura, cert CBBH,
> APIs, cloud), no el eje. Ver [[HTB Academy - qué hacer y qué saltarse]].
> Traducción: **puedes empezar hoy con 0 €** y suscribirte a HTB en el mes 2-3.

---

## FASE 0 — Montaje (semana 1, ~6 h)

- [ ] Leer [[Reglas del juego - legalidad y scope]] entero. **Innegociable.**
- [ ] Montar entorno: [[Instalación del entorno]] (Burp CE, Firefox dedicado, extensiones, Go, contenedor de recon).
- [ ] Crear cuentas: HackerOne, Bugcrowd, Intigriti, YesWeHack. Ver [[Comparativa de plataformas]].
- [ ] Leer [[La verdad incómoda sobre el bug bounty]].
- [ ] Configurar [[Rutina semanal]] en tu calendario. Bloques reales, no "cuando pueda".

## FASE 1 — HTTP y web moderna a nivel de detalle (semanas 1-3, ~30 h)

No es repaso: es el nivel de detalle donde viven los bugs.

- [ ] [[HTTP a fondo]] — parsing de cabeceras, `Host`, `Transfer-Encoding` vs `Content-Length`,
      codificaciones, parser differentials, unicode/normalización.
- [ ] [[Sesiones, cookies y el modelo de origen]] — SameSite, `Secure`/`HttpOnly`, CORS, SOP,
      postMessage, service workers.
- [ ] [[APIs REST y GraphQL]] — verbos, versionado, introspección GraphQL, batching.
- [ ] [[JavaScript moderno para hackers]] — leer bundles, source maps, dónde están los endpoints.
- [ ] PortSwigger: módulo *Information disclosure* completo (calentamiento fácil).

**Entregable:** interceptar y entender por completo una app real que uses a diario (tu banco no;
usa una app cuyo programa de bug bounty exista) y dibujar su mapa de endpoints.

## FASE 2 — Las clases de bug que pagan (semanas 3-20, el grueso)

Orden **por retorno económico real**, no por el orden de OWASP. Una nota por clase en
`02_VULNERABILIDADES`; cada una tiene labs de PortSwigger asignados.

**Bloque A — el dinero de verdad (semanas 3-9)**
- [ ] [[Broken Access Control e IDOR]] ← **empieza por aquí, es la nº1 en pagos**
- [ ] [[Fallos de lógica de negocio]] ← nº2, y no la encuentra ninguna herramienta
- [ ] [[Autenticación y toma de cuentas]] (reset de contraseña, 2FA bypass, account takeover)
- [ ] [[SSRF]] (incluida explotación cloud: metadata AWS/GCP)

**Bloque B — el volumen (semanas 9-14)**
- [ ] [[XSS moderno]] (DOM, sinks de frameworks, CSP bypass, mXSS)
- [ ] [[Inyecciones SQL y NoSQL]] (subir de tu nivel actual a blind/out-of-band)
- [ ] [[Subida de ficheros y path traversal]]
- [ ] [[CSRF y CORS]]
- [ ] [[Exposición de información y secretos]]

**Bloque C — lo que te diferencia (semanas 14-20)**
- [ ] [[OAuth, OIDC, SAML y JWT]]
- [ ] [[Race conditions]]
- [ ] [[Web cache poisoning y deception]]
- [ ] [[HTTP request smuggling]]
- [ ] [[Prototype pollution]]
- [ ] [[SSTI e inyección de plantillas]]
- [ ] [[Deserialización insegura]]
- [ ] [[Subdomain takeover y errores de cloud]]

**Regla:** no pases de bloque sin haber hecho **todos los labs de PortSwigger** de ese tema,
incluidos los *Expert*. Los Expert son los que se parecen a la vida real.

## FASE 3 — Recon y primer target real (a partir de la semana 6, **en paralelo**)

No esperes a terminar la Fase 2. Desde la semana 6, **1 tarde a la semana es de caza real**.

- [ ] [[Recon - superficie de ataque]] — metodología completa
- [ ] [[Metodología de caza]] — qué hacer en las 4 horas de una sesión
- [ ] [[Checklist maestro]] — lo que pruebas en cada endpoint
- [ ] Elegir **un** programa VDP y ficharlo en `09_BITACORA/Targets`
- [ ] Primer report enviado (aunque sea Informative). El objetivo es **pasar el miedo**.

## FASE 4 — Profesionalizar (meses 6-12)

- [ ] Especialización: elige 2. Recomendadas para ti: **APIs/lógica de negocio** + [[Nicho - seguridad de IA y ML]].
- [ ] Automatización propia: [[Automatizar tu recon con IA]] — monitorización continua de tus targets.
- [ ] Objetivo de reputación: entrar en **programas privados por invitación** (ahí baja la competencia).
- [ ] Opcional: certificación **CBBH** de HTB si quieres que esto también te sirva en el CV.
      Ver [[Certificaciones - cuáles valen la pena]].
- [ ] Colaborar con otro cazador (los duos funcionan muy bien: uno recon, otro explotación).

---

## Hitos medibles (no dependen de la suerte)

| Mes | Hito |
|---|---|
| 1 | Entorno montado + 50 labs de PortSwigger + cuentas creadas |
| 2 | Bloque A empezado + primer target fichado + primer report enviado |
| 3 | 120 labs + [[Checklist maestro]] personalizado con cosas tuyas |
| 4 | Bloque A y B completos + 3 targets trabajados en profundidad |
| 6 | Todos los labs relevantes + primera resolución válida (Triaged) |
| 9 | Primer bounty pagado + pipeline de recon propio funcionando |
| 12 | Invitación a programa privado, o primer bug en el nicho de IA |

---

## Qué NO hacer en esta ruta

- ❌ No hagas OSCP ahora. Es de pentesting interno/AD, no de bug bounty. Cuesta ~1.600 € y no
  te va a dar un solo bounty. Ver [[Certificaciones - cuáles valen la pena]].
- ❌ No hagas máquinas de HTB "para practicar". Son divertidas y **no se parecen** al bug bounty.
  Como mucho, 1 al mes por diversión.
- ❌ No te compres cursos de Udemy de bug bounty. Todos son peores que PortSwigger, que es gratis.
- ❌ No empieces por móvil o binarios. Web y API primero: es donde está el 90% del dinero accesible.

Enlaces: [[Rutina semanal]] · [[MOC - Vulnerabilidades]] · [[Enlaces]]
