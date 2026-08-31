---
tags: [reportes, cvss]
---
# Severidad y CVSS

## CVSS 3.1 en 30 segundos
Vector de métricas que da una nota 0-10. Las que más mueven la aguja:
- **AV** (Attack Vector): Network > Adjacent > Local > Physical.
- **AC** (Complexity): Low sube la nota, High la baja.
- **PR** (Privileges Required): None > Low > High.
- **UI** (User Interaction): None sube, Required baja.
- **C/I/A** (Confidentiality/Integrity/Availability): High/Low/None cada una.
- **S** (Scope): Changed sube mucho la nota (el bug afecta más allá del componente).

Calculadora oficial: FIRST.org. Deja que la IA te dé el vector **razonado** y verifica cada métrica
(ver [[Biblioteca de prompts]]).

## Rangos
| Nota | Severidad |
|---|---|
| 9.0-10.0 | Critical (P1) |
| 7.0-8.9 | High (P2) |
| 4.0-6.9 | Medium (P3) |
| 0.1-3.9 | Low (P4) |
| 0 | Informational (P5) |

## Ojo: CVSS ≠ bounty
El pago depende del **impacto de negocio** y de la tabla del programa, no solo del CVSS. Un IDOR
"Medium" en datos de pago puede pagar más que un XSS "High" en una página sin sesión.

## VRT de Bugcrowd
La **Vulnerability Rating Taxonomy** (bugcrowd.com/vrt) lista clase por clase qué prioridad P1-P5
le dan. Es el mejor documento para **calibrar tus expectativas** antes de reportar. Léelo.

## Traducción rápida por clase (orientativo)
- RCE, SQLi con extracción, auth bypass total → P1/Critical
- IDOR sobre datos sensibles, SSRF a interno, account takeover → P2/High
- XSS almacenado, CSRF en acción sensible, IDOR menor → P3/Medium
- XSS reflejado con interacción, open redirect → P4/Low
- Falta de cabecera, versión expuesta, autocompletado → P5/**no reportes** (Informative)

Enlaces: [[Cómo escribir un buen report]] · [[Triage - qué esperar de la respuesta]]
