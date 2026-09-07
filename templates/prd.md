# PRD template / 产品需求文档模板

[English overview](../README.md) · [中文首页](../README.zh-CN.md) · [Workflow / 流程](../docs/workflow.md)

Use this as writing guidance. Replace the prompts with facts and explicit open questions, then publish the completed document as a versioned comment on its issue. Keep the bilingual headings, including the Chinese section names used by the current publishing checks.

以下内容用于指导填写。将提示替换为实际信息或明确的待确认项，再以带版本的评论发布到对应 Issue。保留双语标题，其中中文章节名与当前发布检查要求一致。

Describe **what the user needs**, visible behavior, and observable acceptance. Leave implementation choices to engineering design. Do not convert assumptions into claimed user approval.

写清**用户需要什么**、可见行为和可观察验收。实现方案留给研发设计，不把假设写成已获用户确认的结论。

## 文档信息 / Document information

- Issue / 对应需求：
- Version / 版本：
- Author / 撰写角色：
- Current state / 当前状态：草稿、待评审、打回修改或通过 / Draft, in review, changes requested, or approved

## 背景与目标 / Background and goal

Who experiences the problem, in what context, and what user outcome should improve? State the impact and the evidence available.

谁在什么场景遇到什么问题，希望改善什么用户结果？说明影响及已有证据。

## 目标用户与场景 / Target users and scenarios

Describe the main scenario, relevant permissions, preconditions, and important exceptions.

描述主要使用场景、相关用户权限、前置条件和重要例外。

## 范围 / Scope

### 范围内 / In scope

List the user capabilities and outcomes included in this version.

列出本版包含的用户能力及结果。

### 不做 / Out of scope

List adjacent capabilities that are explicitly excluded, and explain any essential boundary.

列出明确不包含的相邻能力，说明必要边界。

## 用户流程与业务规则 / User flow and business rules

Describe the mandatory entry point, when it is visible, what users can see and do, and the result of each important action.

说明必有入口、可见条件、用户能看到和执行的动作，以及每个重要动作的结果。

## 异常与边界 / Exceptions and boundaries

Consider empty results, insufficient permissions, invalid input, repetition, cancellation, loss of access, and recovery where relevant. Describe the user's experience for each applicable case.

按需求考虑空结果、权限不足、无效输入、重复操作、取消、访问资格变化及恢复路径，说明适用场景中的用户体验。

## 验收标准 / Acceptance criteria

Write observable outcomes with a starting condition, action, and expected result. Use measurable timing only when justified by the requirement, or mark it as a proposal to confirm.

按照前置条件、用户动作、预期结果写可观察验收。时间指标应有需求依据；没有依据时标明待确认提议。

Example / 示例：A member without permission sees an explanation and cannot perform the restricted action. / 没有权限的成员看到原因说明，且无法执行受限操作。

## 待确认项与假设 / Open questions and assumptions

For each unknown: state the question, who can confirm it, its impact, and whether it blocks review. Mark critical product decisions as unresolved instead of inventing an answer.

对每个未知项记录问题、确认对象、影响及是否阻塞评审。关键产品决策未定时明确标记，不自行编造结论。

## 本版修改对照 / Revision log

| Review finding / 评审意见 | Change in this version / 本版修改 | Affected acceptance / 相关验收 |
| --- | --- | --- |
| Actual blocking finding / 实际阻塞问题 | Concrete revision / 具体修改 | Updated observable outcome / 更新后的可观察结果 |

For v1, mark this section as the initial draft. For later versions, address each actual review finding and preserve previous versions in issue comments. The independent reviewer records the review result separately; authoring this section does not grant approval.

v1 标记为初稿；后续版本逐条回应真实评审意见，旧版本保留在 Issue 评论中。评审结果由独立评审角色另行记录，作者填写本节不代表已经通过。
