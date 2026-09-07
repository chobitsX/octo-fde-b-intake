# FDE B · Octo 产品需求池

[English](README.md) | **简体中文**

本仓库用于 **2026 年 9 月 8 日下午场** FDE 实操考核，为 [octo-server](https://github.com/Mininglamp-OSS/octo-server) 提供有源码证据的产品问答、反馈归档、PRD 撰写和独立评审。

上游仓库只读。本仓库保存考试需求与可复用说明，不是上游官方 Issue 跟踪器。

## 快速入口

- [查看需求池](https://github.com/chobitsX/octo-fde-b-intake/issues)
- [流程、标签与考官操作说明（中英双语）](docs/workflow.md#chinese)
- [PRD 模板（中英双语）](templates/prd.md)

## Agent 分工

| 角色 | Octo 机器人 | 职责 |
| --- | --- | --- |
| 产品管家 | FDE-B 产品管家 | 有证据问答、反馈归档、需求认领、PRD 撰写与修订 |
| 独立评审 | FDE-B PRD评审 | 阅读实际 PRD，记录具体通过依据或阻塞问题 |

两个机器人都加入考试 Octo 群。正常问答回复实际提问者，每条群输出额外 @ 主考；需求变化还会通知已记录 Octo 来源身份的相关反馈人。

## 产品流程

1. 收到反馈后，记录类型、优先级、状态、用户场景与待补信息。
2. 开启状态的 Issue 被标记为 `feature` 或 `type:feature` 后进入产品流程。
3. 产品管家认领需求，将带版本的 PRD 写入 Issue 评论，并发起独立评审。
4. 评审提出具体修改意见或给出通过依据；修订保留历史版本，并说明每条意见如何处理。
5. 服务器定时器每 **两分钟** 扫描 Issue 状态和相关标签，包括考官静默关闭的单子。有意义的变化主动回报到 Octo，空扫描不发群消息。

PRD 只描述 **用户需要什么**、可观察行为和验收标准。PRD 通过不代表功能已实现。只有关单、缺少修复证据时，应表述为 **已关闭，修复结论尚未确认**；“未复现”“不做”分别表达。

## 仓库目录

```text
README.md                 英文首页
README.zh-CN.md           中文首页
docs/
  workflow.md             流程、标签和考官操作说明
templates/
  prd.md                  中英双语 PRD 模板
PRD-TEMPLATE.md           保留原有模板入口
```

需求、PRD 版本和评审结论统一以 Issue 及其评论为准。目录保存可复用说明，无需再按文件目录维护一份相同需求。已有的 [rehearsal 演练单](https://github.com/chobitsX/octo-fde-b-intake/issues?q=is%3Aissue%20label%3Arehearsal) 是模拟材料，不代表已确认的上游缺陷。

## 知识与源码证据

源码固定为 2026 年 9 月 7 日取得的 [`c7abadeb183a0ac55252f03e5f47d192a48f6f4d`](https://github.com/Mininglamp-OSS/octo-server/tree/c7abadeb183a0ac55252f03e5f47d192a48f6f4d)。

知识索引覆盖九域：认证与身份、鉴权、配置、模块注册、API 与错误、server/IM 分工、Bot 身份与会话、存储与外部依赖、构建与部署。

回答先读取实际源码，再给出 `来源: <相对路径>#L<起始行>-L<结束行>`。发送前检查路径和行号范围。知识不足时明确说“我不确定”，给出咨询对象和需要补充的证据。

## 考官权限与运行边界

仓库公开可读。关闭他人创建的 Issue、修改标签需要仓库协作者权限；考官先接受邀请，再进行这些操作。

Agent 使用只允许本仓库 Issues 权限的细粒度凭据。凭据、主机配置和私密群聊记录不进入本仓库。这里的文档更新不会修改已冻结的 Agent 运行程序或知识快照。
