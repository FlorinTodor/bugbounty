---
tags: [herramientas, moc]
---
# Stack de herramientas

Todo lo esencial es **gratis**. No necesitas comprar Burp Pro para empezar.

## Interceptación (el centro de todo)
- **Burp Suite Community** — gratis. Proxy, Repeater, Decoder, Intruder (lento). Suficiente meses 1-6.
- **Burp Suite Pro** (~450 €/año) — Intruder rápido, **Scanner**, guardado de proyecto, extensiones
  BApp completas, **Burp AI**. Cómpralo cuando un bounty ya lo pague. No antes.
- **Caido** — alternativa moderna, más barata, buen scripting e integración IA. Muchos migran a ella.

## Extensiones de Burp imprescindibles (BApp Store, gratis)
- **Param Miner** — descubre parámetros/cabeceras ocultos (clave para cache poisoning).
- **Autorize** — automatiza pruebas de access control con 2 sesiones. **Oro para IDOR.**
- **Logger++**, **Turbo Intruder** (race conditions), **JS Link Finder**, **Collaborator Everywhere**,
  **Hackvertor**, **JWT Editor**, **GraphQL Raider**, **Backslash Powered Scanner**.
- **MCP Server** (oficial PortSwigger) — conecta un LLM a tu Burp. Ver [[MOC - IA en bug bounty]].

## Recon (ProjectDiscovery + amigos, todo en Go, gratis)
`subfinder` `httpx` `naabu` `katana` `nuclei` `dnsx` `chaos` · `amass` · `ffuf` `feroxbuster` ·
`gowitness` · `arjun` `x8` · `gau` `waybackurls` · `trufflehog` · `puredns` `gotator`
+ **SecLists** (wordlists). Ver [[Recon - superficie de ataque]].

## Navegador
- **Firefox dedicado** solo para bug bounty (perfil aparte). Extensiones: FoxyProxy, Wappalyzer,
  Cookie-Editor, User-Agent Switcher.
- Certificado CA de Burp instalado en ese Firefox.

## Utilidades
- **jq**, **httpie/curl**, **anew**, **gf** (patrones de grep para bug bounty), **interactsh** (OOB).
- **ffufai** / scripts propios con IA para wordlists contextuales.

## IA
- **Claude Code** (ya lo tienes) — scripts de recon, análisis de código y JS, mantener este vault.
- **Ollama + modelo local** — para datos sensibles que no deben salir de tu máquina.
- **Claude-BugHunter** (skill bundle) — ver [[Claude-BugHunter - valoración]]. Mes 3-4.

## Referencia offline
- **PayloadsAllTheThings** (clónalo local) — payloads reales por categoría. Tu fuente, no la memoria de la IA.
- **HackTricks** (clónalo local) — enciclopedia de técnicas.

## Infra
- **VPS barato** (Hetzner/DigitalOcean, ~5 €/mes) — recon continuo y OOB. Mes 3+.
- Repo **privado** para tus scripts y tu bitácora sensible.

Enlaces: [[Instalación del entorno]] · [[Recon - superficie de ataque]] · [[MOC - IA en bug bounty]]
