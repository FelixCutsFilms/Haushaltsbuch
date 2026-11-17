# Haushaltsbuch

Monatliche Einnahmen und Ausgaben erfassen: eigene Kategorien (Symbol + Farbe), wiederkehrende Buchungen, Auswertung (Ringdiagramm, 6-Monats-Verlauf), Beleg-Scan und Import mehrerer Buchungen aus Bank-Screenshots. Die Texterkennung (Tesseract) ist eingebaut und läuft offline auf dem Gerät. Alle Daten bleiben lokal auf dem Gerät.

## Als Android-App installieren (empfohlen)
1. Auf der Seite **Releases** → „Haushaltsbuch (neueste Version)" die Datei `Haushaltsbuch.apk` herunterladen.
2. Öffnen und installieren. Beim ersten Mal erlaubt Android die Installation aus dieser Quelle (Browser) nach Rückfrage.
3. Updates: neue APK herunterladen und darüber installieren. Die Daten bleiben erhalten. Bitte nicht zwischendurch deinstallieren, dabei werden die Daten gelöscht.

Die Daten liegen im geschützten App-Speicher. „Browserdaten löschen" betrifft sie nicht. Über „Backup erstellen" sicherst du sie als Datei (z. B. in Google Drive), die App erinnert dich alle 14 Tage.

## Als Web-App (PWA)
Die App liegt in `www/` und wird per GitHub Pages veröffentlicht. Lokal testen: `python3 -m http.server 8000 --directory www`.

## Aufbau
- `www/` – die Web-App (eine HTML-Datei, kein Build nötig), `www/vendor/tesseract/` – gebündelte Texterkennung
- `android/` – Capacitor-Projekt, das `www/` in eine native Android-App einpackt
- `.github/workflows/android.yml` – baut die APK und veröffentlicht sie im Release „latest"
- `.github/workflows/pages.yml` – veröffentlicht die Web-Version

## Hinweis zur Signatur
Der Schlüssel in `android/app/haushaltsbuch.jks` ist ein einfacher Schlüssel für die private Nutzung und absichtlich im Repo, damit jedes Update dieselbe Signatur hat. Für eine Veröffentlichung im Play Store müsste ein eigener, geheimer Schlüssel verwendet werden.
