# Rules of the method

Each rule below was paid for. The case that paid it is under it, with the date.

---

* **One file per delivery — never update an existing one.**
  * A new file per delivery makes the log immutable, the diff readable, and collisions
    impossible when two agents write at the same minute.
  * *Paid on 20 September 2026:* an append-only trace file was proposed so that routines which
    run without producing anything could prove they ran. It contradicted this rule within a
    day — two agents appending to the same file. The fix was not a lock; it was one file per
    agent per day.

* **Minimum-scope credential, with an expiry you wrote down.**
  * One repository, one permission. A channel is a door, not a master key.
  * *Paid on 19 September 2026:* a write key created "so the executor could edit the site" was
    never wired to any clone — the delivery path that actually worked was a read-only pull. The
    key was revoked and the pair deleted. **An unused credential is not harmless; it is an
    unlocked door nobody is watching.**

* **The channel is not the source of truth.**
  * Nothing that arrives is a finding until it has been checked on your side. An unverified
    signal quoted in a report is misinformation that looks like work.
  * *Paid on 17 September 2026:* a page correctly marked "NOT SEEN — blocked by the network"
    carried the one number that reversed the reading of two markets. The gap was declared and
    then forgotten. Declaring a gap is not closing it — the gap needs an owner.

* **The commit on the remote is the detector. Not the chat.**
  * *Paid on 17 September 2026:* a delivery was correct and already committed while the chat
    stayed silent for about seventy minutes, then answered the whole queue at once. From the
    outside, success, delay and failure looked the same. **Never build a decision that depends
    on telling "stopped" from "slow".**
  * Corollary, paid on 22 September: before claiming that nothing arrived, **pull**. A clone
    two commits behind reported a silent afternoon that had not happened.

* **Ask for the WHAT and the WHY; let the executor decide the HOW.**
  * A request turned into a step-by-step script wastes the judgement you are paying for.
  * *Measured on 17 September 2026:* of three requests sent the same day, the one where the
    executor designed its own approach came back better than the two that were scripted.

* **A routine that runs and writes nothing still leaves a trace.**
  * One line: it ran, what it read, why there was nothing to write.
  * *Paid on 19 September 2026:* three routines were believed dead for a day. They had all
    run, on time, and correctly produced nothing — the rule said not to create a file without
    a new fact. **A live routine that looks dead costs more than a noisy one.**

* **Silence is not death — but only if a deadline was declared first.**
  * Do not conclude that an executor stopped unless you said, in advance, by when you expected
    it. Otherwise you are reading your own impatience.

* **A rule that contradicts another is followed by the file, and reported.**
  * *Paid on 22 September 2026:* a script read a permission flag from the environment, and the
    prose order it carried repeated the same gate under a **variable name that no longer
    existed**. The script allowed; the text blocked; the executor obeyed the text and delivered
    "BLOCKED". It exited 0 and the log recorded it as "nothing found". **The defect produced no
    error at all** — which is why the rule is to report the contradiction instead of silently
    picking a side.
