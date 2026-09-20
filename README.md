# WePlay Compete — Spear-Phishing Investigation

**Incident ID:** INC-2026-0920-WEPLAY-PHISH
**Severity:** Medium-High *(targeted spear-phishing with account takeover attempt; incident contained, but the underlying infrastructure remains active and continues to be exploited)*
**Status:** Contained / No credential loss / Abuse reports filed with Cloudflare (2026-09-21) for `signnotclo.com` and `signgamergo.com`; takedown outcome pending follow-up
**Detection Source:** End-user (manual recognition) — no automated detection involved
**Date/Time of primary event:** 2026-09-20, 17:03–17:38 (voice call), verification attempt immediately after

## Summary

Targeted spear-phishing attack against a Steam account owner via an "interview for an esports advertiser" pretext. The attacker used compromised legitimate WePlay Esports infrastructure (a hijacked official Discord server + a link on the official Twitch channel) to build trust. The final stage was a browser-in-the-browser (BitB) phishing page mimicking Steam OpenID login, aimed at stealing credentials and intercepting 2FA in real time. The target recognized the fake login window and disengaged before entering any data.

## Timeline

| Time (UTC+3) | Event |
|---|---|
| T-9 days | Initial contact in Steam chat, rapport-building via game-related questions |
| T-9 days | "New segment" pitch — prize offered, framed as low-effort/no-cost |
| T-5..T-1 days | Conversation moved to Discord |
| T0, 20:22 | Friend request accepted from a second, disposable Discord account (verification-stage operator) |
| T0, 17:03–17:38 | 35-minute voice call — the "interview" |
| T0, 17:16 | Routing keyword sent immediately after the call |
| T0 | Redirected to phishing domain → BitB Steam login |
| T0 | Fake login window recognized, no data entered, contact ended |

## Attack Vector

Spearphishing Link (T1566.002) + Spearphishing Voice (T1566.004) → Adversary-in-the-Middle credential capture (T1557) via BitB → intended MFA interception (T1111). A second, parallel vector confirmed via live traffic capture: MFA Request Generation (T1621) via a Steam QR-login relay — the panel requests a real Steam QR session and relays it, so scanning it with the target's own Steam Mobile app approves the attacker's session, no password or 2FA code required. Full mapping in [`attck-mapping.md`](./attck-mapping.md).

## Key IOCs

- `weplayesportse.com` — primary phishing domain
- `signgamergo.com` — companion login page serving the BitB Steam login form
- `signnotclo.com` — third domain, loaded via iframe inside `signgamergo.com`; hosts a unified credential-relay backend at `/9e3403dd6e` confirmed to handle both the plain-password path (`doAuth=1&login=...&password=...`) and the Steam QR-relay path (`doqr=1&qrdata=...`), via live traffic capture (Burp Suite, isolated Kali VM)
- `193.148.56.133` — real, unmasked origin IP shared by `weplayesportse.com` and `signgamergo.com` (confirmed via passive DNS), hosted by Partner Hosting LTD / AS209946; the single highest-value takedown pivot in this case
- Discord Server ID `543078031527510026` — compromised legitimate server (formerly official WePlay Compete)
- Aged Steam recruiter account, disposable Discord verification account
- Compromised link on the official WePlayRocketLeague Twitch channel (65,953 followers) routing to the phishing Discord
- SHA-256 of the `signgamergo.com/login` phishing page — confirmed live 2025-06 through 2026-07 via urlscan.io/VirusTotal (VT: 1/92, flagged as phishing); usable to pivot to other clones of the same kit

Full table: [`ioc.csv`](./ioc.csv)

## Root Cause / Contributing Factors

- Abandoned moderation on a legitimate but defunct Discord server (single admin account, zero messages ever posted — see server audit in the full writeup)
- Broken trust chain: an official Twitch channel unknowingly routes followers into a compromised Discord invite
- No brand-side monitoring of secondary channel integrity after the original platform's 2022 shutdown

## Recommended Actions

1. Report the phishing domain to Steam Support
2. Report the compromised Discord server + dormant admin account to Discord Trust & Safety
3. Report the compromised official-channel-to-phishing link to Twitch Safety
4. ~~Report `signnotclo.com` to **Cloudflare abuse**~~ — **Done, 2026-09-21.** Filed via `abuse.cloudflare.com/phishing`; forwarded to hosting provider per Cloudflare's process.
5. `signgamergo.com` reported via Cloudflare's form (2026-09-21), which Cloudflare forwards to the origin hosting provider (Partner Hosting LTD / AS209946 — see `full-writeup.md`). A direct email to the hosting provider's own abuse contact was deliberately **not** sent — that contact is a personal Gmail address with low-accountability signals, and emailing it directly would expose the reporter's identity for limited added benefit over Cloudflare's intermediated process (see `Scope & Limitations` in `full-writeup.md`). `weplayesportse.com` remains unreported at the domain level, as it's the most easily replaced layer of the kit.
6. Publish IOCs to relevant community channels (Dota 2) — the recruitment vector is still active

## Analyst Note

No automated detection existed for this vector — identification relied entirely on user-side pattern recognition (BitB visual tell, an illogical technical explanation from the operator). This case is a candidate for anti-phishing awareness training and for behavioral detection rule development (e.g., flagging rapid friend-request → voice-call → external-domain-redirect sequences as a generalizable social engineering pattern).

---

## Repository Contents

- **`README.md`** — this file: condensed SOC ticket-style summary
- **[`full-writeup.md`](./full-writeup.md)** — complete investigation writeup: timeline reconstruction from raw chat logs, infrastructure analysis, server moderation history, verification checklist
- **[`attck-mapping.md`](./attck-mapping.md)** — MITRE ATT&CK technique mapping with justification
- **[`ioc.csv`](./ioc.csv)** — structured indicators of compromise
- **[`screenshots/`](./screenshots)** — supporting evidence (chat logs, phishing page, server audit). The author's personal Steam/Discord nickname has been replaced with the pseudonym "Player7" throughout; unrelated third parties' identifying details have been redacted or generalized.

## Disclaimer

This investigation is based on publicly accessible data and the author's own chat logs. No unauthorized access, exploitation, or intrusion was performed — Discord server metadata was retrieved solely via the public Widget API. WePlay Esports' official infrastructure is a victim of compromise in this case, not a knowing participant.
