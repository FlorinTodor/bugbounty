---
tags: [ia, riesgos, imprescindible]
---
# Límites y riesgos de la IA

> [!danger] Léela antes que [[IA para estudiar]] e [[IA para cazar]].
> Usar mal la IA en bug bounty no solo te hace perder tiempo: puede **arruinar tu reputación**
> y meterte en problemas **legales**.

## 1. El "AI slop" te quema con los programas
HackerOne, Bugcrowd y compañía están **inundados** de reports generados por IA que describen bugs
que no existen. Los triagers los odian. Si mandas uno:
- Te cierran el report como inválido → **baja tu reputación** → pierdes acceso a privados.
- Algunos programas ya **banean** por reports de IA no verificados.

**Regla absoluta:** un bug no existe hasta que **tú** lo has reproducido a mano y visto el impacto.
La IA redacta; nunca decide que algo es un bug.

## 2. Alucinaciones en datos técnicos
La IA se inventa con total seguridad: CVEs, versiones, sintaxis, nombres de cabeceras, rutas de API,
flags de comandos. **Verifica siempre** contra la documentación oficial o probándolo. Regla simple:
*si es un dato concreto y comprobable, compruébalo.*

## 3. Confidencialidad y datos del programa — CRÍTICO
Cuando pegas algo en una API de IA (ChatGPT, Claude, etc.), **sale de tu máquina**.

- ❌ **Nunca** pegues datos de usuarios reales del target que hayas encontrado en un bug.
- ❌ **Nunca** pegues contenido de programas **privados** bajo NDA — el brief suele prohibir
  compartir información. Meterla en un chat de IA puede ser **incumplir el NDA**.
- ❌ Cuidado con pegar tráfico que contenga tokens de sesión, claves, PII.
- ✅ Para analizar datos sensibles de un target: **modelo local** (Ollama) que no sale de tu equipo.
- ✅ Anonimiza antes de pegar: sustituye dominios, IDs y tokens reales por placeholders.

## 4. Sesgo de automatización
Si la IA dice "esto parece seguro", tenderás a creerla y a no mirar. **Los mejores bugs están justo
donde la IA no miró.** Úsala para ampliar tu cobertura, no para reducir tu atención.

## 5. Dependencia y atrofia
Si delegas la **comprensión** (no solo el trabajo mecánico), no desarrollas la intuición que
distingue a un cazador de un script. En el mes 1 es tentador. No lo hagas: la comprensión es lo
único que no se puede delegar y lo único que se paga.

## 6. Coste y ruido
Correr LLMs sobre todo tu tráfico es caro y genera mucho ruido. Aplícalos donde el retorno es claro
(bundles JS, código fuente, redacción), no "a ver si encuentra algo" sobre 10.000 peticiones.

## Checklist de uso responsable

- [ ] ¿Voy a **verificar a mano** lo que salga de aquí? Si no, no lo uso para eso.
- [ ] ¿Lo que voy a pegar contiene **datos reales de usuarios** o info de un **programa privado**? → no lo pego / uso local.
- [ ] ¿Estoy delegando **trabajo mecánico** (bien) o **comprensión** (mal)?
- [ ] ¿El report que voy a enviar lo he **reproducido yo**, no solo redactado la IA?

Enlaces: [[IA para cazar]] · [[Reglas del juego - legalidad y scope]] · [[Cómo escribir un buen report]]
