# Entity Match

**🔗 Live demo:** https://biancabcarlson.github.io/Entity-Match/

Matches names, emails, phones, and addresses across accounts — including previously used contact info. Built for KYC / case-review work: catching duplicate accounts, synthetic identities, or an account takeover where the attacker opens a second account using the victim's *previously used* contact info.

## Matching logic (`entity_name_matcher.py`)

- `score_names(a, b)` — fuzzy name similarity (nicknames, initials, reordering, transliteration, legal-suffix noise for orgs)
- `find_pii_collisions(accounts)` — scans a list of account records and flags any pair with matching name/email/phone/address, including a *current* value on one account matching a *retired* value on another (pulled from `activityLog`-style change history)

```
python entity_name_matcher.py "Robert J. Smith" "Bob Smith"
python entity_name_matcher.py --accounts accounts.json
```

## Web demo

Runs entirely client-side — nothing is saved or uploaded. Comes pre-loaded with two example accounts and shows any flagged overlap immediately; there's also a field to search a different name/email/phone/address against all loaded accounts.

Each flagged match shows a masked account number (e.g. `•••1187`) with a click-to-unmask toggle, and states *which* field overlapped (email, phone, address) without restating the value — it's already visible once in the accounts table.

## Privacy Mode

The 🔒 Privacy Mode toggle (top right, shared across the suite via `localStorage`) blurs each account's name, email, phone, and address in the accounts table.

## Used alongside

Paired with the [`simulated-account`](https://github.com/biancabcarlson/simulated-account) fixture, whose second account (`account-data-2.json`) reuses the primary account's retired email and phone at the same address — the exact case this tool is built to catch.

## Other tools in this series

- [Case Calculator](https://biancabcarlson.github.io/Case-Calculator/)
- [Report Builder](https://biancabcarlson.github.io/Report-Builder/)
- [OSINT Assistant](https://biancabcarlson.github.io/OSINT-Assistant/)
- [Documents Folder](https://biancabcarlson.github.io/Documents-Folder/)
- [Entity Match](https://biancabcarlson.github.io/Entity-Match/) *(this repo)*
- [Timeline Builder](https://biancabcarlson.github.io/Timeline-Builder/)
