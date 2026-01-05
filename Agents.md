# AGENTS.md – org-web1 v2 (Eleventy)

## 1. Projektübersicht
Dieses Projekt ist die Migration der bestehenden statischen Website „org-web1“ (v1)
auf eine wartbare v2-Basis mit Eleventy (11ty).

Die Website wird auf **Strato Webhosting (Apache, Shared Hosting)** betrieben.
Auf dem Server findet **kein Build-Prozess** statt.

---

## 2. Ziel des Umbaus (v2)
- 1:1 Migration der bestehenden Website (Layout, Inhalte, Design)
- Entfernen von HTML-Duplikaten durch Layouts & Partials
- Bessere Wartbarkeit, saubere SEO-Basis
- Statischer Build (HTML/CSS/Assets), direkt deploybar

**Wichtig:**  
v2 soll visuell und inhaltlich **identisch zu v1** sein, außer explizit beauftragte Verbesserungen.

---

## 3. Nicht-Ziele / Scope-Grenzen
Folgendes ist **nicht Teil dieses Umbaus**, außer explizit freigegeben:
- Redesign
- neue Inhalte oder Texte
- JavaScript-Frameworks (React, Vue, etc.)
- Backend / Server-Code
- CMS-Integration

---

## 4. Technischer Rahmen

### Stack
- Eleventy (11ty)
- Nunjucks Templates (`.njk`)
- Statische Assets (CSS, Images, SVG)

### Build
- Build erfolgt **lokal oder per CI**
- Output-Verzeichnis: `dist/`
- Nur `dist/` wird deployed

### Repository
- `main` = stabile v1
- `v2-eleventy` = Umbau-Branch

---

## 5. Projektstruktur (Ziel)
src/
_includes/
layouts/
base.njk
partials/
header.njk
footer.njk
cookie-banner.njk
pages/
index.njk
impressum/index.njk
datenschutz/index.njk
assets/
css/style.css
img/
dist/


---

## 6. Phasen & Prioritäten

### Phase 1 (P0 – Pflicht)
- Eleventy-Grundsetup
- Layout + Partials
- 1:1 Migration aller Seiten
- Assets korrekt eingebunden
- URLs funktionsgleich oder weitergeleitet

### Phase 2 (P1 – SEO & Technik)
- Titel & Meta-Descriptions pro Seite
- Canonical URLs
- Sitemap-Generierung
- Saubere 404-Seite

### Phase 3 (P1 – Apache / Strato)
- `.htaccess` konsolidieren
- Redirects von alten URLs
- Cache-Control & GZIP (defensiv via `IfModule`)

---

## 7. Deployment (Strato Webhosting)

- Upload per FTP/SFTP
- Webroot ist z. B. `htdocs/`
- **Inhalt von `dist/` wird direkt in den Webroot kopiert**
- Kein Node, kein Eleventy auf dem Server

### Upload-Regeln
- Erst Assets hochladen, dann HTML
- Alternativ: Upload in temporären Ordner, dann Swap

---

## 8. URL- & SEO-Regeln
- Bevorzugte URL-Form: `/impressum/` (folder-style)
- Alte URLs (z. B. `impressum_page.html`) müssen per 301 weitergeleitet werden
- Canonical URLs dürfen **nicht** auf `localhost` zeigen

---

## 9. Security & .htaccess
- Apache `.htaccess` verwenden (Strato)
- `IfModule`-Blöcke nutzen (Module evtl. nicht verfügbar)
- Security Headers zunächst mild (CSP vorsichtig!)
- HSTS nur nach expliziter Freigabe

---

## 10. Qualitätssicherung / Definition of Done

Ein Task gilt als **fertig**, wenn:
- `npm run build` erfolgreich ist
- `dist/` vollständig deploybar ist
- Alle Seiten erreichbar sind:
  - `/`
  - `/impressum/`
  - `/datenschutz/`
  - echte 404-Seite
- Keine fehlenden Assets (keine 404s im Browser)
- Mobile Ansicht funktioniert

---

## 11. Übergabe & Dokumentation
Am Ende des Projekts muss vorliegen:
- Kurze README: „Wie deploye ich v2 auf Strato“
- Liste alter → neuer URLs
- Hinweis, wo Header/Footer/SEO gepflegt werden
