# Poco a Poco — Spaans leren

Dagelijkse Spaanse training (Spaans uit Spanje, uitleg in het Nederlands): woorden van de dag, een quiz met slimme herhaling, werkwoordsvervoegingen in zes tijden en honderden zinnen.

## Bestanden

| Bestand | Inhoud |
|---|---|
| `index.html` | Opmaak, kleuren (licht en donker) en de navigatie |
| `app.js` | De schermen en de oefenflow |
| `engine.js` | Vervoegingsgenerator, herhalingsalgoritme, sessie-opbouw en opslag |
| `data.js` | Alle inhoud: woorden, werkwoorden en zinnen |

Er zijn geen afhankelijkheden en geen build-stap. De map is direct als statische site te hosten (Vercel, Netlify, GitHub Pages) of lokaal te openen met een simpele webserver:

```bash
python3 -m http.server 8766
```

## Inhoud toevoegen

Alles staat in `data.js` als compacte lijsten:

- **Woord:** `["el perro","de hond","dieren",2]` → Spaans, Nederlands, categorie, niveau (1–3). Een optioneel vijfde veld: `"a"` voor bijvoeglijke naamwoorden, `"o"` voor uitdrukkingen en overige woorden. Zelfstandige naamwoorden krijgen het lidwoord in het Spaans.
- **Werkwoord:** `["tener","hebben",1,{sc:"e>ie",yo:"tengo",ind:"tuv",fut:"tendr"}]` → infinitief, Nederlands, niveau en de onregelmatigheden. De vervoegingen worden gegenereerd in `engine.js`; corrigeer een vorm dus via deze opties, niet met de hand.
- **Zin:** `["Ayer [fui] al mercado.","Gisteren ging ik naar de markt.",2,"ir","indefinido"]` → het invulwoord tussen rechte haken, Nederlands, niveau, infinitief en tijd (of `null`).

## Opslag

Voortgang staat in de browser (`localStorage`). Op claude.ai wordt hij bovendien per gebruiker gesynchroniseerd tussen apparaten. Op een eigen host kun je voortgang overzetten met Exporteer en Importeer onder Instellingen.
