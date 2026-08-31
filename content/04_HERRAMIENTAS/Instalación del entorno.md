---
tags: [herramientas, setup]
---
# Instalación del entorno

Guía de montaje inicial (Fase 0). Estás en Linux, así que casi todo es directo. Adáptalo; no lo
copies a ciegas.

## 1. Navegador dedicado
- [ ] Perfil de Firefox nuevo solo para bug bounty (`firefox -P`).
- [ ] FoxyProxy apuntando a `127.0.0.1:8080` (Burp).
- [ ] Instalar el **certificado CA de Burp** en ese Firefox (`http://burp` → CA cert).
- [ ] Extensiones: Wappalyzer, Cookie-Editor, FoxyProxy.

## 2. Burp Suite Community
- [ ] Descargar de portswigger.net. Crear un proyecto y **guardar el archivo** por target.
- [ ] BApp Store → instalar: Autorize, Param Miner, Logger++, Turbo Intruder, JWT Editor,
      JS Link Finder, GraphQL Raider, Collaborator Everywhere, Hackvertor.
- [ ] (Opcional) MCP Server para IA.

## 3. Toolchain de Go (recon)
```bash
# instala Go primero (paquete de tu distro o go.dev)
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
go install -v github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest
go install -v github.com/projectdiscovery/katana/cmd/katana@latest
go install -v github.com/projectdiscovery/naabu/v2/cmd/naabu@latest
go install -v github.com/ffuf/ffuf/v2@latest
go install -v github.com/tomnomnom/anew@latest
go install -v github.com/tomnomnom/gf@latest
go install -v github.com/lc/gau/v2/cmd/gau@latest
# añade $HOME/go/bin al PATH en tu .zshrc
```

## 4. Otras
```bash
# SecLists (wordlists)
git clone https://github.com/danielmiessler/SecLists ~/tools/SecLists
# PayloadsAllTheThings (referencia local)
git clone https://github.com/swisskyrepo/PayloadsAllTheThings ~/tools/PATT
# HackTricks (referencia local)  -> o usa book.hacktricks.xyz
git clone https://github.com/carlospolop/hacktricks ~/tools/hacktricks
# arjun, trufflehog
pipx install arjun
pipx install trufflehog   # o binario de releases
```

## 5. Contenedor de recon (recomendado)
Ya usas Docker. Monta un contenedor con todo el toolchain para no ensuciar tu sistema y poder
reproducirlo en un VPS. Pídeselo a Claude Code: *"hazme un Dockerfile con el stack de recon de
ProjectDiscovery + ffuf + SecLists"*.

## 6. Cuentas y gestión
- [ ] Cuentas en las plataformas ([[Comparativa de plataformas]]) con 2FA.
- [ ] Gestor de contraseñas + alias de correo (`tucorreo+bb1@gmail.com`) para las cuentas de prueba.
- [ ] Repo git **privado** para scripts y bitácora.

## 7. Verificación
- [ ] Interceptas tráfico HTTPS de tu Firefox en Burp sin errores de certificado.
- [ ] `subfinder -d example.com` devuelve resultados.
- [ ] `nuclei -update` funciona.

Enlaces: [[Stack de herramientas]] · [[Ruta de aprendizaje]]
