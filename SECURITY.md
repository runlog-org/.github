# Security Policy

This policy applies to all repositories in the [`runlog-org`](https://github.com/runlog-org)
organisation. Runlog is a hobby side project maintained by a single
person; we still take security reports seriously, but please calibrate
your expectations on response time accordingly.

## Reporting a vulnerability

**Please do not open a public issue for a security finding.**

Two private channels:

- **Email** — `runlog@volkerotto.net`. Subject line `[security]` is helpful.
- **GitHub Private Vulnerability Reporting** — on repos where it's enabled,
  use the **Security → Report a vulnerability** tab.

A useful report includes: the repo and version (or commit), the
vulnerability class, a clear reproduction (PoC or steps), and the
impact you observed. Screenshots and packet captures are welcome.

If you'd like to encrypt the report, request a public key in your first
message and we'll reply with one.

## In scope

We're particularly interested in findings that affect:

- **Authentication and authorisation** — API key handling, registration,
  session, rate-limit bypass, privilege escalation.
- **Submission integrity** — sanitisation bypass that lets disallowed
  literals into a published entry, allow-list circumvention, or any path
  that lets unverified content reach `status:verified`.
- **Verifier** ([`runlog-verifier`](https://github.com/runlog-org/runlog-verifier))
  — signature forgery, key extraction, replay, or any flaw that lets a
  rejection be misrepresented as a verification.
- **Schema / vocabularies** ([`runlog-schema`](https://github.com/runlog-org/runlog-schema),
  [`runlog-vocabularies`](https://github.com/runlog-org/runlog-vocabularies))
  — flaws in the contract or data that enable malicious submissions
  downstream.
- **Skills** ([`runlog-skills`](https://github.com/runlog-org/runlog-skills))
  — anything that lets an adapter exfiltrate user data, execute code
  outside the documented contract, or escalate beyond what the host
  agent permits.
- **Website / registration** ([`runlog-website`](https://github.com/runlog-org/runlog-website))
  — flaws in the registration flow, token issuance, or anything that
  exposes user-supplied data.

## Out of scope

To keep noise down:

- **Volumetric DoS, stress tests, fuzzing against production.** Please
  don't. If you've found a non-volumetric flaw that a small request load
  triggers, that's in scope — describe it without reproducing at scale.
- **Self-XSS** and clickjacking on pages without sensitive actions.
- **Missing or weak security headers** without a demonstrated exploit.
- **SPF / DKIM / DMARC** configuration issues without a working spoof.
- **Reports from automated scanners** without a working PoC and impact
  description.
- **Vulnerabilities in third-party platforms** we run on — please report
  those to the vendor directly.
- **Social-engineering** of maintainers, contributors, or users.

## What to expect from us

- Acknowledgement within five working days.
- An initial assessment (in scope / out of scope / need more info)
  within ten working days.
- Coordinated disclosure: we'll work with you on a fix and a public
  advisory. We'll credit you by name or handle if you'd like, or keep
  you anonymous if you prefer.
- We're a small project and may be slow on the fix itself. We'd rather
  be honest about that than promise a tight SLA we can't keep.

## Safe harbour

We won't pursue legal action against research conducted in good faith
that:

- accesses no more data than necessary to demonstrate the issue,
- doesn't degrade service for other users,
- stops and contacts us as soon as user data is encountered,
- and gives us a reasonable window to fix the issue before public
  disclosure.

If you're unsure whether your testing crosses one of those lines, ask
us in advance — `runlog@volkerotto.net`.

## Languages

We can read security reports in **English** or **German**.
