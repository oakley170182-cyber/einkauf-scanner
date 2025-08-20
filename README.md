# Einkauf-Scanner (PWA)

Eine kleine, datenschutzfreundliche Web-App, um Einkäufe **ohne Tippen** zu erfassen:
- **Barcode-Scan** (Barcode Detection API; Fallback: Quagga2)
- **Kassenbon-Scan (OCR)** mit Tesseract.js
- **Lokale Speicherung** via IndexedDB (kein Server erforderlich)
- **Analyse/Ranking** der am häufigsten gekauften Artikel
- **PWA**: Installierbar, offline nutzbar
- **Import/Export** der Daten als JSON

> Funktioniert am besten in aktuellen Chromium-Browsern (Android/Chrome). iOS/Safari hat teils Einschränkungen bei Kamera & Barcode-API; dann greift der Quagga2-Fallback.

## Schnellstart (lokal)
1. Lade das ZIP herunter und entpacke es.
2. Starte z. B. einen lokalen Server:
   ```bash
   # Python 3
   python -m http.server 5173
   # und dann http://localhost:5173 im Browser öffnen
   ```
   **Wichtig:** Wegen Kamera-Zugriff muss die Seite über `http(s)` laufen (nicht über `file://`).

## Deployment via GitHub Pages
1. Neues Repo erstellen, z. B. `einkauf-scanner`.
2. Inhalte dieses Ordners committen/pushen.
3. In den Repo-Settings unter **Pages** die Quelle auf `main / root` setzen.
4. Nach wenigen Minuten ist die App als GitHub Page verfügbar.

## Nutzung
- **Scannen → Barcode:** Kamera freigeben, Produkt scannen. Der Name wird – falls möglich – automatisch über OpenFoodFacts geladen (ohne Account/API-Key).
- **Scannen → Bon (OCR):** Foto/Scan des Kassenbons hochladen; erkannte Zeilen bestätigen/korigieren und speichern.
- **Historie:** Einträge bearbeiten/löschen.
- **Analyse:** Rangliste (Top-Artikel) + Balkendiagramm.

## Technologie
- Vanilla HTML/CSS/JS (kein Build nötig)
- Quagga2 (Fallback für Barcode), Tesseract.js (OCR), Chart.js (Charts)
- IndexedDB (lokaler Speicher)
- Service Worker + Manifest (PWA)

## Datenschutz
Alle Daten bleiben **nur in deinem Browser** (IndexedDB). Kein externer Server. Der Produktname wird optional per **OpenFoodFacts** (öffentliche API) nachgeladen.

## Lizenz
MIT
