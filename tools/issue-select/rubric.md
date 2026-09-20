# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| maintainer-alive | Repo facts: the date and author of each entry in "last 5 default-branch commits". | At least 2 of the last 5 default-branch commits are dated within 90 days of the capture date and come from a human: the author name does not end in `[bot]`, or the commit is a bot merging a human's pull request. | required |
| repo-in-use | Repo facts: the `archived:` flag on the repo line and "last push to any branch". | `archived: no` AND the last push to any branch is within 90 days of the capture date. | required |
| scope-fits | The issue body and the Comments section (with each comment's author_association); "linked PRs:" under Repo facts for closed, unmerged PRs. | The issue asks for one bounded change, meaning none of these is true: (a) it is an umbrella or tracking issue: the issue calls itself a tracking/meta/epic issue, or its sub-items are separate issues or PRs (task-list links to other issue numbers) or are explicitly meant to be picked up separately by different people. A single deliverable described as several steps, or as edits to several named files or pages, is NOT an umbrella and does not fail; (b) the thread shows the design still being debated and no OWNER/MEMBER/COLLABORATOR comment has settled it; (c) an OWNER/MEMBER/COLLABORATOR comment says the fix touches core internals; (d) it is a pure usage or support question with no change requested; (e) 2 or more closed, unmerged PRs are linked or mentioned for this issue. A short body, a missing reproduction, a bare acceptance checklist, or a long and detailed proposal is not by itself a fail; a body that names the files to change and what each should say counts as the spec being included. | required |
| unclaimed | Repo facts: "this issue: assignees:" and "linked PRs:" with each PR's state; plus the Comments section, read for claim comments ("I'll take this", "can I work on this", "working on this") and for PRs mentioned but not formally linked. | Assignees is none AND no open PR is linked or mentioned in the thread for this issue AND no claim comment is dated within 30 days of the capture date. A claim older than 30 days with no PR and no follow-up is stale and does not fail. When the linked-PRs line and the thread disagree, the thread wins. | required |
| policy-allows-ai | Repo facts: the "contribution policy" line (CONTRIBUTING.md, AI_POLICY.md / AI_USAGE_POLICY.md, AGENTS.md, PR templates as quoted there). | The policy states no outright ban on AI-assisted contributions. Conditions (disclose AI use, understand and test every change, human review) pass. A ban on only fully AI-generated contributions while assistive use is allowed passes. No stated policy passes. | required |
| responds-to-issues | Repo facts: "maintainer first-response sample" (days to first owner/member/collaborator comment on 5 recently updated issues). | At least 3 of the 5 sampled issues got a first maintainer reply within 30 days. | preferred |
| shipped-recently | Repo facts: "latest release" and its date. | The latest release is dated within 365 days of the capture date. | preferred |
| labelled-friendly | The issue's `labels:` list on the "opened by" line. | Labels include `good first issue`, `help wanted`, or an equivalent beginner label. The label is a friendliness claim only; it never substitutes for maintainer-alive or unclaimed. | preferred |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

Accept only if every required check (maintainer-alive, repo-in-use,
scope-fits, unclaimed, policy-allows-ai) grades pass after the unclear
rule below is applied; otherwise reject.

How `unclear` is treated:

- maintainer-alive, repo-in-use, unclaimed, policy-allows-ai: `unclear`
  counts as fail. Their evidence fields are always present in the
  repo-facts block, so missing evidence there is itself a warning sign.
- scope-fits: `unclear` counts as pass. A terse body is not evidence of
  unbounded work; only one of the five named conditions (a)-(e) fails
  this check.

Preferred checks (responds-to-issues, shipped-recently,
labelled-friendly) never change the verdict. They rank accepted issues:
more preferred passes ranks higher.

All "within N days" thresholds are measured against the bundle's capture
date in eval mode and against today's date in live mode.
