# MITRE ATT&CK Mapping — WePlay Compete Spear-Phishing Case

| Tactic | Technique | ID | Rationale |
|---|---|---|---|
| Reconnaissance | Gather Victim Identity Information: Social Media Accounts | T1589.002 | Target selected based on ownership of a high-value Steam account, contact made through a shared gaming community |
| Reconnaissance | Phishing for Information: Spearphishing Service | T1598.001 | Initial contact via Steam chat under an interview pretext — trust-building ahead of the attack |
| Resource Development | Acquire Infrastructure: Domains | T1583.001 | Typosquatted domains (weplayesportse.com, weplays.de, login.weplay-streams.pro) |
| Resource Development | Compromise Infrastructure: Server | T1584.004 | Use of the hijacked, legitimate WePlay Compete Discord server as ready-made trust infrastructure |
| Resource Development | Establish Accounts: Social Media Accounts | T1585.001 | Aged Steam account "Westward" (7 years, low activity level) — a hallmark of a purchased/aged account |
| Initial Access | Phishing: Spearphishing Link | T1566.002 | Targeted, personalized contact culminating in a click on the phishing link |
| Initial Access | Phishing: Spearphishing Voice | T1566.004 | Discord voice call used as a social engineering channel, increasing real-time pressure |
| Credential Access | Adversary-in-the-Middle | T1557 | The browser-in-the-browser window intercepts credential input in real time (not a classic MFA-relay proxy, but functionally AiTM: the attacker sits between the target and the legitimate Steam OpenID flow) |
| Credential Access | Multi-Factor Authentication Interception | T1111 | The fake window synchronously prompts for a 2FA code immediately after password entry — an attempted real-time account takeover |
| Defense Evasion | Masquerading: Match Legitimate Name or Location | T1036.005 | Domains and page styling imitate the official WePlay Esports brand |
| Credential Access | Multi-Factor Authentication Request Generation | T1621 | Closest-fit technique for a distinct second vector confirmed via live traffic capture: the panel requests a genuine Steam QR authentication session and relays it to the target, who unknowingly approves the attacker's session by scanning it with their own Steam Mobile app. *Analyst judgment note: ATT&CK has no sub-technique specifically for "QR-code login relay" — T1621 is used here as the nearest documented parallel to this class of device-code/out-of-band-approval phishing (the same family covers MFA-fatigue and device-code relay attacks against platforms like Microsoft 365 and Okta), not a literal match to Steam's QR mechanism.* |
| Command and Control | Not applicable in the classic sense — this is a manual, non-malware-based operation | — | The scheme is entirely social-engineering + web-based; there is no C2 infrastructure in the conventional sense |

*Note: this is not a malware incident, so several tactics (Execution, Persistence, Lateral Movement) are not represented — this is purely a social-engineering + credential-phishing chain. Stated explicitly so this isn't read as forcing the framework onto a case it doesn't fully apply to.*
