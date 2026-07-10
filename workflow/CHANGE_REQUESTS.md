# Change Requests

本文件记录所有正式变更。当前 Stage 0 尚无已批准产品基线，因此既往对话中的选择作为发现阶段输入，不登记为变更请求。

## 状态定义

- `Proposed`：已提出，待分析。
- `Clarification Required`：需要澄清后才能判断影响。
- `Approved`：已批准，等待更新基线或实施。
- `In Progress`：正在更新受影响资产。
- `Verified`：已完成并验证，等待关闭。
- `Rejected`：不采纳。
- `Closed`：已完成全部基线、实现、测试或验收处理。

## 变更记录

### CR-001：建立用户依赖事项的即时提醒与禁止绕行约束

- Level: L1 - Workflow Governance
- Status: Verified
- Raised By: 项目发起人（用户）
- Raised At: 2026-07-10（当前对话）
- Current Stage: Stage 0 - Opportunity Validation
- Original Request: 后续需要用户提供帮助、授权、开通或部署时，及时提醒并说明具体操作；不得自行尝试迂回复杂路径造成不必要的额度消耗；将其写入流程作为约束。
- Clarified Requirement:
  - 一旦发现外部依赖，立即告知用户受阻范围、原因和所需责任方。
  - 提供最小且具体的操作步骤、预期结果、验证方式和完成后的恢复点。
  - 未经用户明确批准，不尝试替代账号、额外服务、非必要插件、复杂绕行方案或重复重试。
  - 所有用户待办统一登记在 `workflow/USER_ACTIONS.md`；只继续与阻塞无关且不扩大范围的工作。
- Reason: 提高协作透明度，避免权限类问题触发低价值探索、重复尝试和额度浪费。
- Impact:
  - PRD: 无产品范围影响
  - SPEC: 无产品范围影响
  - Prototype: 无
  - Architecture: 后续若依赖外部资源，必须先执行该协议
  - Implementation Plan: 需标明用户依赖与前置条件
  - Test Cases: 无直接影响
  - Acceptance Criteria: 无直接影响
- Decision: Approved by the user in the originating request
- Updated Baselines:
  - `README.md`
  - `workflow/state.json`
  - `workflow/USER_ACTIONS.md`
  - `context-handoff.md`
- Implementation:
  - Commit: Pending Git author configuration
  - Owner: Workflow Orchestrator
- Verification:
  - Status: Verified
  - Evidence: 约束已写入工作流状态、治理规则、用户待办台账和跨会话交接文件

### CR-002：建立用户优先的效率升级机制

- Level: L1 - Workflow Governance
- Status: Verified
- Raised By: 项目发起人（用户）
- Raised At: 2026-07-10（当前对话）
- Current Stage: Stage 0 - Opportunity Validation
- Original Request: 当 Agent 确实无法完成，或用户操作更省心高效、可避免 Agent 走弯路时，必须先让用户处理；只有用户也无法完成后，Agent 才尝试其他方法。
- Clarified Requirement:
  - Agent 在选择执行路径前，先判断当前工具、权限和上下文是否足以可靠完成。
  - 若 Agent 无法可靠完成，必须立即转为用户待办，不先试复杂替代路径。
  - 若用户能用少量直接步骤完成，而 Agent 路径需要额外安装、外部服务、缺失登录态、复杂 UI 操作或多轮不确定重试，也必须优先交给用户。
  - 用户明确反馈直接路径也无法完成后，Agent 才能选择最小可行替代方案，并说明新增权限、费用、安全和范围影响。
  - 该机制不得用于把正常的本地文档、编码、测试、验证和已授权可逆操作转移给用户。
- Efficiency Triggers:
  - 缺少必要工具能力、账号登录态、权限、验证码或人机验证。
  - Agent 路径需要新装工具、开通服务、使用替代账号或跨多个系统绕行。
  - 已知 Agent 路径成功率低或需要多轮试错，而用户可通过少量明确步骤直接完成。
  - 操作涉及用户本机已有登录会话、专属组织后台或只有用户能判断的界面状态。
- Impact:
  - PRD: 无产品范围影响
  - SPEC: 无产品范围影响
  - Prototype: 无
  - Architecture: 外部依赖和人工前置条件需显式标注
  - Implementation Plan: 任务需区分 Agent 执行与用户前置动作
  - Test Cases: 无直接影响
  - Acceptance Criteria: 无直接影响
- Decision: Approved by the user in the originating request
- Updated Baselines:
  - `README.md`
  - `workflow/state.json`
  - `workflow/USER_ACTIONS.md`
  - `context-handoff.md`
- Implementation:
  - Commit: Pending Git author configuration
  - Owner: Workflow Orchestrator
- Verification:
  - Status: Verified
  - Evidence: 用户优先触发条件、处理顺序、替代路径门槛及不得转移正常职责的边界已写入流程文件

### CR-003：登记并绑定正式 GitHub 远程仓库

- Level: L0 - Project Infrastructure Configuration
- Status: Verified
- Raised By: 项目发起人（用户）
- Raised At: 2026-07-10（当前对话）
- Current Stage: Stage 0 - Opportunity Validation
- Original Request: 使用用户已创建的 `QI-code1992/Expense-Reimbursement-Assistant` GitHub 仓库进行后续版本管理。
- Clarified Requirement:
  - 将该仓库配置为本地仓库唯一正式远程 `origin`。
  - 后续阶段基线、检查点和验收版本使用该仓库的 Commit SHA、分支与标签管理。
  - 未通过阶段门禁的草稿不得标记为正式里程碑。
- Reason: 为正式交付工作流提供可恢复、可审计的远程版本历史。
- Impact:
  - PRD: 无
  - SPEC: 无
  - Prototype: 后续原型检查点可引用远程 Commit SHA
  - Architecture: 无
  - Implementation Plan: 后续开发检查点必须推送到远程开发分支
  - Test Cases: 无
  - Acceptance Criteria: 后续验收绑定远程可追溯的精确 Commit SHA
- Decision: Approved by the user in the originating request
- Updated Baselines:
  - `.gitignore`
  - `README.md`
  - `workflow/state.json`
  - `workflow/USER_ACTIONS.md`
  - `context-handoff.md`
- Implementation:
  - Remote: `origin` -> `https://github.com/QI-code1992/Expense-Reimbursement-Assistant.git`
  - GitHub Account: `QI-code1992`
  - Remote Initial State: Empty
  - Commit: Pending Git author configuration
  - Owner: Workflow Orchestrator
- Verification:
  - Status: Verified
  - Evidence: `gh auth status` 已确认账号与仓库权限；`git ls-remote` 成功且无引用；`git remote -v` 在绑定后复核

下一条变更使用连续编号 `CR-004`，至少记录：请求、原因、影响阶段、受影响基线、风险、决策人、决定、版本移动、验证证据和关闭状态。
