# FDE B · Octo Product Intake

**English** | [简体中文](README.zh-CN.md)

An independent demand pool for the **September 8, 2026 afternoon** FDE practical examination: evidence-based product Q&A, feedback intake, product requirements, and independent review for [octo-server](https://github.com/Mininglamp-OSS/octo-server).

The upstream repository is read-only. This repository holds examination issues and reusable documentation; it is not the upstream issue tracker.

## Start here

- [Browse the demand pool](https://github.com/chobitsX/octo-fde-b-intake/issues)
- [Workflow, labels, and examiner operations — English / 中文](docs/workflow.md)
- [PRD template — English / 中文](templates/prd.md)

## Agents

| Role | Octo bot | Responsibility |
| --- | --- | --- |
| Product steward | FDE-B 产品管家 | Source-backed Q&A, feedback intake, ownership, PRDs, and revisions |
| Independent reviewer | FDE-B PRD评审 | Read the actual PRD and record concrete approval or blocking findings |

Both bots participate in the examination's Octo group. Normal answers address the requester; every group output also mentions the main examiner. Issue updates additionally mention the relevant feedback participants when their originating Octo identity is available.

## Product workflow

1. Archive feedback with its type, priority, status, user context, and explicit missing information.
2. An open issue labeled `feature` or `type:feature` enters product work.
3. The steward claims the issue, publishes a versioned PRD in its comments, and requests independent review.
4. The reviewer approves or requests specific changes. Revisions preserve earlier versions and explain how the findings were addressed.
5. A server-side scheduler scans issue states and relevant labels every **two minutes**, including silently closed issues. Meaningful changes are reported to Octo; empty scans stay silent.

PRDs describe **what users need**, observable behavior, and acceptance criteria. PRD approval does not mean the feature has been implemented. A close without fix evidence is reported as **closed, fix unconfirmed**; “cannot reproduce” and “won't fix” retain their own meanings.

## Repository layout

```text
README.md                 English entry point
README.zh-CN.md           Chinese entry point
docs/
  workflow.md             Workflow, labels, and examiner instructions
templates/
  prd.md                  Bilingual PRD template
PRD-TEMPLATE.md           Compatibility link to the template
```

Issues and their comments are the record of requirements, PRD versions, and review decisions. The directories contain reusable documentation, so the same requirement does not need to be maintained in a second file tree. Existing [rehearsal issues](https://github.com/chobitsX/octo-fde-b-intake/issues?q=is%3Aissue%20label%3Arehearsal) are synthetic preparation material, not confirmed upstream defects.

## Knowledge and source evidence

The fixed source snapshot is [`c7abadeb183a0ac55252f03e5f47d192a48f6f4d`](https://github.com/Mininglamp-OSS/octo-server/tree/c7abadeb183a0ac55252f03e5f47d192a48f6f4d), captured on September 7, 2026.

The knowledge index covers nine domains: authentication; permissions; configuration; module registration; APIs and errors; the server/IM boundary; bot identity and sessions; persistence and external dependencies; build and deployment.

Answers read the actual source and cite `来源: <relative-path>#L<start>-L<end>`. File paths and line ranges are checked before delivery. Missing knowledge is stated as uncertain, with a consultation route and the evidence to obtain.

## Examiner access and operational boundaries

The repository is public. Closing others' issues and changing labels requires repository collaborator access; the examiner must accept the invitation before those operations.

The agents use a fine-grained credential limited to this repository's Issues permission. Credentials, host configuration, and private group transcripts stay out of this repository. Documentation edits here do not update the frozen Agent runtime or its knowledge snapshot.
