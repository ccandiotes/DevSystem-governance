# Architectural Decisions

Record only accepted durable decisions needed to understand and govern
<Project Name>. Do not use this document as an activity log.

## Every planning state has one authority

**Status:** Accepted

Every engineering artefact has exactly one authoritative owner at each stage:

| Lifecycle state | Authoritative location |
|---|---|
| Agreed future idea | `PLANNED_FEATURES.md` |
| Requirement and acceptance criteria | GitHub Issue |
| Live milestone membership and completion state | GitHub Milestone |
| Optional priority, scheduling, roadmap, and cross-repository views | GitHub Project |
| Proposed implementation and review evidence | Pull Request |
| Requirement completion state | Closed GitHub Issue |
| Product/version history | `CHANGELOG.md` |
| Durable high-level repository milestone context | `PROJECT.md` |
| Immutable version/release identity | Git tag |
| Optional release presentation and distribution metadata | GitHub Release associated with the tag |

Promote information between authorities instead of maintaining competing
copies. GitHub Milestones own live Issue membership and completion state.
GitHub Projects are optional planning views; they do not define requirements or
own milestone state. Repository governance describes the model rather than the
current backlog. Optional Implementation Plans refine implementation without
becoming another requirements authority. During implementation, the Issue owns
the requirement and acceptance criteria while its linked Pull Request owns the
proposed implementation increment and review evidence. `PROJECT.md` retains
concise high-level milestone context without becoming a duplicate tracker. A
Git tag is the authoritative immutable version or release marker; an optional
GitHub Release presents notes or assets around that tag without becoming a
competing authority.

## Governance maintenance is a first-class workflow

**Status:** Accepted

Explicitly Product Owner-authorized, non-functional maintenance of designated
governance Markdown may proceed without a parent Issue. It may record an agreed
pre-Issue future idea, correct formatting or typographical errors, or repair
internal links. It remains traceable through authorization, validation, and a
commit, with a maintenance PR when requested or required by protection rules.

Maintenance cannot change product or generated-template behaviour, source code,
architecture, authority boundaries, executable configuration, or the workflow
itself. Ambiguous work follows the normal Issue workflow.

## Workflow responses provide guided handoffs

**Status:** Accepted

Architect and Implementer responses at workflow boundaries provide concise,
advisory guidance naming the next responsible role, action, and exact trigger or
manual step. Guidance never grants authorization. When no valid next action
exists, the response explains why.

The Architect proactively supplies ready-to-use repository artefacts once an
agreed outcome requires a durable record, identifies each artefact's single
authoritative destination, and does not publish it without authorization.
Implementer handoffs report status, validation, manual actions, and the next
applicable workflow trigger.

## Semantic triggers execute to defined terminal states

**Status:** Accepted

Every governed semantic trigger defines an expected terminal workflow state.
The receiving role executes all substeps already authorized by the trigger
until that state is reached or a genuine blocker makes continuation unsafe,
unauthorized, ambiguous, or invalid. Internal decomposition creates no extra
Product Owner authorization boundary, and convenience confirmation is not a
blocker.

A blocker response identifies the intended terminal state, stopping point,
blocker and reason, responsible role, and exact next governed action. This
contract preserves validation, protection, Issue scope, human review, and
Product Owner / Reviewer authority while supporting deterministic human and
future orchestrated operation.

## Guided handoffs use canonical semantic successors

**Status:** Accepted

Semantic triggers are stable workflow protocol identifiers, and together with
guided handoffs they form a deterministic workflow protocol.
Every successful terminal state identifies its permitted governed successors.
When exactly one trigger applies, the role emits it verbatim with only required
identifiers substituted, never a paraphrase, shortcut, or skipped intermediate
role.

Multiple valid successors remain a Product Owner / Reviewer choice, deliberate
human decision boundaries do not gain invented AI triggers, and no-action states
do not create work. A genuine blocker never advances the workflow. This defines
the stable chain `trigger → execution → terminal state → canonical successor`
for human use and future orchestration while allowing explanatory conversation.

Conversation, workspace, repository, subsystem, and project context is
informative rather than authoritative. Authority remains verified active
repository identity and governance, authoritative GitHub state and work
artefacts, and explicit Product Owner / Reviewer decisions. Related context
cannot bypass canonical handoffs. Exact maintained trigger interfaces let
future tooling detect protocol-conformance failures without interpreting
arbitrary prose.

## Governance baselines are distribution-owned and migration-aware

**Status:** Accepted

The installed governance version is supplied by the governance distribution,
not editable project configuration, and is independent of the project's own
release version. Local metadata records the actual installed baseline so the
repository remains self-contained and usable offline.

The published upstream is authoritative for available governance releases; the
project repository remains authoritative for active governance. Discovery is
read-only. Synchronization requires explicit Product Owner authorization and a
defined installed-to-target migration that distinguishes upstream-managed,
project-configured, project-owned, and mixed state. It preserves local identity,
history, decisions, configuration, and documentation, produces a reviewable
repository change, and fails without partial updates when compatibility is not
defined.

## AI conversations bootstrap from the repository

**Status:** Accepted

New Architect and Implementer conversations reconstruct context from current
repository governance and GitHub state rather than prior chat history. Short,
stable role prompts start a read-only verification of identity, governance
baseline, current state, authority, and relevant open work. Bootstrap reports
readiness and discrepancies, ends with a guided handoff, and never authorizes
mutation or replaces a task-specific trigger.

## Development focus bounds AI conversations

**Status:** Accepted

The current development focus and recommended Architect and Implementer
conversation titles are recorded in `PROJECT.md`. A focus
change is the recommended boundary for starting fresh role conversations, which
then use the repository-first bootstrap. The focus and titles are navigation
and context aids only; they do not define requirements, priority, or scheduling.

## Repository milestones preserve significant project outcomes

**Status:** Accepted

Repository milestones represent significant achieved or intended outcomes or
states, not units of active development. GitHub Milestones own live membership
and completion state when GitHub is used; optional GitHub Projects may reference
them but do not own that state. `PROJECT.md` retains concise high-level milestone
context without duplicating Issue tracking or schedules.

Generated projects begin with `Deployed`: successful establishment of the
governed project in its intended working environment. `First Release` may be
suggested or configured later but is not mandatory. Project-type extensions may
define or recommend additional domain-appropriate milestone conventions.

## Decision title

**Status:** Proposed | Accepted | Superseded

**Context:** What durable problem or constraint requires a decision?

**Decision:** What was decided?

**Consequences:** What trade-offs, obligations, or follow-up result?
