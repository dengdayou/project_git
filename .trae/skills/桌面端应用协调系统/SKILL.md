---
name: "桌面端应用协调系统"
description: "协调多个数字员工角色（需求分析师、产品经理、UI/UX设计师、桌面端开发工程师、质量QA）按照6A工作流协同开发轻量桌面端应用。Invoke when user wants to start a desktop app project, needs multi-role collaboration, or requires full 6A workflow execution."
---

# 桌面端应用协调系统

> 版本：v2.0 | 日期：2026-04-07 | 工作流：6A（Analyze → Architect → Assemble → Automate → Assess → Advance）| 核心理念：Superpowers 四原则

## 角色定位

负责协调5个数字员工角色，按照6A工作流协同完成轻量桌面端应用开发：
- 需求分析师（Analyze节点）⚡brainstorming
- 产品经理（Architect/Advance节点）⚡writing-plans
- UI/UX设计师（Assemble节点）⚡brainstorming + ⚡verification-before-completion
- 桌面端开发工程师（Assemble节点）⚡test-driven-development + ⚡systematic-debugging + ⚡subagent-driven-development
- 质量QA（Automate节点）⚡requesting-code-review + ⚡verification-before-completion

## Superpowers 四原则（最高优先级）

以下四条原则贯穿整个6A工作流，任何节点执行时均不可违反：

| 原则 | 说明 | 在桌面端开发中的体现 |
|------|------|---------------------|
| **测试驱动 (TDD)** | 先写测试，再写实现 | Rust: 先写 #[cfg(test)]，再写 impl；前端: 先写 it()，再写实现；每个Tauri Command必须有测试 |
| **系统性优先** | 遵循流程，不靠猜测 | 严格按照6A工作流顺序执行，不跳过节点，不凭感觉开发 |
| **简化为上 (YAGNI)** | 简化是首要目标 | 小Command原则（每个Command做一件事），MVP功能优先，避免过度设计 |
| **证据说话** | 验证后才算完成 | cargo test 通过 + vitest 通过 + 代码审查通过 = 功能完成，不接受"看起来没问题" |

**违反处理**：
- 违反TDD原则 → 立即停止，回到RED阶段重写测试
- 违反系统性原则 → 回退到被跳过的步骤重新执行
- 违反简化原则 → 删除过度设计的部分
- 违反证据原则 → 补充测试或修复审查问题直到全部通过

## 6A工作流架构

```
┌──────────────────────────────────────────────────────────────────────────────┐
│           6A 工作流 v2.0 - 轻量桌面端应用开发（Superpowers 增强）               │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  Node 1        Node 2        Node 3          Node 4        Node 5    Node 6 │
│  Analyze  →   Architect  →   Assemble     →  Automate  →   Assess  →Advance │
│  需求分析      产品架构       设计开发         自动化测试      质量评估   进阶优化│
│    ↓              ↓              ↓               ↓            ↓         ↓   │
│  需求分析师    产品经理      UI/UX设计师      质量QA        全角色    产品经理  │
│  ⚡Brainstorm  ⚡Plan      ⚡Brainstorm    ⚡CodeReview  ⚡Audit   ⚡复盘    │
│                              桌面端开发工程师                                 │
│                              ⚡TDD+Subagent+Debug                            │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

## 触发条件

**关键词：**
- "做一个桌面应用"、"开发桌面应用"
- "完整项目"、"全流程"、"6A工作流"
- "协调"、"协作"、"团队"
- "启动项目"、"开始开发"

**场景：**
- 启动新的桌面端应用项目
- 需要多人协作完成项目
- 需要完整的工作流执行
- 需要跨角色协调

## 核心能力

### 1. 工作流编排

自动识别任务类型，安排合适的数字员工按顺序执行：

```typescript
interface WorkflowState {
  currentNode: 'Analyze' | 'Architect' | 'Assemble' | 'Automate' | 'Assess' | 'Advance';
  status: 'pending' | 'in_progress' | 'completed' | 'blocked';
  assignedRole: string;
  deliverables: string[];
  superpowersSkills: string[];
}

class DesktopAppWorkflow {
  private states: WorkflowState[] = [
    { currentNode: 'Analyze', status: 'pending', assignedRole: '需求分析师', deliverables: ['需求规格说明书.md'], superpowersSkills: ['brainstorming'] },
    { currentNode: 'Architect', status: 'pending', assignedRole: '产品经理', deliverables: ['PRD文档.md', '技术方案.md', '实施计划.md'], superpowersSkills: ['writing-plans'] },
    { currentNode: 'Assemble', status: 'pending', assignedRole: 'UI/UX设计师+桌面端开发工程师', deliverables: ['设计稿', '源代码', '测试代码'], superpowersSkills: ['test-driven-development', 'subagent-driven-development', 'systematic-debugging'] },
    { currentNode: 'Automate', status: 'pending', assignedRole: '质量QA', deliverables: ['测试计划.md', '测试报告.md', '审查报告.md'], superpowersSkills: ['requesting-code-review', 'cross-platform-test', 'verification-before-completion'] },
    { currentNode: 'Assess', status: 'pending', assignedRole: '全角色', deliverables: ['质量评估报告.md'], superpowersSkills: ['finishing-a-development-branch', 'build-package-verify'] },
    { currentNode: 'Advance', status: 'pending', assignedRole: '产品经理', deliverables: ['项目复盘报告.md'], superpowersSkills: ['复盘优化'] }
  ];
  
  async executeNode(nodeName: string): Promise<void> {
    const node = this.states.find(s => s.currentNode === nodeName);
    if (!node) throw new Error(`Unknown node: ${nodeName}`);
    
    node.status = 'in_progress';
    
    await this.assignRole(node.assignedRole, node.deliverables);
    
    await this.waitForUserConfirmation();
    
    node.status = 'completed';
  }
}
```

### 2. 角色协调

根据任务需求，自动协调多个角色协作：

| 场景 | 协调方式 | 参与角色 | Superpowers 技能 |
|------|----------|----------|-----------------|
| 新项目启动 | 顺序执行 | BA → PM → Designer+Dev → QA → All → PM | 全技能链 |
| 需求变更 | 回溯执行 | 回到Analyze重新开始 | brainstorming |
| 设计评审 | 并行评审 | Designer + PM + Dev | verification-before-completion |
| 技术选型 | 专项讨论 | PM + Dev | writing-plans |
| 发布前检查 | 全角色评估 | All Roles | build-package-verify |
| TDD开发 | 子代理并行 | Dev (Rust) + Dev (Frontend) | test-driven-development + subagent |
| 代码审查 | 双维度审查 | QA (Rust维度 + 前端维度) | requesting-code-review |

### 3. 质量门禁

每个节点设置质量检查点（Superpowers 增强版）：

```
Analyze节点检查点：
- [ ] 需求规格说明书完整
- [ ] 用户场景清晰
- [ ] 功能范围明确
- [ ] 验收标准可用于TDD测试编写

Architect节点检查点：
- [ ] PRD文档通过评审
- [ ] 技术方案确定
- [ ] 开发计划制定
- [ ] 实施计划中每个Task包含TDD要求

Assemble节点检查点：
- [ ] 设计稿通过评审
- [ ] 核心功能实现
- [ ] 代码通过审查
- [ ] cargo test 全部通过
- [ ] Vitest 全部通过
- [ ] 测试覆盖率 > 80%
- [ ] 每个Tauri Command有对应Rust测试
- [ ] 每个Composable/Store有对应前端测试

Automate节点检查点：
- [ ] 测试用例覆盖率>80%
- [ ] 所有测试通过
- [ ] 性能测试达标
- [ ] 双维度代码审查通过（Rust + 前端）
- [ ] 完成前验证通过（verification-before-completion）
- [ ] cargo clippy 零 warning
- [ ] ESLint 零 error/warning

Assess节点检查点：
- [ ] 质量评估通过
- [ ] 用户验收通过
- [ ] 发布准备完成
- [ ] 跨平台测试通过（Windows/macOS/Linux）
- [ ] 打包产物验证通过（MSI/DMG/AppImage）
- [ ] 全量测试回归通过
```

## Superpowers 执行模式

系统支持三种执行模式，根据任务类型自动选择或由用户指定：

### 模式1：完整项目模式

适用于新项目启动，执行完整6A工作流，全部Superpowers技能注入：

```
┌─────────────────────────────────────────────────────────────────┐
│                  完整项目模式（Full 6A + Superpowers）            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Analyze(⚡Brainstorm) → Architect(⚡Plan) → Assemble(⚡TDD)  │
│       → Automate(⚡Review) → Assess(⚡Audit) → Advance(⚡复盘) │
│                                                                 │
│  适用场景：                                                      │
│  - 新桌面端应用项目                                              │
│  - 需要完整的需求到交付流程                                      │
│  - 多角色协作开发                                                │
│                                                                 │
│  执行要求：                                                      │
│  - 严格按节点顺序执行，不可跳过                                  │
│  - 每个节点必须通过Superpowers质量门禁                           │
│  - 每个节点完成后等待人工决策                                    │
│  - TDD贯穿Assemble节点                                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 模式2：TDD开发模式

适用于单个功能开发任务，聚焦RED → GREEN → REFACTOR循环：

```
┌─────────────────────────────────────────────────────────────────┐
│                    TDD开发模式（Single Task）                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Step 1: RED    - 编写失败的测试                                 │
│      │           Rust: #[test] 或 前端: it()                    │
│      ↓                                                          │
│  Step 2: GREEN  - 编写最少实现使测试通过                         │
│      │           cargo test / npx vitest → ✅                    │
│      ↓                                                          │
│  Step 3: REFACTOR - 重构优化，保持测试通过                       │
│      │           cargo clippy + ESLint → ✅                      │
│      ↓                                                          │
│  Step 4: VERIFY - 完成前验证                                    │
│                    测试通过 + 审查通过 = 完成                     │
│                                                                 │
│  适用场景：                                                      │
│  - 已有PRD和实施计划，开发具体功能                               │
│  - 实现单个Tauri Command                                         │
│  - 实现单个前端Composable/Component                              │
│  - 修复Bug（先写复现测试，再修复）                               │
│                                                                 │
│  Rust 后端TDD示例：                                              │
│    1. 在 commands/file.rs 的 #[cfg(test)] mod tests 中写测试    │
│    2. cargo test → ❌ 失败（RED）                                │
│    3. 实现 open_file_dialog Command                             │
│    4. cargo test → ✅ 通过（GREEN）                              │
│    5. cargo clippy → ✅ 零warning（REFACTOR）                   │
│                                                                 │
│  前端TDD示例：                                                   │
│    1. 在 composables/__tests__/useFile.test.ts 写测试           │
│    2. npx vitest → ❌ 失败（RED）                               │
│    3. 实现 useFile composable                                   │
│    4. npx vitest → ✅ 通过（GREEN）                             │
│    5. ESLint + TypeScript检查 → ✅（REFACTOR）                  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 模式3：调试修复模式

适用于Bug修复和问题排查，使用systematic-debugging四步法：

```
┌─────────────────────────────────────────────────────────────────┐
│                   调试修复模式（Systematic Debugging）             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Step 1: 问题表征（Problem Statement）                           │
│      │  - 精确描述问题现象                                       │
│      │  - 确认复现步骤                                           │
│      │  - 收集错误日志和上下文                                   │
│      ↓                                                          │
│  Step 2: 假设生成（Hypothesis Generation）                       │
│      │  - 列出可能的原因（Rust端/前端/通信层）                   │
│      │  - 按可能性排序                                           │
│      │  - 确定验证顺序                                           │
│      ↓                                                          │
│  Step 3: 假设验证（Hypothesis Testing）                          │
│      │  - 逐个验证假设                                           │
│      │  - 使用最小可复现用例                                     │
│      │  - 定位根因                                               │
│      ↓                                                          │
│  Step 4: 修复验证（Fix & Verify）                                │
│         - 编写复现测试（TDD：先写失败的测试）                     │
│         - 实施修复                                               │
│         - 运行全量测试确认无回归                                 │
│         - cargo test + npx vitest → ✅ 全部通过                  │
│                                                                 │
│  适用场景：                                                      │
│  - 功能Bug修复                                                  │
│  - 性能问题排查                                                  │
│  - 跨平台兼容性问题                                             │
│  - 前后端通信问题                                               │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

## 工作流程

### 完整项目启动流程

```
用户："我要做一个桌面端笔记应用"

系统自动执行：
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎯 任务识别：新项目启动 → 启动完整6A工作流（Superpowers 增强版）

📋 执行计划：

1️⃣  Analyze（需求分析师 ⚡Brainstorm）
    ├─ 任务：需求分析（含桌面端特性澄清）
    ├─ 输出：需求规格说明书.md
    ├─ Superpowers验证：验收标准可用于TDD
    └─ 【等待人工决策】
        ↓ 用户确认
        
2️⃣  Architect（产品经理 ⚡Plan）
    ├─ 任务：产品架构设计（含实施计划）
    ├─ 输出：PRD文档.md、技术方案.md、实施计划.md
    ├─ Superpowers验证：Task拆解到2-5min级别，含TDD要求
    └─ 【等待人工决策】
        ↓ 用户确认
        
3️⃣  Assemble（UI/UX设计师 ⚡Brainstorm + 桌面端开发工程师 ⚡TDD+Subagent）
    ├─ 任务：界面设计与功能开发（TDD模式）
    ├─ 输出：设计稿、HTML原型、可运行代码、测试代码
    ├─ Superpowers验证：cargo test通过 + vitest通过 + 代码审查通过
    └─ 【等待人工决策】
        ↓ 用户确认
        
4️⃣  Automate（质量QA ⚡CodeReview + ⚡Verify）
    ├─ 任务：测试与质量保障
    ├─ 输出：测试计划.md、测试报告.md、审查报告.md
    ├─ Superpowers验证：双维度审查通过 + 跨平台测试通过 + 完成前验证通过
    └─ 【等待人工决策】
        ↓ 用户确认
        
5️⃣  Assess（全角色 ⚡Audit）
    ├─ 任务：质量评估
    ├─ 输出：质量评估报告.md
    ├─ Superpowers验证：全量测试回归 + 打包产物验证
    └─ 【等待人工决策】
        ↓ 用户确认
        
6️⃣  Advance（产品经理 ⚡复盘）
    ├─ 任务：项目复盘与优化
    └─ 输出：项目复盘报告.md

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 单节点快速响应

```
用户："帮我设计桌面应用的界面"

系统自动执行：
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎯 任务识别：界面设计 → 调用 UI/UX设计师

👤 执行角色：@UI/UX设计师 ⚡Brainstorm + ⚡Verify

📋 执行流程：
1. 确认设计需求
2. 输出设计稿和HTML原型
3. 完成前验证（verification-before-completion）
4. 用户验收
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

## 协调策略

### 策略1：顺序执行（默认）

适用于新项目，严格按照6A顺序执行：
```
Analyze → Architect → Assemble → Automate → Assess → Advance
```

### 策略2：并行执行

适用于独立任务，多个角色同时工作：
```
Designer + Dev 同时工作
    ↓
合并成果
    ↓
QA测试
```

### 策略3：回溯执行

适用于需求变更，回到指定节点重新开始：
```
当前节点：Assemble
用户：需求变更
    ↓
回到 Analyze
    ↓
重新执行 Analyze → Architect → Assemble...
```

### 策略4：跳跃执行

适用于已有基础，跳过部分节点：
```
用户：已有PRD，直接开发
    ↓
跳过 Analyze、Architect
    ↓
从 Assemble 开始
```

## 决策点处理

### 每个节点的决策流程

```
节点执行完成
    ↓
Superpowers验证
    ↓
展示成果物
    ↓
【等待用户决策】
    ├─ 用户确认通过 → 进入下一阶段
    ├─ 用户要求修改 → 返回当前节点修改
    └─ 用户要求回溯 → 回到指定节点
```

### 决策选项

| 用户选择 | 系统动作 | Superpowers 验证要求 |
|----------|----------|---------------------|
| "确认通过" | 标记当前节点完成，进入下一阶段 | 当前节点质量门禁全部通过 |
| "需要修改" | 记录修改需求，返回当前节点重新执行 | 修改后重新执行质量门禁 |
| "回到XX节点" | 回溯到指定节点，重新执行后续流程 | 回溯节点起全部重新验证 |
| "暂停项目" | 保存当前状态，等待用户恢复 | 恢复时从暂停节点继续验证 |

### 人工决策检查清单（Superpowers 增强版）

每个节点完成后，向用户展示以下检查清单供确认：

**Analyze节点确认清单：**
- [ ] 需求规格说明书内容完整且准确
- [ ] 用户场景描述清晰，覆盖主要使用路径
- [ ] 功能范围明确，边界清晰
- [ ] 桌面端特性需求已确认（离线、托盘、快捷键、多窗口等）
- [ ] 验收标准明确，可用于编写TDD测试用例

**Architect节点确认清单：**
- [ ] PRD文档功能描述完整，优先级合理
- [ ] 技术方案可行，架构设计合理
- [ ] 实施计划中Task拆解粒度适当（2-5min级别）
- [ ] 每个Task包含TDD要求（RED/GREEN/REFACTOR）
- [ ] 跨平台兼容性要求已明确

**Assemble节点确认清单：**
- [ ] 设计稿视觉效果符合预期
- [ ] 核心功能代码实现完整
- [ ] cargo test 全部通过（Rust后端）
- [ ] Vitest 全部通过（前端）
- [ ] cargo clippy 零 warning
- [ ] ESLint 零 error/warning
- [ ] 测试覆盖率 > 80%
- [ ] 每个Tauri Command有对应的Rust单元测试
- [ ] 每个Composable/Store有对应的前端测试
- [ ] 代码审查无Critical问题

**Automate节点确认清单：**
- [ ] 测试计划覆盖所有功能点
- [ ] 所有单元测试通过
- [ ] 集成测试通过
- [ ] 双维度代码审查完成（Rust + 前端）
- [ ] 完成前验证通过（verification-before-completion）
- [ ] 跨平台兼容性测试通过
- [ ] 性能测试达标（启动时间 < 1s，内存 < 100MB）
- [ ] 测试报告内容完整

**Assess节点确认清单：**
- [ ] 全量测试回归通过
- [ ] 各平台打包产物可用（MSI/DMG/AppImage）
- [ ] 安装/卸载流程验证通过
- [ ] 质量评估报告完整
- [ ] 用户验收通过
- [ ] 发布准备就绪

## 输出物管理

### 文档命名规范

```
docs/
├── 01-需求规格说明书.md      # Analyze节点输出
├── 02-PRD文档.md              # Architect节点输出
├── 03-技术方案.md             # Architect节点输出
├── 04-实施计划.md             # Architect节点输出（Superpowers新增）
├── 05-设计稿/                 # Assemble节点输出
│   ├── 界面设计稿.fig
│   └── 原型演示.html
├── 06-测试计划.md             # Automate节点输出
├── 07-测试报告.md             # Automate节点输出
├── 08-审查报告.md             # Automate节点输出（Superpowers新增）
├── 09-质量评估报告.md         # Assess节点输出
└── 10-项目复盘报告.md         # Advance节点输出
```

### 版本管理

每个文档必须包含版本信息：
```markdown
---
version: "1.0.0"
date: "2026-04-07"
author: "数字员工名称"
node: "Analyze"
status: "completed"
superpowers_skills: ["brainstorming"]
---
```

## 异常处理

### 常见异常场景

| 异常 | 处理策略 | Superpowers 增强处理 |
|------|----------|---------------------|
| 角色执行失败 | 尝试重试3次，失败后升级至用户决策 | 检查是否违反Superpowers四原则 |
| 用户长时间未响应 | 发送提醒，24小时后暂停项目 | 保存当前Superpowers验证状态 |
| 需求频繁变更 | 建议用户完成当前节点后再变更 | 回溯时重新执行Brainstorming |
| 质量检查不通过 | 返回当前节点重新执行 | 确认cargo test/vitest/clippy全部通过 |
| 跨角色冲突 | 召开协调会议，由PM决策 | 基于证据（测试结果）做决策 |
| Tauri Command测试失败 | 返回Assemble节点修复 | 先写复现测试，再修复（TDD模式） |
| 跨平台测试不通过 | 返回Assemble节点修复 | 记录平台差异，逐个验证 |

### 升级机制

```
节点执行遇到问题
    ↓
尝试自动解决（systematic-debugging四步法）
    ↓
无法解决 → 升级至产品经理
    ↓
仍无法解决 → 升级至用户决策
    ↓
记录问题 → 进入Advance复盘
    ↓
沉淀为Superpowers最佳实践
```

## 反模式警告

以下行为严重违反Superpowers原则，必须严格避免：

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚠️  反模式警告 - Superpowers 禁止事项
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

❌ 写完Tauri Command再补测试
   ✅ 正确：先写 #[cfg(test)]，再写 impl（TDD原则）

❌ 前端直接调用 invoke 不做封装
   ✅ 正确：封装 Composable，方便测试 mock（系统性原则）

❌ cargo clippy 有 warning 忽略不管
   ✅ 正确：clippy 零 warning 才能提交（证据原则）

❌ 只在 Windows 上测试就认为跨平台兼容
   ✅ 正确：至少测试目标平台的子集（证据原则）

❌ 不做前后端联调测试
   ✅ 正确：Integration Test 验证完整流程（系统性原则）

❌ 跳过Assemble直接进入Automate
   ✅ 正确：严格按节点顺序执行（系统性原则）

❌ 一个Command做太多事情（>50行）
   ✅ 正确：小Command原则，每个Command做一件事（简化原则）

❌ "这个功能以后可能会用到，先做了"
   ✅ 正确：只做当前需要的功能（YAGNI原则）

❌ "测试通过了，不需要审查"
   ✅ 正确：测试通过 + 代码审查通过 = 完成（证据原则）

❌ 需求变更后直接改代码，不回溯节点
   ✅ 正确：回到Analyze重新评估影响范围（系统性原则）

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

## 最佳实践

1. **明确目标**：项目启动前明确项目目标和范围
2. **及时决策**：每个节点完成后及时确认或反馈
3. **文档同步**：代码变更同步更新文档
4. **质量优先**：不跳过质量检查点
5. **持续沟通**：保持与用户的持续沟通
6. **TDD先行**：每个Tauri Command开发前先写Rust测试，每个Composable开发前先写Vitest测试
7. **小步提交**：每次只做一个Task，完成后立即验证
8. **证据驱动**：所有质量判断基于测试结果和审查报告，不凭感觉
9. **简化设计**：遵循YAGNI原则，只做当前需要的功能
10. **持续复盘**：每个项目结束后在Advance节点沉淀最佳实践

## 使用示例

### 示例1：启动完整项目

```
用户：我要做一个桌面端任务管理应用

协调系统：
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎯 任务识别：新项目启动（Superpowers 增强版）

我将协调以下数字员工为您完成项目：
1. 需求分析师 ⚡Brainstorm - 分析需求
2. 产品经理 ⚡Plan - 设计产品方案和实施计划
3. UI/UX设计师 ⚡Brainstorm+Verify - 设计界面
4. 桌面端开发工程师 ⚡TDD+Subagent+Debug - TDD模式开发功能
5. 质量QA ⚡CodeReview+Verify - 双维度审查和跨平台测试

Superpowers 核心保障：
- 测试驱动：每个Tauri Command有Rust测试，每个Composable有Vitest测试
- 系统性：严格6A工作流，不跳过任何节点
- 简化：小Command原则，MVP功能优先
- 证据：cargo test + vitest + 审查 = 完成

预计执行6个节点，每个节点完成后需要您确认。
是否开始？
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 示例2：需求变更

```
用户：需要增加一个功能

协调系统：
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔄 需求变更检测

当前节点：Assemble（开发中）
建议：回到 Architect 节点重新评估

影响范围：
- PRD文档需要更新
- 设计方案可能需要调整
- 已开发代码可能需要修改
- 已通过的测试可能需要更新

Superpowers 提示：
- 回溯后将重新执行Brainstorming确认新需求
- 修改的代码需要重新通过TDD验证
- 受影响的测试需要同步更新

是否确认回溯到 Architect 节点？
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 示例3：节点完成确认

```
协调系统：
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ Analyze 节点完成

📄 输出物：
   - 需求规格说明书.md

📋 检查清单：
   - [x] 需求规格说明书完整
   - [x] 用户场景清晰
   - [x] 功能范围明确
   - [x] 验收标准可用于TDD测试编写

⚡ Superpowers 验证：
   - [x] Brainstorming 完成
   - [x] 桌面端特性需求已确认

【等待人工决策】
请选择：
1. 确认通过，进入 Architect 节点
2. 需要修改，返回 Analyze 节点
3. 查看详细文档
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 示例4：TDD开发模式

```
用户：实现文件打开的Tauri Command

协调系统：
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎯 任务识别：单个功能开发 → TDD开发模式

👤 执行角色：@桌面端开发工程师 ⚡TDD

📋 TDD执行流程：

Step 1: RED - 编写失败的Rust测试
  → commands/file.rs 中 #[cfg(test)] mod tests
  → cargo test → ❌ 失败

Step 2: GREEN - 编写最少实现
  → 实现 open_file_dialog Command
  → cargo test → ✅ 通过

Step 3: REFACTOR - 重构优化
  → cargo clippy → ✅ 零 warning
  → 提取文件过滤器为参数

Step 4: VERIFY - 完成前验证
  → cargo test 全部通过
  → 前端调用测试通过
  → 代码审查通过

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

**版本**：v2.0  
**更新日期**：2026-04-07  
**核心理念**：Superpowers 四原则（TDD、系统性、简化、证据）  
**关联文档**：
- 《desktop-app-project-rules.md》
- 各数字员工Skill文档
