# Architecture Overview 🏗️

Goal: Show a clear, minimal architecture for WS010 that judges can grasp in 30–60s.

Overview (flow)

User Browser (client)
- Encrypts complaint in-browser using Web Crypto API (AES-256 per-complaint key)
- Encrypts the per-complaint key for selected authorities using their public keys (RSA/ECC)
- Submits: {encryptedComplaint, encryptedKeys[], metadata}

Secure Backend (Go)
- Stores encrypted blob and encrypted keys in DB
- Provides APIs for authorities to fetch encrypted blobs
- Does NOT have access to plaintext or reporter keys

Database (Postgres)
- Stores encrypted complaint, wrapped keys, minimal anonymized metadata
- No IP logging / no personal identifiers

Authorities / Access
- Authorities (HR/ICC/NGO) fetch encrypted complaint
- Authority uses their private key to unwrap per-complaint key and decrypt locally

Diagram (simple)

User Browser --(encrypted data)--> Backend/API --(store)--> Postgres
                               \-> Authorities fetch encrypted blob -> decrypt client-side

Notes
- Key rotation: backend stores public-key versions; authorities can rotate keys and provide new key metadata for re-wrapping future reports.
- Revocation: revoked keys listed in metadata; previously wrapped keys remain usable unless re-encrypted.

Files
- See `docs/security.md` for encryption details.

***
