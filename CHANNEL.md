# Channel contract — template

Copy this into the README of the repository you are using as a channel, fill in the angle
brackets, and delete what does not apply. **This file is what the agent re-reads before every
run.** Write it for the agent, not for yourself.

Keep it short. A contract nobody re-reads is a contract that does not exist.

---

# `<channel-name>`

This repository is a **channel**: the place where `<who asks>` and `<who executes>` exchange
work. Nothing here is a chat log. Every delivery is a file, and the file is the record.

## Who writes where

| Path | Written by | What goes in it |
|---|---|---|
| `<requests>/` | `<the requester>` | one file per request: `REQUEST_<YYYYMMDD>_<id>.md` |
| `<deliveries>/` | `<the executor>` | one file per delivery: `<NAME>_<YYYYMMDD>.md` |
| `<reviews>/` | `<the requester>` | what was accepted or rejected, and why |
| `README.md` | `<the requester>` | this contract |

**Never write outside your own paths.** If you think something belongs elsewhere, say so in
your delivery; do not move it yourself.

## What a delivery looks like

* **One file per delivery. Never update an existing file.** If a new fact arrives after
  today's file exists, write `<NAME>_<YYYYMMDD>_<HHMM>.md` next to it.
* **Say what you did not see, and why.** An unchecked gap declared is information. An
  unchecked gap hidden is a defect that surfaces three days later.
* **Every claim of state carries a source and a date, or the words NOT VERIFIED.**
* **A routine that runs and produces nothing still leaves a trace** — one line saying it ran,
  what it read, and why there was nothing to write. A live routine must not look like a dead one.

## What this channel is for

`<one paragraph: what the executor is expected to do, and what it must never do. Be explicit
about what is out of scope — logins, contacting people, spending money, touching production.>`

## What this channel is NOT

* **It is not the source of truth.** Nothing that arrives here is a finding until it has been
  checked on the requester's side.
* **It is not for secrets.** No credential, token, password or private key, in any file, ever
  — not even temporarily, not even in a code block.
* **It is not a chat.** If it needs a conversation, have the conversation; then write the
  result here.

## Access

* Credential: `<one repository, one permission>`, expires `<date>`.
* `<how the executor is woken up: a schedule, a webhook, a human. Say which.>`

## When something goes wrong

* If you cannot do what was asked, **write that as the delivery**, with the reason. Silence is
  the one answer that cannot be acted on.
* If the contract contradicts itself, **follow the file and report the contradiction**. Do not
  guess which half was meant.
