# A real channel

This is the channel this contract was extracted from, described as it actually runs. Nothing
here is illustrative: every number is measured, and the dates are the dates.

## The setup

One person, on a Windows machine. Four agents on a vendor's cloud, on a machine that is not
hers, which she cannot ssh into and whose session she does not control. A fifth agent on a
Linux VPS.

The machine and the cloud agents have nothing in common except a **private Git repository**.

## What goes through it

The machine collects public market data twice a day, writes one file per pass, commits, pushes
and fires a webhook. The cloud agents wake up, read the contract in the README, read the new
file, and write their own deliveries — one file each, in their own folder. The machine reads
the commits, checks what it can check, and writes back a single daily file saying what was
accepted, what was rejected, and why.

That daily file is the only shared memory. Without it, each agent reinvents its own — which is
exactly what they said, unprompted, in the first meeting: *"all three gaps fall in the same
pipe; without it each of us reinvents memory."*

## What it looks like on disk

```
channel/
  README.md                      the contract — re-read before every run
  AGENT_A.md AGENT_B.md ...      one contract per agent: what it does, what it never touches
  requests/    REQUEST_<date>_<id>.md
  raw/         DATA_<date>_<time>.jsonl     one file per pass, never updated
  signals/     SIGNAL_<date>_<topic>.md     agent A writes here, and only here
  content/     CONTENT_<date>.md            agent B
  review/      REVIEW_<date>.md             agent C
  feedback/    FEEDBACK_<date>.md           the requester writes here — the shared memory
  meetings/    MEETING_<date>_<time>.md     minutes, when the contract itself changes
```

## What it cost, and what it took

* **Setup:** one afternoon, on 17 September 2026. First closed loop — request written and
  pushed, webhook fired, delivery back in the repository — in **4 minutes 45 seconds**.
* **Running cost:** zero infrastructure. No queue, no daemon, no service to keep up. A
  repository and a token.
* **Six days later** the same channel was carrying four agents, nine scheduled routines, a
  twice-daily data series, and seven contract revisions — all in the history, all readable by
  someone who was not there.

## What went wrong, and what it taught

* **The chat lied by omission.** A delivery sat correct and committed while the chat window
  stayed quiet for seventy minutes. *Watch the remote, not the conversation.*
* **A stale clone reported a silence that never happened.** Pull before claiming absence.
* **A rule written in prose contradicted a flag read from the environment**, under a variable
  name that had been renamed. The executor obeyed the prose, delivered "BLOCKED", exited 0, and
  the log recorded it as "nothing found". *Contradictions are reported, not resolved silently.*
* **Three routines looked dead and were not.** They had run and correctly produced nothing.
  That is why a routine that writes nothing still leaves one line.

## The part that surprised us

Agents that re-read a written contract **start correcting it**. Asked what they would stop
doing, two of the four proposed cutting their own routines, with a reason. Asked where a
missing line should live, all four answered the same thing without conferring.

None of that happens over a chat window, because over a chat window there is nothing to
re-read.
