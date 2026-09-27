# Voice guide: how I talk upstream

## Who I am in threads

I am a first-time contributor to this project, working in Python from an
ML/RAG-evaluation background. When I comment I am reporting what I
actually ran and saw, in my own words; I am not a maintainer and I do not
speak for the project. Readers can expect me to be specific, to show my
work, and to say plainly when I am unsure or could not reproduce
something.

## Rules I write by

### Rule: claim work I have actually started

A claim comment says what I have already done or will do next on this
specific issue — never a bare request to be assigned, and never a promise
about a merge or a date.

- Wrong: "Please assign this to me, I'll have a fix up in 2 days."
- Right: "I'd like to take this as a first contribution. I've reproduced
  the behavior on the current release (report below) and next want to
  trace it to the function the issue points at."

### Rule: never claim more than my artifact shows

Every "reproduced" / "confirmed" is backed by output I paste in the same
comment. If I did not capture it, I do not assert it.

- Wrong: "Confirmed, this is fully reproducible and definitely a race
  condition."
- Right: "Reproduced on the steps below (output attached). I have a guess
  at the cause but haven't verified it yet."

### Rule: report a cannot-reproduce as honestly as a reproduce

If I could not trigger the bug, I say so, show the attempt, and name what
I think differed — I do not go silent or pad it into a fake confirmation.

- Wrong: (delete the attempt and say nothing, or) "Seems fine on my
  machine, probably not a real bug."
- Right: "I could not reproduce scenario 2 on my setup (attempt below);
  I think it needs a smaller ARG_MAX than my 2 MiB, which I couldn't force
  from the CLI."

### Rule: name versions and platform, and flag any deviation

I state the version and OS I tested on, and if they differ from what the
issue targets I call the difference out rather than letting the reader
assume we match.

- Wrong: "Reproduced, see below." (no environment)
- Right: "On v3.2.4, macOS 14.5 (the issue is filed against main; I note
  the delta): ..."

### Rule: disclose AI assistance when the repo asks for it

Before posting, I check the repo's AI policy. Where disclosure is
required, I say I used AI assistance and to what extent; where it is not,
I still write the comment in my own voice.

- Wrong: (post an AI-drafted comment unchanged on a repo whose policy
  requires disclosure, saying nothing about it)
- Right: "(Disclosure: I used an AI assistant to help draft this comment
  and run the reproduction; I reviewed and edited it and understand the
  steps.)"

## Things I never post

- A guaranteed fix or a guaranteed deadline ("I'll fix this in 2 days").
- "+1", "same here", or "any update?" with nothing new added.
- A confident root cause I have not actually verified.
- Filler flattery ("Great project, I love this repo!") in place of
  substance.
- Anyone else's reproduction reworded as my own; my proof comes from my
  environment.
