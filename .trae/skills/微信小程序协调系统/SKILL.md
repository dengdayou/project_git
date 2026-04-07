---
name: "微信小程序协调系统"
description: "协调多个数字员工角色（需求分析师、产品经理、UI/UX设计师、小程序开发工程师、质量QA）按照6A工作流协同开发微信小程序。Invoke when user wants to start a WeChat mini program project, needs multi-role collaboration, or requires full 6A workflow execution."
---

# 微信小程序协调系统

> 版本：v2.0 | 日期：2026-04-07 | 工作流：6A（Analyze → Architect → Assemble → Automate → Assess → Advance）
> 核心理念：Superpowers 四原则（TDD、系统性、简化、证据）

## 角色定位

负责协调5个数字员工角色，按照6A工作流协同完成微信小程序开发：
- 需求分析师（Analyze节点）⚡brainstorming
- 产品经理（Architect/Advance节点）⚡writing-plans
- UI/UX设计师（Assemble节点）⚡brainstorming + ⚡verification-before-completion
- 小程序开发工程师（Assemble节点）⚡test-driven-development + ⚡systematic-debugging
- 质量QA（Automate节点）⚡requesting-code-review + ⚡verification-before-completion

## Superpowers 四原则

```
┌─────────────────────────────────────────────────────────────────────┐
│                 Superpowers 核心原则（最高优先级）                     │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  原则1：测试驱动 (TDD)                                              │
│  ─────────────────────                                              │
│  小程序单元测试先行：先写测试用例，再写功能实现                       │
│  ├─ 页面组件：先写 .test.ts，再写 .vue/.wxml                        │
│  ├─ 工具函数：先写测试，再写逻辑                                     │
│  └─ 违反时：立即停止，回到RED阶段                                    │
│                                                                     │
│  原则2：系统性优先                                                   │
│  ─────────────────────                                              │
│  严格按照6A工作流顺序执行，不跳过、不猜测                             │
│  ├─ 每个节点必须完成并通过质量门禁                                   │
│  └─ 违反时：回退到被跳过的步骤                                       │
│                                                                     │
│  原则3：简化为上 (YAGNI)                                            │
│  ─────────────────────                                              │
│  MVP优先，只做当前需要的功能，避免过度设计                            │
│  ├─ 分包策略：最小可用主包优先                                       │
│  ├─ 微信能力：按需集成，不全量接入                                   │
│  └─ 违反时：删除过度设计的部分                                       │
│                                                                     │
│  原则4：证据说话                                                     │
│  ─────────────────────                                              │
│  测试通过 + 审查通过 = 功能完成                                      │
│  ├─ 单元测试通过 + 代码审查通过 = Assemble完成                       │
│  ├─ 真机测试通过 + 审核规范通过 = Automate完成                       │
│  └─ 违反时：补充测试或修复审查问题                                   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

## Superpowers 技能矩阵（微信小程序）

```
┌─────────────────────────────────────────────────────────────┐
│        微信小程序开发技能树（Superpowers 增强）              │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  【流程类技能】                                              │
│  ├── brainstorming        需求澄清与架构探索                │
│  ├── writing-plans         任务拆解与实施计划               │
│  ├── test-driven-development  测试驱动开发(前端)           │
│  ├── systematic-debugging  系统化调试(4步法)               │
│  └── verification-before-completion  完成前验证             │
│                                                             │
│  【小程序专项技能】                                          │
│  ├── miniprogram-component-dev  小程序组件开发(TDD)        │
│  ├── miniprogram-api-integration  微信能力集成(TDD)        │
│  ├── miniprogram-subpackage    分包加载优化                 │
│  └── miniprogram-performance   性能优化与体积控制          │
│                                                             │
│  【协作类技能】                                              │
│  ├── subagent-driven-development  子代理并行开发           │
│  ├── requesting-code-review       代码审查(前端)           │
│  └── finishing-a-development-branch  分支收尾              │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## 6A工作流架构

```
┌─────────────────────────────────────────────────────────────────────────────┐
│              6A 工作流 v2.0 - 微信小程序开发（Superpowers 增强）             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Node 1        Node 2        Node 3        Node 4        Node 5    Node 6  │
│  Analyze  →   Architect  →   Assemble  →   Automate  →   Assess  →Advance  │
│  需求分析      产品架构       设计开发       自动化测试      质量评估  进阶优化│
│    ↓              ↓              ↓              ↓           ↓         ↓    │
│  需求分析师    产品经理      UI/UX设计师     质量QA      全角色    产品经理  │
│  ⚡Brainstorm  ⚡Plan      小程序开发工程师                                    │
│                              ⚡TDD+Debug      ⚡Review    ⚡Audit   ⚡复盘    │
│                              ⚡Subagent       ⚡Verify                       │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘

⚡ = Superpowers 技能注入点
```

### 各节点核心职责（Superpowers 增强版）

| 节点 | 角色 | Superpowers 技能 | 核心任务 | 文档输出 |
|------|------|------------------|----------|----------|
| **Analyze** | 需求分析师 | `brainstorming` | 需求澄清、微信能力分析、用户场景梳理 | 需求规格说明书.md |
| **Architect** | 产品经理 | `writing-plans` | PRD、技术选型、任务拆解、实施计划 | PRD文档.md、技术方案.md、实施计划.md |
| **Assemble** | UI/UX设计师<br>+ 小程序开发工程师 | `test-driven-development`<br>`systematic-debugging`<br>`subagent-driven-development` | 设计稿、TDD开发、子代理并行 | 设计稿、功能代码、测试代码 |
| **Automate** | 质量QA | `requesting-code-review`<br>`verification-before-completion` | 测试执行、代码审查、完成前验证 | 测试计划.md、测试报告.md、审查报告.md |
| **Assess** | 全角色 | `verification-before-completion` | 质量评估、真机验证、审核预检 | 质量评估报告.md |
| **Advance** | 产品经理 | 复盘优化 | 项目复盘、知识沉淀 | 项目复盘报告.md |

## 触发条件

**关键词：**
- "做一个小程序"、"开发小程序"
- "微信小程序"、"微信应用"
- "完整项目"、"全流程"、"6A工作流"
- "协调"、"协作"、"团队"
- "启动项目"、"开始开发"

**场景：**
- 启动新的微信小程序项目
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
  superpowersSkill: string;
  verificationRequired: boolean;
}

class MiniProgramWorkflow {
  private states: WorkflowState[] = [
    { currentNode: 'Analyze', status: 'pending', assignedRole: '需求分析师', deliverables: ['需求规格说明书.md'], superpowersSkill: 'brainstorming', verificationRequired: true },
    { currentNode: 'Architect', status: 'pending', assignedRole: '产品经理', deliverables: ['PRD文档.md', '技术方案.md', '实施计划.md'], superpowersSkill: 'writing-plans', verificationRequired: true },
    { currentNode: 'Assemble', status: 'pending', assignedRole: 'UI/UX设计师+小程序开发工程师', deliverables: ['设计稿', '源代码', '测试代码'], superpowersSkill: 'test-driven-development', verificationRequired: true },
    { currentNode: 'Automate', status: 'pending', assignedRole: '质量QA', deliverables: ['测试计划.md', '测试报告.md', '审查报告.md'], superpowersSkill: 'requesting-code-review', verificationRequired: true },
    { currentNode: 'Assess', status: 'pending', assignedRole: '全角色', deliverables: ['质量评估报告.md'], superpowersSkill: 'verification-before-completion', verificationRequired: true },
    { currentNode: 'Advance', status: 'pending', assignedRole: '产品经理', deliverables: ['项目复盘报告.md'], superpowersSkill: 'review', verificationRequired: false }
  ];
  
  async executeNode(nodeName: string): Promise<void> {
    const node = this.states.find(s => s.currentNode === nodeName);
    if (!node) throw new Error(`Unknown node: ${nodeName}`);
    
    node.status = 'in_progress';
    
    await this.assignRole(node.assignedRole, node.deliverables);
    
    if (node.verificationRequired) {
      await this.runSuperpowersVerification(node.superpowersSkill);
    }
    
    await this.waitForUserConfirmation();
    
    node.status = 'completed';
  }

  async runSuperpowersVerification(skill: string): Promise<boolean> {
    switch (skill) {
      case 'brainstorming':
        return this.verifyBrainstormingOutput();
      case 'writing-plans':
        return this.verifyPlanCompleteness();
      case 'test-driven-development':
        return this.verifyAllTestsPass();
      case 'requesting-code-review':
        return this.verifyCodeReviewPassed();
      case 'verification-before-completion':
        return this.verifyCompletionCriteria();
      default:
        return true;
    }
  }
}
```

### 2. 角色协调

根据任务需求，自动协调多个角色协作：

| 场景 | 协调方式 | 参与角色 |
|------|----------|----------|
| 新项目启动 | 顺序执行 | BA → PM → Designer+Dev → QA → All → PM |
| 需求变更 | 回溯执行 | 回到Analyze重新开始 |
| 设计评审 | 并行评审 | Designer + PM + Dev |
| 技术选型 | 专项讨论 | PM + Dev |
| 发布前检查 | 全角色评估 | All Roles |
| TDD开发 | 子代理并行 | Designer(设计) + Dev(测试+实现) + QA(审查) |

### 3. 质量门禁（Superpowers 增强版）

每个节点设置质量检查点，包含Superpowers验证要求：

```
Analyze节点检查点：
- [ ] 需求规格说明书完整
- [ ] 用户场景清晰
- [ ] 微信能力需求明确
- [ ] ⚡ 验收标准可用于TDD（可测试、可量化）

Architect节点检查点：
- [ ] PRD文档通过评审
- [ ] 技术方案确定（原生/Taro/uni-app）
- [ ] 分包策略制定
- [ ] ⚡ 实施计划包含每个Task的TDD要求
- [ ] ⚡ Task拆解到2-5min级别，含测试依赖关系

Assemble节点检查点：
- [ ] 设计稿符合微信设计规范
- [ ] 核心功能实现
- [ ] 微信能力集成完成
- [ ] 分包加载配置正确
- [ ] ⚡ 单元测试通过（每个页面/组件有对应测试）
- [ ] ⚡ 代码通过审查（ESLint + TypeScript检查）
- [ ] ⚡ TDD三阶段完成（RED → GREEN → REFACTOR）

Automate节点检查点：
- [ ] 真机测试通过
- [ ] 性能测试达标（首屏<2s）
- [ ] 包体积检查通过（主包<2MB）
- [ ] 微信审核规范检查通过
- [ ] ⚡ 双维度代码审查通过（功能维度 + 微信规范维度）
- [ ] ⚡ 完成前验证通过（verification-before-completion）
- [ ] ⚡ 测试覆盖率 > 80%

Assess节点检查点：
- [ ] 质量评估通过
- [ ] 用户验收通过
- [ ] 微信审核预检通过
- [ ] ⚡ 真机测试通过（多机型覆盖）
- [ ] ⚡ 微信审核规范检查通过（隐私协议、用户协议、类目合规）
```

## Superpowers 执行模式

### 模式一：TDD 开发模式（小程序专项）

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📱 微信小程序 - TDD 开发模式
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

【前端 TDD 流程 - 小程序组件】

  Task: 实现商品列表组件

  Step 1: RED - 编写失败的测试
  ┌─────────────────────────────────────────────┐
  // src/components/goods-list/__tests__/
  // goods-list.test.ts
  describe('GoodsList', () => {
    it('should render goods list correctly', () => {
      const goods = [
        { id: 1, name: '商品A', price: 99.9 },
        { id: 2, name: '商品B', price: 199.9 }
      ]
      // 验证组件正确渲染商品列表
    })

    it('should emit event when goods clicked', () => {
      // 验证点击商品触发正确的自定义事件
    })

    it('should show empty state when list is empty', () => {
      // 验证空列表展示空状态
    })
  })
  └─────────────────────────────────────────────
  → 运行 npx vitest → ❌ 失败（组件不存在）

  Step 2: GREEN - 编写最少实现
  ┌─────────────────────────────────────────────
  <!-- src/components/goods-list/goods-list.wxml -->
  <view class="goods-list">
    <view wx:for="{{goods}}" wx:key="id"
          class="goods-item"
          bindtap="onGoodsTap"
          data-id="{{item.id}}">
      <text>{{item.name}}</text>
      <text class="price">¥{{item.price}}</text>
    </view>
    <view wx:if="{{goods.length === 0}}" class="empty">
      暂无商品
    </view>
  </view>
  └─────────────────────────────────────────────
  → 运行 npx vitest → ✅ 通过

  Step 3: REFACTOR - 重构优化
  ├── 提取价格格式化为独立工具函数
  ├── 添加下拉刷新和上拉加载
  └── 运行 npx vitest → ✅ 全部通过

【微信能力集成 TDD】

  Task: 实现微信登录功能

  Step 1: RED - 编写失败的测试
  ┌─────────────────────────────────────────────
  // src/utils/__tests__/auth.test.ts
  describe('WeChat Auth', () => {
    it('should call wx.login and get openid', async () => {
      // 验证登录流程正确调用微信API
    })

    it('should handle login failure gracefully', async () => {
      // 验证登录失败时的错误处理
    })
  })
  └─────────────────────────────────────────────
  → 运行 npx vitest → ❌ 失败

  Step 2: GREEN - 编写最少实现
  ┌─────────────────────────────────────────────
  // src/utils/auth.ts
  export async function wxLogin(): Promise<string> {
    const { code } = await wx.login()
    const res = await request('/api/login', { code })
    return res.openid
  }
  └─────────────────────────────────────────────
  → 运行 npx vitest → ✅ 通过

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 模式二：子代理并行开发模式

```
主代理协调者
    │
    ├── 子代理 A: 页面开发（TDD）
    │   ├── pages/index/ (首页)
    │   ├── pages/goods/ (商品页)
    │   └── pages/cart/ (购物车)
    │
    ├── 子代理 B: 组件开发（TDD）
    │   ├── components/goods-list/
    │   ├── components/order-card/
    │   └── components/search-bar/
    │
    ├── 子代理 C: 工具与服务开发（TDD）
    │   ├── utils/request.ts
    │   ├── utils/auth.ts
    │   └── services/order.ts
    │
    └── 子代理 D: 联调与审查（等 A、B、C 完成）
        ├── Integration Tests
        ├── 代码审查
        └── 性能优化
```

### 模式三：系统化调试模式（4步法）

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔍 微信小程序 - 系统化调试 4步法
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

【Step 1】问题明确
  ├── 复现步骤记录
  ├── 预期行为 vs 实际行为
  ├── 真机 vs 开发者工具差异
  └── 错误日志收集（wx.getRealtimeLogManager）

【Step 2】假设生成
  ├── 列出所有可能原因（按概率排序）
  ├── 微信API兼容性问题？
  ├── 分包路径配置问题？
  ├── 样式兼容性问题（rpx vs px）？
  └── 生命周期时序问题？

【Step 3】假设验证
  ├── 逐个验证假设
  ├── 使用开发者工具调试面板
  ├── 使用 vConsole 排查
  └── 真机远程调试

【Step 4】修复与预防
  ├── 实施修复
  ├── 编写回归测试（防止再犯）
  ├── 更新相关文档
  └── 运行全量测试确认无副作用

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

## 工作流程

### 完整项目启动流程

```
用户："我要做一个微信小程序商城"

系统自动执行：
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎯 任务识别：新项目启动 → 启动完整6A工作流（Superpowers增强）

📋 执行计划：

1️⃣  Analyze（需求分析师）⚡Brainstorming
    ├─ 任务：需求分析与微信能力探索
    ├─ 输出：需求规格说明书.md
    ├─ ⚡ 验证：验收标准可测试、可量化
    └─ 【等待人工决策】
        ↓ 用户确认
        
2️⃣  Architect（产品经理）⚡Writing-Plans
    ├─ 任务：产品架构设计与实施计划
    ├─ 输出：PRD文档.md、技术方案.md、实施计划.md
    ├─ ⚡ 验证：Task拆解含TDD要求
    └─ 【等待人工决策】
        ↓ 用户确认
        
3️⃣  Assemble（UI/UX设计师 + 小程序开发工程师）⚡TDD+Debug
    ├─ 任务：界面设计与TDD功能开发
    ├─ 输出：设计稿、可运行代码、测试代码
    ├─ ⚡ 验证：单元测试通过 + 代码审查通过
    └─ 【等待人工决策】
        ↓ 用户确认
        
4️⃣  Automate（质量QA）⚡Review+Verify
    ├─ 任务：测试、代码审查与完成前验证
    ├─ 输出：测试计划.md、测试报告.md、审查报告.md
    ├─ ⚡ 验证：双维度审查通过 + 完成前验证通过
    └─ 【等待人工决策】
        ↓ 用户确认
        
5️⃣  Assess（全角色）⚡Audit
    ├─ 任务：质量评估、真机验证、审核预检
    ├─ 输出：质量评估报告.md
    ├─ ⚡ 验证：真机测试通过 + 微信审核规范通过
    └─ 【等待人工决策】
        ↓ 用户确认
        
6️⃣  Advance（产品经理）⚡复盘
    ├─ 任务：项目复盘与优化
    └─ 输出：项目复盘报告.md

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 单节点快速响应

```
用户："帮我设计小程序的界面"

系统自动执行：
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎯 任务识别：界面设计 → 调用 UI/UX设计师

👤 执行角色：@UI/UX设计师 ⚡brainstorming + ⚡verification-before-completion

📋 执行流程：
1. 确认设计需求
2. 输出设计稿和原型
3. ⚡ 完成前验证（设计规范检查）
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
Designer + Dev 同时工作（⚡Subagent模式）
    ↓
合并成果
    ↓
QA测试（⚡Review模式）
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
从 Assemble 开始（⚡TDD模式）
```

## 决策点处理

### 每个节点的决策流程

```
节点执行完成
    ↓
⚡ Superpowers验证（测试通过？审查通过？）
    ↓
展示成果物
    ↓
【等待用户决策】
    ├─ 用户确认通过 → 进入下一阶段
    ├─ 用户要求修改 → 返回当前节点修改
    └─ 用户要求回溯 → 回到指定节点
```

### 决策选项

| 用户选择 | 系统动作 |
|----------|----------|
| "确认通过" | 标记当前节点完成，进入下一阶段 |
| "需要修改" | 记录修改需求，返回当前节点重新执行 |
| "回到XX节点" | 回溯到指定节点，重新执行后续流程 |
| "暂停项目" | 保存当前状态，等待用户恢复 |

### 人工决策检查清单（Superpowers 增强）

每个节点完成后，用户决策前系统自动执行以下验证：

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 人工决策前 - Superpowers 自动验证清单
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

【Analyze 节点验证】
- [ ] 需求是否有明确验收标准？
- [ ] 验收标准是否可测试、可量化？
- [ ] 微信能力需求是否已列出？

【Architect 节点验证】
- [ ] 实施计划是否包含每个Task的TDD要求？
- [ ] 技术方案是否考虑分包策略？
- [ ] Task依赖关系是否明确？

【Assemble 节点验证】
- [ ] 所有单元测试是否通过？
- [ ] ESLint检查是否无error/warning？
- [ ] TypeScript类型检查是否通过？
- [ ] 测试覆盖率是否 > 80%？
- [ ] TDD三阶段是否完整（RED/GREEN/REFACTOR）？

【Automate 节点验证】
- [ ] 代码审查是否双维度通过？
- [ ] 完成前验证是否通过？
- [ ] 真机测试是否通过？
- [ ] 包体积是否 < 2MB（主包）？
- [ ] 首屏加载是否 < 2s？

【Assess 节点验证】
- [ ] 多机型真机测试是否通过？
- [ ] 微信审核规范检查是否通过？
- [ ] 隐私协议和用户协议是否完整？
- [ ] 应用类目是否合规？

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
验证全部通过 → 展示给用户决策
验证有失败项 → 阻止进入下一阶段，返回当前节点修复
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

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
version: "2.0.0"
date: "2026-04-07"
author: "数字员工名称"
node: "Analyze"
status: "completed"
superpowers_skill: "brainstorming"
---
```

## 异常处理

### 常见异常场景

| 异常 | 处理策略 |
|------|----------|
| 角色执行失败 | 尝试重试3次，失败后升级至用户决策 |
| 用户长时间未响应 | 发送提醒，24小时后暂停项目 |
| 需求频繁变更 | 建议用户完成当前节点后再变更 |
| 质量检查不通过 | 返回当前节点重新执行 |
| 跨角色冲突 | 召开协调会议，由PM决策 |
| 单元测试不通过 | 阻止进入下一阶段，回到Assemble修复 |
| 代码审查有Critical问题 | 阻止进入下一阶段，回到Assemble修复 |
| 真机测试不通过 | 阻止进入Assess，回到Assemble修复 |

### 升级机制

```
节点执行遇到问题
    ↓
⚡ 尝试自动解决（systematic-debugging 4步法）
    ↓
无法解决 → 升级至产品经理
    ↓
仍无法解决 → 升级至用户决策
    ↓
记录问题 → 进入Advance复盘
```

## 反模式警告

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🚫 微信小程序开发 - 反模式警告（Superpowers）
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

❌ 写完组件再补测试
   ✅ 正确：先写 .test.ts，再写 .vue/.wxml

❌ 不做分包，所有页面塞进主包
   ✅ 正确：主包 < 2MB，按功能模块分包

❌ 微信API直接裸调用，不做封装
   ✅ 正确：封装 Service 层，方便测试 mock

❌ 只在开发者工具测试，不上真机
   ✅ 正确：开发者工具 + 真机双环境测试

❌ 跳过Automate节点直接提交审核
   ✅ 正确：测试通过 + 审查通过 + 审核预检通过

❌ ESLint有warning忽略不管
   ✅ 正确：ESLint零error零warning才能提交

❌ 需求变更直接改代码，不回溯流程
   ✅ 正确：需求变更回到Analyze，重新走6A

❌ 性能问题等上线再优化
   ✅ 正确：Assemble阶段就考虑性能（分包、懒加载、缓存）

❌ 不写审查报告直接进入Assess
   ✅ 正确：Automate必须输出审查报告

❌ 发布前不做微信审核规范预检
   ✅ 正确：Assess阶段必须完成审核预检

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

## 最佳实践

1. **明确目标**：项目启动前明确项目目标和范围
2. **及时决策**：每个节点完成后及时确认或反馈
3. **文档同步**：代码变更同步更新文档
4. **质量优先**：不跳过质量检查点
5. **持续沟通**：保持与用户的持续沟通
6. **测试先行**：遵循TDD三阶段（RED → GREEN → REFACTOR）
7. **小程序专项**：开发时考虑分包策略、包体积、真机兼容性
8. **审查必做**：代码审查双维度（功能 + 微信规范）不可跳过
9. **证据说话**：测试通过 + 审查通过 = 功能完成，不接受口头保证
10. **复盘沉淀**：每个项目完成后进入Advance，沉淀最佳实践

## 使用示例

### 示例1：启动完整项目

```
用户：我要做一个微信小程序商城

协调系统：
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎯 任务识别：新项目启动（Superpowers增强模式）

我将协调以下数字员工为您完成项目：
1. 需求分析师 ⚡brainstorming - 分析需求
2. 产品经理 ⚡writing-plans - 设计产品方案
3. UI/UX设计师 ⚡brainstorming+verify - 设计界面
4. 小程序开发工程师 ⚡TDD+debug - 开发功能
5. 质量QA ⚡review+verify - 测试验收

预计执行6个节点，每个节点完成后需要您确认。
每个节点将执行Superpowers验证（测试+审查）。
是否开始？
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 示例2：需求变更

```
用户：需要增加微信支付功能

协调系统：
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔄 需求变更检测

当前节点：Assemble（开发中）
建议：回到 Architect 节点重新评估

影响范围：
- PRD文档需要更新
- 技术方案需要调整（支付接口）
- 可能需要申请商户号
- ⚡ 现有测试用例需要更新

是否确认回溯到 Architect 节点？
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 示例3：节点完成确认

```
协调系统：
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ Assemble 节点完成

📄 输出物：
   - 设计稿
   - 源代码
   - 测试代码

📋 检查清单：
   - [x] 设计稿符合微信设计规范
   - [x] 核心功能实现
   - [x] 微信能力集成完成
   - [x] 分包加载配置正确
   - [x] ⚡ 单元测试通过（覆盖率 85%）
   - [x] ⚡ 代码审查通过（0 error, 0 warning）
   - [x] ⚡ TDD三阶段完成

【等待人工决策】
请选择：
1. 确认通过，进入 Automate 节点
2. 需要修改，返回 Assemble 节点
3. 查看详细文档
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

**版本**：v2.0  
**更新日期**：2026-04-07  
**核心理念**：Superpowers 四原则（TDD、系统性、简化、证据）  
**数字员工数量**：5个（BA、PM、Designer、Dev、QA）  
**Superpowers 技能**：14+ 个核心技能 + 小程序专项技能  
**关联文档**：
- 《wechat-miniapp-project-rules.md》
- 各数字员工Skill文档
