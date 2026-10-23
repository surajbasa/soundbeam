# SoundBeam

A browser-based experimental file-transfer demo that sends file bytes as audible multi-frequency tones and receives them through a microphone.

## Features
- No upload server; the file payload is transmitted acoustically between devices.
- 16-FSK symbols: each tone represents 4 bits.
- File name and length are included in the packet.
- CRC-32 checksum detects corrupted transfers.
- Works as a static website, including GitHub Pages.

## Run it
1. Put `index.html` in the root of a GitHub repository.
2. In **Settings → Pages**, deploy from the `main` branch and `/ (root)`.
3. Open the HTTPS GitHub Pages URL on both devices.
4. On the receiver, tap **Start microphone** and grant microphone permission.
5. On the sender, choose a small file and tap **Play transfer tones**.
6. Keep the speaker near the receiving microphone.

You can also run a local server from this folder with Python:
```bash
python -m http.server 8000
```
Then open `http://localhost:8000` on the computer. Microphone access is generally restricted to HTTPS or localhost.

## Important limitations
This is an experimental proof of concept, not production-ready transfer software. Browser audio processing, room noise, microphone sampling, and symbol timing can cause errors. The receiver uses simple dominant-frequency detection and does not yet implement robust timing recovery, retransmission, encryption, or adaptive error correction. Begin with tiny files (a few hundred bytes) in a quiet room. The current conservative symbol timing makes transfer slow.

Do not use it for sensitive or important files. For reliable, high-speed offline transfers, local Wi-Fi / Wi-Fi Direct is usually a better option.
