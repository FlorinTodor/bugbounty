---
tags: [ia, moc]
---
# MOC - IA en bug bounty

Cómo usar la IA en las dos mitades de esto:

- [[IA para estudiar]] — acelerar el aprendizaje 2-3x sin engañarte a ti mismo
- [[IA para cazar]] — dónde aporta de verdad durante una sesión
- [[Automatizar tu recon con IA]] — construir tu pipeline propio (tu ventaja real)
- [[Límites y riesgos de la IA]] — **léela antes que las otras tres**
- [[Biblioteca de prompts]] — prompts concretos, copiables

## La tesis en una frase

> La IA no encuentra bugs por ti. **Elimina el trabajo aburrido que hay entre tú y los bugs**:
> leer 4 MB de JavaScript, entender una tecnología que no conoces, redactar un report, mantener
> un pipeline de monitorización. Eso es donde se te van las horas, y es donde la IA te devuelve tiempo.

## Regla de las tres capas

| Capa | ¿Delegable a la IA? |
|---|---|
| **Comprensión** (entender la app, el modelo de permisos, el negocio) | ❌ No. Es tuya. Es donde están los bugs |
| **Generación de hipótesis** ("¿qué probaría aquí?") | ⚠️ Sí, como lluvia de ideas. Nunca como verdad |
| **Trabajo mecánico** (parsear, resumir, transformar, escribir código, redactar) | ✅ Sí, delegar agresivamente |

## Herramientas que te interesan concretamente

| Herramienta | Uso |
|---|---|
| **Claude Code** (lo que estás usando ahora) | Escribir tus scripts de recon, analizar código fuente de targets open source, mantener este vault, generar wordlists contextuales |
| **MCP Server de Burp** (BApp oficial de PortSwigger) | Conecta un LLM a tu Burp: puede leer el historial de proxy, mandar peticiones al Repeater y analizar respuestas. Instálalo desde el BApp Store |
| **Burp AI** (solo Burp Pro) | *Explore Issue*, *Shadow Repeater*, explicación de findings. Útil, no imprescindible |
| **Caido** | Alternativa moderna a Burp, con integración de IA y buen scripting. Barata |
| **Modelos locales** (Ollama + un modelo mediano) | Para analizar datos de clientes/targets que **no debes** mandar a una API externa |

Enlaces: [[Límites y riesgos de la IA]] · [[Stack de herramientas]]
