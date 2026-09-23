# Where this came from

Not a design. A residue.

Between 17 and 23 September 2026, one person needed agents running on three different machines
— a Windows desktop, a vendor's cloud, a Linux VPS — to work on the same thing without any of
them being able to see the others. There was no plan for a "channel". There was a request that
had to reach an agent in a browser tab that nobody could script.

The first version was a chat window. It failed on the first day, and not by going down: it
answered **seventy minutes late**, after the work was already correct and committed. That is
the whole origin of this document. Everything else is consequence.

## What the practice added, in order

* **17 Sep** — a private repository as the transport; the contract written in its README
  instead of repeated in every message. First closed loop in 4 min 45 s.
* **18 Sep** — the second channel, to a VPS, with the direction reversed: there the agent is
  the author and the desktop reads. Same three rules, opposite flow. The rules held.
* **19 Sep** — the agents were asked what was missing. All of them, separately, asked for the
  same thing: a written record of what had been accepted and rejected. It became the daily
  feedback file — the only shared memory in the system.
* **20 Sep** — "one file per delivery" survived its first contradiction: an append-only trace
  file was proposed to prove that silent routines had run. Two writers, one file. The fix was
  one file per agent per day, not a lock.
* **22 Sep** — a gate written in prose contradicted a flag read from the environment. Exit 0,
  no error, wrong result. The rule about reporting contradictions instead of resolving them
  was written that night.
* **23 Sep** — the agents themselves proposed cutting their own routines, with reasons. That
  is when it became clear this was not a transport trick but a contract, and worth extracting.

## What is deliberately not here

* **No tooling.** No CLI, no action, no template repository to generate. Every attempt to turn
  this into a tool made it worse: the value is that the contract is a file the agent reads, and
  a file needs no installer.
* **No opinion about which agent, model or vendor.** All three of the machines above ran
  different ones, and the channel did not notice.
* **No promise that it scales.** It was measured with five agents and two channels over six
  days. Beyond that, it is untested — **NOT VERIFIED**, which is the phrase this whole family
  of contracts exists to make normal.

## License

CC0 1.0 Universal. Copy it, change it, ship it, credit nobody.
