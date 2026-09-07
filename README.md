# FDE B · Octo product intake

This is the independent examination demand pool for the Sep 8, 2026 afternoon practical. It is not the upstream Octo issue tracker. The upstream `Mininglamp-OSS/octo-server` repository is read-only.

## Agents

| Role | Octo bot | Responsibility |
| --- | --- | --- |
| Product steward | FDE-B 产品管家 | Evidence-based Q&A, feedback intake, product ownership, PRDs and revisions |
| Independent reviewer | FDE-B PRD评审 | Review actual PRDs, document blocking findings or approval |

## Workflow

1. Archive feedback with type, priority, status, user context and explicit missing information.
2. An open issue labeled `feature` enters the product workflow.
3. The steward claims the issue, publishes a versioned PRD, and requests independent review.
4. The reviewer records concrete approval or change requests. Revisions keep prior versions and explain the changes.
5. A scheduler checks issue state and relevant labels every two minutes, including issues silently closed by a maintainer. Notifications mention the examiner and affected participants in the originating Octo group.

PRDs describe **what users need**, user-visible behavior and acceptance criteria. Approval means the product document passed review; it does not mean the feature was implemented.

## Labels

- Type: `type:bug`, `type:feature`, `type:question`, `type:task`.
- Priority: `priority:P0` (critical), `P1` (high impact), `P2` (normal), `P3` (polish).
- Status: `status:triage`, `status:needs-info`, `status:needs-human`, `status:in-progress`, `status:in-review`, `status:changes-requested`, `status:approved`.
- Resolution: `resolution:fixed`, `resolution:cannot-reproduce`, `resolution:wontfix`. Plain `wontfix` and GitHub `not_planned` are also recognized.
- `rehearsal`: synthetic preparation data, not a confirmed upstream defect.

A closed issue without authoritative fix evidence is reported as **closed, fix unconfirmed**. “Cannot reproduce” and “won't fix” remain separate from “fixed”.

## Source evidence

The preparation source snapshot is `c7abadeb183a0ac55252f03e5f47d192a48f6f4d` of `Mininglamp-OSS/octo-server` (September 7, 2026).

Code answers use repository-relative evidence such as `来源: main.go#L45-L60`, after reading the actual corresponding lines. Paths and line ranges are checked before publishing an answer. The example format does not assert that this particular range answers any question.

The knowledge base covers authentication, permissions, configuration, module registration, APIs and errors, the server/IM boundary, bot identity and sessions, persistence, and build/deployment.

## Examiner operations

The examiner may read all issues publicly. Closing other people's issues and changing labels requires accepting the repository collaborator invitation first. The invitation is scoped to this examination repository.

To exercise automation, change an issue on GitHub without sending another Octo message. A new `feature` label triggers product work; a silent close or `wontfix` produces an appropriately worded change notification. Empty polls remain silent.

The agents use a fine-grained credential scoped to this repository's Issues permission. No secrets, host configuration or private group transcripts are stored in this repository.
