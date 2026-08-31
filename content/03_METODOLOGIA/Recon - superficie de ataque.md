---
tags: [metodologia, recon]
---
# Recon - superficie de ataque

Objetivo del recon: **maximizar superficie donde nadie ha mirado**, no correr escáneres. Con tu base
de nmap/OSINT ya sabes la mitad; esto lo orienta a **web moderna**.

## Fases

### 1. Ampliar el scope horizontal (¿qué dominios/IP son de la empresa?)
- ASN y rangos IP de la empresa (`amass intel`, BGP.he.net).
- Dominios raíz relacionados, adquisiciones, marcas.
- ⚠️ **Solo lo que esté en scope.** Confirma cada activo contra el brief.

### 2. Enumeración de subdominios (vertical)
- Pasivo: `subfinder`, `amass enum -passive`, `chaos` (ProjectDiscovery), crt.sh, `github-subdomains`.
- Bruteforce: `puredns` / `shuffledns` con wordlist buena (`best-dns-wordlist`).
- Permutaciones: `gotator` / `dnsgen` (dev-, staging-, api-, admin-…).

### 3. Sondas de vivos y tecnología
- `httpx` → cuáles responden, títulos, status, tecnologías, longitudes.
- `wappalyzer`/`httpx -td` → stack. Guarda todo, es la base para priorizar.
- Captura de pantalla masiva: `gowitness` / `aquatone` → revisas visualmente qué es interesante.

### 4. Descubrimiento de contenido (por host interesante)
- Crawling: `katana`, `hakrawler`, o el crawler de Burp.
- Fuzzing de rutas: `ffuf` / `feroxbuster` con wordlists (`raft`, `SecLists`). Wordlist contextual
  con IA (ver [[Automatizar tu recon con IA]]).
- **Bundles JS**: `katana -jc`, `getJS`, luego extraer endpoints/secretos con `linkfinder` **+ LLM**
  (ver [[IA para cazar]]). Aquí sale mucho oro que otros no leen.
- Parámetros ocultos: `arjun`, `x8`, `param-miner` (extensión Burp).
- Históricos: `gau`, `waybackurls` (URLs antiguas → endpoints muertos que a veces siguen vivos).

### 5. APIs
- Busca `/api`, `/graphql`, `/v1`, `/swagger`, `/openapi.json`, `.well-known/`.
- GraphQL: prueba introspección; si está abierta, `graphql-voyager` para ver el esquema entero.

### 6. Cloud y fugas
- Buckets S3/GCS mal configurados, subdomain takeover (`nuclei -t takeovers`), CNAMEs colgados.
- Secretos en GitHub (`trufflehog`, github dorks), en JS, en `.env` expuestos, en `.git/` expuesto.

## Stack recomendado (todo gratis)
**ProjectDiscovery** es el ecosistema estándar en Go: `subfinder`, `httpx`, `naabu`, `katana`,
`nuclei`, `dnsx`, `chaos`. Instálalos todos. + `ffuf`, `amass`, `gowitness`, `SecLists`, `arjun`,
`trufflehog`, `gau`. Todo esto va en tu [[Instalación del entorno]].

## Salida del recon (qué guardas por target)
En `09_BITACORA/Targets/<target>/`:
- `subdominios.txt`, `vivos.txt`, `tecnologias.md`
- `endpoints.md` (de los bundles JS)
- `mapa.canvas` (opcional, un canvas de Obsidian con la arquitectura)
- `roles-y-permisos.md` (tu comprensión del negocio — lo más valioso)

## Recon continuo (mes 3+)
El recon no se hace una vez: se **monitoriza**. Un subdominio nuevo mañana es tu bug de pasado
mañana. Automatízalo → [[Automatizar tu recon con IA]].

## ⚠️ Legalidad
Rate limiting suave, solo scope, y respeta si el programa prohíbe scanning automático.
Ver [[Reglas del juego - legalidad y scope]].

Enlaces: [[Metodología de caza]] · [[Stack de herramientas]] · [[Automatizar tu recon con IA]]
