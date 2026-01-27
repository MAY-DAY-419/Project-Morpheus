# Security & Privacy — High Level 🔐

Key principles

- Client-side encryption: All complaint text is encrypted in the user browser using the Web Crypto API.
- Zero-knowledge backend: The backend stores only encrypted blobs and never sees plaintext or per-complaint symmetric keys.
- Authority-wrapped keys: Per-complaint symmetric key is encrypted (wrapped) with selected authorities' public keys.
- Minimal anonymized metadata: Timestamps and department tags only — no IPs, no account links.

Encryption flow

1. Generate random AES-256 key in browser per complaint.
2. Encrypt complaint data with AES-GCM (or AES-CBC + HMAC) locally.
3. For each selected authority, encrypt the AES key with that authority's public key (RSA-OAEP or ECIES).
4. Submit: {encryptedComplaint, wrappedKeys[], metadata}

Key management notes

- Public keys for authorities are stored and versioned publicly; key rotation involves publishing a new public key and metadata for future reports.
- Revocation: backend flags revoked keys; previously encrypted complaints remain decryptable by the private key holder unless re-wrapped.

Privacy measures

- No IP logging (configurable at server level) and no personal identifiers in the payload.
- Rate-limiting and CAPTCHA to reduce spam while preserving anonymity.
- Encrypted backups and database-level encryption for defense-in-depth.

Audit & Compliance

- All authority access requests are logged as encrypted audit entries.
- Legal and NGO guidance pages are linked, but platform does not force escalation.

***
