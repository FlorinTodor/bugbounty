---
tags: [legal, imprescindible]
---
# Reglas del juego - legalidad y scope

> [!danger] Lo único que separa "investigador de seguridad" de "delito informático" es **la autorización**.
> Esa autorización es **el texto del programa de bug bounty**. Ni más, ni menos.

## Marco legal en España (resumen práctico, no asesoramiento jurídico)

- **Art. 197 bis CP** — acceso no autorizado a un sistema de información: hasta 2 años de prisión.
  Da igual que no rompieras nada y que lo hicieras "para avisar".
- **Art. 197 ter CP** — facilitar/producir herramientas para lo anterior.
- **Art. 264 y ss. CP** — daños informáticos, interferencia en el funcionamiento de un sistema
  (aquí entra un DoS, aunque sea accidental por un escáner agresivo).
- **RGPD / LOPDGDD** — si accedes a datos personales de terceros, aunque sea por un IDOR legítimo,
  **no los descargues, no los guardes, no los publiques**. Demuestras el bug con **tu propia
  segunda cuenta** o con 1-2 registros redactados.

**Consecuencia práctica:** un programa público con "safe harbor" te cubre *dentro de su scope y
sus reglas*. Fuera de eso, no te cubre nadie.

## Checklist antes de tocar CUALQUIER cosa

- [ ] He leído el **policy/brief completo** del programa, no solo la lista de dominios.
- [ ] El dominio/IP concreto está en **In scope** (no en "out of scope", ni ausente: ausente = fuera).
- [ ] He comprobado las **exclusiones** típicas y las respeto (abajo).
- [ ] Sé si permiten **automated scanning** y a qué rate limit.
- [ ] Sé si exigen **identificador en el User-Agent** (muchos lo piden: p. ej. `X-Bug-Bounty: h1-tuusuario`).
- [ ] He creado **dos cuentas propias** de prueba para probar access control entre ellas.
- [ ] Tengo el brief guardado en la nota del target (`09_BITACORA/Targets`) con fecha.

## Lo que está prohibido en prácticamente todos los programas

- ❌ **DoS / DDoS / stress testing**, y esto incluye fuzzing agresivo que tumbe el servicio.
- ❌ **Ingeniería social** a empleados o usuarios. Phishing. Llamadas.
- ❌ **Ataques físicos** a oficinas o personal.
- ❌ **Fuerza bruta masiva** de credenciales / password spraying contra usuarios reales.
- ❌ **Acceder, modificar o exfiltrar datos de usuarios reales.** Prueba contra tus cuentas.
- ❌ **Pivotar**: si consigues RCE, paras y reportas. No exploras la red interna.
- ❌ **Persistencia**: no dejes webshells, usuarios, ni backdoors. Si creas algo, lo dices en el report.
- ❌ **Publicar el bug** antes de que autoricen la divulgación (normalmente tras el fix, o nunca).
- ❌ Probar **dominios de terceros** que aparezcan por ahí (proveedores, CDNs, SaaS del cliente).

## Zonas grises que te van a pasar

| Situación | Qué hacer |
|---|---|
| Encuentro un bug en un dominio **no listado** de la empresa | Preguntar al programa antes de seguir. Muchos lo aceptan; algunos no. **Preguntar, no asumir.** |
| El IDOR me devuelve datos de un usuario real | Capturo **una** evidencia mínima, redacto los datos, no descargo más, lo digo en el report. |
| Consigo RCE | Paro inmediatamente. `whoami` / `hostname` como prueba y ya. Nada más. |
| Encuentro credenciales válidas en un repo | **No inicio sesión con ellas.** Reporto la exposición. Usarlas es acceso no autorizado. |
| El programa no responde en 30 días | Uso el canal de mediación de la plataforma. **Nunca** divulgo por mi cuenta. |
| Encuentro algo grave en una empresa **sin** programa | Contacto por `security.txt` / `security@`, sin haber probado nada intrusivo. Con mucho cuidado: en España ha habido denuncias a gente que avisó de buena fe. |

## Higiene operativa

- Usa un **navegador dedicado** solo para bug bounty. Nunca tu sesión personal.
- **VPS o VPN**: algunos programas prohíben Tor/VPN, otros lo exigen. Léelo.
- **No compartas** hallazgos sin resolver en Discord/Twitter. Ni "pistas".
- Guarda **logs de todo lo que haces** (proyecto de Burp + bitácora). Si algo se rompe, tu log es
  tu defensa.
- No pruebes desde la red de tu trabajo o de la universidad.

## Impuestos (España)

Un bounty es **renta**. Si esto empieza a generar ingresos recurrentes tendrás que declararlo
(actividad económica, IRPF, y valorar alta en autónomos según recurrencia e ingresos). Muchas
plataformas piden formulario fiscal (W-8BEN para las de EE. UU.). Guarda todos los justificantes
desde el primer euro. Consulta con un gestor cuando llegue el momento — no antes, no te bloquees por esto.

Enlaces: [[Cómo elegir un programa]] · [[Plantilla - Target]] · [[Cómo escribir un buen report]]
