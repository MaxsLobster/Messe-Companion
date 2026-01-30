# Messe Companion App 🎪

Mobile Companion App für die Messestand-Verwaltung - perfekt für unterwegs auf iPhone oder iPad.

## Features

- **🔍 Schnelle Suche**: Standnummer eingeben → sofort da
- **🚦 Status-Toggle**: Frei ↔ Besetzt ↔ Reserviert mit einem Tap
- **📝 Notizen**: Schnell Infos zum Stand notieren
- **💰 Bezahlt-Status**: Ein Klick zum Umschalten
- **📊 Live-Statistik**: Übersicht aller Stände
- **⏱️ Zuletzt angesehen**: Schneller Zugriff auf letzte Stände

## Installation

### Als PWA auf iPhone/iPad:
1. Öffne `https://maxslobster.github.io/Messe-Companion`
2. Tippe auf "Teilen" (Safari)
3. Wähle "Zum Home-Bildschirm"
4. Fertig! App-Icon erscheint auf dem Homescreen

### Icons generieren:
Das SVG-Icon (`icon.svg`) kann zu PNGs konvertiert werden:
- `icon-192.png` (192x192)
- `icon-512.png` (512x512)

Online-Tool: https://cloudconvert.com/svg-to-png

## Airtable Integration

### Schritt 1: Tabelle erstellen
In deiner Airtable Base "Messe OS - Aussteller & Finanzen" eine neue Tabelle "Standplan" anlegen:

| Feld | Typ |
|------|-----|
| Standnummer | Number |
| Status | Single Select (Frei, Besetzt, Reserviert) |
| Aussteller | Link to Aussteller |
| Notizen | Long Text |
| Bezahlt | Checkbox |

### Schritt 2: API-Key erstellen
1. Gehe zu https://airtable.com/create/tokens
2. Klick "Create new token"
3. Name: "Messe Companion"
4. Scopes: `data.records:read`, `data.records:write`
5. Access: Deine "Messe OS" Base
6. Kopiere den Token

### Schritt 3: In der App aktivieren
In `index.html` die CONFIG-Werte eintragen:
```javascript
const CONFIG = {
    AIRTABLE_API_KEY: 'patXXX...', // Dein API Token
    AIRTABLE_BASE_ID: 'appXXX...', // Aus der URL
    AIRTABLE_TABLE_NAME: 'Standplan',
    ...
};
```

Die Base-ID findest du in der Airtable URL:
`https://airtable.com/appXXXXXXXXX/...`
                         ^^^^^^^^^^^
                         Das ist die Base-ID

## Sync mit Saalplan Hauptapp

Sobald beide Apps auf Airtable umgestellt sind:
- iPad (Saalplan) → Airtable ← iPhone (Companion)
- Echtzeit-Sync über das gemeinsame Backend
- Anna kann auch direkt in Airtable arbeiten

## Tech Stack

- Vanilla HTML/CSS/JavaScript
- PWA-ready
- LocalStorage als Offline-Fallback
- Airtable REST API

## Made with ❤️ by Claude + Max
