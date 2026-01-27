# Database — Notes 🗄️

Tech: PostgreSQL

Schema (high-level)
- reports: id, created_at, encrypted_blob, metadata(json), key_wrapped(json)
- authorities: id, name, public_key, key_version, status

Storage: encrypted backups + DB at-rest encryption recommended.
