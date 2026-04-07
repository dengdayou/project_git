# 微信小程序开发项目规则

> 版本：v2.0 | 日期：2026-04-07 | 更新内容：**集成Superpowers理念，引入TDD、子代理开发、任务拆分、代码审查等机制**
> 工作流：6A（Analyze → Architect → Assemble → Automate → Assess → Advance）
> 核心框架：Superpowers 四原则

---

## 规则概述

本规则定义了微信小程序开发的 **6A + Superpowers 增强工作流** 执行规范，适配原生小程序、Taro、uni-app等技术栈。

本版本深度融合 **Superpowers 核心理念**，让微信小程序开发遵循结构化、可验证、高质量的工程标准。

**核心原则**：
1. **用户体验优先**：快速加载、流畅交互、优雅降级
2. **微信生态融合**：充分利用微信登录、支付、分享等能力
3. **性能优化**：包体积控制、渲染优化、数据缓存
4. **开发即文档**：代码与文档同步编写

---

## Superpowers 核心原则（四原则）

| 原则 | 说明 | 在小程序开发中的体现 |
|------|------|---------------------|
| **测试驱动开发 (TDD)** | 先写测试，再写实现 | 小程序单元测试先行，Jest/miniprogram-simulate 同步 |
| **系统性优于临时方案** | 遵循流程，不靠猜测 | 强制执行 6A 工作流 + 小程序开发规范 |
| **复杂性降低 (YAGNI)** | 简化是首要目标 | MVP功能优先，避免过度设计 |
| **证据优于声明** | 验证后才算完成 | 测试通过 + 审查通过 = 功能完成 |

---

## 数字员工技能矩阵（微信小程序 + Superpowers）

```
┌─────────────────────────────────────────────────────────────┐
│      微信小程序开发技能树（Superpowers 增强）                │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  【流程类技能】                                              │
│  ├── brainstorming        需求澄清与架构探索                  │
│  ├── writing-plans         任务拆解与实施计划                 │
│  ├── test-driven-development  测试驱动开发(Jest+模拟器)     │
│  ├── systematic-debugging  系统化调试(4步法)                │
│  └── verification-before-completion  完成前验证             │
│                                                             │
│  【小程序专项技能】                                          │
│  ├── miniprogram-page-dev    小程序页面开发(TDD)            │
│  ├── miniprogram-component   小程序组件开发(TDD)            │
│  ├── wechat-api-integration  微信能力集成(TDD)              │
│  ├── subpackage-optimization 分包加载优化                   │
│  └── review-guidelines-check 审核规范检查                   │
│                                                             │
│  【协作类技能】                                              │
│  ├── subagent-driven-development  子代理并行开发            │
│  ├── requesting-code-review       代码审查(JS+WXML+WXSS)   │
│  └── finishing-a-development-branch  分支收尾              │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 6A 工作流定义（Superpowers 增强版）

```
┌─────────────────────────────────────────────────────────────────────────┐
│          6A 工作流 v2.0 - 微信小程序开发（Superpowers 增强）             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  Node 1        Node 2        Node 3        Node 4        Node 5   Node6│
│  Analyze  →   Architect  →   Assemble  →   Automate  →   Assess  →Adv │
│  需求分析      产品架构       设计开发       自动化测试      质量评估  优化│
│    ↓              ↓              ↓              ↓              ↓       ↓ │
│  需求分析师    产品经理      UI/UX设计师    质量QA        全角色    PM  │
│                              小程序开发工程师                            │
│  ⚡Brainstorm  ⚡Plan      ⚡TDD+Subagent  ⚡Test+Review ⚡Audit  ⚡复盘│
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

⚡ = Superpowers 技能注入点
```

### 各节点核心职责（增强版）

| 节点 | 角色 | Superpowers 技能 | 核心任务 | 文档输出 |
|------|------|------------------|----------|----------|
| **Analyze** | 需求分析师 | `brainstorming` | 需求澄清、小程序生态特性分析 | 需求规格说明书.md |
| **Architect** | 产品经理 | `writing-plans` | PRD、技术选型、任务拆解 | PRD文档.md、技术方案.md、**实施计划.md** |
| **Assemble** | UI/UX设计师<br>+ 小程序开发工程师 | `test-driven-development`<br>`subagent-driven-development`<br>`miniprogram-page-dev`<br>`miniprogram-component`<br>`systematic-debugging` | 设计稿、TDD开发、子代理并行 | 设计稿、原型、功能代码、**测试代码** |
| **Automate** | 质量QA | `requesting-code-review`<br>`review-guidelines-check`<br>`verification-before-completion` | 测试执行、审核规范检查、代码审查 | 测试计划.md、测试报告.md、**审查报告.md** |
| **Assess** | 全角色 | `finishing-a-development-branch`<br>`subpackage-optimization` | 质量评估、性能测试、分包验证 | 质量评估报告.md |
| **Advance** | 产品经理 | 复盘优化 | 项目复盘、知识沉淀 | 项目复盘报告.md |

---

## 技术栈规范

### 推荐技术栈

| 技术方案 | 适用场景 | 优点 | 缺点 |
|----------|----------|------|------|
| **原生微信小程序** | 简单项目、快速上线 | 官方支持、性能最好 | 代码复用性差 |
| **Taro + React** | 复杂项目、跨平台需求 | React生态、可转H5/APP | 学习成本 |
| **uni-app + Vue** | 跨平台需求、Vue开发者 | Vue生态、跨平台能力强 | 性能略低 |
| **kbone** | 已有Web项目迁移 | 可复用Web代码 | 性能一般 |

### 默认技术栈（推荐）

```
框架选择：原生微信小程序 / Taro 3.x / uni-app
状态管理：MobX / Redux / Vuex / Pinia
UI组件：Vant Weapp / Taro UI / uView
样式方案：SCSS / Less
构建工具：微信开发者工具 / Webpack / Vite
云开发：微信云开发 / 自有后端

【Superpowers 新增】
测试框架：Jest + miniprogram-simulate
覆盖率工具：Jest --coverage / istanbul
代码检查：ESLint + Stylelint
审核检查：miniprogram-ci + 自定义审核规则
```

---

## 项目结构规范（Superpowers 增强版）

### 原生小程序结构

```
miniprogram/
├── app.js                    # 小程序入口
├── app.json                  # 全局配置
├── app.wxss                  # 全局样式
├── project.config.json       # 项目配置
├── sitemap.json              # 搜索配置
├── pages/                    # 页面目录
│   ├── index/
│   │   ├── index.js
│   │   ├── index.json
│   │   ├── index.wxml
│   │   ├── index.wxss
│   │   └── __tests__/        # ⭐ 页面单元测试（新增）
│   │       └── index.test.js
│   └── logs/
├── components/               # 组件目录
│   └── custom-component/
│       ├── custom-component.js
│       ├── custom-component.json
│       ├── custom-component.wxml
│       ├── custom-component.wxss
│       └── __tests__/        # ⭐ 组件单元测试（新增）
│           └── custom-component.test.js
├── utils/                    # 工具函数
│   ├── util.js
│   ├── api.js
│   └── __tests__/            # ⭐ 工具函数单元测试（新增）
│       └── util.test.js
├── services/                 # 服务层
│   ├── request.js
│   ├── storage.js
│   └── __tests__/            # ⭐ 服务层单元测试（新增）
│       └── request.test.js
├── stores/                   # 状态管理
│   └── __tests__/            # ⭐ Store 单元测试（新增）
├── constants/                # 常量定义
├── styles/                   # 公共样式
│   └── common.wxss
├── images/                   # 图片资源
├── docs/                     # 项目文档
│   ├── 01-需求规格说明书.md
│   ├── 02-PRD文档.md
│   ├── 03-技术方案.md
│   ├── 04-实施计划.md        # ⭐ 新增（Writing-Plans 输出）
│   ├── 05-设计稿/
│   ├── 06-测试计划.md
│   ├── 07-审查报告.md        # ⭐ 新增（Code Review 输出）
│   └── 08-项目复盘.md
├── tests/                    # ⭐ 测试文件（增强）
│   ├── unit/                 # 单元测试
│   │   ├── pages/            # 页面测试
│   │   ├── components/       # 组件测试
│   │   └── utils/            # 工具函数测试
│   ├── integration/          # 集成测试
│   │   └── wechat-api/       # 微信API集成测试
│   └── e2e/                  # 端到端测试（miniprogram-automator）
├── jest.config.js            # ⭐ Jest 配置（新增）
└── package.json
```

### Taro项目结构

```
taro-miniapp/
├── config/                   # 配置目录
│   ├── index.js
│   └── dev.js
├── src/                      # 源码目录
│   ├── app.config.ts         # 全局配置
│   ├── app.tsx               # 入口组件
│   ├── app.scss              # 全局样式
│   ├── pages/                # 页面目录
│   │   └── index/
│   │       ├── index.config.ts
│   │       ├── index.tsx
│   │       ├── index.scss
│   │       └── __tests__/    # ⭐ 页面单元测试（新增）
│   │           └── index.test.tsx
│   ├── components/           # 组件目录
│   │   └── __tests__/        # ⭐ 组件单元测试（新增）
│   ├── utils/                # 工具函数
│   │   └── __tests__/        # ⭐ 工具函数单元测试（新增）
│   ├── services/             # 服务层
│   │   └── __tests__/        # ⭐ 服务层单元测试（新增）
│   ├── stores/               # 状态管理
│   │   └── __tests__/        # ⭐ Store 单元测试（新增）
│   └── constants/            # 常量定义
├── types/                    # 类型定义
├── docs/                     # 项目文档
│   ├── 04-实施计划.md        # ⭐ 新增
│   └── 07-审查报告.md        # ⭐ 新增
├── tests/                    # 测试文件（增强）
│   ├── unit/
│   ├── integration/
│   └── e2e/
├── jest.config.ts            # ⭐ Jest 配置（新增）
└── package.json
```

---

## 数字员工角色与任务匹配规则（Superpowers 增强版）

### 1. 需求分析师 (BA) ⚡ Brainstormer

**Superpowers 技能**：`brainstorming`

**触发关键词：**
- "分析需求"、"需求分析"、"调研"
- "用户画像"、"业务场景"
- "可行性分析"、"需求文档"
- "新项目启动"、"需求变更"

**任务特征：**
- 输入：业务诉求、用户痛点、市场机会
- 输出：需求规格说明书
- 节点：Analyze

**小程序特殊关注点（Brainstorming 阶段必须确认）**：
- 微信生态能力需求（登录、支付、分享、订阅消息）
- 用户授权场景（哪些信息需要授权）
- 性能要求（首屏加载时间、包体积限制）
- 分享传播场景（分享卡片、海报生成）
- 微信审核合规性要求
- 离线使用场景
- 云开发 vs 自有后端决策
- 分包加载策略初步评估

---

### 2. 产品经理 (PM) ⚡ Planner

**Superpowers 技能**：`writing-plans`

**触发关键词：**
- "PRD"、"产品文档"、"产品方案"
- "功能设计"、"功能规划"
- "优先级"、"路线图"
- "竞品分析"、"验收标准"

**任务特征：**
- 输入：需求规格说明书
- 输出：PRD文档、**实施计划**、技术选型建议
- 节点：Architect / Advance

**小程序特殊关注点（Planning 阶段必须规划）**：

**Writing-Plans 输出示例**：
```markdown
## 实施计划：[小程序名称]

### Phase 1: 基础设施搭建
┌────────┬────────────────────┬────────┬──────┐
│ Task ID │ 任务名             │ 时间   │ 依赖 │
├────────┼────────────────────┼────────┼──────┤
│ T-001  │ 小程序项目初始化    │ 3min   │ 无   │
│ T-002  │ 基础页面骨架搭建    │ 5min   │ T001 │
│ T-003  │ 网络请求封装        │ 5min   │ T001 │
│ T-004  │ 测试环境配置        │ 5min   │ T002 │
└────────┴────────────────────┴────────┴──────┘

### Phase 2: 核心功能开发
┌────────┬────────────────────┬────────┬──────┐
│ Task ID │ 任务名             │ 时间   │ 依赖 │
├────────┼────────────────────┼────────┼──────┤
│ T-005  │ 微信登录能力集成    │ 10min  │ T003 │
│ T-006  │ 首页页面开发        │ 15min  │ T002 │
│ T-007  │ 列表组件开发        │ 10min  │ T002 │
│ T-008  │ 详情页开发          │ 10min  │ T007 │
│ T-009  │ 分包配置            │ 5min   │ T006 │
└────────┴────────────────────┴────────┴──────┘

每个 Task 必须包含：
- TDD 要求（RED/GREEN/REFACTOR）
- Jest 单元测试用例
```

**小程序技术决策点**：
- 技术选型决策（原生 vs Taro vs uni-app）
- 微信能力集成方案（登录、支付、分享、订阅消息）
- 分包加载策略（主包<2MB，按功能分包）
- 审核规范合规性检查清单
- 云开发 vs 自有后端架构决策
- 版本更新与发布策略

---

### 3. UI/UX设计师 + 小程序开发工程师 (Designer + Dev) ⚡ TDD Developer

**Superpowers 技能**：
- `test-driven-development`（核心）
- `subagent-driven-development`
- `systematic-debugging`
- `miniprogram-page-dev`（小程序专项）
- `miniprogram-component`（小程序专项）
- `wechat-api-integration`（小程序专项）

**触发关键词：**
- "设计"、"界面"、"UI"、"UX"
- "原型"、"线框图"、"视觉稿"
- "开发"、"编码"、"实现"
- "小程序"、"页面"、"组件"

**任务特征：**
- 输入：PRD文档、**实施计划**
- 输出：设计稿、可运行代码、**测试代码**
- 节点：Assemble

**TDD 开发工作流（小程序专项）**：

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📱 微信小程序 - TDD 开发模式
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

【小程序页面 TDD 流程】

  Task: 实现商品列表页面

  Step 1: RED - 编写失败的 Jest 测试
  ┌─────────────────────────────────────────────┐
  // pages/goods-list/__tests__/index.test.js
  describe('goods-list page', () => {
      it('should load goods data on load', async () => {
          const page = await createPage()
          await page.onLoad()
          expect(page.data.list.length).toBeGreaterThan(0)
          expect(page.data.loading).toBe(false)
      })

      it('should pull down to refresh', async () => {
          const page = await createPage()
          await page.onPullDownRefresh()
          expect(page.data.list).toEqual([])
          // 验证 loadData 被调用
      })

      it('should load more on reach bottom', async () => {
          const page = await createPage()
          page.data.hasMore = true
          await page.onReachBottom()
          expect(page.data.list.length).toBeGreaterThan(0)
      })
  })
  └─────────────────────────────────────────────
  → 运行 npx jest → ❌ 失败（页面不存在）

  Step 2: GREEN - 编写最少实现
  ┌─────────────────────────────────────────────
  // pages/goods-list/index.js
  Page({
      data: { list: [], loading: false, hasMore: true },
      onLoad() { this.loadData() },
      onPullDownRefresh() { this.refreshData() },
      onReachBottom() { this.loadMore() },
      async loadData() { ... }
  })
  └─────────────────────────────────────────────
  → 运行 npx jest → ✅ 通过

  Step 3: REFACTOR - 重构优化
  ├── 提取公共数据加载逻辑
  ├── 添加错误处理
  └── 运行 npx jest → ✅ 全部通过

【小程序组件 TDD 流程】

  Task: 实现 custom-list 组件

  Step 1: RED - 编写失败的组件测试
  ┌─────────────────────────────────────────────
  // components/custom-list/__tests__/custom-list.test.js
  describe('custom-list component', () => {
      it('should render list items correctly', async () => {
          const comp = await createComponent({
              properties: { list: mockData }
          })
          const items = comp.dom.querySelectorAll('.list-item')
          expect(items.length).toBe(mockData.length)
      })

      it('should trigger itemtap event on click', async () => {
          const comp = await createComponent({
              properties: { list: mockData }
          })
          comp.dom.querySelectorAll('.list-item')[0].triggerEvent('tap')
          expect(comp.triggerEvent).toHaveBeenCalledWith('itemtap', expect.any(Object))
      })
  })
  └─────────────────────────────────────────────
  → 运行 npx jest → ❌ 失败

  Step 2: GREEN - 编写最少实现
  → 运行 npx jest → ✅ 通过

  Step 3: REFACTOR - 重构优化
  └── 运行 npx jest + ESLint → ✅ 全部通过

【微信能力集成 TDD】

  Task: 验证微信登录流程

  Step 1: 编写集成测试
  ┌─────────────────────────────────────────────
  // tests/integration/wechat-api/login.test.js
  describe('WeChat Login Integration', () => {
      it('should complete full login flow', async () => {
          // 1. mock wx.login
          // 2. 验证后端接口被正确调用
          // 3. 验证 token 被正确存储
          // 4. 验证页面状态正确更新
      })
  })
  └─────────────────────────────────────────────

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**小程序特殊关注点（Assemble 阶段）**：
- 适配不同屏幕尺寸（rpx响应式设计）
- 微信设计规范遵循
- 性能优化（图片懒加载、虚拟列表）
- 微信组件使用（swiper、scroll-view等）
- **每个 Page 都有对应的 Jest 单元测试**
- **每个 Component 都有对应的 Jest 单元测试**
- **每个 Service/Util 都有对应的 Jest 单元测试**

**子代理并行开发模式（小程序）**：

```
主代理协调者
    │
    ├── 子代理 A: 核心页面开发
    │   ├── pages/index/ (TDD)
    │   ├── pages/detail/ (TDD)
    │   └── pages/mine/ (TDD)
    │
    ├── 子代理 B: 公共组件开发
    │   ├── components/custom-list/ (TDD)
    │   ├── components/custom-card/ (TDD)
    │   └── components/custom-form/ (TDD)
    │
    └── 子代理 C: 服务层 + 微信能力集成（等 A、B 完成）
        ├── services/request.js (TDD)
        ├── services/storage.js (TDD)
        ├── utils/wechat.js (TDD)
        └── Integration Tests
```

---

### 4. 质量QA (QA) ⚡ Reviewer & Verifier

**Superpowers 技能**：
- `requesting-code-review`
- `review-guidelines-check`
- `verification-before-completion`

**触发关键词：**
- "测试"、"测试用例"、"测试计划"
- "质量"、"QA"、"验收"
- "缺陷"、"Bug"、"回归"
- "自动化测试"、"性能测试"

**任务特征：**
- 输入：PRD、设计稿、可运行版本、测试代码
- 输出：测试计划、测试报告、**审查报告**
- 节点：Automate

**小程序 QA 工作流（Superpowers 增强）**：

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔍 微信小程序 - Quality Assurance 模式
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

【Phase 1】双重代码审查

  维度A：JavaScript 逻辑审查
  ├── ESLint 通过无 error/warning？
  ├── Jest 单元测试全部通过？
  ├── 代码结构清晰？
  ├── 错误处理完善？
  └── 安全性检查（XSS、数据校验等）

  维度B：WXML/WXSS 审查
  ├── WXML 结构语义化？
  ├── WXSS 类名规范？
  ├── rpx 使用合理？
  ├── 无冗余嵌套？
  └── 样式复用性？

【Phase 2】微信审核规范检查
  ├── 用户隐私协议合规？
  ├── 用户授权使用合理？
  ├── 类目与功能匹配？
  ├── 禁止内容检查？
  └── 虚拟支付合规？

【Phase 3】兼容性与性能测试
  ├── 真机测试（iOS/Android 多机型）
  ├── 不同微信版本兼容性
  ├── 性能测试（首屏时间 < 2s）
  ├── 内存占用测试（< 300MB）
  └── 包体积检查（主包 < 2MB）

【Phase 4】完成前验证（Verification-Before-Completion）
  - [ ] 所有单元测试通过
  - [ ] 代码审查无 Critical 问题
  - [ ] 真机测试通过
  - [ ] 性能测试达标
  - [ ] 微信审核预检通过
  - [ ] 文档完整且准确

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**小程序特殊关注点（Automate 阶段）**：
- 真机兼容性测试（iOS/Android 多机型）
- 微信版本兼容性（基础库2.x+）
- 性能测试（首屏时间 < 2s，内存 < 300MB）
- 包体积检查（主包 < 2MB，总体积 < 20MB）
- 微信审核规范检查
- **单元测试覆盖率 > 80%**
- **代码审查已完成（双维度：JS + WXML/WXSS）**
- **完成前验证通过**

---

### 5. 全角色评估 (Assess) ⚡ Finishing & Verify

**Superpowers 技能**：
- `finishing-a-development-branch`
- `subpackage-optimization`

**触发关键词：**
- "评估"、"评审"、"质量检查"
- "发布前检查"、"上线前评估"
- "验收"、"签字"

**任务特征：**
- 输入：测试报告、可运行版本
- 输出：质量评估报告
- 节点：Assess

---

## 工作流执行规则（Superpowers 增强版）

### 规则0：Superpowers 四原则（最高优先级）

```
在任何时候，以下四条原则不可违反：

1. 测试驱动 (TDD)
   → 先写 Jest it() 测试，再写 Page/Component 实现
   → 违反时：立即停止，回到RED阶段

2. 系统性优先
   → 遵循 6A 工作流 + 小程序开发规范
   → 违反时：回退到被跳过的步骤

3. 简化为上 (YAGNI)
   → 只做当前需要的功能，MVP优先
   → 违反时：删除过度设计的部分

4. 证据说话
   → Jest 通过 + 审查通过 = 完成
   → 违反时：补充测试或修复审查问题
```

### 规则1：严格按照节点顺序执行

```
Analyze → Architect → Assemble → Automate → Assess → Advance
   ↓          ↓          ↓          ↓           ↓         ↓
 必须完成    必须完成    必须完成    必须完成     必须完成   必须完成
(Brainstorm)(Planning) (TDD)      (Review+Test) (Audit)   (复盘)
 才能进入    才能进入    才能进入    才能进入     才能进入   才能进入
 下一阶段
```

### 规则2：开发即文档原则（增强版）

**强制要求**：
1. **同步开发**：代码开发 + 测试编写 + 文档编写同步进行
2. **组件完成即测试完成**：每完成一个 Page/Component，对应的 Jest 测试必须同时完成
3. **功能调整即全量更新**：任何功能调整/新增，必须同步更新相关文档和相关测试
4. **质量门禁**：Assemble 节点必须通过 **Jest 测试 + ESLint 检查 + 代码审查** 才能进入 Automate

### 规则2.5：TDD 强制执行原则（小程序专项）

**小程序 TDD 要求**：
```
每个 Page 必须有对应的 __tests__/index.test.js
每个 Component 必须有对应的 __tests__/xxx.test.js
每个 Service/Util 必须有对应的 __tests__/xxx.test.js

开发顺序：
1. 编写 Jest 测试函数（describe/it/expect）
2. 运行 npx jest → 确认失败（RED）
3. 编写最少实现
4. 运行 npx jest → 确认通过（GREEN）
5. 运行 ESLint 检查
6. 重构优化（REFACTOR）
7. 再次运行 npx jest + ESLint → 确认全部通过
```

### 规则2.6：完成前验证（Verification-Before-Completion）

**Automate 节点必须通过的验证清单**：
```
- [ ] 所有 Jest 单元测试通过
- [ ] ESLint 检查通过（无 error）
- [ ] 代码审查双维度通过（JS + WXML/WXSS）
- [ ] 真机测试通过（至少2台设备）
- [ ] 微信审核预检通过
- [ ] 性能指标达标（首屏 < 2s，主包 < 2MB）
- [ ] 测试覆盖率 > 80%
- [ ] 文档完整且准确
```

### 规则3：每个节点必须人工决策 + 验证

每个节点完成后，必须等待用户确认才能进入下一阶段：

```
节点执行 → Superpowers验证 → 输出成果 → 【等待人工决策】 → 用户确认 → 进入下一阶段
                ↓                              ↓
         verification-before-completion    用户拒绝
                ↓                              ↓
         - Jest 通过？                    返回当前节点重新执行
         - ESLint 通过？
         - 审查通过？
         - 文档完整？
```

### 规则4：不允许跳过节点的场景

以下情况**严禁**跳过节点的：
1. 新项目必须从Analyze开始（启用 Brainstorming）
2. 有需求变更必须回到Analyze
3. 设计变更必须回到Assemble
4. **单元测试不通过必须回到Assemble**
5. **代码审查有 Critical 问题必须回到Assemble**
6. **微信审核预检不通过必须回到Assemble**

### 规则5：允许跳过节点的场景

以下情况**可以**直接调用特定角色：
1. 已有明确需求，直接调用产品经理（启用 Writing-Plans）
2. 已有 PRD + 实施计划，直接调用开发工程师（启用 TDD 模式）
3. 已有可运行版本，直接调用QA（启用 Code Review 模式）
4. 需要技术选型建议，直接调用产品经理

---

## 小程序开发规范

### 页面规范

```javascript
// pages/index/index.js
Page({
  data: {
    userInfo: null,
    list: [],
    loading: false,
    hasMore: true
  },

  onLoad(options) {
    this.loadData();
  },

  onShow() {
  },

  onHide() {
  },

  onUnload() {
  },

  onPullDownRefresh() {
    this.refreshData();
  },

  onReachBottom() {
    this.loadMore();
  },

  onShareAppMessage() {
    return {
      title: '分享标题',
      path: '/pages/index/index'
    };
  },

  async loadData() {
    this.setData({ loading: true });
    try {
      const res = await api.getList();
      this.setData({
        list: res.data,
        loading: false
      });
    } catch (error) {
      this.setData({ loading: false });
      wx.showToast({ title: '加载失败', icon: 'none' });
    }
  },

  handleTap(e) {
    const { id } = e.currentTarget.dataset;
    wx.navigateTo({
      url: `/pages/detail/detail?id=${id}`
    });
  }
});
```

### 组件规范

```javascript
// components/custom-list/custom-list.js
Component({
  properties: {
    list: {
      type: Array,
      value: []
    },
    loading: {
      type: Boolean,
      value: false
    }
  },

  data: {
  },

  lifetimes: {
    attached() {
    },
    detached() {
    }
  },

  pageLifetimes: {
    show() {
    }
  },

  methods: {
    handleItemTap(e) {
      const { index } = e.currentTarget.dataset;
      this.triggerEvent('itemtap', { index, item: this.data.list[index] });
    }
  }
});
```

```xml
<!-- components/custom-list/custom-list.wxml -->
<view class="custom-list">
  <view 
    class="list-item" 
    wx:for="{{list}}" 
    wx:key="id"
    data-index="{{index}}"
    bindtap="handleItemTap"
  >
    <image class="item-image" src="{{item.image}}" mode="aspectFill" lazy-load />
    <view class="item-content">
      <text class="item-title">{{item.title}}</text>
      <text class="item-desc">{{item.description}}</text>
    </view>
  </view>
  
  <view class="loading-tip" wx:if="{{loading}}">
    <text>加载中...</text>
  </view>
</view>
```

### 网络请求规范

```javascript
// services/request.js
const BASE_URL = 'https://api.example.com';

const request = (options) => {
  return new Promise((resolve, reject) => {
    wx.request({
      url: `${BASE_URL}${options.url}`,
      method: options.method || 'GET',
      data: options.data,
      header: {
        'Content-Type': 'application/json',
        'Authorization': wx.getStorageSync('token')
      },
      success: (res) => {
        if (res.statusCode === 200) {
          resolve(res.data);
        } else if (res.statusCode === 401) {
          wx.navigateTo({ url: '/pages/login/login' });
          reject(new Error('登录已过期'));
        } else {
          reject(new Error(res.data.message || '请求失败'));
        }
      },
      fail: (err) => {
        reject(new Error('网络请求失败'));
      }
    });
  });
};

const api = {
  getUserInfo: () => request({ url: '/user/info' }),
  getList: (params) => request({ url: '/list', data: params }),
  postForm: (data) => request({ url: '/form', method: 'POST', data })
};

module.exports = { request, api };
```

### 状态管理规范（使用MobX）

```javascript
// stores/userStore.js
import { observable, action } from 'mobx-miniprogram';

export const userStore = observable({
  userInfo: null,
  isLogin: false,

  get userName() {
    return this.userInfo ? this.userInfo.nickName : '';
  },

  setUserInfo: action(function(info) {
    this.userInfo = info;
    this.isLogin = true;
    wx.setStorageSync('userInfo', info);
  }),

  logout: action(function() {
    this.userInfo = null;
    this.isLogin = false;
    wx.removeStorageSync('userInfo');
    wx.removeStorageSync('token');
  })
});
```

### 微信能力封装

```javascript
// utils/wechat.js
const wxLogin = () => {
  return new Promise((resolve, reject) => {
    wx.login({
      success: (res) => {
        if (res.code) {
          resolve(res.code);
        } else {
          reject(new Error('登录失败'));
        }
      },
      fail: reject
    });
  });
};

const getUserProfile = () => {
  return new Promise((resolve, reject) => {
    wx.getUserProfile({
      desc: '用于完善用户资料',
      success: resolve,
      fail: reject
    });
  });
};

const wxPay = (payment) => {
  return new Promise((resolve, reject) => {
    wx.requestPayment({
      ...payment,
      success: resolve,
      fail: reject
    });
  });
};

const chooseImage = (count = 1) => {
  return new Promise((resolve, reject) => {
    wx.chooseMedia({
      count,
      mediaType: ['image'],
      sourceType: ['album', 'camera'],
      success: resolve,
      fail: reject
    });
  });
};

module.exports = {
  wxLogin,
  getUserProfile,
  wxPay,
  chooseImage
};
```

---

## 性能优化规范

### 1. 包体积优化

```json
// app.json
{
  "pages": [
    "pages/index/index",
    "pages/mine/mine"
  ],
  "subpackages": [
    {
      "root": "packageA",
      "pages": [
        "pages/detail/detail",
        "pages/list/list"
      ]
    },
    {
      "root": "packageB",
      "pages": [
        "pages/settings/settings"
      ]
    }
  ],
  "preloadRule": {
    "pages/index/index": {
      "network": "all",
      "packages": ["packageA"]
    }
  }
}
```

### 2. 图片优化

```xml
<image src="{{item.image}}" lazy-load mode="aspectFill" />

<image src="{{item.image}}?imageView2/1/w/200/h/200" />
```

### 3. 列表优化

```xml
<recycle-view batch="{{batchSetRecycleData}}" id="recycleId">
  <view slot="item" class="item" wx:for="{{recycleList}}" wx:key="id">
    <image src="{{item.image}}" lazy-load />
    <text>{{item.title}}</text>
  </view>
</recycle-view>
```

### 4. 数据缓存

```javascript
Page({
  data: {
    list: []
  },

  onLoad() {
    const cached = wx.getStorageSync('list_cache');
    if (cached) {
      this.setData({ list: cached });
    }
    this.loadData();
  },

  async loadData() {
    const res = await api.getList();
    this.setData({ list: res.data });
    wx.setStorageSync('list_cache', res.data);
  }
});
```

---

## 质量门禁标准（Superpowers 增强版）

### Assemble节点检查清单

- [ ] 代码通过 ESLint 检查（无 error/warning）
- [ ] **单元测试通过（Jest）**
- [ ] **每个 Page 有对应的测试文件**
- [ ] **每个 Component 有对应的测试文件**
- [ ] **代码通过 Stylelint 检查**
- [ ] 核心功能已实现并可运行
- [ ] 微信能力集成正常（登录、分享等）
- [ ] UI设计符合设计稿
- [ ] 适配不同屏幕尺寸
- [ ] 分包加载配置正确

### Automate节点检查清单

- [ ] **双维度代码审查通过（JS + WXML/WXSS）**
- [ ] **完成前验证通过（verification-before-completion）**
- [ ] 真机测试通过
- [ ] 不同微信版本兼容性测试
- [ ] 性能测试通过（首屏<2s）
- [ ] 包体积检查（主包<2MB）
- [ ] 微信审核规范检查
- [ ] **测试覆盖率 > 80%**

### Assess节点检查清单

- [ ] **全量测试通过（Jest + 真机）**
- [ ] **测试覆盖率达标**
- [ ] 代码审查通过（双维度）
- [ ] 文档完整且准确
- [ ] 用户验收测试通过
- [ ] 微信审核预检通过
- [ ] 分包验证通过（各分包体积达标）

---

## 反模式警告

```
写完 Page/Component 再补测试
   正确：先写 Jest it() 测试，再写实现

Page 逻辑全部堆在 onLoad 里不分层
   正确：提取 Service/Util，分层架构便于测试

ESLint 有 warning 忽略不管
   正确：ESLint 零 error 才能提交

只用开发者工具测试不跑真机
   正确：至少2台真机（iOS + Android）测试通过

不检查包体积直接提交审核
   正确：主包 < 2MB，总体积 < 20MB

微信授权一步到位请求所有权限
   正确：按需授权，用户触发才请求

不做分包直接把所有页面放主包
   正确：合理规划分包，主包只放核心页面
```

---

## 用户指令识别表（增强版）

| 用户指令 | 识别结果 | 执行动作 | Superpowers 技能 |
|----------|----------|----------|----------------|
| "做一个小程序" | 新项目 | 启动完整6A工作流 | 全技能链 |
| "分析需求" | 需求分析 | 调用需求分析师 | `brainstorming` |
| "写PRD" | 产品设计 | 调用产品经理 | `writing-plans` |
| "技术选型" | 技术决策 | 调用产品经理 | `planning` |
| "设计界面" | 界面设计 | 调用UI/UX设计师 | `tdd` |
| "开发功能" | 功能开发 | 调用小程序开发工程师 | `tdd` + `miniprogram-page-dev` |
| "测试小程序" | 测试 | 调用质量QA | `code-review` + `review-guidelines-check` |
| "审查代码" | 代码审查 | 调用质量QA | `requesting-code-review` |
| "完整项目" | 完整流程 | 启动完整6A工作流 | 全技能链 |

---

## 输出物标准检查（增强版）

### 每个节点的标准输出

| 节点 | 角色 | 必须输出 | Superpowers 验证要求 |
|------|------|----------|---------------------|
| Analyze | BA | 需求规格说明书.md | 含清晰验收标准（可用于TDD） |
| Architect | PM | PRD文档.md、技术方案.md、**实施计划.md** | Task拆解到2-5min级别 |
| Assemble | Designer + Dev | 设计稿、原型、可运行代码、**测试代码** | TDD完成 + Jest通过 + ESLint通过 |
| Automate | QA | 测试计划.md、测试报告.md、**审查报告.md** | 双维度审查 + 真机测试 + 覆盖率达标 |
| Assess | 全角色 | 质量评估报告.md | 全量验证 + 性能达标 + 审核预检 |
| Advance | PM | 项目复盘报告.md | 含最佳实践沉淀 |

---

**规则版本**：v2.0
**适用工作流**：6A + Superpowers 增强（Analyze → Architect → Assemble → Automate → Assess → Advance）
**数字员工数量**：5个（BA、PM、Designer、Dev、QA）
**Superpowers 技能**：14+ 个核心技能 + 小程序专项技能
**更新日期**：2026-04-07

## 版本更新记录

| 版本 | 日期 | 更新内容 |
|------|------|----------|
| **v2.0** | **2026-04-07** | **重大升级：集成Superpowers理念，引入TDD（Jest+miniprogram-simulate）、子代理开发、系统化调试、任务拆分、代码审查、微信审核预检等机制** |
| v1.0 | 2026-04-01 | 初始版本，定义6A工作流和小程序开发规范 |
