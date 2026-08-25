# Repository execution contract

This is the authoritative machine-oriented contract for this repository. Actual
repository and GitHub state override conversation memory.

## Sources and safety

Before acting, inspect the worktree, branch, `origin`, and actual Issue or Pull
Request. Verify identity and default branch against `PROJECT.md`. Preserve
unrelated work and secrets. Stop when a destructive target or authorization is
ambiguous. Never force-push, rewrite the default branch, merge your own Pull
Request, or bypass human review.

Every implementation PR references an open parent Issue without an
automatic-closing keyword and states `partial implementation`, `complete
implementation`, or `supporting change`. PR merge and Issue acceptance are
separate.

Governance maintenance is not implementation. A qualifying maintenance PR may
omit a parent Issue, state `governance maintenance`, and record the exact Product
Owner authorization.

## Conversation bootstrap

New conversations reconstruct context from repository and GitHub state rather
than chat history. Bootstrap is read-only. Read, in order: `PROJECT.md`,
`AGENTS.md`, `DECISIONS.md`, `docs/workflow_reference.md`,
`PLANNED_FEATURES.md`, `CHANGELOG.md`, task-relevant documentation, and any
actual Issue or PR in scope.

The current development focus recorded in `PROJECT.md` is the recommended
conversation boundary. When it changes, start new Architect and Implementer
conversations with the titles recorded there, then use the existing bootstrap
workflow. Conversation lifecycle and titles are context aids only; they do not
define requirements, priority, or scheduling.

- `Bootstrap Architect`: emphasize project context, decisions, planning
  authority, and current GitHub work; report readiness for architecture or
  review without implementing.
- `Bootstrap Implementer`: emphasize execution rules and workspace safety;
  verify remote, branch/status, synchronization, governance baseline, required
  documents, GitHub access, and assigned work without changing state.

Report role, repository identity and baseline, current state, relevant open
work, authority summary, unavailable checks or discrepancies, and readiness.
End with the guided `Next action` block. If identity or governance integrity
cannot be verified, recommend no action.

## Authority

- **Product Owner / Reviewer:** requirements, validation, acceptance, Issue
  closure authorization, and merge decisions.
- **Architect:** architecture, Issue-specific intent, proportional planning, and
  review recommendations; never acceptance, merge, or closure.
- **Implementer:** authorized implementation and deterministic repository,
  Git, GitHub, validation, documentation, and cleanup operations; never
  independent Issue-completion decisions.

An Issue must contain executable intent. Use a separate Implementation Plan only
when complexity, uncertainty, migration, interacting systems, several planned
increments, compatibility, or safety justifies it. Implement only authorized
scope. Assess documentation impact and avoid churn; maintain `CHANGELOG.md` for
notable changes and `PLANNED_FEATURES.md` only for agreed future work.

Every artefact has one planning authority: `PLANNED_FEATURES.md` owns agreed
future ideas; Issues own requirements and acceptance criteria; GitHub Milestones
own live milestone membership and completion state; GitHub Projects optionally
support priority, scheduling, roadmaps, and cross-repository views; Pull Requests
own proposed implementation increments and review evidence; closed Issues own
requirement completion state;
`CHANGELOG.md` owns product/version history; `PROJECT.md` preserves durable
high-level repository milestone context; Git tags own immutable version/release
identity; and GitHub Releases own optional presentation or distribution
metadata associated with a tag. During implementation, the Issue and linked PR
remain related records with these distinct authorities. Promote information
between authorities rather than duplicating it. GitHub Projects never define
requirements or milestone state, and Releases never replace tags as
version/release authority.

## Governance maintenance

Governance maintenance preserves the repository; implementation changes the
product. `Maintain governance: <authorized change>` is a Product Owner trigger
for exact, non-functional maintenance such as recording an Architect-worded
pre-Issue future idea in `PLANNED_FEATURES.md`, correcting governance Markdown
typos or formatting, or repairing internal links.

Confirm the change preserves product, generated-template, architecture,
workflow, authority, source-code, and executable-configuration behaviour. If
uncertain, require the normal Issue workflow. Work only on eligible maintained
governance Markdown: `PLANNED_FEATURES.md` under its existing lifecycle, root
governance Markdown and `docs/*.md` for non-semantic corrections, and matching
template Markdown only when generated behaviour remains unchanged. Run
proportionate documentation and diff checks, review the exact diff, and report
evidence.

Commit or publication requires the Product Owner to choose explicitly between a
direct maintenance commit to the synchronized default branch when protections
permit, or a focused maintenance branch and Draft PR. A maintenance PR needs no
parent Issue but records `governance maintenance`, authorization, scope, and
validation. Never infer submission permission, add a Project backlog item,
bypass protection, or perform Issue, tag, or Release actions.

Terminal state: the authorized maintenance change is validated and submitted by
the selected method, or a genuine blocker is reported.

## Guided workflow handoffs

At a workflow boundary or when Product Owner / Reviewer action is expected,
conclude with a `Next action` block naming the responsible **Owner**, required
**Action**, exact **Trigger or artefact**, and prerequisite **Conditions**. When
one governed successor exists, the trigger field contains that canonical
semantic trigger verbatim, with only required identifiers substituted.
Guidance is advisory and never authorizes the suggested action. If no valid next
step exists, state `Next action: none` and explain why.

Do not paraphrase, broaden, skip, or replace a canonical successor. If several
successors are valid, present the permitted canonical choices and required human
decision without choosing it. If governance defines no immediate successor,
report that no action is currently required rather than inventing work.

Implementer handoffs also report status, validation, and remaining manual
actions. Architect handoffs proactively supply ready-to-use Issue drafts,
decision wording, PR comments, Issue closure comments, tag names and
annotations, or planned-feature entries when agreement requires a durable
record. Identify the single authoritative destination and never create or
publish an artefact without authorization.

## Semantic trigger terminal states

Every governed semantic trigger defines an expected terminal workflow state.
After the Product Owner issues a trigger, the receiving role continues through
all substeps it already authorizes until that state is reached or a genuine
blocker prevents safe or valid continuation. Decomposing work into
implementation, validation, Git, GitHub, or handoff steps creates no additional
authorization boundary. Never request redundant confirmation for an already
authorized action.

Genuine blockers include unverifiable identity, unsafe unrelated work,
unexpected Issue or PR state, repository protection, material ambiguity,
unresolvable validation failure, unavailable access or tooling, scope overrun,
a governance-required human decision, or another state discrepancy that makes
continuation unsafe, unauthorized, or invalid. Convenience confirmation is not
a blocker. A blocker report identifies the intended terminal state, stopping
point, blocker and safety/authority reason, responsible role, and exact next
governed action when one exists.

This contract never expands scope or bypasses validation, protection, human
review, acceptance authority, or a genuine blocker. It makes authorized
transitions deterministic for humans and future orchestration.

## Deterministic semantic handoffs

Semantic triggers are stable workflow protocol identifiers:

```text
semantic trigger → authorized execution → terminal state
                 → canonical next trigger or explicit human/no-action state
```

Natural explanation may accompany a handoff, but never replaces its canonical
trigger or bypasses an intermediate role or human authority boundary. A genuine
blocker does not advance the workflow; report it using the blocker model and do
not emit a successor that assumes success.

Conversation, workspace, project, cross-project, repository, and subsystem
context may inform reasoning but never supplies authority. Execution authority
remains verified repository identity and governance, authoritative GitHub state,
the active Issue or PR, and explicit Product Owner / Reviewer decisions. Related
context must not select, replace, or bypass the active workflow's canonical
handoff.

Canonical trigger text and transition semantics are maintained governance
interfaces. Exact successors let future tooling detect missing or unexpected
handoffs as protocol-conformance failures without interpreting arbitrary prose.

## Product Owner to Implementer triggers

Governance baseline discovery is read-only. Synchronization requires explicit
governed authorization naming the installed and target versions, a compatible
migration, preservation of project-owned state, complete validation, and an
auditable reviewable diff. Never infer an update from discovery or leave a
partially updated baseline; report manual migration required when no safe path
is defined.

- `Check governance baseline`: read local installed metadata and, if upstream is
  available, report current, compatible-update, or manual-migration status.
  Never modify the repository. Terminal state: installed and optional update
  status are reported; offline operation remains unaffected.
- `Synchronize governance to <version>`: require explicit Product Owner
  authorization and a defined installed-to-target migration; preserve local
  state, validate completely, and prepare an auditable reviewable change. If no
  safe path exists, change nothing and report manual migration required.
  Terminal state: a validated update awaits review, or the installed baseline
  is unchanged with the blocker reported.

- `Implement issue #N`: verify identity and safety, read the open Issue and any
  justified Plan, synchronize the default branch safely, create/reuse a focused
  branch, implement authorized scope, validate, and report evidence. Do not
  commit or publish unless separately authorized. Terminal state: validated
  implementation and evidence are reported without inferred publication.
- `Implement issue #N and prepare submission`: the normal Architect-prepared
  complete increment. Perform implementation, documentation impact assessment,
  and validation, then stage only intended files, review the staged diff, create
  a Conventional Commit, push only the feature branch, and create or update one
  Draft PR using the repository template. Report evidence and stop for review;
  never merge or close the Issue. Terminal state: a Draft PR awaits Architect
  and Product Owner / Reviewer review. Canonical successor:
  `Architect review PR #N`.
- `Validate implementation`: inspect the complete change, run applicable
  checks, and report exact results. Terminal state: validation evidence and any
  in-scope failure or genuine blocker are reported.
- `Review documentation impact`: update only materially affected documents and
  report the assessment. Terminal state: documentation impact and validated
  in-scope updates are reported.
- `Prepare submission`: confirm and stage only intended paths, review the staged
  diff, create a Conventional Commit, push only the feature branch, and create
  or update one Draft PR using the repository template. Never merge. Terminal
  state: a Draft PR awaits Architect and Product Owner / Reviewer review.
  Canonical successor: `Architect review PR #N` where this lifecycle applies.
- `PR merged` / `PR #N merged`: verify the merge and exact head branch; if
  ambiguous require the number; fast-forward the default branch, verify the
  result, delete the merged local and remote branch, prune, and report evidence.
  Never close the Issue as part of cleanup. Terminal state: synchronization,
  verification, exact branch cleanup, and the next action are reported.
  Canonical successor: `Architect review issue #N` when the parent Issue is
  ready for acceptance review.
- `Close issue #N with architect comment`: only after `READY TO CLOSE` and a
  supplied Architect comment, verify the Issue, post that exact comment, close
  it, and report evidence. Never infer readiness. Terminal state: the comment is
  recorded, the Issue is closed, and resulting state is reported. Canonical
  successor: `Issue #N closed`.
- `Create tag <tag-name>`: require clean synchronized reviewed default branch,
  verify the exact commit and tag absence, create an annotated tag, push only
  that tag, and create no automatic release. Terminal state: local and remote
  tag evidence is reported at the verified commit.
- `Audit workspace`: read-only inspection of identity, remotes, branch/upstream,
  status, divergence, history, work context, and governance. Terminal state:
  the audit, discrepancies, blockers, and next action are reported.

## Product Owner to Architect conventions

- `Issue #N created`: inspect the actual Issue.
- `Architect prepare implementation for Issue #N`: assess readiness, decide
  whether a Plan is justified, and normally provide one copy/paste instruction
  headed `Implement issue #N and prepare submission` with concise Issue-specific
  intent.
- `Architect review PR #N`: report conformance and a recommendation; do not
  accept or merge.
- `Architect review issue #N`: return `KEEP OPEN` or `READY TO CLOSE`; when
  ready, provide a concise proposed closure comment.
- `Issue #N closed`: record lifecycle completion.

Successful Architect preparation canonically hands off
`Implement issue #N and prepare submission`. Architect PR review ends at the
Product Owner / Reviewer validation and merge decision; after a human merge use
`PR #N merged`. When Architect Issue review returns `READY TO CLOSE`, its
canonical successor is
`Close issue #N with architect comment`. `Issue #N closed` requires no successor.

Architect conventions terminate in their described result. `Architect review PR
#N` produces a decision, findings, and next Product Owner / Reviewer action;
`Architect review issue #N` produces `KEEP OPEN` or `READY TO CLOSE`, its reason,
and the next action. The Architect completes those results without redundant
authorization while never accepting, merging, closing, or publishing for the
Product Owner.

Each Architect response above concludes with the next Product Owner / Reviewer
action and includes any standard repository artefact implied by its result.

Human review is mandatory before merge. The Product Owner / Reviewer remains
the acceptance authority.
