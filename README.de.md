# Sicherer File Transfer - Version 27

> Browserbasierter Datei- und Chat-Transfer mit PIN-Freigabe, Verschlüsselung und Internet-Modus.

## Schnellüberblick

| Punkt | Wert |
|---|---|
| Aktive Version | **V27** |
| Vorversion | **V26** |
| Release von V26 | **12. Februar 2026** |
| Status von V26 | Eingestellt |
| Stand dieser Doku | **5. März 2026** |

Datumsinfo: "3 Wochen vor dem 5. März 2026" ist der **12. Februar 2026**.

## Navigation

- [Was die App kann](#was-die-app-kann)
- [Was noch fehlt](#was-noch-fehlt)
- [Unterstützte Geräte und Browser](#unterstützte-geräte-und-browser)
- [WLAN + mobile Daten (ohne gleiches WLAN)](#wlan--mobile-daten-ohne-gleiches-wlan)
- [Netzwerkmodi](#netzwerkmodi)
- [Schnellstart](#schnellstart)
- [Troubleshooting](#troubleshooting)
- [Versionen](#versionen)

## Was die App kann

| Funktion | Status | Details |
|---|---|---|
| WebRTC-Verbindung | Aktiv | Direkte Verbindung zwischen Browsern |
| Verschlüsselter Chat | Aktiv | Nachrichten nur nach Authentifizierung |
| Datei-Transfer | Aktiv | Versand an mehrere authentifizierte Geräte |
| Chunk-Transfer | Aktiv | Stabiler bei größeren Dateien |
| PIN-Freigabe | Aktiv | Schlüsseltausch per 6-stelliger PIN |
| ZIP-Download | Aktiv | Alle empfangenen Dateien gesammelt laden |
| Internet-Modus | Aktiv | Für verschiedene Netze (z. B. WLAN + mobile Daten) |
| TURN-Fallback | Aktiv | Öffentliches Relay als Standard-Fallback |

## Was noch fehlt

| Bereich | Aktueller Stand |
|---|---|
| 100%-Erreichbarkeit über alle Netze | Nicht garantiert (öffentliche Relays können limitiert sein) |
| Server-Relay für Dateien als zweiter Fallback | Noch nicht eingebaut |
| Resume bei Abbruch | Noch nicht eingebaut |
| Konten/Login/Cloud-Sync | Nicht vorhanden |
| Vollständige Integritätsanzeige im UI | Derzeit begrenzt |

## Unterstützte Geräte und Browser

### Empfohlen

| Kategorie | Support |
|---|---|
| Desktop | Aktuelle Versionen von macOS, Windows, Linux |
| Mobile | Aktuelle Android- und iOS-Browser |
| Browser | Aktuelle Chrome-, Edge-, Firefox- und Safari-Versionen |

### Eingeschränkt oder nicht unterstützt

| Plattform | Hinweis |
|---|---|
| Internet Explorer | Nicht unterstützt |
| Legacy Edge (vor Chromium) | Nicht unterstützt |
| Alte Android WebViews | Häufig unvollständige WebRTC/WebCrypto-APIs |
| Stark restriktive Firmen-/Campusnetze | TURN/WebRTC kann geblockt sein |

## WLAN + mobile Daten (ohne gleiches WLAN)

Ja, das ist in V27 vorgesehen.

Damit es funktioniert:

1. Auf beiden Geräten den Modus **Internet** verwenden.
2. Beide Geräte müssen Internet haben (gleiches WLAN ist nicht nötig).
3. Verbinden + PIN bestätigen.
4. Wenn Verbindung scheitert: eigenen TURN-Server eintragen (`turnUrl`, optional `turnUser`/`turnPass`).

Praxisbeispiel:

- PC im Heim-WLAN
- Handy über mobile Daten
- Verbindung läuft über Relay/TURN statt lokaler LAN-Verbindung

## Netzwerkmodi

| Modus | Zweck | Verhalten |
|---|---|---|
| `Internet` | Unterschiedliche Netze | Nutzt Relay/TURN, Standard in V27 |
| `Auto` | Gemischte Umgebung | STUN-first, TURN optional |
| `Nur LAN` | Lokales Netz | Fokus auf lokale Verbindung |

### TURN-Felder in der UI

- `turnUrl` (z. B. `turn:turn.example.com:3478`)
- `turnUser` (optional)
- `turnPass` (optional)

Hinweis: Das integrierte Relay ist ein öffentlicher Fallback. Ein eigener TURN-Server ist meist stabiler.

## Sicherheit (Kurzfassung)

- PIN-basierter Schlüsseltausch
- AES-GCM für Chat und Datei-Chunks
- Transport über WebRTC-Datenkanäle

## Schnellstart

1. Auf jedem Gerät App öffnen.
2. Gerätename setzen und **Starten** klicken.
3. Partner über Namen oder Link hinzufügen.
4. PIN auf einem Gerät anzeigen, auf dem anderen eingeben.
5. Danach Chat und Dateien normal nutzen.

## Troubleshooting

| Problem | Check |
|---|---|
| Geräte finden sich nicht | Namen prüfen, beide online, Browser aktuell |
| Geht nur im selben WLAN | Modus auf `Internet`, TURN prüfen |
| Transfer bricht ab | Kleinere Datei testen, Netzqualität prüfen |
| Verbindung instabil | Eigenen TURN verwenden |

## Versionen

| Version | Zeitraum | Status |
|---|---|---|
| V27 | Stand 5. März 2026 | Aktiv |
| V26 | Release 12. Februar 2026 | Eingestellt |
| V25 und älter | 2025 bis Anfang 2026 | Eingestellt |

## Lizenz

Siehe [LICENSE.txt](LICENSE.txt).
