# WePlay Compete — Spear-Phishing Investigation

**Incident ID:** INC-2026-0920-WEPLAY-PHISH
**Severity:** Medium-High
**Status:** Contained, no credential loss. Abuse reports filed with Cloudflare (2026-09-21) for `signnotclo.com` and `signgamergo.com`; takedown outcome pending.
**Detection Source:** End-user (manual recognition) — no automated detection involved
**Date/Time of primary event:** 2026-09-20, 17:03–17:38 (voice call), verification attempt immediately after

## Summary

Targeted spear-phishing attack against a Steam account owner via an "interview for an esports advertiser" pretext, using compromised legitimate WePlay Esports infrastructure (hijacked Discord server + a link on the official Twitch channel) as a trust vector. Final stage was a browser-in-the-browser (BitB) fake Steam login, with a second confirmed vector — a Steam QR-login relay — enabling account takeover without a password or 2FA code. The target recognized the fake login window and disengaged before entering data.

Full narrative, technical mechanics, and live traffic-capture evidence: [`full-writeup.md`](./full-writeup.md).

## Timeline

| Time (UTC+3) | Event |
|---|---|
| T-9 days | Initial contact in Steam chat, rapport-building |
| T-9 days | "New segment" pitch offered |
| T-5..T-1 days | Conversation moved to Discord |
| T0, 17:03–17:38 | 35-minute voice call — the "interview" |
| T0, 17:16 | Routing keyword sent immediately after the call |
| T0 | Redirected to phishing domain → BitB Steam login |
| T0 | Fake login window recognized, no data entered, contact ended |

## Attack Vector

Spearphishing Link (T1566.002) + Spearphishing Voice (T1566.004) → Adversary-in-the-Middle credential capture (T1557) via BitB → MFA Interception (T1111), plus a parallel Steam QR-relay vector (T1621). Full mapping and rationale: [`attck-mapping.md`](./attck-mapping.md).

## Key IOCs

- `weplayesportse.com`, `signgamergo.com`, `signnotclo.com` — three-tier phishing kit chain
- `193.148.56.133` — real, unmasked origin IP (Partner Hosting LTD / AS209946) — highest-value takedown pivot
- Discord Server ID `543078031527510026` — compromised legitimate WePlay Compete server
- Compromised link on the official WePlayRocketLeague Twitch channel (65,953 followers)

Full table with detail and provenance: [`ioc.csv`](./ioc.csv)

## Root Cause / Contributing Factors

- Abandoned moderation on a legitimate but defunct Discord server
- Broken trust chain: an official Twitch channel routes followers into a compromised Discord invite
- No brand-side monitoring of secondary channel integrity after the original platform's 2022 shutdown

## Recommended Actions

1. Report the phishing domain to Steam Support
2. Report the compromised Discord server + dormant admin account to Discord Trust & Safety
3. Report the compromised official-channel-to-phishing link to Twitch Safety
4. ~~Report to Cloudflare abuse~~ — **Done, 2026-09-21** for `signnotclo.com` and `signgamergo.com`. See `full-writeup.md` for what was and wasn't done regarding the origin hosting provider, and why.
5. Publish IOCs to relevant community channels (Dota 2) — the recruitment vector is still active

## Analyst Note

No automated detection existed for this vector — identification relied entirely on user-side pattern recognition (BitB visual tell, an illogical technical explanation from the operator). Candidate for anti-phishing awareness training and behavioral detection rule development (e.g., flagging rapid friend-request → voice-call → external-domain-redirect sequences).

---

## Repository Contents

- **`README.md`** — this file: condensed SOC ticket-style summary
- **[`full-writeup.md`](./full-writeup.md)** — complete investigation: timeline reconstruction, technical attack mechanics, live traffic-capture analysis, infrastructure, scope & limitations
- **[`attck-mapping.md`](./attck-mapping.md)** — MITRE ATT&CK technique mapping with justification
- **[`ioc.csv`](./ioc.csv)** — structured indicators of compromise
- **[`screenshots/`](./screenshots)** — supporting evidence. The author's personal Steam/Discord nickname has been replaced with the pseudonym "Player7" throughout; unrelated third parties' identifying details have been redacted or generalized.

## Disclaimer

This investigation is based on publicly accessible data and the author's own chat logs. No unauthorized access, exploitation, or intrusion was performed — Discord server metadata was retrieved solely via the public Widget API. WePlay Esports' official infrastructure is a victim of compromise in this case, not a knowing participant.
