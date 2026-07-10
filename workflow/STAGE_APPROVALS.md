# Stage Approvals

本文件是正式阶段门禁的连续审批台账。只有用户可以批准阶段转换。

### INIT-001：启动 Formal Software Delivery Workflow

- Status: Approved
- Approver: 项目发起人（用户）
- Approved At: 2026-07-10（当前对话）
- Current Stage: 尚未建立正式基线
- Next Stage: Stage 0 - Opportunity Validation
- Artifacts Reviewed: 当前对话总结与项目现场盘点
- Evidence Reviewed: 工作区为空、无 Git 仓库、无 PRD/SPEC/原型/代码/测试
- Version / Commit SHA: N/A
- Decision: 建立 Formal Software Delivery Workflow 并直接进入下一步
- Conditions / Scope Exceptions: 无
- Notes: 该审批只授权创建 Stage 0 与治理基线，不等同于批准 Stage 0 -> Stage 1。

### GATE-001：Stage 0 -> Stage 1

- Status: Approved
- Approver: 项目发起人（用户）
- Approved At: 2026-07-10（当前对话）
- Current Stage: Stage 0 - Opportunity Validation
- Next Stage: Stage 1 - Requirements Definition
- Artifacts Reviewed:
  - `00-opportunity/OPPORTUNITY.md` v1.0
  - `00-opportunity/COMPETITOR_ANALYSIS.md` v1.0
  - `00-opportunity/FEASIBILITY.md` v1.0
- Evidence Reviewed: 当前对话确认、Stage 0 机会结论、竞品官方资料、可行性与风险分析、MVP 边界、协作治理约束
- Version / Commit SHA: 首次基线提交后补记
- Decision: 批准 Stage 0 v1.0，进入 Stage 1 - Requirements Definition
- Conditions / Scope Exceptions:
  - Stage 1 统一 OCR 目标中 80% 与 95% 两种历史口径。
  - Stage 1 明确首发 IM 平台、数据与制度样本、安全合规、规模、集成、时间和预算约束。
  - 继续执行“RAG + 结构化规则 + 人工兜底”责任模型。
- Notes: Stage 0 基线标签为 `baseline/stage-00-opportunity-v1.0`；创建后补记精确 Commit SHA。
