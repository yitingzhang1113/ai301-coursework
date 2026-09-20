# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

[The individual Path Review issue page. A link to the repository or the issue list
does not satisfy this field.]

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/56

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

````
I have all the evidence needed. Here's the read-out.

## Repo-level facts (shared, capture date = today 2026-09-19)
- **archived:** no · **last push:** 2026-09-16 (3 days ago) · **stars:** 1 · **latest release:** none
- **Last 5 default-branch commits:** all by human `Aburke225` (Andrew Burke); three on 2026-09-16, two on 2026-08-24 — all within 90 days
- **Contribution policy:** no CONTRIBUTING.md / AI_POLICY.md / AGENTS.md; PR template and README are silent on AI → silence passes
- All three issues: **no assignees, no linked PRs, no comments** (staff-seeded bug repo)

## Grading (all five required checks pass for every candidate)

| Check | #56 | #60 | #59 |
|---|---|---|---|
| maintainer-alive | pass | pass | pass |
| repo-in-use | pass | pass | pass |
| scope-fits | pass (bounded bug + repro + named failing test) | pass | pass |
| unclaimed | pass | pass | pass |
| policy-allows-ai | pass | pass | pass |
| labelled-friendly (pref) | pass (`good first issue` + `tier-1`) | pass (`tier-1`) | pass (`tier-1`) |
| shipped-recently (pref) | fail (no release) | fail | fail |
| responds-to-issues (pref) | unclear (seeded issues mostly uncommented) | unclear | unclear |

## Ranked accepted candidates (fit order)

All three **accept**. Ranked by your fit profile (Python; LLM-as-judge / faithfulness & grounding evaluation; prefer RAG/evaluation/ingestion; avoid frontend/CI/GPU):

1. **#59 — Faithfulness checker scores claims unsupported when context uses different words.** Bullseye for you: it's in `rag/evaluator/faithfulness_checker.py`, and the defect ("support should not depend on shared wording") is exactly the grounding/faithfulness problem your LLM-as-judge evaluation pipeline experience speaks to. Bounded by a named failing test, pure Python, no frontend/GPU.
2. **#60 — Faithfulness checker crashes on `text: None`.** Same evaluation module and a clean pytest repro, but it's a trivial `None`-guard — strong fit, less to learn than #59.
3. **#56 — Structural chunker drops heading-less documents.** In the ingestion/chunking module (still a preferred area) and the friendliest-labelled (`good first issue`), but further from your faithfulness/evaluation specialty than the two `rag/evaluator` bugs.

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/59",
    "checks": [
      {"name": "maintainer-alive", "grade": "pass", "evidence": "3 of last 5 default-branch commits dated 2026-09-16 by human Aburke225, within 90 days of 2026-09-19"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "archived: no; last push 2026-09-16, within 90 days"},
      {"name": "scope-fits", "grade": "pass", "evidence": "one bounded bug in _is_supported() with a named failing test test_multiple_context_chunks; no umbrella/debate/core-internals/support-question/abandoned-PRs"},
      {"name": "unclaimed", "grade": "pass", "evidence": "assignees none; no linked or mentioned PR; zero comments"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "no CONTRIBUTING/AI policy; PR template silent on AI — silence passes"},
      {"name": "labelled-friendly", "grade": "pass", "evidence": "labels include tier-1 (Starter difficulty)"},
      {"name": "shipped-recently", "grade": "fail", "evidence": "latestRelease is null; no releases"},
      {"name": "responds-to-issues", "grade": "unclear", "evidence": "seeded issues are mostly uncommented; cannot confirm 3/5 maintainer replies within 30 days"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/60",
    "checks": [
      {"name": "maintainer-alive", "grade": "pass", "evidence": "3 of last 5 default-branch commits dated 2026-09-16 by human Aburke225, within 90 days of 2026-09-19"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "archived: no; last push 2026-09-16, within 90 days"},
      {"name": "scope-fits", "grade": "pass", "evidence": "one bounded TypeError on text:None with a named failing test test_none_context_chunk_text; none of conditions (a)-(e) hold"},
      {"name": "unclaimed", "grade": "pass", "evidence": "assignees none; no linked or mentioned PR; zero comments"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "no CONTRIBUTING/AI policy; PR template silent on AI — silence passes"},
      {"name": "labelled-friendly", "grade": "pass", "evidence": "labels include tier-1 (Starter difficulty)"},
      {"name": "shipped-recently", "grade": "fail", "evidence": "latestRelease is null; no releases"},
      {"name": "responds-to-issues", "grade": "unclear", "evidence": "seeded issues are mostly uncommented; cannot confirm 3/5 maintainer replies within 30 days"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/56",
    "checks": [
      {"name": "maintainer-alive", "grade": "pass", "evidence": "3 of last 5 default-branch commits dated 2026-09-16 by human Aburke225, within 90 days of 2026-09-19"},
      {"name": "repo-in-use", "grade": "pass", "evidence": "archived: no; last push 2026-09-16, within 90 days"},
      {"name": "scope-fits", "grade": "pass", "evidence": "one bounded bug in StructuralChunker.chunk() with repro and named failing test test_document_with_no_headings"},
      {"name": "unclaimed", "grade": "pass", "evidence": "assignees none; no linked or mentioned PR; zero comments"},
      {"name": "policy-allows-ai", "grade": "pass", "evidence": "no CONTRIBUTING/AI policy; PR template silent on AI — silence passes"},
      {"name": "labelled-friendly", "grade": "pass", "evidence": "labels include good first issue and tier-1"},
      {"name": "shipped-recently", "grade": "fail", "evidence": "latestRelease is null; no releases"},
      {"name": "responds-to-issues", "grade": "unclear", "evidence": "seeded issues are mostly uncommented; cannot confirm 3/5 maintainer replies within 30 days"}
    ],
    "verdict": "accept"
  }
]
```
````

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

1. Smoke run with `--limit 3` (partial, first draft of the rubric):
   `agreement: 2/3 scored items`. The miss was
   `issue-01  accept  reject   NO     failed: scope-fits, responds-to-issues (preferred), labelled-friendly (preferred)`.
2. After I tightened condition (a) of `scope-fits`, I re-graded only that issue with
   `--only issue-01` (partial): `agreement: 1/1 scored items`.
3. Full 20-issue run with `--save-run eval-run.txt`, same rubric as run 2:
   `agreement: 19/20 scored items  (bar: 18/20: PASS)`
   with `categories: claimed 4/4  clear-accept 8/8  dead-repo 3/3  policy 1/1  scope 3/4`.

Run 3 is the run in `eval-run.txt`. I did not change `rubric.md` after it.

**Issue analysis**

[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]

Issue: `issue-20` (excalidraw/excalidraw#11811, category `scope`). The row in my final run:

```
issue-20  reject  accept   NO     graded accept
```

My rubric decided **accept**; the gold label is **reject**. The gold note calls it a
"one-line feature wish with no spec and a product decision hiding inside".

My rubric accepted it because `scope-fits` only fails on five named conditions (umbrella,
unsettled design debate in the thread, a maintainer saying it touches core internals, a
pure usage question, or 2+ closed unmerged PRs). This issue is a feature request, "Add
company logo shape to the toolbar", opened by `cursor[bot]` with no labels and
"Comments (0 total, first 0 shown)". With zero comments there is no debate for condition
(b) to see, and no maintainer comment for (c). The body looks organised ("Success looks
like: ..."), and my check says a short or thin body "is not by itself a fail" and my
verdict rule says "scope-fits: `unclear` counts as pass", so it passed. What my rubric did
not see is that nobody with merge rights ever agreed to the feature: whether a general
whiteboard tool should ship a company logo shape is a product decision, and the body itself
says "Logo asset TBD". The repo-level checks passed because excalidraw is clearly active
("last push to any branch: 2026-08-04", "assignees: none; linked PRs: none"), so nothing
else could catch it.

**Check rationale**

[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]

The check, as it is written now in `tools/issue-select/rubric.md`:

> | scope-fits | The issue body and the Comments section (with each comment's author_association); "linked PRs:" under Repo facts for closed, unmerged PRs. | The issue asks for one bounded change, meaning none of these is true: (a) it is an umbrella or tracking issue: the issue calls itself a tracking/meta/epic issue, or its sub-items are separate issues or PRs (task-list links to other issue numbers) or are explicitly meant to be picked up separately by different people. A single deliverable described as several steps, or as edits to several named files or pages, is NOT an umbrella and does not fail; (b) the thread shows the design still being debated and no OWNER/MEMBER/COLLABORATOR comment has settled it; (c) an OWNER/MEMBER/COLLABORATOR comment says the fix touches core internals; (d) it is a pure usage or support question with no change requested; (e) 2 or more closed, unmerged PRs are linked or mentioned for this issue. A short body, a missing reproduction, a bare acceptance checklist, or a long and detailed proposal is not by itself a fail; a body that names the files to change and what each should say counts as the spec being included. | required |

Why it looks like this: in my first smoke run condition (a) said "it is an umbrella or
tracking issue whose body lists sub-items meant to be split into separate work". That
wording rejected `issue-01` (conda docs task, gold `accept`, category `clear-accept`),
because its body has several headings under "Proposed changes" ("Add a new task page",
"Update `manage-pkgs.rst`", "Update `new-features.md`") and the grader read them as
sub-items. They are steps of one deliverable, not separate issues. So I rewrote (a) to fail
only when the issue calls itself a tracking/meta/epic issue, or its sub-items are other
issues/PRs, or they are meant to be picked up by different people, and I added the sentence
"A single deliverable described as several steps, or as edits to several named files or
pages, is NOT an umbrella and does not fail". I kept (b)-(e) as named conditions because the
lecture's family 3 is "One bounded change, spec included", and named conditions are
something another grader can apply the same way I do.

**Trade-offs**

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

What `scope-fits` gives up: it only rejects on positive evidence of bad scope, and it treats
a thin issue body as fine. That is what fixed `issue-01`: I re-ran it as a canary with
`--only issue-01` and it went from `reject` to `accept` (`agreement: 1/1 scored items`). The
cost shows up in the full run as `issue-20  reject  accept   NO     graded accept`: a feature request that no maintainer has agreed to gets through, because my check needs a visible debate or a maintainer comment before it fails. I accept
that miss for now. Making "spec included" a hard requirement would risk rejecting short but
well-bounded bug reports (the three Path Review issues I graded in live mode are all like
that), and the other 3
scope issues and all 8 clear-accept issues agree with gold under the current wording
(`categories: claimed 4/4  clear-accept 8/8  dead-repo 3/3  policy 1/1  scope 3/4`).

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.]

1. **Fit and time.** I have written the chunking step of a RAG pipeline myself, so I know
   why a chunker that silently returns no chunks is a real problem: the document just
   disappears from the index and nothing tells you. The issue also gives a one-line
   reproduction and names the failing test (`test_document_with_no_headings`), so I know
   what "done" means. I only have about 3-5 hours a week for this course, and this is small
   enough to fit that.
2. **What the verdict got right, and what I weighed that the rubric could not.** The
   verdict correctly saw that the repo is active, that nobody has claimed the issue, and
   that it is one bounded bug with a repro and a named test. But the skill ranked #59 first
   and #56 third, because #59 matches my faithfulness-evaluation background best. I still
   chose #56. #59 says "Support should not depend on shared wording" but does not say how
   to fix it, so I would have to design the semantic matching myself, and that probably
   means adding an embedding model as a heavy dependency, which my laptop handles badly and
   the maintainer may not want. #56 is also the only one of the three with the
   `good first issue` label. My rubric only checks whether an issue is acceptable; it
   cannot see how open-ended the fix is.
3. **Anticipated difficulty in claiming it.** The whole class shares this repo, so other
   students may claim #56 too. The house rule says that does not block me, but there may be
   duplicate PRs. I also have to choose the fallback behaviour (treat a heading-less
   document as one chunk, or fall back to another chunking strategy), and the maintainer
   may prefer one. And I have never written a claim comment before, so I will wait for
   Unit 2's voice guide before posting anything.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
