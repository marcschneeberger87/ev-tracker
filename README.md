# ⚡ EV Ladetracker

Progressive Web App (PWA) zum Erfassen und Auswerten von EV-Ladevorgängen – optimiert für den **Opel eFrontera**, nutzbar auf jedem Smartphone-Browser.

![Screenshot](https://via.placeholder.com/393x200/007AFF/FFFFFF?text=EV+Ladetracker)

## Features

- **Ladevorgänge erfassen** – Datum, Anbieter, kWh, Betrag, Akkustand (SoC), Km-Stand
- **Tarif automatisch berechnet** – aus kWh + Betrag CHF
- **kWh/100km Verbrauch** – berechnet aus den Km-Ständen
- **Monatliche Auswertung** – Kosten- und kWh-Diagramme
- **Anbieter-Statistik** – Vergleich M-Charge, eCarUp etc.
- **Offline-fähig** – funktioniert als installierte PWA ohne Internet
- **Daten lokal** – alles im Browser-LocalStorage, keine Cloud, kein Login
- **Dark Mode** – automatisch via System-Einstellung

## Schnellstart

### Option A – GitHub Pages (empfohlen)

1. Dieses Repo forken oder klonen
2. In den Repository-Einstellungen unter **Pages** → Source: `main` Branch, Folder: `/ (root)`
3. App ist erreichbar unter `https://[dein-username].github.io/ev-tracker`

### Option B – Lokal

```bash
# Einfach index.html im Browser öffnen
open index.html

# Oder mit lokalem Webserver (für PWA-Features)
npx serve .
# → http://localhost:3000
```

## Als App installieren (PWA)

### iPhone / iPad (Safari)
1. Safari öffnen → URL der App aufrufen
2. Teilen-Symbol → **„Zum Home-Bildschirm"**
3. App erscheint wie eine native App auf dem Homescreen

### Android (Chrome)
1. Chrome öffnen → URL aufrufen
2. Banner „App installieren" erscheint automatisch → tippen
3. Alternativ: Menü → **„App installieren"**

## Datenstruktur

Jeder Ladevorgang enthält:

| Feld | Typ | Beschreibung |
|------|-----|--------------|
| `id` | String | Eindeutige ID (Timestamp) |
| `date` | String | ISO-Datum `YYYY-MM-DD` |
| `station` | String | Anbieter / Standort |
| `type` | `AC` / `DC` | Ladetyp |
| `kwh` | Number | Geladene Energiemenge |
| `cost` | Number | Betrag in CHF |
| `socStart` | Number? | Akkustand Start in % |
| `socEnd` | Number? | Akkustand Ende in % |
| `km` | Number? | Kilometerstand |

Gespeichert in `localStorage` unter dem Key `ev_ladetracker_v2`.

## Daten exportieren / sichern

Da alles im Browser gespeichert ist, empfiehlt sich regelmässiges Exportieren:

```javascript
// In der Browser-Konsole ausführen:
copy(localStorage.getItem('ev_ladetracker_v2'))
// → Daten sind in der Zwischenablage als JSON
```

## Kompatibilität

| Browser | Unterstützt |
|---------|-------------|
| Safari (iOS 16+) | ✅ |
| Chrome (Android) | ✅ |
| Firefox | ✅ |
| Samsung Internet | ✅ |

## Geplante Erweiterungen

- [ ] CSV-Export
- [ ] eCarUp API-Anbindung
- [ ] Mehrjahres-Auswertung
- [ ] Eigene Fahrzeuge konfigurierbar

## Lizenz

MIT – Frei verwendbar und anpassbar.
