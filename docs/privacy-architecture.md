# Privacy Architecture

## Overview

Apex Pulse is designed with a zero-trust, zero-cloud privacy model. Every component of the system is built to ensure health data never leaves the device without explicit user action.

## Core Principles

### 1. On-Device Processing

All sensor data is processed by a dedicated privacy chip embedded in the Apex Pulse band:

- **Biometric data ingestion** — raw sensor readings flow directly to the privacy chip
- **On-device inference** — AI models run locally, no network call required
- **Encrypted local storage** — all derived insights are stored in hardware-encrypted memory on the band

### 2. No Cloud Dependency

Apex Pulse has **no cloud backend** for health data:

- No telemetry sent to Apex Electronics servers
- No third-party analytics SDKs
- No advertising identifiers
- Bluetooth pairing with the Apex Health app is local-only (BLE, not via cloud relay)

### 3. App-to-Band Communication

```
Apex Health App (iOS/Android)
        ↕ BLE (local only)
  Apex Pulse Band
        ↓
  Privacy Chip (on-device AI)
        ↓
  Encrypted Storage (on-band)
```

The mobile app reads insights already computed on the band. Raw sensor data never transits to the app unless you explicitly export it.

### 4. Export Controls

If a user chooses to export their health data:
- Export is initiated manually by the user
- Data is encrypted with a user-controlled key before export
- Export destination is chosen by the user (local file, personal cloud, doctor portal)
- Apex Electronics has no access to exported data

## Security Audit

The complete firmware architecture was independently audited by Cure53. The full, unredacted report is available at:

**[Audit report — publishing May 7, 2026]** *(URL: apexelectronics.com/security/cure53)*

Audit scope:
- Privacy chip firmware
- BLE stack and pairing protocol
- NFC payment module
- OTA update signing and verification
- Cryptographic storage implementation
- Mobile app (iOS and Android)
