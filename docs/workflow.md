# Workflow and examiner guide / 流程与考官说明

[English overview](../README.md) · [中文首页](../README.zh-CN.md) · [中文正文](#chinese)

## English

### Where records live

- **Issue body:** feedback, user goal, actual and expected behavior, scenario or reproduction steps, environment, impact, workaround, and explicit missing information.
- **Issue comments:** claim record, PRD v1/v2 and later versions, independent review, human feedback, and revision notes.
- **Labels:** type, priority, processing status, and resolution.
- **Octo group:** final answers, missing-information questions, review requests, and meaningful changes from scheduled scans.
- **This file and the template directory:** reusable guidance. They do not replace the live issue history.

### Labels

| Dimension | Labels | Meaning |
| --- | --- | --- |
| Type | `type:bug`, `type:feature`, `type:question`, `type:task` | Feedback classification |
| Priority | `priority:P0`, `priority:P1`, `priority:P2`, `priority:P3` | Critical, high impact, normal, polish; explain the impact behind the choice |
| Triage | `status:triage`, `status:needs-info`, `status:needs-human` | Awaiting triage, missing facts, or human judgment |
| Product work | `status:in-progress`, `status:in-review`, `status:changes-requested`, `status:approved` | Claimed, awaiting review, rejected, or PRD approved |
| Closure | `status:closed`, `resolution:fixed`, `resolution:cannot-reproduce`, `resolution:wontfix` | Labels for closure and resolution; GitHub's actual open/closed state is authoritative |
| Triggers and compatibility | `bug`, `feature`, `wontfix` | Common labels; an open `feature` or `type:feature` issue starts product work |
| Exercise data | `rehearsal` | Synthetic preparation issue, not a confirmed upstream defect |

### Silent changes and autonomous work

The server-side cron runs every two minutes. It reads all issue states through paginated GitHub REST requests and compares them with persisted snapshots. It does not need an Octo message to wake up, and it does not use GitHub Search.

The examiner can change GitHub issue state or labels without notifying the bots:

1. Close an issue without a fix conclusion: expect “closed, fix unconfirmed”.
2. Close as not planned or add `wontfix`: expect “won't fix”, not “fixed”.
3. Add `feature` to an open issue: expect claim → PRD → independent review → revisions if requested.

GitHub's actual rate-limit responses govern cooldown. After a limit is reached, new GitHub calls stop until the recorded cooldown expires. Empty scans remain silent; real execution records are available from the Agent's health tool. The two-minute interval is the normal polling schedule, not an absolute delivery deadline during an outage or cooldown.

Every group output includes a real mention of the main examiner. Replies address the requester; issue updates also mention known feedback participants in their originating group. Messages waiting for delivery retain their state and are retried.

### PRD and review

Use the [bilingual template](../templates/prd.md). The steward claims an open issue before publishing a PRD. The reviewer reads the actual current version and records concrete findings. A rejected version is revised against those findings, with a change log and a new review request. Closed issues pause further product work.

Describe user goals, visible behavior, scope, exceptions, and observable acceptance. Technical implementation belongs in a later engineering design. PRD approval does not mean implementation or a bug fix is complete.

### Access and evidence

Reading is public. The examiner needs collaborator access to close others' issues or change labels. Existing `rehearsal` issues are preparation evidence; use new issues for the actual examination.

Code conclusions cite the fixed source revision with repository-relative paths and line ranges. If evidence is missing, state the uncertainty, who should confirm it, and which knowledge is missing. Keep credentials, private host configuration, and private group transcripts out of issues and attachments.

<a id="chinese"></a>

## 中文

### 记录放在哪里

- **Issue 正文**：反馈、用户目标、实际与预期表现、场景或复现步骤、环境、影响、替代方案与待补信息。
- **Issue 评论**：认领记录、PRD v1/v2 及后续版本、独立评审、人工意见和修改对照。
- **标签**：类型、优先级、处理状态与处置结论。
- **Octo 群**：最终回答、待补信息提问、评审请求以及定时扫描发现的有效变化。
- **本说明与模板目录**：可复用指引，不替代实际 Issue 历史。

### 标签体系

| 维度 | 标签 | 含义 |
| --- | --- | --- |
| 类型 | `type:bug`、`type:feature`、`type:question`、`type:task` | 对反馈进行分类 |
| 优先级 | `priority:P0`、`priority:P1`、`priority:P2`、`priority:P3` | 灾难性影响、高影响、普通、体验打磨；说明判断依据 |
| 分诊 | `status:triage`、`status:needs-info`、`status:needs-human` | 待分诊、缺少事实、需要人工判断 |
| 产品处理 | `status:in-progress`、`status:in-review`、`status:changes-requested`、`status:approved` | 已认领、待评审、打回、PRD 通过 |
| 关闭与处置 | `status:closed`、`resolution:fixed`、`resolution:cannot-reproduce`、`resolution:wontfix` | 用于表达关闭与处置；是否开启以 GitHub 实际状态为准 |
| 触发及兼容 | `bug`、`feature`、`wontfix` | 常见标签；开启状态的 `feature` 或 `type:feature` 单进入产品流程 |
| 演练数据 | `rehearsal` | 模拟反馈，不代表已确认的上游缺陷 |

### 静默变更与自动运行

服务器 cron 每两分钟执行一次。程序通过 GitHub REST 分页读取所有状态的 Issue，与持久快照比较。它不依赖新的 Octo 消息，也不使用 GitHub Search。

考官可以只在 GitHub 操作，不额外提醒机器人：

1. 关闭一个没有修复结论的单子：应回报“已关闭，修复结论尚未确认”。
2. 以 not planned 关闭，或增加 `wontfix`：应回报“不做”，不得转述为“已修复”。
3. 给开启的单子增加 `feature`：应进入认领 → PRD → 独立评审 → 按实际打回意见修订的流程。

程序按照实际限流响应进入冷却，冷却结束前停止新的 GitHub 请求。空扫描不发群消息；可以向 Agent 索取健康工具中的真实执行记录。两分钟是正常轮询周期，网络故障或限流时不承诺在两分钟内必达。

每条群输出都真实 @ 主考。问答回复提问者，需求变更还会通知已记录来源身份的相关反馈人。待发送消息保留状态，失败后可以重试。

### PRD 与评审

使用[中英双语模板](../templates/prd.md)。产品管家先认领开启的需求，再发布 PRD；评审阅读实际当前版本并提出具体意见。被打回后逐条修订，留下修改对照和新版本，再次请求评审。需求关闭后暂停继续推进。

PRD 描述用户目标、可见行为、范围、异常与可观察验收。技术实现留给后续研发设计。PRD 通过不代表功能开发完成，也不代表 Bug 已修复。

### 权限与证据

仓库公开可读。考官需获得协作者权限，才能关闭他人创建的 Issue 或修改标签。已有 `rehearsal` 单是准备阶段的证据，正式考试用新单。

代码结论引用固定版本中的相对路径和行号范围。证据不足时，明确不确定、应找谁确认、缺少哪些知识。凭据、私密主机配置与私密群聊记录不放进 Issue 或附件。
