# Evidence guide: where proof lives in a reproduction package

<!--
The map for the rubric's checks: for each proof family, where to find it
in a package (eval bundle sections; live mode locations) and what good
looks like when you do.
-->

## Environment

**Where it lives.** In an eval bundle: the repro report's opening
"Environment:" line (OS, tool version, language/runtime versions,
install method, code state). The issue's stated target lives in the
issue body ("Version: ...", the reported OS/platform) and the repo-facts
"bug reports" line, which quotes what the repo's template asks a reporter
to include. In live mode: the issue body and its bug-report template on
GitHub for the target; the student's draft repro comment for what they
actually ran.

**What good looks like.** The record names the OS and the version of the
tool under test, plus any axis the issue's behavior turns on: for a
platform-specific issue (a Windows-only crash, a driver-specific bug),
the platform/driver/backend is named. The tested version matches the
version the issue targets, OR the report states the difference out loud
("issue is on main; I tested 3.2.4"). A record that silently tests an
older version than the issue was confirmed on, or omits the platform on a
platform-specific issue, is not sufficient — the reader cannot place the
attempt.

## Steps

**Where it lives.** In an eval bundle: the repro report's "Steps:"
section and its fenced command blocks. In live mode: the student's draft
repro comment. Cross-check against the issue's own reproduction steps
(issue body) to confirm the same trigger is exercised.

**What good looks like.** A stranger with a clean machine could copy the
commands and reach the trigger: concrete commands or inputs, the
starting state (files created, config used), and every artifact the steps
depend on is shared inline (a config file's contents, a minimal input).
Warning signs: a placeholder step ("set up the project as usual"), a
dependency on a private or unshared repo/config/asset, or steps that stop
short of the action that triggers the bug.

## Behavior shown

**Where it lives.** In an eval bundle: the repro report's fenced output
excerpts, exit codes (`echo $?`), logs, or described screenshots, plus
the "Expected"/"Actual" lines. Read them against the issue's described
symptom: the exact error text, the exit code, the observable failure in
the issue body and its own output block.

**What good looks like.** The artifact shows the SAME symptom the issue
names, produced by the issue's own trigger: the same error message, the
same exit code, the same failure mode. An artifact shows an ADJACENT
behavior — and does not count — when it is a graceful validation error
where the issue reports a crash (different exit code), when the input or
syntax differs from the issue's (a prefix range vs the issue's
offset-from-end range), or when it only shows the tool starting/running
rather than failing. For a cannot-reproduce, the artifact shows the real
attempt (the commands run and the non-failing output), which backs the
honest negative rather than a positive claim.

## Honesty

**Where it lives.** The seam between the report's conclusion words
("confirmed", "fully reproducible", "guaranteed", "I verified the race
condition", "could not reproduce") and the artifacts in the same report.
In an eval bundle both sit in the repro report; in live mode both sit in
the draft repro comment.

**What good looks like.** Every claim is only as strong as a shown
artifact supports. A modest, exact report ("with one custom header the
Content-Type is absent; control run shows it present") is honest; so is a
plainly stated cannot-reproduce that shows the failed attempt and names
what likely differed. Over-claiming looks like: a confident confirmation
with no artifact, a "guaranteed reproducible"/"ran it ten times" wrapped
around an artifact that shows a different behavior, or a root-cause
diagnosis asserted with nothing shown. The tell is a conclusion the
artifact does not demonstrate — or contradicts.

## Comms

**Where it lives.** The claim comment (eval bundle: "Candidate claim
comment"; live: the student's draft claim) read against the issue. The
repo's conventions live in the repo-facts "bug reports" template line and
the "contribution policy" line, which quotes any CONTRIBUTING.md /
AI_POLICY.md rules, including AI-use disclosure requirements. In live
mode, read the same from the repo on GitHub.

**What good looks like.** The claim is specific to this issue and honest
about intent — what the author has done or will do next — not
interchangeable boilerplate ("please assign me, I'll fix in 2 days
guaranteed") or a bare "+1". For AI disclosure: check the policy line.
If it requires disclosing AI usage in comments (e.g. "all AI usage must
be disclosed, stating the tool and extent"), a compliant package has at
least one comment that names the assistance; treat course packages as
AI-assisted, so silence on a disclosure-required repo is a violation. If
the policy asks only for the contributor's own voice, or limits its
disclosure ask to pull requests, or states nothing, no comment
disclosure is required and the check passes.
