---
tags: [vulnerabilidad]
clase: Cloud
estado: 🔴 pendiente
paga_bien: ⭐⭐
---
# Subdomain takeover y errores de cloud

> Esqueleto. Complétalo **con tus palabras** al hacer los labs. Estructura completa en
> `_plantillas/Plantilla - Vulnerabilidad`.

## Qué es
Subdomain takeover: un CNAME apunta a un servicio (S3, Heroku, GitHub Pages...) que ya no existe y que puedes reclamar → controlas el subdominio. Además: buckets S3/GCS abiertos, permisos IAM excesivos (a menudo vía [[SSRF]]), credenciales cloud filtradas. Se caza con recon continuo.

## Labs de PortSwigger (fuente principal)
- [ ] (No hay módulo específico; usa nuclei -t takeovers y HackTricks Cloud)

## Recursos
- PayloadsAllTheThings (categoría correspondiente) — payloads reales.
- HackTricks — técnicas y bypass.

## Mis notas de caza
- 

Enlaces: [[Recon - superficie de ataque]] · [[SSRF]]
