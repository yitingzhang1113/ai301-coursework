# Scope: where to look, and who is looking

<!--
This file is the skill's field of view. The rubric (rubric.md) decides
whether an issue is GOOD; the scope decides which issues are candidates
at all, and whose hands the issue would land in. It applies in live mode
only: in eval mode the bundle is the whole world and this file is
ignored.

Two parts. Staff wrote the first; you write the second.
-->

## Where candidates come from

Only issues in the course's Path Review repository are candidates:

- Repo: `codepath/pathreview-ai301-fa26-s1`

Do not search, fetch, or grade issues from any other repository, however
promising. The wider GitHub comes later in the course; for now the field
is Path Review.

**Path Review house rule.** Path Review is a classroom, and your
classmates are not strangers. Ignore the usual claim signals here: other
students' claim comments (and there may be several on one issue) do not
block an issue, and finding some on the issue you want is normal. Claim
anyway: course credit attaches to the pull request you open, not to
whether it merges, so a shared issue costs nobody anything. Everything
else in the rubric applies as written.

## Your fit profile

<!-- YOU write this part: a few sentences about you. What languages and
tools you have actually used, what you want to get better at, anything
you want to avoid. The skill uses this only to RANK the issues your
rubric accepts, never to change a verdict: fit cannot rescue an issue
your rubric rejects, and cannot sink one it accepts. -->

I work mostly in Python. I have built a video RAG system end to end
(chunking, embedding retrieval, BM25/hybrid search, LLM generation) and an
LLM-as-judge evaluation pipeline for grounding and faithfulness, so I am
comfortable with pytest, regex, JSON parsing of model output, and reading
retrieval and evaluation code. I have used FastAPI and SQL lightly, and I
have little frontend (React/TypeScript) or DevOps/CI experience.

I want to get better at contributing to a codebase I did not write: reading
unfamiliar modules, reproducing a bug from a failing test, and making a
small, well-tested change. I am aiming for ML engineer / applied scientist
roles, so I prefer issues in the RAG, ingestion, evaluation, and safety
modules over docs-only or frontend work.

I want to avoid frontend issues, CI/infrastructure work, and anything that
needs heavy local compute or a GPU; my laptop is only good for running unit
tests and API calls.
