# C4 — Infrastructure, Configuration & Deployment Security: Prompts

> AISVS Reference: C4.1–C4.3 | Controls: 4.1.1–4.3.5

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C4-CODE-02: Implement Edge Device Authentication

**Objective**
- You are implementing the authentication layer for edge AI devices connecting to central infrastructure.

**Required Controls**
- Apply AISVS C4.3.1 and C4.3.2.

**Execution Steps**
- Implement mutual TLS (mTLS) authentication for edge device-to-central-infrastructure communication.
- Each edge device must have a unique device certificate issued by the organization's CA.
- Implement certificate rotation with automatic renewal before expiry.
- For model delivery to edge/mobile devices:
- Sign model packages with a code-signing certificate before delivery.
- Implement on-device signature verification before model loading.
- Reject unsigned or signature-mismatched models.
- Log all authentication events and signature verification outcomes.
- Output: mTLS configuration + model package signing workflow + on-device verification implementation.

**Expected Artifacts**
- mTLS configuration + model package signing workflow + on-device verification implementation.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing the authentication layer for edge AI devices connecting to central infrastructure.
Apply AISVS C4.3.1 and C4.3.2.

Requirements:
- Implement mutual TLS (mTLS) authentication for edge device-to-central-infrastructure communication.
- Each edge device must have a unique device certificate issued by the organization's CA.
- Implement certificate rotation with automatic renewal before expiry.
- For model delivery to edge/mobile devices:
  - Sign model packages with a code-signing certificate before delivery.
  - Implement on-device signature verification before model loading.
  - Reject unsigned or signature-mismatched models.
- Log all authentication events and signature verification outcomes.

Output: mTLS configuration + model package signing workflow + on-device verification implementation.
```


### C4-CODE-03: Implement Secure Model Storage for Edge/Mobile

**Objective**
- You are implementing model storage for a mobile/IoT AI application.

**Required Controls**
- Apply AISVS C4.3.4 and C4.3.5.

**Execution Steps**
- Encrypt model weights at rest using hardware-backed key storage:
- Android: Android Keystore with AES-256-GCM
- iOS: Secure Enclave with CryptoKit
- Embedded/IoT: Hardware Security Module (HSM) or TPM-backed key
- The decryption key must never leave the secure enclave.
- Model decryption must happen inside the trusted runtime — never write decrypted weights to disk.
- Implement integrity verification (HMAC or signature check) before decryption.
- Prevent model extraction from the app package (obfuscate storage paths, use platform DRM where applicable).
- Output: secure model loader with hardware-backed key storage + extraction prevention measures.

**Expected Artifacts**
- secure model loader with hardware-backed key storage + extraction prevention measures.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing model storage for a mobile/IoT AI application.
Apply AISVS C4.3.4 and C4.3.5.

Requirements:
- Encrypt model weights at rest using hardware-backed key storage:
  - Android: Android Keystore with AES-256-GCM
  - iOS: Secure Enclave with CryptoKit
  - Embedded/IoT: Hardware Security Module (HSM) or TPM-backed key
- The decryption key must never leave the secure enclave.
- Model decryption must happen inside the trusted runtime — never write decrypted weights to disk.
- Implement integrity verification (HMAC or signature check) before decryption.
- Prevent model extraction from the app package (obfuscate storage paths, use platform DRM where applicable).

Output: secure model loader with hardware-backed key storage + extraction prevention measures.
```


---
