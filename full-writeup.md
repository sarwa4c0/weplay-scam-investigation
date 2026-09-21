# WePlay Compete — Spear-Phishing Scam Infrastructure Dossier

2026-09-20 · Investigation by: sarw4c0

## Case Summary

In September 2026, the owner of a Steam account was targeted in a spear-phishing social engineering attack: contact was made under the pretext of an interviewer working with the esports commentary platform "WePlay," discussing a Dota 2-themed interview, followed by an invitation to register on an "advertiser" website and verify the account via Steam. Verification led to a phishing domain hosting a fake browser-in-the-browser (BitB) Steam login window, mimicking the real steamcommunity.com/openid/login page.

The objective was to obtain the Steam login/password and intercept 2FA in real time, with the likely end goal of stealing the account's skins/inventory or the account itself.

**The attack failed**: the target (the author of this dossier) recognized the fake window, refused to enter any credentials, and did not fall for the operator's attempts to explain away suspicion (a false claim about "cookies") or for social pressure tactics (sunk cost, FOMO). The subsequent investigation showed this was not an isolated incident, but part of a years-long, actively exploited infrastructure piggybacking on the name of the real esports organization WePlay Esports.

## Timeline

| Date | Event |
| --- | --- |
| Oct 27–30, 2022 | Official shutdown of the WePlay Compete tournament platform (admin post citing the war in Ukraine). On the same day (Oct 30, 2022), a complaint already appears in the channel — "Skins and accounts are being stolen through your server" — met with mockery rather than a substantive response. |
| Jan 5–6, 2023 | A complaint about skins stolen via a clone site; a participant replies "Not our site, a copy... contact Steam Support" — the remaining admin presence is still distancing itself from the fake site, but no action is taken. Another victim describes losing a valuable in-game item accumulated through significant personal effort — server member AkuLa (not an admin) responds indifferently: "That's a shame, guess you'll have to collect it again" (see "Role of Server Administration"). |
| Feb 2023 | The WePlay Esports bot is still active on Feb 8, 2023 (moderating profanity); on Feb 6–7, 2023, a participant with a handle suggesting a moderator role on a different community directly warns about a specific individual: "this person scams and steals accounts. Don't meet up with them." |
| Oct 6, 2023 | A recurring (automated or manual) warning from user se.keep: the domain **login.weplay-streams.pro** is flagged as a scam, tied to a "streamer" pretext asking users to log in via Steam. |
| Mar 4 – May 15, 2025 | Two threads about account bans — confirms some active moderation is still taking place on the server; the reason for the bans is not established. |
| May 29, 2025 | A "I got scammed" thread from another participant — another complaint in the same period. |
| Jun 20, 2026 | A Turkish-speaking user ("~070") posts "Selam Ben Admin Olmak istiyorum Weplayda id 92795210" (a request for admin rights) — matches the language of the 2025 ban threads, a possible trace of a Turkish-speaking cluster connected to the server's current operation. |
| Jul 24, 2026 | Open warnings from a participant ("♡"): threads titled "SCAM," "THIS DISCORD IS A SCAM," "THEY STEAL YOUR STUFF HERE," "DON'T ENTER ANY DATA," with a detailed description of the scheme (recruitment via Dota 2 community servers, invitation to a "tournament," theft via fake Steam login confirmation). |
| Sep 2026 | The current case: contact via an interview/advertiser pretext, the weplayesportse.com site, a fake Steam verification window — the attack is recognized and rejected. |

**Conclusion:** the picture is closer to gradual moderation decay after the project's shutdown than to a single takeover event: theft complaints appear as early as the shutdown day (Oct 2022), the remaining official presence still distances itself from clone sites in 2023, and by 2025–2026 the server is already being actively used as a recruitment funnel.

## Victim Engagement Vectors

The infrastructure is the same, but over the years it has been run under at least three different pretexts targeting different audience types:

| Vector | Period | Mechanics | Target Audience |
| --- | --- | --- | --- |
| "Streamer invites you to play" | Confirmed by 2023 | Contact posing as a streamer, asking the target to log in via Steam to play together | Broad, random players |
| Tournament/party via Dota 2 community | Confirmed 2024–2026 | Recruitment via party-finding in Dota 2 servers → invitation to the scam Discord to "play a tournament" → promised prizes | Mass-market, regular Dota 2 players |
| "Interview for an advertiser" (September 2026 case) | 2026 | Extended trust-building: game-themed interview → Discord/Twitch/YouTube verification → "advertiser" website → Steam verification | Targeted (spear-phishing), aimed at high-value account owners |

**Breakdown of the targeted vector (September 2026 case):**

1. Contact made under the pretext of an interviewer working with the "WePlay" commentary platform — the interview about Dota 2 genuinely took place and appeared harmless.
2. After the interview, transition to "working with advertisers": a Discord server, Twitch channel, and YouTube channel are referenced by name only (not by direct link), which lowers suspicion.
3. Final stage — registration on the "advertiser" website (weplayesportse.com) with mandatory Steam verification.
4. The target recognizes the fake window and cites technical issues to buy time without confrontation.
5. The operator uses a prepared pseudo-technical explanation ("WePlay doesn't use browser cookies") and, when that fails, softly disengages using sunk-cost/FOMO framing ("we've spent a lot of time on this, I'll move on").

### Contact Reconstruction from Logs (Steam Chat + Discord)

| Date/Time | Event |
| --- | --- |
| Day 1, 21:47–21:55 | First contact in **Steam chat** from the account "Westward." The conversation opens with neutral rapport-building questions: "how long have you been playing dota?", "what's your MMR?" — a typical ice-breaker built on a shared game context. |
| Day 1, 21:55 | Participation pitch: a "new segment" on Westward's channel, prize offered as a game arcana, "no investment required from you besides 15–20 minutes and being in the mood" — framing built around zero cost and minimal effort, to lower the target's natural distrust barrier. |
| Day 1, 21:56–22:02 | The target independently notices a red flag: the Westward account looks like an empty/smurf account. Westward takes over three hours to respond, then returns with an explanation: "The account is used by a moderator for work, we're not going to play" — an explanation that doesn't reconcile with the fact that this same account was used for live conversation about MMR a minute earlier. |
| Sep 15–19, 2026 | Scheduling the call stretches out over five days. Westward requests a Discord contact for further coordination — moving the conversation from Steam to Discord, where a different account will take over. |
| Sep 17, 2026, 20:22 | A Discord friend request is accepted from **skubiduy1337** — the same account previously identified as the recruitment operator (registered Aug 14, 2026). In other words, **Westward on Steam and skubiduy1337 on Discord are separate, coordinated accounts**: the first handles initial contact and builds trust through shared game context, the second runs the actual verification stage on Discord — a division of labor between recruiter and verification operator. |
| Sep 20, 2026, 17:03–17:38 | A 35-minute Discord voice call — the "interview" described above. |
| Sep 20, 2026, 17:16 | Immediately after the call, skubiduy1337 sends a single word: "weplayrocketleague." This is the exact name of the Twitch channel (WePlayRocketLeague) through which the link to the compromised Discord server was confirmed — likely a code word/identifier for routing the target to a specific phishing scenario tied to that brand. |

**Findings from the reconstruction:**

- Contact did not start on Discord but in **Steam chat** — meaning the entry vector is broader than initially assumed: the recruiter sources targets directly through Steam's own game context, not only through gaming communities.
- **Role separation is confirmed by live logs**: one account (Westward) handles recruitment through in-game rapport, a second (skubiduy1337) handles the technical verification stage. This supports the hypothesis of a pipelined, distributed model with stage-based specialization.
- Westward's "moderator's account" explanation is a prepared response to the "empty account" objection, functionally similar to the "no cookies" explanation used for the phishing window — meaning the scheme has a ready set of rebuttals for common victim objections.
- The identifier "weplayrocketleague," sent immediately after the call, directly ties the operator to the specific brand channel through which the compromised Discord link was found — likely not a coincidence, but part of internal routing tied to specific entry points within the scheme.

## Technical Attack Mechanics

**Brand typosquatting.** The domain used closely resembles the real WePlay Esports brand (real domain: weplay.gg): weplayesportse.com (an extra "e" at the end), with weplays.de and login.weplay-streams.pro observed previously. Key point: domains are rotated regularly — when one is blocked, the next is deployed.

**Browser-in-the-browser (BitB) window.** Instead of a genuine redirect to steamcommunity.com, the site renders an HTML/CSS imitation of a browser window directly inside its own page — complete with a fake address bar, lock icon, and "secure connection" text. Visually indistinguishable from a real browser window, but it is not a separate tab/window — it cannot be dragged outside the page's boundaries. This technique is documented in the industry as a "browser-in-the-browser" attack (Group-IB, 2022): instead of a popup, a full replica is rendered directly on the page.

**Framing substitution: "verification," not "login."** The fake window is labeled "Connect Steam" rather than "Log in" — psychologically this lowers suspicion, even though technically, via Steam OpenID, it is the same credential-transfer process.

**A legitimate URL as cover.** steamcommunity.com/openid/login is a genuine Valve endpoint. The openid.return_to parameter in such a URL determines where the target lands after login; in the original report that prompted this investigation, it pointed to an untrusted third-party domain. In the case analyzed here, the window apparently never opened the real URL at all — it was fully rendered/fake from the start.

**The "cookies" pretext.** When the target raised suspicion, the operator claimed the site "doesn't use cookies," so the target needed to "log in to Steam again." This is a false, improvised-after-the-fact explanation: Steam OpenID does not require local cookies from a third-party site by design — the session is managed by Steam itself, which is the whole point of the protocol. The suggestion to copy the link into a separate tab is also part of the manipulation: the real URL in a genuine tab would indeed open the authentic Steam page, but the fake is rendered on the phishing site itself, to intercept input directly through its own JS/HTML.

**Real-time 2FA interception (as documented in industry sources for this type of scheme).** After obtaining the login/password, operators attempt to log into the real Steam account in real time; the real Steam prompts for a 2FA code, and the fake window simultaneously displays a matching code prompt — the entered code is then used immediately to take over the account.

**A second, parallel vector: Steam QR-login relay.** Confirmed via live traffic capture (see below), the same page also offers Steam's genuine "log in via QR code" option — and the panel does not fake this path, it relays it. The client-side JS requests a real QR authentication session from Steam itself (a real `s.team/q/1/<session_id>` link — Steam's own official URL shortener for this feature) and posts it to the phishing backend, which polls it for approval status. If the target scans the displayed QR code with their own Steam Mobile app — trusting it because the link genuinely is Steam's — they are not logging themselves in: they are approving a login session that the attacker's backend is holding open. This requires no password and no 2FA code at all; the target's own device does the "authorizing." This is functionally the same class of attack as MFA/device-code relay phishing documented against other platforms (Microsoft 365, Okta) — see `attck-mapping.md` for the closest-fit ATT&CK technique.

**Live voice pressure.** Communicating over a Discord voice channel instead of text creates social pressure and denies the target time for calm verification; a pause ("I'm having some technical issues") without revealing the true reason is an effective way to buy time for analysis without tipping off the operator that the scheme has been recognized.

### Passive Technical Analysis (VirusTotal / urlscan.io)

No live interaction with the phishing infrastructure was performed for this section — all data below comes from third-party passive-scan services (VirusTotal, urlscan.io), which is the standard, safe way to inspect a suspected phishing page's client-side behavior without submitting any data or risking the analyst's own machine.

**VirusTotal ([community report](https://www.virustotal.com/gui/url/ed1f8c98a27928f282923cbfe5f80e76625e62789edd02998191810d63a55de5/community)):**
- Final URL: `https://signgamergo.com/login`
- Detection: **1/92** security vendors flag the URL as malicious (LevelBlue → Phishing); the remaining 91 report it clean. A low detection ratio is typical of small, rotating typosquat domains that fly under most blocklists' radar — it is not evidence of legitimacy.
- Category: gaming. Tags: `password-input`, `external-resources`.
- First submission: 2025-05-19. Last analysis: 2026-07-16 — the domain has been live and serving the same login page for over a year.

**urlscan.io ([scan 01972ab7-0982-742b-b729-576bbb0211ef](https://urlscan.io/result/01972ab7-0982-742b-b729-576bbb0211ef/)):**
- The page loads a convincing front-end built on public libraries (jQuery 3.7, jQuery UI 1.13.2, AOS.js, Google Fonts) — consistent with a templated clone rather than a from-scratch build, and explains why it renders so cleanly.
- Two same-origin scripts with randomized, hash-like filenames (`be2e3e8.js`, `a38c4c1.js`) are requested from `signgamergo.com` itself. In this scan, both returned **HTTP 500** with empty bodies — meaning their actual logic was not captured. Serving an error specifically to a known scanning service (rather than to a real visitor's browser) is a common anti-analysis technique: the page likely detects automated/sandboxed traffic and withholds the credential-handling code from it. This is consistent with, though does not by itself prove, that these two files carry the actual exfiltration logic (where entered credentials/2FA codes are sent) referenced earlier in this document's BitB analysis.
- Serving infrastructure is Cloudflare-fronted (edge IP `172.67.210.212` at scan time; VirusTotal separately recorded `2.27.15.173` on a later check) — the real origin server is masked, which matters for takedown: an abuse report needs to go to **Cloudflare**, not just the domain registrar or a hosting ISP that may only be a CDN pass-through.
- SHA-256 of the login page's HTML response: `9208a2c885fcc5a44cc0b494b2696b6a4d4cd647cae71bf96ec4cd8b1947f30f`. This is a usable pivot: searching this hash on urlscan.io or VirusTotal can surface other domains serving byte-for-byte the same phishing page (i.e., new clones of this exact kit), which is more precise than matching on visual similarity or domain-name patterns alone.

**Limitation (passive data only):** because the two suspect scripts failed to load in this particular scan, the exact exfiltration endpoint could not be confirmed from passive scan data alone. This gap is closed below — the live capture confirms the endpoint for both the QR-relay path and the plain password path.

### Live Sandbox Traffic Capture (Burp Suite, Isolated Kali VM)

To move past the limits of passive scanning, a controlled dynamic test was performed: Burp Suite Community Edition running as an intercepting proxy inside an isolated Kali Linux VM, with Firefox's traffic routed through it and Burp's CA certificate trusted for TLS inspection. Methodology was deliberately conservative — Intercept left **off** so traffic simply logged to HTTP history in the background, and exactly **one** submission of non-functional dummy data to the login form, purely to observe where the data was sent. No repeated submissions, no automated tooling, no interaction with the phishing panel beyond this single passive observation.

**Third domain discovered: `signnotclo.com`.** The Site map showed this domain loaded inside `signgamergo.com` via an `<iframe>` (request headers confirm `Sec-Fetch-Dest: iframe`, `Sec-Fetch-Site: cross-site`). This reveals the kit's real architecture as three tiers, not two:

1. `weplayesportse.com` — the outward, brand-spoofing "shell" domain shown to the target first
2. `signgamergo.com` — a generic, reusable login-panel domain (not itself WePlay-branded — likely shared across multiple campaigns/brands using the same kit)
3. `signnotclo.com` — a separate backend, embedded as an iframe, that the login panel talks to

Separating the outward-facing brand domain from the backend this way lets the operators swap tier 1 (the part most likely to get reported/blocklisted for brand impersonation) without touching tiers 2–3, which is a meaningful resilience/evasion property worth flagging for takedown requests: reporting only `weplayesportse.com` would leave the reusable panel and backend fully intact for the next shell domain.

**Endpoint captured:** a `POST` to `https://signnotclo.com/9e3403dd6e` was recorded following the single dummy-data submission. Request body (URL-encoded): `doqr=1&qrdata=https://s.team/q/1/<session_id>`. Despite a `Content-Type: text/html` response header, the response body is JSON, polled repeatedly by the client-side JS as the QR session's status changes — observed values included `{"status":"qrlink","qrlink":"..."}` and `{"status":"wait","qrlink":"...","left":<milliseconds remaining>}`, the countdown matching Steam's own real QR-challenge expiry window. This is the mechanism described above under "A second, parallel vector: Steam QR-login relay" — `signnotclo.com` is that relay backend.

Static assets on `signnotclo.com` follow the same randomized, hash-like naming convention observed earlier on `signgamergo.com` (e.g., paths under `/12357fefc/a0136/`, also covering image files such as `0425aa4.png`), consistent with the same kit family or the same operator's tooling reused across domains. Server headers confirmed Cloudflare fronting here as well (`Server: cloudflare`, `Cf-Ray`, `Report-To`/`Nel`, `Alt-Svc`) — the same takedown caveat applies: an abuse report needs to reach Cloudflare, not just the registrar of whichever shell domain is live at the time.

One additional request type appeared in the Site map that is worth explicitly ruling out rather than leaving ambiguous: periodic `POST /cdn-cgi/rum?` calls to the same host. `cdn-cgi` is Cloudflare's own reserved path namespace, and this is a standard Real User Monitoring (RUM) performance beacon (204 No Content, ordinary Cloudflare response headers, no attacker-relevant payload) — not a second attacker-controlled exfiltration channel. Logged here so it isn't mistaken for one.

**Password path also captured.** A second, separate test submission — this time through the ordinary login form rather than the QR option — produced a `POST` to the *same* endpoint, `https://signnotclo.com/9e3403dd6e`, but with a different body: `Content-Type: application/x-www-form-urlencoded`, payload `doAuth=1&login=<value>&password=<value>`. This resolves the gap left open above: `/9e3403dd6e` is not two separate backends for two separate attack paths, it is a **single unified auth-relay endpoint** that dispatches on which body parameter is present — `doqr` routes to the QR-relay flow, `doAuth` routes to a conventional credential-capture flow. Both the password path and the QR path exfiltrate through the same handler on `signnotclo.com`, which is itself the domain loaded as an iframe inside `signgamergo.com`.

**What this now resolves:** with both submissions captured, the exfiltration endpoint is confirmed for **both** vectors described in this document — the BitB password/2FA path and the QR-relay path — closing the limitation noted earlier in the passive-analysis section. What remains unconfirmed (and out of scope for this investigation, since it would require deeper access than passive/single-submission testing allows) is what `signnotclo.com` itself does with the captured credentials after receiving them — e.g., whether it replays them live against Steam's real login in real time, or queues them for manual use — since that would require either server-side visibility the analyst doesn't have, or timing/replay tests against live attacker infrastructure that cross well past passive observation and were deliberately not attempted.

**WHOIS and origin-server observations.** A WHOIS lookup on `signnotclo.com` shows it registered through **NICENIC INTERNATIONAL GROUP CO., LIMITED**, a low-cost Hong Kong-based bulk registrar commonly associated with phishing/scam infrastructure due to minimal identity verification at registration time — consistent with, though not proof of, disposable-infrastructure practices. The domain was created 2025-12-09 (roughly nine months before this campaign was observed, so not a same-day throwaway registration), expires 2026-12-09, and uses Cloudflare nameservers; registrant identity is redacted via standard WHOIS privacy.

A plain HTTP (port 80) request to each of the three domains revealed a useful asymmetry. `weplayesportse.com` and `signgamergo.com` both return **raw origin-server headers with no Cloudflare involvement at all** (`Server: nginx/1.18.0 (Ubuntu)`) on their HTTP→HTTPS redirect responses, while `signnotclo.com` is Cloudflare-fronted even on port 80 (`Server: cloudflare`, `CF-RAY`, standard `Report-To`/`Nel` headers). Two things follow from this:
- The identical `nginx/1.18.0 (Ubuntu)` signature on both tier-1 and tier-2 domains is independent evidence (beyond naming/behavioral similarity) that they sit on the same hosting setup or template, reinforcing the shared-operator hypothesis.
- Because the tier-1/tier-2 redirect responses aren't proxied on port 80, the real origin IP for those two domains was directly resolvable via ordinary passive DNS lookup, rather than being fully masked behind Cloudflare's edge as `signnotclo.com` is.

**Real origin IP identified.** A passive DNS lookup (`nslookup`, no active scanning) confirmed exactly this: both `weplayesportse.com` and `signgamergo.com` resolve to the same IP, **`193.148.56.133`** — not a Cloudflare range — while `signnotclo.com` resolves to ordinary Cloudflare anycast addresses (`104.21.92.97`, `172.67.191.94`, and IPv6 `2606:4700:...`), as expected. This is the single highest-value pivot of the entire investigation: an unmasked origin server shared by the two outward-facing tiers of the kit.

A WHOIS lookup on that IP block (`193.148.56.0/24`, AS209946) returned:
- **Organisation:** Partner Hosting LTD (org-type: OTHER), registered address **71-75 Shelton Street, Covent Garden, London WC2H 9JQ, United Kingdom** — a widely recognized bulk company-formation/virtual-office address used by very large numbers of UK-registered shell entities, including ones tied to low-accountability hosting. This alone isn't proof of anything, but it's a familiar pattern to anyone who's done infrastructure-abuse work.
- **Abuse contact:** a personal Gmail address (`a99423123@gmail.com`) rather than a corporate `abuse@` mailbox — again not conclusive on its own, but a recurring characteristic of resellers that don't run a real abuse-handling process, sometimes described informally as "bulletproof-adjacent" hosting.
- **Netblock/route object created 2026-06-10** — roughly three months before this campaign was observed, consistent with a relatively fast-turnover hosting block rather than long-established infrastructure.

This closes out the infrastructure analysis with a genuine, actionable pivot: an abuse report for the primary phishing kit can now go directly to the origin hosting provider (`a99423123@gmail.com` / AS209946), in addition to Cloudflare (for `signnotclo.com`, which remains fully proxied) and the domain registrars. No further action was taken against the identified IP beyond this passive resolution and WHOIS lookup — this is where the investigation stops, and where reporting to the relevant abuse contacts and platforms takes over.

**Reports filed (2026-09-21):** Abuse reports were submitted through Cloudflare's phishing report form (`abuse.cloudflare.com/phishing`) for both `signnotclo.com` and `signgamergo.com`, each citing the confirmed endpoint, request/response evidence, and IOCs documented above; both reports opted to forward to the respective hosting provider (Cloudflare automatically relays to origin hosts/owners as part of its process) while withholding reporter contact details from that forward. This is the point where the investigation transitions from analysis to actual remediation — status of any resulting takedown wasn't yet known at time of writing and would need a follow-up check.

## Infrastructure

### Clone Domains (Timeline of Appearance)

| Domain | First Observed | Pretext |
| --- | --- | --- |
| weplays.de | 2023 | Streamer invitation to play |
| login.weplay-streams.pro | ≤ Oct 2023 | Streamer invitation to play |
| weplayesportse.com | ≤ Sep 2026 | "Advertiser"/interview |
| signgamergo.com | ≤ Sep 2026 | Companion login page, seen in the same chain |
| signnotclo.com | 2026-09 (confirmed via live capture) | Backend relay for the Steam QR-login vector, embedded as an iframe inside signgamergo.com |

All domains are variations on the real WePlay Esports brand name; none is official.

### Discord Server

The server used in this scheme is the genuine, formerly official **WePlay Compete** server, shut down by the WePlay team on Oct 27–30, 2022. It was not created from scratch by the scammers — it is a hijacked/decayed legitimate asset, which explains why it appears so convincing: a real multi-year history, thousands of members, and organic reactions accumulated over the years.

The brand's social channels (e.g., the Twitch account "Weplay_RocketLeague," ~23K followers, styled and described to match the real WePlay Esports) also turned out to be fake/compromised — the "Discord" link in their description leads to the same scam server and phishing site. Conclusion: an outwardly convincing secondary channel with an accurate brand description is not proof of legitimacy without checking the verification badge and where its own links actually lead.

**Confirmed:** a second verified channel — **WePlayRocketLeague** (65,953 followers, attributed to "WePlay Studios," paid subscriptions) — is clearly part of the genuine official structure: the page includes a "WePlay Esports" panel listing sister channels (WePlayDota, WePlayDotaB, WePlay_UA, WePlayCSGO4). The **Discord** button on this page still leads to the compromised/decayed WePlay Compete server. Given the channel's significance (65,953 followers, listed alongside other recognizable WePlay Dota 2, CS:GO, and Ukraine-region brand channels), coincidence is highly unlikely. **Updated conclusion:** this is no longer a standalone fake account, but a compromise of the link between the brand's genuinely active official Twitch channels and malicious infrastructure: anyone who clicks the official Discord link from the real Twitch channel lands on the phishing server. This raises the priority of urgently contacting Twitch Safety and WePlay Esports directly — not just Discord Trust & Safety.

**State of the official website (weplay.tv).** The homepage/"About Us" loads and contains an accurate company history (founded in 2012 in Kyiv, founders Ura Lazebnikov and Oleg Krot, WePlay Esports/WePlay Studios brand), but every other section of the site returns a 404. This points to general neglect of the digital infrastructure as a whole (an abandoned CMS/domain migration without completed redirects, or a lack of internal oversight) rather than a full project abandonment. This indirectly supports the investigation's core finding: the brand has no actively maintained map of its own resources, which is how an outdated link to a compromised Discord server has gone unnoticed for years, both on Twitch channels and on the website.

From June 2023 through July 2026, the server accumulates an open trail of victim complaints (threads titled "SCAM," "THEY STEAL YOUR STUFF HERE," "DON'T ENTER ANY DATA") that are never removed.

### Associated Accounts

**Scammer's Steam account ("Westward").** "7 Years of Service" at Level 10, only 18 games, 4 badges, 2 artworks. A strong mismatch between account age and depth of activity — a hallmark of a purchased/aged account, used to bypass trade restrictions and increase perceived trustworthiness.

**Scammer's Discord account (skubiduy1337).** Registered Aug 14, 2026 — less than a month before contact. Generic handle, no activity history, no linked accounts — indicators of a disposable, single-campaign account. **Membership of this account on the same Discord server** (formerly WePlay Compete) is confirmed — a direct link between this specific operator and the infrastructure.

**Turkish-language trace.** Several Turkish-language messages at different times (the March–May 2025 ban threads, the June 2026 admin request) initially suggested a persistent Turkish-speaking cluster among those interacting with the server. Independent verification (message search, server role list) did not confirm this hypothesis: these are two isolated episodes over a year apart, with no signs of coordination or overlap with the real administration — a language coincidence, nothing more.

## Role of Server Administration

The moderation history shows gradual erosion of accountability rather than a single takeover event:

- **Oct 27–30, 2022** — the still-active administration officially announces the platform's shutdown; on the same day, a complaint appears in the channel about accounts/skins being stolen through the server — another participant's reply, tagged EXR, is mocking and dismissive rather than substantive (independent verification showed the EXR tag is unrelated to admin/mod roles — it's a 2024/2025+ tag from an entirely different, unrelated server, mistakenly read as an admin indicator on initial screenshot review).
- **Jan 5–6, 2023** — a victim writes "all my skins were stolen through your site," a participant replies: "Not our site, a copy... contact Steam Support" — still distancing from the fake site, but taking no action. Independent verification showed this participant also holds no admin/mod role on the server — a regular member, not an administration representative.
- **Jan 6, 2023, key finding** — another victim describes the theft of a valuable in-game item, accumulated through significant personal effort. **AkuLa** responds (independent verification of server roles confirmed AkuLa is a regular member, with no admin/mod role): "That's a shame, guess you'll have to collect it again."

**Why this matters:** this is the reaction of a regular server member, not the administration — independent role verification confirmed AkuLa held no admin/mod permissions. What matters more: the server's single real administrator (Theo, holding the Tournament Admin + WePlay Staff roles) never posted a single message during the entire lifetime of their account on the server — meaning the administration formally exists but is effectively dead. No one moderates or responds to complaints, which is exactly what has allowed the server to serve as scam infrastructure for years.

**A related marker:** the "WePlay Esports" bot was still active in February 2023 (moderating profanity), and a separate participant directly named a specific individual as an account scammer (Feb 6–7, 2023) — meaning at this stage some partial, targeted reaction still existed, but without systemic cleanup.

By 2025–2026, the situation worsens: open "SCAM" threads go uncleaned, a participant with no permissions requests admin rights directly in chat — and nothing stops it, because there is no one left to stop it. Conclusion: the server did not travel from "an aware but indifferent administration" to its current state — it went from a formally existing but effectively dead administration from the start (the one real admin never posted a single message) to fully unmonitored infrastructure, exploited as a victim recruitment funnel (2025–2026).

### Server Technical Artifacts (Independent Verification)

A separate investigation session performed a direct walkthrough of the server via Discord (no hacking involved — only publicly available data and the Widget API) and confirmed several facts that refine the picture:

- **Server ID:** 543078031527510026.
- **The only real administrator** — the account "Theo Ä(◁)⯸ 💗L&DS" (theradiationgone), holding the Tournament Admin, WePlay Staff, and Toxic roles. A search for `from:theradiationgone` across the server's full message history returns zero messages — the account is present in the member list but has never been used for moderation.
- **Two active invite links:** one published by the organization itself on the WePlayRocketLeague Twitch channel, and a second (`discord.com/invite/xHXZpHcx`) discovered through the public Widget API (`/api/guilds/543078031527510026/widget.json`) — this method allows checking a server's state (online status, invites) without joining it.
- **Presence count:** ~3,192 concurrent users online (as of Sep 20, 2026) — the server is not technically abandoned; the audience is active, while moderation is absent.
- **#rules channel:** rule 1.1 instructs members to escalate disputes directly to the administration — but the escalation channel is currently inaccessible to regular members; rule 1.8 prohibits impersonating official WePlay representatives — ironic, given that this is exactly what is happening on the server now.
- Separately, a message from Oct 30, 2022, 19:48 was found in the server history — a still-legitimate prize giveaway bot, asking users to add the organizer as a Steam friend to participate. This is likely the origin of the "add me as a friend for a prize" behavioral pattern later adopted by the scam scheme.

## New Contact Verification Checklist

Apply immediately to any new inbound contact, especially if it later involves clicking a link or logging into an account.

1. **Account age vs. activity volume.** An old Steam account with a low level, few games, and few badges is a sign of a purchased/aged account. Same for Discord: a recent registration date paired with a claimed long industry track record is a mismatch.
2. **Community age ≠ safety.** Even an old, genuine, and once-reputable Discord server can be abandoned or hijacked. Check the age and activity of the specific individual you're talking to, not just the community itself.
3. **Verify secondary channels by name, not by link.** Search for Discord/Twitch/YouTube channels by name rather than clicking sent links — this alone rules out landing on a clone immediately.
4. **But even a channel found via search needs further verification:** does it carry a verification badge (e.g., Twitch Partner), does the username match the official one from an independent source (Wikipedia, press releases), not just inside the scam chain itself. A convincing look and a relevant description are not proof.
5. **Character-by-character domain check.** Compare against the known official domain letter by letter, especially before entering any data.
6. **The browser-in-the-browser test.** Try to drag the login popup outside the browser tab's boundaries — a real browser window will extend past the page, a rendered fake one won't.
7. **Copy the link into a separate tab rather than trusting the window embedded in the page.**
8. **Check the other party's technical explanations for logical consistency.** Genuine OpenID/OAuth does not require re-login due to "missing cookies" — any such explanation is a red flag.
9. **Check with the community/search engines.** Search for scam mentions tied to the brand/domain name before interacting, including within the server/channel itself (complaint threads).
10. **Don't give in to live voice/time pressure.** Citing technical issues and taking a pause to analyze is an effective, non-confrontational way to buy time.

### Recommendations for This Case

- Compile the screenshots into a single dossier (this document + attached images) and submit it to Discord Trust & Safety (key argument: the server's only admin account has never posted a single message, the complaint escalation channel is closed to regular members, and roughly 3,192 users are online concurrently — i.e., active but fully unmonitored infrastructure).
- Optionally, report the phishing attempt to Steam Support, even without a successful theft — this helps get domains blocked faster.
- Cease all further interaction with this server/these accounts; warn contacts in the Dota 2 community, since the party-finder recruitment vector remains active.

## Scope & Limitations

This is a solo investigation, conducted by the account holder who was targeted, not a formal incident-response engagement — worth stating plainly rather than letting the polished write-up imply otherwise.

- **No peer review.** Every finding here was gathered, interpreted, and written up by one analyst. There was no second reviewer to catch a misread packet, a wrong ATT&CK mapping, or a conclusion drawn one step further than the evidence supports. Where a finding rests on interpretation rather than direct evidence (e.g., the WHOIS/hosting "bulletproof-adjacent" pattern read), that's flagged inline as analyst judgment, not stated as fact.
- **Tooling was what a single analyst has on a personal machine**, not an enterprise stack: Burp Suite Community Edition (not Pro — no built-in scanner, no extensions used), free-tier VirusTotal and urlscan.io (both partially gated behind login/CAPTCHA, which was respected rather than bypassed — see below), and standard Kali command-line tools (`nslookup`, `whois`, `curl`). No SIEM, no EDR telemetry, no access to the target platforms' backend logs (Steam, Discord, Twitch) — everything here comes from what's externally observable.
- **Live testing was intentionally minimal and one-shot.** All dynamic analysis happened in an isolated Kali VM, with exactly one dummy-data submission per form path (one for the QR-relay flow, one for the password flow) — never repeated, automated, or used to probe further than "where does this go and what comes back." No exploitation, no attempt to access the phishing kit's backend/database/admin panel, no active port scanning, and no interaction beyond what a real (if suspicious) visitor's single form submission would generate.
- **No attribution was attempted.** This document identifies infrastructure (domains, IPs, a hosting provider, a registrar) — it does not attempt to identify or accuse any individual operator. Patterns like the registrar choice or the Gmail abuse contact are noted as infrastructure-hygiene signals, not as claims about who is behind the campaign.
- **This is a point-in-time snapshot (September 2026).** Domains, IPs, and hosting can and likely will change; some IOCs in this document may already be stale by the time it's read. The investigation reflects what was observable during the window it was conducted, not a continuously monitored feed.
- **Reporting to platforms/abuse contacts was recommended, not necessarily completed and verified end-to-end** at the time of writing — see Recommended Actions above and in `README.md`.
- **Deliberately did not email the origin hosting provider's abuse contact directly.** Cloudflare abuse reports were filed for `signnotclo.com` and `signgamergo.com`, which Cloudflare itself forwards to the relevant hosting provider as part of its process. A direct email to the hosting provider's own listed abuse address (`a99423123@gmail.com`) was considered and deliberately not sent: that contact shows several low-accountability signals (a personal Gmail address rather than a corporate mailbox, a bulk virtual-office registration address), and emailing it directly from a personal account would expose the reporter's own email address to an entity with no established trust or accountability, for a domain-level takedown that Cloudflare's intermediated process already covers reasonably well. This is a deliberate OPSEC/reputational-risk tradeoff, not an oversight.

None of this is a disclaimer to lower confidence in the specific technical claims made (each one is tied to a specific piece of captured evidence, cited above) — it's here so a reader evaluating this as portfolio work knows exactly what kind of investigation this was and wasn't, rather than assuming a scope or rigor that wasn't actually there.

---

*The author's personal Steam/Discord nickname has been replaced with the pseudonym "Player7" across all attached screenshots. Identifying details of unrelated third parties have been redacted or generalized.*
