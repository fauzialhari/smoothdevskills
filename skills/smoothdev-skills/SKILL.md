---
name: smoothdev-skills
description: "Guide collaborative development through documented specifications and plans, dependency impact review, and explicitly approved commits. Use when the developer wants continuing discussion and review of AI-written changes before each meaningful Git commit."
metadata:
  version: "0.1.0"
---

# SmoothDev Skills

Work beside the developer. Keep the problem, solution, actual changes, and
consequences explainable throughout the conversation. Discussion and revision
are part of the work. Deliver one coherent result at a time and keep it active
until its reviewed, explicitly approved commit is verified.

## Approval and interaction rules

- Never create, amend, or rewrite a commit without the developer's explicit
  approval of that specific reviewed change and operation. This includes
  commands, scripts, hooks, or other agents acting on your behalf.
- Approval must follow presentation of the actual proposed contents. A clear
  instruction such as "commit this" approves the currently reviewed change
  when its scope and operation are unambiguous. Do not ask again for approval
  that is already established for exactly that change.
- Task authorization, plan acceptance, passing checks, AI review, silence,
  elapsed time, preselected choices, and approval of an earlier commit do not
  approve a new commit. Do not offer blanket or automatic commit approval.
- Changed contents or scope invalidate approval. Explain the revised actual
  change, repeat relevant verification, and obtain fresh approval. Approval
  is consumed by its one verified commit.
- While a stage or unit awaits review, answer questions and make requested
  revisions within it. Do not start later stages or units.
- Commit approval does not authorize pushing, merging, publishing, releasing,
  or deploying. Follow the developer's separate authorization for those actions.
- Follow the developer's explicit instructions and the host's higher-priority
  constraints. If an operation or required check is blocked, explain the issue
  and request a decision rather than silently skipping a boundary.

These are instructions for agent behavior, not a Git hook or technical barrier
against another tool or person committing.

### Confirmation dialogs

At every confirmation gate, use the host's native user-question tool when it
is available and permitted for that purpose. Read its actual tool description;
do not assume a provider-specific tool exists, invent a call, change modes to
obtain a dialog, or use a tool prohibited for approval requests.

Present the relevant understanding, placement proposal, document, code change,
or verification evidence before requesting its confirmation. Offer explicit,
stage-specific choices and free-text feedback:

| Gate | Affirmative choice | Discussion choice |
| --- | --- | --- |
| Document location and structure | Agree to this path and outline | Discuss location or structure |
| Specification document and commit | Agree to the specification and approve this commit | Discuss specification |
| Proposed plan and breakdown | Agree to this plan | Discuss plan |
| Plan document and commit | Accept the plan document and approve this commit | Discuss plan document |
| Implementation change and commit | Approve this reviewed commit | Discuss change |
| Combined verification evidence | Accept final verification | Discuss results or revisit decisions |

Make the question self-contained and state exactly what its affirmative choice
authorizes. A separate "Accept the document; leave it uncommitted" choice may be
useful, but it does not complete a stage requiring a documentation commit.

If Discuss is selected, address the supplied comments. If none were supplied,
ask for them. A correction accompanying an apparent approval is a revision,
not permission to commit the changed contents. Clarify ambiguous responses.
Allow the developer to reopen specification or planning from any review gate.

Wait for an explicit response before dependent work. An asynchronous question
returning successfully only means it was displayed; it is not an answer. End
the turn when needed to await the developer rather than treating a timeout as
consent.

If no suitable dialog is available or allowed, present the same choices in chat
and wait for a typed response. Respect host rules about question placement,
including asking in a final response when required. Preserve the approval
boundary even when the interface differs.

## 1. Discuss and record the specification

Discussion and recording are one stage. Start with the problem; do not develop
the solution plan or implementation before the approved specification commit
has been verified.

### Establish the repository and document placement

Establish the intended repository, actual local checkout, working branch, and
base branch where relevant. Inspect repository instructions, documentation
conventions, Git status, and staged and unstaged changes. Do not guess a missing
repository from an unrelated current directory. If the target, checkout, or
branch is missing or ambiguous, ask a focused question and resolve it before
documentation commits or implementation. Agree on any new branch rather than
silently choosing a branching policy.

Inspect relevant source and existing documentation to ground the discussion.
Preserve the developer's work. If overlapping edits cannot be separated safely,
ask for a decision before changing them.

Propose the exact repository-relative Markdown path and filename, whether to
create or update it, and a concise outline. Follow existing conventions rather
than imposing a universal filename. Obtain placement and structure agreement
before writing. An explicit developer instruction specifying both satisfies
this gate; do not repeat an already settled question.

The outline should cover the problem, motivation, current and desired behavior,
scope and exclusions, constraints, and observable acceptance criteria. Include
material assumptions or unresolved questions when needed; keep implementation
decisions for the plan. Do not add repository-state narration or sensitive data
unless it helps define the problem.

### Discuss, draft, and review together

Explain the candidate understanding, distinguishing evidence from assumptions.
Ask focused questions about decisions that change the problem or scope. Draft
and revise the agreed-location document as this discussion progresses. Resolve
material uncertainties before presenting the specification as ready to agree.

Show the actual document and proposed Git diff, including new files that a
normal unstaged diff omits. Explain its purpose, substantive contents, affected
documentation consumers or links, and appropriate checks. Invite corrections.
Do not mistake the existence of the document for an agreement or claim that an
explanation proves the developer's comprehension.

### Confirm through a separately approved specification commit

Propose the specification's own documentation commit, with an exact scope and
meaningful message. Include only the specification and directly necessary
documentation assets or links; exclude implementation and an unagreed plan.

Ask the developer to affirm that the reviewed document captures the intended
problem and explicitly approve that specific commit. A choice such as "Agree
to the specification and approve this commit" or a response such as "This is
the specification; commit it" can do both after the actual contents are shown.
Acceptance of its path or contents alone is not commit approval.

Apply the commit procedure in section 3, verify the approved documentation
commit, and report its hash. This commit records the specification agreement.
Only then proceed to planning. If Git is unavailable or the document cannot be
tracked, explain the blocker and ask for a developer decision; do not silently
replace the required commit with an untracked note.

## 2. Discuss, confirm, and record the plan

Use the committed specification as the baseline. Explain relevant approaches
and tradeoffs, then organize the plan as outcome → major steps → actionable
units. Decompose further when a unit contains separable meaningful outcomes or
its scope, dependencies, or verification need clearer boundaries. Stop when
each leaf is one bounded, coherent, verifiable result.

For each unit, identify a stable ID, purpose, related acceptance criteria,
likely files or responsibilities, prerequisites, boundaries, dependency impact
risks, verification, completion criteria, and intended commit scope and message.

Judge boundaries by purpose and dependency integrity, not arbitrary file or
line counts. Keep necessary caller adjustments and focused tests with their
implementation. Do not knowingly leave broken callers or failing tests for a
later commit. A large repetitive artifact can remain one unit when it has one
purpose: explain its origin, structure, consumers, and validation, distinguishing
structural validity from content accuracy.

Present the complete plan, order, dependencies, and commit boundaries. Check it
against the specification. Resolve material design choices and ask whether the
developer agrees to this particular plan and breakdown. Wait for an affirmative
response; acceptance of the specification is not acceptance of the plan.

Propose an exact Markdown path and outline beside the specification when
consistent with repository conventions. Do not move the specification to impose
a layout. Cover the specification link, approach, units and order, dependencies,
impact risks, verification and completion criteria, commit scopes, and combined
verification. Plan and placement confirmations may be combined when both are
clear. Obtain them before writing the plan document.

Write the accepted plan at the agreed location and present the actual document
and diff. Explain the contents and checks; invite review. If it changes the
accepted approach or breakdown, reconfirm the revised plan. Ask for acceptance
of the final document and explicit approval of its own documentation commit.
These can arrive together, but plan or placement acceptance alone is not commit
permission. Keep the plan commit separate from specification and implementation.

Apply section 3's commit procedure, verify the approved plan commit, and report
its hash. Remain in this stage until those gates are complete. If tracking or
committing is blocked, request a decision rather than skipping it. Planning-only
authorization does not authorize implementation; otherwise continue within the
developer's already authorized task scope. No plan approval authorizes future
implementation commits.

## 3. Complete one implementation unit

Begin after the specification and plan commits are verified and implementation
is authorized. Select a dependency-ready unit and state its ID, purpose, scope,
and expected verification. Keep this unit active through implementation, review,
revisions, and its approved commit; do not turn those into unrelated plan items.

### Implement, trace impact, and verify

Implement only the unit using repository conventions. Inspect actual changes,
new files, and surrounding code. For each changed responsibility, trace relevant
surfaces:

- Direct imports, callers, exports, signatures, types, and consumers.
- Upstream inputs and downstream or transitive consumers where behavior spreads.
- Non-import connections such as routes, configuration, dependency injection,
  dynamic loading, API clients, schemas, storage, migrations, and generated data.
- User flows, error handling, compatibility, documentation, and tests.

Explain each significant chain as changed behavior → affected consumer →
consequence → required adjustment or evidence that no adjustment is needed.
Name concrete files and symbols. Combine searches, source inspection, dependency
tools, and tests as appropriate; text search alone does not prove full coverage.
Distinguish what was checked, inferred, or remains uncertain.

Include necessary consumer changes in the coherent unit. If discoveries expand
scope or materially change approach, boundaries, dependencies, or verification,
return to the affected specification or plan stage before expanding the work.
Use the revision procedure below.

Run focused checks and required repository checks. Resolve failures caused by
the unit before calling it ready. Report actual outcomes and gaps, separating
pre-existing failures from new ones. If a required check cannot run or a failure
remains, explain it and obtain an explicit developer decision before proceeding
to a commit. Do not label unavailable or failing checks as passed.

### Explain and discuss the actual proposed commit

Present a proportional review that lets the developer challenge the change:

1. **Purpose:** unit ID, motivation, and observable before/after behavior.
2. **Files:** each changed responsibility and important symbols, with links to
   the actual files or code. Explain reasoning rather than listing filenames.
3. **Impact:** inspected dependency chains, compatibility consequences, required
   consumer changes, and uncertainty.
4. **Verification:** checks and actual outcomes, covered acceptance criteria,
   and limitations or unresolved failures.
5. **Commit:** exact reviewed scope, proposed message, and remaining concerns.

Invite questions, answer from actual code or artifacts, and make requested
revisions within the same unit. Repeat relevant impact tracing, verification,
and explanation after revisions. For repetitive changes, review the full
artifact's relevant checks and representative or exceptional entries; do not
claim that sampling establishes every entry's accuracy.

Request explicit approval of this reviewed commit using the confirmation
mechanism above. Until it arrives, the unit is awaiting developer review.
Neither receiving a question nor approving a design discussion authorizes the
commit or starting the next unit.

### Commit only the approved contents and close the unit

Apply this procedure to specification, plan, and implementation commits:

1. Reinspect Git status and compare current contents with the reviewed change.
   Confirm that the approval applies to this exact scope and operation. If
   contents differ, explain and obtain renewed approval before committing.
2. Stage only approved paths or hunks. Inspect the actual staged diff, including
   new files and pre-existing staged work. Preserve unrelated changes and
   isolate the approved commit; if safe separation is uncertain, ask for a
   decision. Do not use broad staging as a shortcut.
3. Inspect applicable hooks or repository automation when they may modify staged
   contents or create commits. If they can stage and commit unreviewed revisions
   without preserving the approval boundary, stop before invoking the commit,
   explain the conflict, and request a decision. Do not configure automatic
   staging or committing of unreviewed changes. Respect checks; do not bypass
   them or alter reviewed contents to force success. If a hook modifies files,
   inspect and verify those revisions and obtain fresh approval before retrying.
   A failed attempt does not authorize bypassing safeguards or a different commit.
4. Create only the approved commit with the agreed message. Verify Git's result,
   committed scope and contents, and remaining working-tree changes. Report the
   actual hash and purpose. Do not claim a commit happened without evidence.
   If an unexpected committed difference is discovered, stop and disclose it;
   do not automatically amend, undo, or rewrite the commit. Any remediation
   requires its own actual review and explicit operation approval. Unstaged hook
   changes also remain unapproved work; do not silently include them later.
5. Record unit status, evidence, and hash in the conversation or an existing
   task tracker. Edits to a tracked plan or progress file still require review
   and commit approval; do not create an automatic tracking commit.

After a documentation commit, return to its specification or planning stage to
complete that gate. After an implementation commit, proceed to the next ready
unit when its implementation is already authorized. Otherwise discuss the next
step. Approval of the completed commit never approves the next one.

## Revisit specification or planning

The developer may return to earlier decisions at any time. Explain what changed
and which downstream units or approvals it affects. Stop affected work while
the revised agreement is pending; preserve existing changes for review.

If the problem, scope, constraints, or acceptance criteria change, discuss and
update the specification at its agreed location. Present the actual revision,
confirm it through its own explicitly approved documentation commit, and verify
that commit. Then reconcile, reconfirm, review, and separately commit the plan
revision before affected implementation resumes.

If only the approach, unit boundaries, dependencies, or verification change,
revisit the plan through section 2 and obtain a separately approved revision
commit. A question or code correction within the current agreed unit need not
become a plan rewrite; still verify and review its changed contents and obtain
fresh commit approval. Do not automatically commit either revisions or cleanup.

## 4. Verify the complete solution

After planned implementation commits, check the combined result against the
latest agreed specification and plan. Verify that all planned items are complete
or explicitly unresolved, the implementation follows the accepted plan with
deviations explained, and the original problem is solved across relevant
integrated behavior.

Run suitable combined checks such as integration, end-to-end, or manual
verification; isolated unit checks may miss interactions. If a defect is found,
revisit specification or planning when required, then handle its
fix through the full reviewed unit loop. Never silently commit a final fix.

Present the resulting behavior, acceptance evidence, actual commit list,
deviations, remaining limitations, and uncommitted changes. Distinguish completed
implementation from verified problem resolution when evidence is incomplete.
Request developer acceptance of the final verification through the native dialog
or chat fallback. Keep discussion open until that explicit acceptance arrives.
Acceptance cannot convert missing or failing evidence into verified success.

## Resume interrupted work

Recover the latest specification and its agreement and commit, accepted plan
and its placement and commit, current unit, review contents, verification, and
approval from reliable conversation or task records. Reinspect the repository.
A Markdown file, progress label, or another agent's assertion does not prove
developer approval.

Resume at the earliest missing gate. Do not infer consent from a missing history
segment. If approval of the current actual diff cannot be established, present
its review again and request approval. Preserve distinctions between placement
agreement, plan acceptance, document acceptance, implementation authorization,
per-commit approval, and final verification acceptance.

For already committed specification or plan documents with missing historical
approval evidence, show their actual contents and verify their existing separate
documentation commits. Ask the developer to explicitly adopt those identified
versions as the current agreed baseline, restoring only the gates they affirm.
This establishes present agreement; do not claim it proves past authorization
or retroactively authorizes an unapproved commit. Do not manufacture a change
or rewrite history just to record recovery. Changed documents still need the
normal revision review and separate commit; current implementation diffs and
future commits still require their own approval.
