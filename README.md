# 智能报销助手 Agent

面向中小企业的会话式报销提报产品。员工通过企业微信、钉钉或飞书机器人上传发票并补充业务信息，系统完成识别、制度辅助判断、报销单草稿生成和审批流转；员工确认后才正式提交。

## 当前状态

- 交付模式：Formal Software Delivery Workflow（Stage-Gate）
- 当前阶段：Stage 1 - Requirements Definition
- 当前门禁：Stage 1 需求基线编制中；完成后提交 `GATE-002` 审批
- 产品形态：聊天报销 Agent + 简单 Web 管理后台 + 财务制度 RAG + 结构化规则引擎
- 工程状态：尚未进入架构与开发阶段
- 正式远程仓库：[QI-code1992/Expense-Reimbursement-Assistant](https://github.com/QI-code1992/Expense-Reimbursement-Assistant)

项目状态以 `workflow/state.json` 为准，聊天记录不作为唯一基线。

## 阶段目录

| 阶段 | 目录 | 目标 |
|---|---|---|
| 0 | `00-opportunity/` | 机会、竞品与可行性验证 |
| 1 | `01-requirements/` | PRD、SPEC、验收标准与追踪矩阵 |
| 2 | `02-product-interaction-design/` | 业务流、用户流与页面功能矩阵 |
| 3 | `03-ui-prototype/` | 视觉基线与可交互高保真原型 |
| 4 | `04-architecture-plan/` | 架构、数据、接口与实施计划 |
| 5 | `05-development/` | 开发、自测、评审与功能检查点 |
| 6 | `06-testing/` | 测试计划、用例、缺陷与报告 |
| 7 | `07-acceptance/` | 按精确版本独立验收 |
| 8 | `08-release-handoff/` | 发布、回滚、运维与移交 |

## 治理规则

1. 每个阶段必须产出规定文件并通过用户明确审批。
2. 已批准需求的实质变更统一进入 `workflow/CHANGE_REQUESTS.md`。
3. 当前有效文档原位更新，历史版本依赖 Git 提交与里程碑标签恢复。
4. RAG 负责制度检索、解释和软性判断；金额阈值、审批路径、抬头、必填项、重复票和权限由结构化规则控制。
5. 开发、测试和验收必须绑定明确的 Commit SHA。
6. 凡后续工作需要用户提供帮助、授权、账号/服务开通、配置或部署操作，Agent 必须立即说明阻塞范围和最小操作步骤，并登记到 `workflow/USER_ACTIONS.md`。
7. 在用户完成或明确批准前，Agent 不得自行尝试迂回方案、额外服务、替代账号、非必要插件或复杂绕行路径；同一外部阻塞不得反复试错消耗额度。
8. 不受外部阻塞影响的工作可以继续，但不得借此掩盖阻塞、扩大范围或越过阶段门禁。
9. 当 Agent 无法可靠完成某动作，或用户通过少量直接操作明显更省时、省步骤、省 Token 时，必须优先请用户处理；只有用户明确反馈无法完成后，Agent 才能尝试其他路径。
10. “用户优先”不用于转移正常工程职责：本地文档、代码、测试、验证和已授权的可逆操作仍由 Agent 主动完成。
