# Forensic Audit & Security Specs

## 1. Transport Security
*   **Signal Protocol**: Double Ratchet algorithm for every E2EE tunnel.
*   **Forward Secrecy**: Unique rotating keys for every individual message.

## 2. Persistence Hardening
*   **At-Rest**: SQLCipher AES-256 with keys in the Android TEE/SE.
*   **RAM Sanitization**:ByteArray keys are physically zeroed out (`Arrays.fill(key, 0)`) immediately after use.
*   **Physical Shredding**: Overwrites data with `[PURGED]` before deletion to defeat free-list recovery.

## 3. Duress Mechanism
*   **Silent Wipe**: Duress Password triggers background deletion of Signal keys and database `VACUUM`.
*   **The Alibi**: Displays a fake "Critical Error 503" to observers.
