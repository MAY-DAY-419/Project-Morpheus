# Slide: Solution & Approach — Single Slide Content 🎯

Title (centered): Solution & Approach

Layout suggestion (judge-friendly)

- Top: Title (large)
- Left column: "What" + 3 bullets (short)
- Center: Small diagram (3–4 boxes flow)
- Right column: "Why Secure" + 2 bullets + "HR-is-the-Harasser" callout
- Footer: Links — GitHub repo | Demo (Drive)

Slide text (copy-paste friendly)

What
- Privacy-first, anonymous workplace harassment reporting platform.
- Client-side encrypted reports; no accounts or IP logging.
- Reporter chooses which authorities can access the report.

How it works (3-step)
1. Reporter encrypts complaint in browser (AES-256).
2. Browser wraps AES key for chosen authorities with their public keys.
3. Backend stores encrypted blob + wrapped keys; authorities decrypt locally.

Why it's secure
- Zero-knowledge backend: plaintext never sent to server.
- Per-report keys + authority key-wrapping prevent unilateral suppression.

HR-is-the-Harasser (callout)
- Reporter can omit HR and select ICC/NGO — prevents internal suppression.
- Multiple authority approvals reduce single-point censorship.

Visual / Table options for judges
- Point-based: Short bullets with an icon each — fastest to scan.
- Two-column table: Left "Feature", Right "Benefit" — very clear.
- Mini-diagram: 3-step flow with icons — great for clarity.

Example 2-column table (simple)

| Feature | Benefit |
|---|---|
| Client-side encryption | Backend never sees plaintext |
| Authority-wrapped keys | Prevents unilateral deletion |
| No accounts/IP logging | Minimizes retaliation risk |

Links
- GitHub: https://github.com/your-repo (replace with real link)
- Demo/Drive: https://drive.google.com/your-demo (replace with real link)

Speaker notes (1–2 lines)
- "We provide a privacy-first, survivor-controlled channel ensuring reports can be acted on without exposing reporters."

***
