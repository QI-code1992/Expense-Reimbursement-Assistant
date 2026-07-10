# User Actions

本文件是需要项目发起人提供帮助、授权、账号/服务开通、配置或部署操作的连续台账。

## 强制处理协议

发现用户依赖时，Agent 必须：

1. 立即说明受阻的工作范围、原因、所需责任方和是否影响当前阶段门禁。
2. 给出完成目标所需的最小操作步骤，不把探索性或可选动作混入必需步骤。
3. 说明预期结果、验证方式、权限/费用/安全影响，以及完成后 Agent 从哪里继续。
4. 在选择执行路径前判断 Agent 是否能可靠完成，以及用户直接操作是否明显更省时、省步骤、省 Token。
5. 若 Agent 无法可靠完成，或用户能以少量直接步骤明显更高效地完成，先创建用户待办并等待用户处理。
6. 只有用户明确反馈直接操作也无法完成后，Agent 才能尝试最小可行替代路径；不得提前使用替代账号、额外服务、非必要插件或复杂绕行方案。
7. 对同一外部阻塞不进行重复重试；仅可继续与该阻塞无关、在原范围内且不越过门禁的工作。
8. 不得以“用户优先”为由转移正常的本地文档、编码、测试、验证或已授权可逆操作。
9. 完成后更新本台账状态并记录验证证据。

## 用户优先触发条件

满足任一条件时，应先交由用户处理：

- 当前工具或环境客观上不能完成该动作。
- 需要用户账号登录态、组织管理员权限、验证码、MFA、人机验证或本人身份确认。
- Agent 路径需要额外安装、开通服务、替代账号、跨系统绕行或多轮不确定重试。
- 用户可通过少量明确步骤直接完成，且相较 Agent 路径能显著减少时间、复杂度或 Token 消耗。
- 操作结果依赖用户看到的专属界面状态，Agent 无法可靠验证。

如果上述条件均不成立，Agent 应直接完成原范围内的正常工作，不额外打扰用户。

## 状态定义

- `Open`：等待用户处理。
- `In Progress`：用户正在处理。
- `Resolved`：已完成并通过验证。
- `Deferred`：用户明确延期。
- `Canceled`：后续不再需要。

## 当前待办

当前无。

## 已关闭待办

### UA-001：配置本项目 Git 作者身份

- Status: Resolved
- Raised At: 2026-07-10
- Owner: 项目发起人（用户）
- Required By: 创建首个提交和 Stage 0 里程碑标签之前
- Blocking Scope: Git 提交与阶段标签
- Non-Blocking Scope: Stage 0 文档评审和门禁决策
- Reason: 本地 Git 仓库及正式 GitHub 远程 `origin` 已配置，GitHub 账号 `QI-code1992` 已通过认证，但 `user.name` 与 `user.email` 未配置；不得伪造提交者身份。
- Minimal Action:

```bash
cd "/Users/qiqi/Documents/Expense Reimbursement Assistant"
git config --local user.name "你的姓名"
git config --local user.email "你的邮箱"
```

- Validation:

```bash
git config --local --get user.name
git config --local --get user.email
```

- Expected Result: 两条验证命令分别输出预期姓名和邮箱。
- Permission / Cost / Security Impact: 只修改当前仓库的本地 Git 配置；不会自动上传代码或产生费用。姓名和邮箱会写入后续提交元数据，并在推送后显示于 GitHub 提交历史。
- Resume Point: 配置完成后，Agent 可创建治理基线提交并推送至 `origin/main`；Stage 0 获批后再创建正式里程碑标签。
- Evidence: 2026-07-10 已验证当前仓库 `user.name` 为 `QI QI`，`user.email` 为 `qiqi417813490@gmail.com`。
