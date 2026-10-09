# SmoothDev Skills — Specification

SmoothDev Skills is a reusable AI development workflow built around shared
understanding, explainable changes, developer review, and explicitly approved
commits. This file specifies the required workflow. Proposed revisions are
reviewed through Git diffs, and approved commits record the agreement and its
changes over time.

## Problem and current behavior

The developer uses AI as a development partner and wants to remain able to
explain and take responsibility for the problem, solution, changes, and
consequences of every commit. An AI proceeding without explicit agreement or
committing before the developer has reviewed the actual change breaks that
collaboration.

The workflow needs explicit confirmation boundaries throughout specification
discussion, documentation, planning, implementation review, and final
verification. Each boundary must let the developer either agree or continue
the discussion, including returning to earlier decisions.

## Motivation

Make AI-assisted development a continuing discussion in which the developer
can challenge the reasoning, inspect consequences, revise decisions, and approve
each meaningful commit. Record agreements so subsequent work has an explicit
baseline without mistaking a document for proof of developer approval.

## Desired workflow

![SmoothDev Skills workflow: specification, planning, implementation, and final verification with approval and discussion loops](docs/workflow.png)

1. **Discuss and record the specification.** Establish the target repository,
   local checkout, and intended working branch. Agree on the Markdown path and
   structure. Discuss the problem, desired outcome, scope, constraints, and
   observable acceptance criteria while drafting and revising the specification.
   Present the actual document and Git diff for developer review. Explicit
   approval of that reviewed specification commit confirms the agreement and
   authorizes its separate documentation commit. Wait for the verified commit
   before solution planning or implementation; discussion and recording are
   parts of this same stage.
2. **Discuss and record the plan.** Present major steps and break them down into
   meaningful, bounded, verifiable units, decomposing further when useful. Wait
   for affirmative plan acceptance and agreement on its Markdown location and
   structure, preferably beside the problem agreement. Review the written plan
   and obtain explicit approval for its own separate documentation commit before
   implementation.
3. **Complete one implementation unit at a time.** Implement, trace dependency
   impacts, and run appropriate checks. Explain the motivation, actual file and
   behavior changes, affected consumers, consequences, verification evidence,
   and proposed commit. Discuss questions and revisions until the developer
   explicitly approves that specific reviewed change for a Git commit. Keep the
   unit active while review is pending; do not advance to later units.
4. **Verify the complete solution.** Check all planned items, adherence to the
   agreed plan, and resolution of the original problem across the combined
   behavior. Present evidence, deviations, and limitations, then obtain explicit
   developer acceptance of final verification before declaring the workflow
   complete. Acceptance cannot substitute for missing verification evidence.

At confirmation and review gates, use the host's native selection dialog when
available and permitted, offering stage-specific approval and discussion choices
with free-text feedback. If discussion is selected without comments, ask for the
comments. Use an explicit typed response in chat when a suitable dialog is
unavailable. Silence, timeout, or a preselected option never establishes consent.

The developer may return to specification discussion or planning from any stage.
Reconfirm affected agreements, reconcile the plan, and review and separately
approve the required documentation revisions before affected implementation
continues. Changed proposed contents invalidate prior commit approval.

## Scope and exclusions

- The skill must be self-contained and branded SmoothDev Skills.
- The workflow must establish repository and documentation placement, record
  the specification and plan, and require explicit approval of each reviewed
  commit. Specification discussion and recording form one stage, with its
  approved commit recording the agreement.
- Support repeated discussion and revision throughout the workflow.
- This is an agent workflow; it does not install a Git hook or technically
  prevent other tools or people from committing.
- No push, pull request creation, merge, release, or deployment is authorized by
  this agreement or by approval of a local commit.

## Constraints

- Repository: <https://github.com/fauzialhari/smoothdevskills>.
- Stable branch: `master`; this task's branch: `feat/smoothdev-workflow`.
- This project's specification lives in `specs.md`. Review and explicitly
  approve a separate commit for each agreed revision so Git records its history.
- Preserve the agreement, plan, and implementation as separate meaningful
  commits. Any later merge strategy should preserve their individual history.
- Agree on the repository and working branch during specification discussion;
  if they are missing or ambiguous, resolve them before documentation commits or
  implementation. Preserve existing developer changes.
- Never create or rewrite a commit without explicit developer approval of that
  particular reviewed change and operation. Approval of a stage or previous
  commit does not authorize a subsequent commit.
- Keep each implementation unit coherent, explainable, and manageable for review.
  Keep necessary caller adjustments and focused tests with their implementation;
  avoid splitting a unit in a way that knowingly leaves the result broken.
- Trace relevant direct and transitive consumers, including non-import
  connections where applicable. Distinguish evidence, inference, and uncertainty.
- Respect the host's available tools and higher-priority instructions. The skill
  cannot guarantee identical dialog appearance across hosts.

## Observable acceptance criteria

- **AC1 — Self-contained identity:** The delivered skill is branded SmoothDev
  Skills and defines its workflow without requiring a private or local skill.
- **AC2 — Repository established:** Specification discussion establishes the
  target repository, local checkout, and working branch before documentation
  commits or implementation.
- **AC3 — Agreed specification:** The AI discusses and records the specification
  within one stage after agreeing on its path and structure. It presents the
  actual document and Git diff, obtains explicit approval confirming that
  specification and authorizing its separate commit, and verifies the commit
  before proceeding to solution planning or implementation.
- **AC4 — Confirmed plan:** The AI presents the breakdown and waits for plan and
  placement confirmations, reviews the actual plan document, and obtains its
  separate commit approval before implementation.
- **AC5 — Explained units:** Each unit includes implementation, relevant impact
  tracing, verification, explanation of actual changes, developer discussion,
  and specific commit approval before committing or advancing to another unit.
- **AC6 — Confirmation interaction:** Every confirmation gate offers native
  selectable approval/discussion choices and free-text feedback when supported,
  with a chat fallback and no inferred consent.
- **AC7 — Revisit decisions:** Specification or plan revisions return to the
  affected gates, invalidate affected approvals, and receive separately reviewed
  and approved documentation commits before affected work resumes.
- **AC8 — Final acceptance:** Combined verification checks plan completion and
  problem resolution, reports actual evidence and limitations, and waits for
  explicit developer acceptance of its results.
- **AC9 — Commit boundaries:** No blanket, automatic, or unreviewed commits occur;
  local commit approval never implies push or merge approval.
