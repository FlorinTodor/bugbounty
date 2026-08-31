---
tags: [recursos, htb]
---
# HTB Academy - qué hacer y qué saltarse

Vas a pagar la mensualidad de estudiante. Para que rinda, úsala **enfocada**, no de principio a fin.
Recuerda: tu material nº1 sigue siendo **PortSwigger (gratis)**. HTB Academy aporta **estructura,
temas que PortSwigger no cubre, y el path hacia el cert CBBH**.

## Ruta HTB para bug bounty: el **Job Role Path "Bug Bounty Hunter" → CBBH**
Es el path alineado. Prioriza sus módulos de:
- **Web requests / Introduction to Web Applications** — rápido, salta lo que ya sepas.
- **Using Web Proxies (Burp/ZAP)** — útil aunque ya conozcas Burp.
- **Information Gathering - Web** — recon web (complementa [[Recon - superficie de ataque]]).
- **Attacking Web Applications with Ffuf** — fuzzing.
- **Login Brute Forcing**, **SQL Injection Fundamentals**, **XSS**, **File Inclusion**,
  **Command Injections**, **File Upload Attacks**, **Web Attacks** (IDOR, XXE...),
  **Session Security**, **Web Service & API Attacks**.
- **Bug Bounty Hunting Process** — metodología y **reporting** (muy útil).

## Módulos extra que te convienen por tu perfil/nicho
- **Introduction to APIs** / API attacks.
- Cualquier módulo de **cloud** (AWS/attacking cloud) → apoya [[SSRF]] y [[Subdomain takeover y errores de cloud]].
- Los de **GraphQL** si los tienen.

## Qué SALTARTE (no es bug bounty)
- Todo lo de **Active Directory**, Windows interno, pivoting, C2, post-explotación → es CPTS/OSCP,
  no bug bounty. Interesante para empleo de pentester, no para tu objetivo ahora.
- Módulos de fundamentos de Linux/redes que ya dominas (tienes vault propio de Linux).

## Cómo exprimir la suscripción
- Ve por **objetivos**, no por completar el 100%. Cada módulo que toques debe apoyar un tema de
  [[Ruta de aprendizaje]].
- HTB Academy **complementa** los labs de PortSwigger; no los sustituye. Si tienes que elegir dónde
  pasar una tarde, PortSwigger gana para bug bounty puro.
- Apunta a **CBBH** hacia el mes 6-9 si vas bien ([[Certificaciones - cuáles valen la pena]]).
- **Máquinas de HTB (el HTB "normal", no Academy)**: máximo 1/mes por diversión. No son bug bounty.

Enlaces: [[Ruta de aprendizaje]] · [[Certificaciones - cuáles valen la pena]] · [[Enlaces]]
