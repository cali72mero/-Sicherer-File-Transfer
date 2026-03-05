# Sicherer File Transfer - Version 27

Stand: **5. Maerz 2026**

## 1. Projektstatus

- Aktive Version: **V27**
- Vorversion: **V26** (Release: **12. Februar 2026**, jetzt eingestellt)
- Aeltere Versionen aus 2025/2026: eingestellt und nicht mehr gepflegt

Hinweis zur Datumsangabe: "3 Wochen vor dem 5. Maerz 2026" entspricht dem **12. Februar 2026**.

## 2. Was das Programm kann

- Direkte Verbindung zwischen Geraeten ueber WebRTC (Peer-to-Peer)
- Verschluesselter Chat zwischen verbundenen, authentifizierten Geraeten
- Versand von Dateien an mehrere Geraete
- PIN-basierte Geraete-Freigabe (Authentifizierung)
- Chunk-basierter Datei-Transfer (stabiler bei groesseren Dateien als in V26)
- ZIP-Download aller empfangenen Dateien
- Dark/Light/Matrix-Theme
- Link-Sharing mit `?connect=<geraetename>`

## 3. Was das Programm aktuell noch nicht kann

- Kein garantierter Versand ohne TURN-Server ueber verschiedene Netze hinweg
- Kein Server-Fallback fuer Dateien (wenn P2P blockiert ist, scheitert der Transfer)
- Kein Resume/Fortsetzen von unterbrochenen Datei-Transfers
- Keine Benutzerkonten, kein Login, keine Cloud-Ablage
- Keine echte Ordnersynchronisation
- Keine nachgewiesene Integritaetspruefung mit Dateihash im aktuellen UI-Flow
- Optionen wie "Kompression" und "Stealth" sind vorhanden, aber funktional derzeit begrenzt

## 4. Unterstuetzte Geraete und Browser

### Unterstuetzt (empfohlen)

- Desktop/Laptop: macOS, Windows, Linux
- Browser: aktuelle Versionen von Chrome, Edge, Firefox, Safari
- Mobile: aktuelle Android- und iOS-Browser mit WebRTC/WebCrypto-Unterstuetzung

### Nicht oder nur eingeschraenkt unterstuetzt

- Internet Explorer
- Legacy Edge (vor Chromium)
- Sehr alte Android WebViews/Browser ohne moderne WebRTC- und Crypto-APIs
- Stark restriktive Firmen-/Campus-Netze ohne erlaubten WebRTC/TURN-Traffic

## 5. Voraussetzungen

- JavaScript muss aktiviert sein
- Internetzugang fuer:
- Laden externer Bibliotheken (PeerJS, JSZip via CDN)
- Peer-Signalisierung (PeerJS-Server)
- Fuer Verbindungen ueber unterschiedliche Netze: TURN-Server dringend empfohlen

## 6. Schnellstart

1. Auf jedem Geraet die App oeffnen.
2. Geraetenamen setzen und auf **Starten** klicken.
3. Partner hinzufuegen:
- Entweder Name eingeben und verbinden
- Oder Link teilen und oeffnen
4. Authentifizieren:
- Ein Geraet zeigt PIN
- Das andere Geraet gibt PIN ein
5. Nach erfolgreicher Authentifizierung koennen Chat und Dateien genutzt werden.

## 7. Netzwerkmodi (V27)

- `Auto`: Standard, nutzt STUN; TURN optional
- `Internet`: fuer unterschiedliche Netze, TURN empfohlen
- `Nur LAN`: fuer lokale Netze

TURN-Konfiguration:
- `turnUrl` z. B. `turn:turn.example.com:3478`
- Optional: `turnUser`, `turnPass`

## 8. Sicherheit (technische Kurzfassung)

- PIN-basierter Schluesseltausch zwischen zwei Geraeten
- AES-GCM fuer verschluesselte Nutzdaten (Chat/Datei-Chunks)
- Verbindungen laufen ueber WebRTC-Datenkanaele

Wichtig:
- Ohne korrektes TURN kann eine Verbindung ueber verschiedene Netze fehlschlagen.
- Sicherheit haengt auch von Browser, Endgeraet und Netzumgebung ab.

## 9. Typische Probleme und Loesungen

- Problem: "Geraete finden sich nicht"
- Pruefe Namen/Praefix, Browserkonsole und Netzwerkfreigaben.
- Problem: "Verbindung nur im gleichen WLAN"
- TURN-Server eintragen und `Internet`-Modus nutzen.
- Problem: "Transfer bricht ab"
- Kleinere Datei testen, Netzstabilitaet pruefen, beide Browser aktualisieren.

## 10. Versionen (Uebersicht)

- **V27** (aktiv, Stand 5. Maerz 2026)
- Verbesserte Transfer-Stabilitaet (Chunk + Backpressure)
- Verbesserte Verbindungs-/Statusbehandlung
- TURN-/Netzmodus-Konfiguration
- **V26** (eingestellt, Release 12. Februar 2026)
- Vorlaeufer der Multi-Geraete-Version
- **V25 und aelter** (2025 bis Anfang 2026, eingestellt)
- Interne/iterative Entwicklungsstaende, nicht mehr gepflegt

## 11. Lizenz

Siehe [LICENSE.txt](LICENSE.txt).

