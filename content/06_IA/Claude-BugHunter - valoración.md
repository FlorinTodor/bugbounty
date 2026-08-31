---
tags: [ia, herramientas, claude]
---
# Claude-BugHunter - valoración

Skill bundle para **Claude Code** orientado a bug hunting. Lo compartiste desde LinkedIn.
Repo: `github.com/elementalsouls/Claude-BugHunter` · MIT + CC BY 4.0 · ~3.9k ⭐ · mantenido activamente.

## Qué es
Un paquete de skills y slash commands que especializa a Claude Code para caza de bugs web:
- **~83 skills** (58 de vulns web, 10 de plataformas enterprise, 6 de reporting/validación, 5 de recon, 4 de metodología).
- **15 slash commands**: `/hunt`, `/recon`, `/report`, etc.
- **681 patrones** extraídos de reports públicos de HackerOne, sobre 24 clases de vuln.
- **Integración con el MCP de Burp** y un **workflow de scope-enforcement** (allowlist de dominios).
- Se instala como plugin: `/plugin marketplace add elementalsouls/Claude-BugHunter`.
- **Solo superficie externa**: excluye AD interno, C2, post-explotación, persistencia, evasión, binarios.

## Mi valoración honesta para TU caso

**Sí, vale la pena mirarlo — pero en el mes 3-4, no ahora.** Motivos:

### A favor
- Es **exactamente el patrón que defiende este vault**: usar la IA para el trabajo mecánico
  (recon, parseo, redacción de reports, checklists) con **scope-enforcement** integrado, que es la
  precaución nº1 de [[Reglas del juego - legalidad y scope]] y [[Automatizar tu recon con IA]].
- Los 681 patrones de HackerOne son **material de estudio** en sí mismos, aunque no lances nada.
- Encaja con tu stack: ya usas Claude Code, y el MCP de Burp está en tu [[Stack de herramientas]].
- Licencia limpia (MIT/CC BY), popular y mantenido → riesgo de "código basura" bajo.

### En contra / cuidado
- ⚠️ **No lo uses de muleta antes de entender las vulns.** Si en el mes 1 le dices `/hunt` a una
  web sin saber qué es un IDOR, aprenderás cero y mandarás "AI slop" que te quema la reputación
  (ver [[Límites y riesgos de la IA]]). La herramienta amplifica a quien ya sabe; al que no sabe lo
  hace ruidoso.
- ⚠️ **Revisa qué hace cada skill antes de correrla.** Es código de un tercero que lanzará
  peticiones contra tus targets. Lee el skill, entiende su scope-enforcement, y confirma que su
  allowlist funciona **antes** de apuntar a un programa real. Un fallo suyo escaneando fuera de
  scope es **tu** responsabilidad legal.
- ⚠️ **Cyber Verification.** Algunas acciones ofensivas pueden bloquearse por los safeguards de
  Anthropic salvo que te apuntes a su programa gratuito de verificación para trabajo legítimo.
- ⚠️ No sustituye criterio: **no elige target, no confirma bugs, no entiende el negocio.** Sigue
  siendo tuyo lo que paga.

## Plan concreto
1. **Ahora (mes 1):** clónalo y **léelo como material** — mira cómo estructura las 24 clases de
   vuln y los patrones de HackerOne. Eso ya te enseña. No lo ejecutes contra nada todavía.
2. **Mes 3-4:** cuando domines el Bloque A de [[MOC - Vulnerabilidades]], instálalo y pruébalo
   **contra un lab tuyo o un target propio autorizado**, revisando cada skill antes.
3. **Mes 4+:** intégralo en tu flujo de recon junto con lo tuyo de [[Automatizar tu recon con IA]].
   Compáralo con tu pipeline: quédate con lo mejor de cada uno.

> Regla: **entiende primero, automatiza después.** Esta herramienta acelera a quien ya sabe cazar;
> no enseña a cazar. Úsala en ese orden.

Enlaces: [[MOC - IA en bug bounty]] · [[Límites y riesgos de la IA]] · [[Automatizar tu recon con IA]] · [[Stack de herramientas]]
