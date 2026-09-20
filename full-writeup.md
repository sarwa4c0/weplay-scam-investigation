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

**Live voice pressure.** Communicating over a Discord voice channel instead of text creates social pressure and denies the target time for calm verification; a pause ("I'm having some technical issues") without revealing the true reason is an effective way to buy time for analysis without tipping off the operator that the scheme has been recognized.

## Infrastructure

### Clone Domains (Timeline of Appearance)

| Domain | First Observed | Pretext |
| --- | --- | --- |
| weplays.de | 2023 | Streamer invitation to play |
| login.weplay-streams.pro | ≤ Oct 2023 | Streamer invitation to play |
| weplayesportse.com | ≤ Sep 2026 | "Advertiser"/interview |
| signgamergo.com | ≤ Sep 2026 | Companion login page, seen in the same chain |

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

---

*The author's personal Steam/Discord nickname has been replaced with the pseudonym "Player7" across all attached screenshots. Identifying details of unrelated third parties have been redacted or generalized.*
