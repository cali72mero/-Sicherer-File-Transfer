# Secure File Transfer - Version 27

> Browser-based file transfer and chat with PIN authentication, encryption, and cross-network mode.

## Quick Snapshot

| Item | Value |
|---|---|
| Active version | **V27** |
| Previous version | **V26** |
| V26 release date | **February 12, 2026** |
| V26 status | Discontinued |
| Document date | **March 5, 2026** |

Date note: "3 weeks before March 5, 2026" is **February 12, 2026**.

## Navigation

- [What the app can do](#what-the-app-can-do)
- [Current limitations](#current-limitations)
- [Supported devices and browsers](#supported-devices-and-browsers)
- [WLAN + mobile data scenario](#wlan--mobile-data-scenario)
- [Network modes](#network-modes)
- [Quick start](#quick-start)
- [Troubleshooting](#troubleshooting)
- [Versions](#versions)

## What the app can do

| Feature | Status | Details |
|---|---|---|
| WebRTC connection | Active | Direct browser-to-browser transport |
| Encrypted chat | Active | Available after authentication |
| File transfer | Active | Send to multiple authenticated devices |
| Chunk pipeline | Active | Better stability for larger files |
| PIN auth | Active | 6-digit key exchange flow |
| ZIP download | Active | Download all received files in one archive |
| Internet mode | Active | Works across different networks |
| TURN fallback | Active | Public relay fallback by default |

## Current limitations

| Area | Current status |
|---|---|
| 100% cross-network reliability | Not guaranteed (public relays can be limited) |
| Server relay fallback for files | Not implemented yet |
| Transfer resume | Not implemented yet |
| Accounts/login/cloud sync | Not available |
| Full integrity UI visibility | Currently limited |

## Supported devices and browsers

### Recommended

| Category | Support |
|---|---|
| Desktop | Current macOS, Windows, Linux |
| Mobile | Current Android and iOS browsers |
| Browser engines | Current Chrome, Edge, Firefox, Safari |

### Limited or unsupported

| Platform | Note |
|---|---|
| Internet Explorer | Unsupported |
| Legacy Edge (pre-Chromium) | Unsupported |
| Old Android WebViews | Often missing modern WebRTC/WebCrypto APIs |
| Strict enterprise/campus networks | TURN/WebRTC may be blocked |

## WLAN + mobile data scenario

Yes, V27 is built for this.

To make it work reliably:

1. Use **Internet** mode on both devices.
2. Both devices need internet access (same WLAN is not required).
3. Connect and complete PIN authentication.
4. If it still fails, configure your own TURN server (`turnUrl`, optional `turnUser`/`turnPass`).

Example:

- PC on home WLAN
- Phone on mobile data
- Connection goes through relay/TURN instead of local LAN

## Network modes

| Mode | Purpose | Behavior |
|---|---|---|
| `Internet` | Different networks | Relay/TURN-first, default in V27 |
| `Auto` | Mixed environments | STUN-first, TURN optional |
| `LAN only` | Same local network | Local connectivity focus |

### TURN fields in settings

- `turnUrl` (example: `turn:turn.example.com:3478`)
- `turnUser` (optional)
- `turnPass` (optional)

Note: The built-in relay is a public fallback. A custom TURN server is usually more stable.

## Security (short)

- PIN-based key exchange
- AES-GCM for chat and file chunks
- WebRTC data channel transport

## Quick start

1. Open the app on each device.
2. Set device name and click **Start**.
3. Add partner by name or share link.
4. Show PIN on one side and enter it on the other side.
5. Use chat and file transfer.

## Troubleshooting

| Problem | Check |
|---|---|
| Devices cannot find each other | Verify names, internet access, browser version |
| Works only on same WLAN | Switch to `Internet`, check TURN |
| Transfer fails | Retry with smaller files, verify network quality |
| Unstable connection | Use a custom TURN server |

## Versions

| Version | Period | Status |
|---|---|---|
| V27 | As of March 5, 2026 | Active |
| V26 | Released February 12, 2026 | Discontinued |
| V25 and older | 2025 to early 2026 | Discontinued |

## License

See [LICENSE.txt](LICENSE.txt).
