# Rubric: is this reproduction package ready to post?

<!--
Checks cover the five proof families the lecture named: the environment
is recorded, the steps are followable, the behavior shown is the issue's
(not an adjacent one), the outcome is stated honestly (an evidenced
cannot-reproduce is a pass), and the words respect the repo's
conventions (including any AI-disclosure requirement). Each pass
condition judges the thing itself — the artifact read against the
issue — never the write-up's shape.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| environment-recorded | The repro report's environment record (OS, the version of the tool under test, and any runtime/driver/backend the issue's behavior depends on, plus code state), read against the issue's stated target version and the repo-facts bug-report template asks. | The report names the OS and the version of the tool under test, and every additional axis the issue's behavior turns on (for a platform- or driver-specific issue, that platform/driver/backend). The tested version either matches the version the issue targets, or the report explicitly calls out the difference. A silent version or platform deviation from the issue's target fails. | required |
| steps-rerunnable | The repro report's steps/commands section, read as a stranger starting from a clean setup. | The steps give the concrete commands or inputs and the starting state a stranger could follow from scratch to reach the trigger, using only artifacts the report shares. Fails if any step is a placeholder ("set up the project", "configure as usual"), if the reproduction depends on a private or unshared repo, config, or asset a stranger cannot obtain, or if the steps never exercise the issue's actual trigger. | required |
| faithful-reproduction | The repro report's artifacts (command output, exit codes, logs, screenshots) and the exact trigger/input used, read against the specific symptom the issue describes (its error text, exit code, or observable behavior). | If the report claims a positive reproduction, its artifact shows the issue's specific symptom — the same error/message, the same exit code or failure mode — produced by the issue's own trigger or input. Fails when the artifact shows a different or adjacent behavior (a graceful error where the issue reports a crash, a different exit code, a different input/syntax than the issue's), or when the trigger differs from the issue's without being called out. An honest, evidenced cannot-reproduce makes no positive claim and is NOT failed here. | required |
| honest-outcome | The report's stated conclusion ("reproduced", "confirmed", "cannot reproduce", a root-cause claim) set beside what its own artifacts actually show. | The stated conclusion matches what the shown artifacts demonstrate: a "confirmed"/"reproduced"/"verified" claim is backed by an artifact that shows it, and an evidenced cannot-reproduce that says so plainly and shows the failed attempt passes. Fails when the report claims more than its evidence shows — a confident confirmation, a "guaranteed reproducible", or a root-cause diagnosis with no artifact that demonstrates it, or a conclusion the artifact contradicts. | required |
| claim-comment-intent | The candidate claim comment, read against the issue. | The claim states a specific, honest intent grounded in this issue: what the author has already done or will concretely do next. Fails if it is interchangeable boilerplate ("please assign me", "I love this project", a bare "+1"/me-too with no intent) or makes a promise it cannot keep (a guaranteed fix by a fixed deadline). | required |
| ai-disclosure | The repo-facts contribution/AI-policy line (CONTRIBUTING.md, AI_POLICY.md, PR/issue templates as quoted there), read against the claim and repro comments. Treat course packages as AI-assisted work. | Passes when the repo's stated policy does NOT require disclosing AI assistance in issue comments (no policy, or a policy whose disclosure ask is limited to pull requests, or one that asks only for the contributor's own voice rather than a disclosure). When the policy requires disclosing AI usage in comments, passes only if at least one of the comments discloses that assistance (names that a tool/AI was used). Fails when disclosure in comments is required and neither comment discloses. | required |
| control-contrast | The repro report for a control or contrast run (the same command with the trigger removed, or the non-failing case) shown alongside the failing run. | A control/contrast run is present that isolates the trigger — the expected-vs-actual is shown as two runs, not just asserted. Never changes the verdict; it marks the strongest reproductions. | preferred |

## Verdict rule

Accept only if every required check — environment-recorded,
steps-rerunnable, faithful-reproduction, honest-outcome,
claim-comment-intent, and ai-disclosure — grades pass; otherwise reject.

`unclear` counts as fail on every required check: a reproduction whose
proof cannot be verified is not ready to post. The one exception is the
claim-only live draft below.

`ai-disclosure` grades pass (not unclear) whenever the repo states no
disclosure requirement for comments; absence of a requirement is a pass,
not missing evidence.

The preferred check (control-contrast) never changes the verdict; it
only marks how strong an accepted reproduction is.

**Claim-only live draft (live mode only).** When only a claim comment is
being graded (no repro report yet), the checks whose evidence is the
repro report — environment-recorded, steps-rerunnable,
faithful-reproduction, honest-outcome, and control-contrast — are
reported `unclear` with evidence `not yet applicable: claim-only draft`
and left out of the verdict. The verdict then combines only
claim-comment-intent and ai-disclosure, answering: is this claim comment
ready to post?

All "matches the version/target" judgments are read against the issue's
stated target in the bundle (eval mode) or the live issue (live mode).
