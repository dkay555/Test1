# AGENTS.md

## Projektüberblick
Dieses Repository enthält eine statische Website für **babixGO** (Monopoly GO Services). Alle Inhalte sind als HTML/CSS-Dateien organisiert, ohne Build-System oder Framework.

## Wichtige Dateien & Ordner
- `index.html`: Startseite mit Angebotsblöcken (Partner, Racers, Sticker, Accounts, Würfel) sowie Navigationslinks und Tracking-Skripten.
- `anleitungen/`: Sammlung von Anleitungsseiten.
  - `anleitungen/freundschaftsbalken-fuellen/index.html`: Anleitung inkl. SEO-Meta-Tags, Schritt-für-Schritt-Inhalten und Download-Verweisen.
- `assets/`: Statische Assets (CSS, Icons, Bilder).
  - `assets/css/style.css`: Globales Stylesheet für die gesamte Website.
- `downloads/`: Landing/Index für Download-Dateien (verlinkt aus Anleitungen und Navigation).
- `public/`: Weitere statische Dateien/Assets für die Website (z. B. zusätzliche Inhalte oder Seiten).
- `robots.txt` und `sitemap.xml`: SEO/Indexierungs-Konfigurationen.

## Inhalte & Navigation
- Hauptnavigation in `index.html` verlinkt auf Sektionen (Anker: `#partner`, `#racers`, `#sticker`, `#accounts`, `#wuerfel`) sowie externe Kontaktlinks.
- Die Anleitungsseite verlinkt zurück zur Startseite und zu Downloads unter `/downloads/`.

## Tracking & SEO
- `index.html` enthält Meta Pixel sowie Google Tag (`gtag.js`).
- SEO-Meta-Tags und Canonical-Links sind in den HTML-Dateien gepflegt.

## Lokales Testen
- Da es sich um eine statische Seite handelt, reicht es, die `index.html` direkt im Browser zu öffnen.
- Für relative Pfade empfiehlt sich ein einfacher Static-Server (z. B. `python -m http.server`) im Repository-Root.
