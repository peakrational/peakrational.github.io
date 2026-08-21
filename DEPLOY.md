# Deployment auf GitHub Pages – Schritt für Schritt

## 1. Repository anlegen

Erstelle auf GitHub ein neues, leeres Repository (ohne README/License):

- **Variante A (empfohlen):** Repo-Name `DEINUSERNAME.github.io` → Seite liegt später direkt unter `https://DEINUSERNAME.github.io/`
- **Variante B:** beliebiger Name, z. B. `homepage` → Seite liegt unter `https://DEINUSERNAME.github.io/homepage/`

## 2. `site` (und ggf. `base`) in `astro.config.mjs` anpassen

Öffne `astro.config.mjs` und ändere die Zeile `site: ...`:

**Variante A:**

```js
site: "https://DEINUSERNAME.github.io/",
```

**Variante B (zusätzlich `base` ergänzen, direkt unter `site`):**

```js
site: "https://DEINUSERNAME.github.io/homepage/",
base: "/homepage",
```

Committe die Änderung: `git add astro.config.mjs && git commit -m "Set site URL"`

## 3. Pushen

Im entpackten Projektordner (die Git-Historie ist im ZIP enthalten):

```bash
git remote remove origin        # entfernt das Original-Fuwari-Remote
git remote add origin https://github.com/DEINUSERNAME/DEINREPO.git
git push -u origin main
```

## 4. GitHub Pages aktivieren

Auf GitHub: **Settings → Pages → Build and deployment → Source: „GitHub Actions"**.

Der mitgelieferte Workflow (`.github/workflows/deploy.yml`) baut die Seite bei jedem Push auf `main` automatisch und veröffentlicht sie. Der erste Lauf startet direkt nach dem Push (Tab **Actions**); nach 1–2 Minuten ist die Seite online.

## 5. Inhalte später ändern

- Texte der Seiten: `src/content/spec/about.md`, `publications.md`, `teaching.md`, `cv.md`, `contact.md`
- Name, Bio, Links in der Sidebar sowie Navigation: `src/config.ts`
- Profilbild: `src/assets/images/avatar.png` ersetzen (aktuell ein Platzhalter mit „KS")
- Akzentfarbe: `themeColor.hue` in `src/config.ts` (0–360)

Nach jedem Push auf `main` wird die Seite automatisch neu gebaut.

## Lokal testen (optional)

```bash
pnpm install
pnpm dev        # http://localhost:4321
```
