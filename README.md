# Channel Contract

**A versioned repository as the channel between you and an agent that runs somewhere else.**

The contract lives in the channel itself, and the agent re-reads it on every run — instead of
being told the same things again in every message. It outlives the session, the model change,
and everybody's memory.

The method, the reasoning behind it, and the server it was tested on:
**[edgebuildlabs.github.io](https://edgebuildlabs.github.io/)** (also in
[Português](https://edgebuildlabs.github.io/pt/) and [Español](https://edgebuildlabs.github.io/es/)).
The brand site, for hiring: [edgebuildlabs.tech](https://edgebuildlabs.tech/) (PT, EN).

## The problem

Your agent runs on another machine — a vendor's cloud, a VPS, another account. It delivers in
a chat window. Then the session ends, and so does everything it knew and everything it said.
Next week nobody can tell what it delivered, or under which rule it was told to work.

There is a worse failure, and it is quiet. **The chat reports late, and late is
indistinguishable from never.** While the message has not arrived, success, delay and failure
look exactly the same from your side. Measured on 17 September 2026: a delivery was correct
and already committed while the chat stayed silent for about seventy minutes, then answered
the whole queue at once. Any decision that depends on telling "stopped" from "slow" is a
decision you cannot make.

## What this is

A repository used as a channel. Not a framework, not a queue, not CI — a folder with a
contract in it and a history that anyone can read.

The agent gets one credential, writes one file per delivery, and reads the contract before
each run. You read the commits. Nothing depends on a chat window staying open, and nothing
depends on either side remembering anything.

## How to use it in four steps

1. **Create a repository.** Private is fine. It is the channel.
2. **Copy `CHANNEL.md` into its README and fill it in** — what the channel is for, who writes
   where, and what a delivery looks like. This is what the agent re-reads.
3. **Give the agent a minimum-scope credential:** one repository, one permission, an expiry
   date you wrote down.
4. **Ask by file, receive by file.** The commit on the remote is your detector. Not the chat.

## The three rules

Everything else is detail. These three are the contract:

* **One file per delivery — never update an existing one.** Appending to a live file is where
  two writers collide and where history quietly disappears. A new file per delivery makes the
  log immutable and the diff meaningful.
* **Minimum-scope credential.** One repository, one permission, an expiry you know. A channel
  is a door; do not make it a master key.
* **The channel is not the source of truth.** Nothing that arrives in it is a finding until it
  has been checked on your side. An unverified signal quoted in a report is misinformation
  that looks like work.

## What this is NOT

* It is not a message queue, a job runner, or CI. There is no daemon and no service to keep up.
* It does not require any specific tool, plugin, model, or vendor.
* It does not replace an evidence contract. **The channel carries the delivery; the evidence
  contract is what makes the delivery provable.** Use both.
* It is not a place for secrets. Ever.

## Companion pieces

This says how you **talk** to an agent that runs elsewhere. Its companions say how you **ask**
and how the agent **proves**:

* [work-order-contract](https://github.com/edgebuildlabs/work-order-contract) — how to ask for
  the work so that proof is possible.
* [evidence-contracts](https://github.com/edgebuildlabs/evidence-contracts) — how the agent
  reports what it ran, when, and what came back.

## License

CC0 1.0 Universal. See `LICENSE`. Copy it, change it, ship it, credit nobody.
