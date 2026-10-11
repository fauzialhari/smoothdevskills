# SmoothDev Skills — Implementation Plan

## Specification baseline

This plan implements the agreed [specification](specs.md), recorded in commit
`e585a715688b38a7dabd730890b1b38c2e1406b4`, and the subsequently agreed packaging
and versioning decisions below. Acceptance criterion IDs refer to that
specification.

The working branch is `feat/smoothdev-workflow`, based on `master`.

## Approach and tradeoffs

- Keep one complete, self-contained workflow in
  `skills/smoothdev-skills/SKILL.md`. Its directory and standard `name` are
  `smoothdev-skills`; its document title is **SmoothDev Skills**.
- Use standard YAML frontmatter for `name`, `description`, and
  `metadata.version`. Start at `"0.1.0"`, with that metadata value as the single
  version source. Do not add `agents/openai.yaml` or invented configuration
  files for other providers.
- Describe confirmation by the host's available, permitted user-question
  capability, rather than requiring one provider's tool name. Retain explicit
  approval and discussion choices, free-text feedback, and chat fallback.
- Distinguish the shared instruction format from host-specific installation,
  invocation, and dialogs. Native skill discovery is an application capability;
  a model API alone does not provide it.
- Keep all workflow stages together in U1 so a partial implementation cannot
  omit necessary approval boundaries. Separate public onboarding and versioning
  policy into U2 and U3 because they have distinct reviewable purposes.
- Validate both structure and decisions. Format validation checks the skill
  file; scenario review checks how its instructions apply to development
  situations. Neither guarantees identical behavior across every host or model.
- Use the repository's source directory as the distributable skill. Do not add
  an archive, installer, hooks, automatic commits, or release automation.

## Major steps and execution order

1. **Deliver the complete skill:** U1 implements and verifies the workflow.
2. **Explain public use:** U2 documents installation, invocation, and interaction.
3. **Define versioned changes:** U3 documents versioning and release history.
4. **Verify the combined result:** check the specification, plan, and delivered
   files together, then obtain developer acceptance of final verification.

Execute **U1 → U2 → U3**. Each leaf below is one meaningful, bounded result and
one intended commit. Its subtasks stay within that unit; they do not justify
separate commits that deliver an incomplete workflow or broken documentation.

The plan itself requires review and its own explicitly approved documentation
commit before U1 begins: `docs: record SmoothDev Skills implementation plan`.
Plan acceptance is not approval of this commit or any implementation commit.

## U1 — Complete portable development skill

**Purpose:** give an AI the complete agreed collaboration workflow, independent
of provider-specific UI configuration. Covers **AC1–AC9**.

**Files:** `skills/smoothdev-skills/SKILL.md` only.

**Prerequisite:** the actual plan document is reviewed, accepted, and separately
committed with explicit developer approval. Implementation remains within the
original request to create the skill.

**Actions and boundaries:**

- Write standard discovery metadata, version `"0.1.0"`, the branded title, and
  instructions sufficient to use the workflow without private or local skills.
- Establish the repository, checkout, branch, existing changes, and relevant
  repository instructions during specification discussion.
- Keep specification discussion and recording in one stage. Agree on document
  placement before writing, review the actual document and diff, and use explicit
  approval of its separate commit to confirm the agreement. Verify that commit
  before planning or implementation.
- Define plan discussion, meaningful decomposition, plan and placement
  confirmation, document review, and a separate approved plan commit before
  implementation.
- Define the complete implementation-unit loop: implement, trace direct and
  relevant transitive impact, verify, explain actual changes and evidence,
  discuss revisions, obtain specific approval, isolate approved contents,
  commit, and verify the resulting commit.
- Define stage-specific native approval/discussion questions, comment handling,
  and chat fallback. Missing responses, preselected options, general task
  authorization, and previous approvals never authorize a commit.
- Define revisiting specification or planning, invalidation of affected
  approvals, interrupted-task recovery, final combined verification, and
  explicit acceptance of its evidence. Preserve developer changes and report
  blocked checks honestly.
- Keep push, merge, release, and deployment authorization separate from local
  commit approval. Do not install or modify local skills.

**Dependency impact and risks:** the main consumers are skill loaders and the
AI reading the instructions. Metadata affects discovery; instructions affect
when the AI may advance, write documents, and commit. Check for conflicting
gates, implied consent, accidental provider requirements, and dependencies on
files outside the distributable skill directory. U2 and U3 must reflect this
actual delivered contract rather than introduce different rules.

**Verification:**

- Run the skill-creator format validator and check the standard Agent Skills
  frontmatter, directory/name match, string metadata, and absence of unfinished
  placeholders or references to unavailable files.
- Map every specification acceptance criterion to the actual instructions.
- Use the authorized independent reviewing agent for realistic scenarios:
  missing repository details; specification or plan approval pending; document
  acceptance without commit permission; questions during implementation review;
  changed contents after approval; unrelated developer changes; unavailable
  dialogs; interrupted work with incomplete approval evidence; and failed final
  verification.
- Keep that evaluation read-only and isolated from live task actions. The
  reviewer must not commit, edit the working repository, contact other chats,
  or open real approval dialogs. Review its actual conclusions and resolve
  supported defects within U1 before presenting the unit for approval.
- Report scenario review as instruction-level evidence, not proof that Claude,
  Qwen, DeepSeek, or every other model has been tested in a live integration.

**Complete when:** the file is valid, all nine criteria are covered, material
review findings are resolved or explicitly disclosed, the developer reviews and
approves the actual change, and its commit is verified.

**Intended commit:** `feat: add SmoothDev Skills workflow`.

## U2 — Public onboarding README

**Purpose:** let repository visitors understand and use the delivered skill.
Supports **AC1** and **AC6**, and explains the approval boundaries in **AC9**.

**Files:** `README.md` only.

**Prerequisite:** U1 is reviewed and committed.

**Actions and boundaries:**

- Explain the skill's purpose and complete workflow, using the existing
  `docs/workflow.png` image.
- Document obtaining and installing the shared skill directory in supported
  applications, with current primary documentation for the installation and
  invocation details.
- Explain Codex, Claude Code, and Qwen Code usage, distinguishing their actual
  invocation conventions. Explain that using DeepSeek depends on the selected
  agent application's skill-loading and interaction capabilities.
- Describe approval/discussion interactions, free-text feedback, chat fallback,
  and returning to earlier decisions. Avoid claims of identical UI or guaranteed
  model compliance.
- Link the specification and plan. Explain that the skill is agent guidance,
  not technical enforcement of Git operations. Do not install anything or modify
  the skill instructions as part of this unit.

**Dependency impact and risks:** README is the repository's public entry point.
Its examples must agree with U1; image and document links must resolve. A wrong
installation path or universal invocation claim would mislead users even if the
skill itself is valid. Separate documented format support from runtime testing.

**Verification:** check local links and the embedded image; verify host-specific
details against primary documentation; compare the described flow and examples
with U1 and the specification. Review the README as a new visitor would.

**Complete when:** the instructions are accurate, links resolve, relevant
limitations are clear, and the reviewed README has its own approved and verified
commit.

**Intended commit:** `docs: explain SmoothDev Skills usage`.

## U3 — Versioning and release policy

**Purpose:** communicate how the skill evolves and distinguish reviewed
development work from published versions. Implements the agreed versioning
decision while preserving **AC9**.

**Files:** update `README.md`; create `CHANGELOG.md`.

**Prerequisites:** U1 and U2 are reviewed and committed.

**Actions and boundaries:**

- Document `metadata.version` in `SKILL.md` as the single version source. Do not
  introduce a separate VERSION file or a second authoritative version value.
- Start at `0.1.0` during initial development. During `0.x`, increment minor for
  workflow changes and patch for compatible corrections.
- Treat the documented workflow and approval rules as the compatibility
  contract. From `1.0.0`, increment major for incompatible changes, minor for
  compatible additions, and patch for compatible corrections. Do not call an
  incompatible approval-rule change a patch merely because its diff is small.
- Create a changelog with an **Unreleased** section describing delivered changes.
  The development version value does not establish that a release was published.
- Explain that a release may group several reviewed commits, so versions do
  not increment for every commit. A future tag such as `v0.1.0` must identify the
  matching, verified release contents; published version contents are immutable.
- Document the later release process without executing it. Do not create or
  push tags, publish a release, push commits, or merge the branch in this unit.

**Dependency impact and risks:** maintainers and users rely on metadata,
changelog entries, and release identifiers agreeing. Check for duplicate version
sources, misleading release claims, and policy that silently grants additional
Git permissions. Initial metadata already belongs to U1; U3 adds the policy and
change record rather than duplicating that implementation.

**Verification:** compare the policy with Semantic Versioning and the actual
metadata; exercise examples of compatible fixes, compatible additions, and
changed approval semantics; check changelog scope against delivered commits and
ensure no unpublished work is represented as a published release.

**Complete when:** the version source, increment rules, unreleased record, and
future release boundaries are clear, and the actual documentation change has
its own reviewed, approved, and verified commit.

**Intended commit:** `docs: define versioning and release policy`.

## Combined final verification

- Check all nine specification acceptance criteria against the final skill,
  public guidance, and scenario evidence.
- Verify each planned unit's completion and actual commit, explaining any
  deviations or unresolved work.
- Confirm that the workflow image, specification, skill, README, and plan do
  not contradict one another, particularly at agreement and commit boundaries.
- Recheck the final skill format and repository links when changes warrant it.
  Confirm that metadata and the changelog accurately describe the development
  version without implying publication.
- Present the resulting behavior, acceptance evidence, actual commit list,
  limitations, and uncommitted changes. Obtain explicit developer acceptance of
  final verification before declaring the workflow complete.
- If verification reveals a defect, return to the affected agreement or plan
  gate when required and handle the fix through the full reviewed unit loop.
  Do not silently commit cleanup.

Record progress and commit hashes in the conversation. Changes to this tracked
plan still require review and explicit approval of their own commit; progress
tracking never authorizes an automatic follow-up commit.
