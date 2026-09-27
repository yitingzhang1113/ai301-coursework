# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

[Your GitHub username, exactly as it appears on your profile — no `@`, no profile URL. Your
comments upstream are identified by this name.]

yitingzhang1113

---

## Posted upstream

**Claim comment**

[Link to the comment where you claimed the issue. Use the comment's own permalink, not the
issue page on its own. **Then paste the text of that comment underneath the link** — the
pasted text is what this field is graded on, so copy across what you actually posted.]

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/56#issuecomment-5859783019

Hi! I'd like to take this on as a first contribution to PathReview.

I reproduced the behavior on the current `main` (commit `f89c06f`): the exact snippet in the issue returns `0` chunks for a heading-less document, and the same text with a single leading `#` heading returns `1`, so the trigger really is the absence of any markdown heading. The `test_document_with_no_headings` xfail test fails as marked. Full reproduction is in a follow-up comment below.

Next I want to trace it in `StructuralChunker._extract_sections()`: my read of the code suggests content lines are only collected once `heading_stack` is non-empty, which would leave a heading-less document with no sections so `chunk()` returns `[]` — but I still need to confirm that against the code before claiming it. I'll work toward the behavior the test asks for — a heading-less document chunked as a single block — and check how the fix interacts with the `SECTION_TOKEN_LIMIT` sub-chunking path before opening a PR.

**Reproduction comment**

[Link to the comment where you posted your reproduction. It must record the environment
(OS, relevant versions, code state), steps a stranger could follow, and what you observed.
**Then paste the text of that comment underneath the link** — the pasted text is what this
field is graded on, so copy across what you actually posted.]

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/56#issuecomment-5859784226

**Reproduced on current `main`.** Details below so anyone can re-run it.

**Environment**
- OS: macOS 26.6.2 (Darwin 25.6.0, arm64)
- Python: 3.13.12 (fresh venv)
- Repo: `codepath/pathreview-ai301-fa26-s1` at commit `f89c06f` (2026-09-16), unmodified
- Deps: `tiktoken` 0.14.0, `numpy` 2.5.3, `pytest` 9.1.1

**Steps (from a clean checkout)**
```bash
python3 -m venv .venv && . .venv/bin/activate
pip install tiktoken numpy pytest pytest-asyncio
```

1. Run the issue's exact snippet:
```bash
python -c "from ingestion.chunking.structural_chunker import StructuralChunker
c = StructuralChunker()
print(len(c.chunk('This is a plain document with no headings at all. ' * 20, {})))"
```
Output:
```
0
```

2. Control — the same ~1000-char text with a single leading `#` heading:
```bash
python -c "from ingestion.chunking.structural_chunker import StructuralChunker
c = StructuralChunker()
print(len(c.chunk('# Title\n' + ('This is a plain document with no headings at all. ' * 20), {})))"
```
Output:
```
1
```

3. The related unit test (marked `xfail(strict=True)`):
```bash
python -m pytest tests/unit/test_structural_chunker.py::TestStructuralChunker::test_document_with_no_headings -rX
```
Output:
```
tests/unit/test_structural_chunker.py x                                  [100%]
============================== 1 xfailed in 0.08s ==============================
```

**Expected:** a heading-less document is chunked into at least one chunk (the test asserts `len(result) >= 1`), so it still reaches the index.

**Actual:** `chunk()` returns `[]` (0 chunks) for the heading-less document, while the identical text with one heading returns 1 chunk — so the whole document is silently dropped exactly as reported. The control run isolates the trigger to the absence of any markdown heading.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

1. Smoke run with `--limit 3` (partial, to confirm the setup and the rubric on one
   clear-accept and one wrong-target): `agreement: 3/3 scored items`.
2. Full 20-package run with `--save-run eval-run.txt`, same rubric as run 1:
   `agreement: 20/20 scored items  (bar: 18/20: PASS)`
   with `categories: clear-accept 8/8  disclosure 1/1  no-evidence 4/4  unfollowable-comms 3/3  wrong-target 4/4`.

Run 2 is the run in `eval-run.txt`. No disagreements appeared, so no revise-and-re-run
loop was needed; I did not change `rubric.md` between runs.

**Package analysis**

[Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.]

Package: `pkg-09` (sharkdp/fd#2033, category `clear-accept`). My rubric decided **accept**;
the gold label is **accept** (agree).

This package is an honest cannot-reproduce: the report opens "I could NOT reproduce
scenario 2". My rubric read it as accept because two checks are written to protect exactly
this case. `faithful-reproduction` says "An honest, evidenced cannot-reproduce makes no
positive claim and is NOT failed here", so the report is not failed for showing no positive
symptom. `honest-outcome` passed because the stated conclusion matches what the artifact
shows — the log "ONE / ONE / ONE / TWO / TWO / TWO" across five runs — and the report names
what likely differed ("uniform name lengths", "2 MiB ARG_MAX", "did not find a knob to
force a smaller limit"). `ai-disclosure` passed because fd's policy, quoted in the
repo-facts block, "states no disclosure ask for issue comments". A rubric that failed any
report without a positive reproduction would have wrongly rejected this honest negative;
that carve-out is what makes pkg-09 agree with gold.

**Check rationale**

[Quote one check from the `rubric.md` you uploaded to `tools/repro-check`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.]

The `ai-disclosure` check, as it reads now in `tools/repro-check/rubric.md`:

> | ai-disclosure | The repo-facts contribution/AI-policy line (CONTRIBUTING.md, AI_POLICY.md, PR/issue templates as quoted there), read against the claim and repro comments. Treat course packages as AI-assisted work. | Passes when the repo's stated policy does NOT require disclosing AI assistance in issue comments (no policy, or a policy whose disclosure ask is limited to pull requests, or one that asks only for the contributor's own voice rather than a disclosure). When the policy requires disclosing AI usage in comments, passes only if at least one of the comments discloses that assistance (names that a tool/AI was used). Fails when disclosure in comments is required and neither comment discloses. | required |

Why it reads that way: the eval set has a one-package `disclosure` category (`pkg-20`,
ghostty) that exists as the category floor, so a rubric with no disclosure check scores
`0/1` there and fails the floor even at high agreement. I made the check conditional on the
repo's stated policy rather than an absolute "always disclose", because most repos in the
set have no such requirement and an absolute rule would false-reject every clear-accept
(fd `pkg-09`, conda `pkg-05`, ripgrep `pkg-03`). I rejected the "always disclose" wording
for that reason. The "Treat course packages as AI-assisted work" line is what turns silence
on ghostty — whose policy requires disclosing "all AI usage in any form" — into a fail.

**Trade-offs**

[Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

What `ai-disclosure` gives up: it keys entirely off the repo's policy as quoted in the
repo-facts block. A case I accept it will miss: if a repo genuinely required comment
disclosure but its repo-facts block failed to quote that policy, my check would pass a
non-disclosing comment — a false accept. I accept that because in this set every
disclosure-required repo has its policy quoted (ghostty's AI_POLICY is in `pkg-20`'s
repo-facts), so the check fires where it must. And nothing changed elsewhere: the check
passed all eight clear-accepts (p5.js `pkg-07` discloses as its policy asks; conda `pkg-05`,
fd `pkg-09`, ripgrep `pkg-03` need no disclosure), giving
`categories: clear-accept 8/8  disclosure 1/1` — the floor is met with no collateral
rejects.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
