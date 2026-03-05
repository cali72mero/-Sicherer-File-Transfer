# Secure File Transfer - Version 27

Status date: **March 5, 2026**

## 1. Project Status

- Active version: **V27**
- Previous version: **V26** (released on **February 12, 2026**, now discontinued)
- Older versions from 2025/2026: discontinued and no longer maintained

Date clarification: "3 weeks before March 5, 2026" is **February 12, 2026**.

## 2. What the program can do

- Direct device-to-device connections via WebRTC (peer-to-peer)
- Encrypted chat between connected, authenticated devices
- File transfer to multiple devices
- PIN-based device authentication
- Chunk-based file transfer (more stable for larger files than V26)
- ZIP download for all received files
- Dark/Light/Matrix theme
- Share link support using `?connect=<device-name>`

## 3. What the program cannot do yet

- No guaranteed cross-network transfer without a TURN server
- No server relay fallback for files (if P2P is blocked, transfer fails)
- No resume for interrupted file transfers
- No user accounts, login, or cloud storage
- No real folder sync
- No fully enforced integrity/hash verification in the current UI flow
- Options like "Compression" and "Stealth" exist but are currently limited

## 4. Supported devices and browsers

### Supported (recommended)

- Desktop/Laptop: macOS, Windows, Linux
- Browsers: current Chrome, Edge, Firefox, Safari
- Mobile: current Android and iOS browsers with WebRTC/WebCrypto support

### Not supported or limited

- Internet Explorer
- Legacy Edge (pre-Chromium)
- Very old Android WebViews/browsers without modern WebRTC/Crypto APIs
- Highly restricted enterprise/campus networks that block WebRTC/TURN traffic

## 5. Requirements

- JavaScript must be enabled
- Internet access is required for:
- External libraries (PeerJS and JSZip from CDN)
- Peer signaling (PeerJS server)
- For cross-network use: TURN server is strongly recommended

## 6. Quick Start

1. Open the app on each device.
2. Set a device name and click **Start**.
3. Add partner device:
- Enter partner name and connect
- Or share/open the generated link
4. Authenticate:
- One device shows PIN
- The other device enters PIN
5. After successful authentication, chat and file transfer are available.

## 7. Network Modes (V27)

- `Auto`: default, uses STUN; TURN optional
- `Internet`: for different networks, TURN recommended
- `LAN only`: for local network usage

TURN setup:
- `turnUrl` e.g. `turn:turn.example.com:3478`
- Optional: `turnUser`, `turnPass`

## 8. Security (technical summary)

- PIN-based key exchange between devices
- AES-GCM for encrypted payloads (chat/file chunks)
- Transport over WebRTC data channels

Important:
- Without valid TURN configuration, cross-network connections can fail.
- Security also depends on browser, device state, and network environment.

## 9. Common Issues and Fixes

- Issue: "Devices cannot find each other"
- Verify names/prefix, browser console logs, and network permissions.
- Issue: "Works only on same Wi-Fi"
- Configure TURN and use `Internet` mode.
- Issue: "Transfer stops/fails"
- Retry with smaller file, check network stability, update both browsers.

## 10. Versions (Overview)

- **V27** (active, as of March 5, 2026)
- Improved transfer stability (chunking + backpressure)
- Improved connection/status handling
- TURN/network mode configuration
- **V26** (discontinued, released February 12, 2026)
- Predecessor multi-device release
- **V25 and older** (2025 to early 2026, discontinued)
- Iterative development builds, no longer maintained

## 11. License

See [LICENSE.txt](LICENSE.txt).

