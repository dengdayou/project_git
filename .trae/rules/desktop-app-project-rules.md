# 轻量桌面端应用开发项目规则

> 版本：v2.0 | 日期：2026-04-07 | 更新内容：**集成Superpowers理念，引入TDD、子代理开发、任务拆分、代码审查等机制**
> 工作流：6A（Analyze → Architect → Assemble → Automate → Assess + Advance）
> 核心框架：Superpowers 四原则

---

## 规则概述

本规则定义了轻量桌面端应用软件开发的 **6A + Superpowers 增强工作流** 执行规范，**默认采用Tauri架构**，实现极致轻量、高性能的桌面应用。

本版本深度融合 **Superpowers 核心理念**，让 Tauri 桌面端开发遵循结构化、可验证、高质量的工程标准。

---

## Superpowers 核心原则（四原则）

| 原则 | 说明 | 在 Tauri 开发中的体现 |
|------|------|---------------------|
| **测试驱动开发 (TDD)** | 先写测试，再写实现 | Rust 单元测试先行，前端 Vitest/Jest 同步 |
| **系统性优于临时方案** | 遵循流程，不靠猜测 | 强制执行 6A 工作流 + Tauri 规范 |
| **复杂性降低 (YAGNI)** | 简化是首要目标 | 最小可行功能优先，避免过度设计 |
| **证据优于声明** | 验证后才算完成 | 测试通过 + 审查通过 = 功能完成 |

---

## 数字员工技能矩阵（Tauri + Superpowers）

```
┌─────────────────────────────────────────────────────────────┐
│        Tauri 桌面端开发技能树（Superpowers 增强）            │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  【流程类技能】                                              │
│  ├── brainstorming        需求澄清与架构探索                  │
│  ├── writing-plans         任务拆解与实施计划                 │
│  ├── test-driven-development  测试驱动开发(Rust+前端)       │
│  ├── systematic-debugging  系统化调试(4步法)                │
│  └── verification-before-completion  完成前验证             │
│                                                             │
│  【Tauri 专项技能】                                          │
│  ├── tauri-command-dev      Tauri Command 开发(TDD)        │
│  ├── frontend-backend-sync  前后端联调(TDD)                │
│  ├── cross-platform-test   跨平台兼容性测试                 │
│  └── build-package-verify  构建打包验证                     │
│                                                             │
│  【协作类技能】                                              │
│  ├── subagent-driven-development  子代理并行开发            │
│  ├── requesting-code-review       代码审查(Rust+前端)      │
│  └── finishing-a-development-branch  分支收尾              │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 6A 工作流定义（Superpowers 增强版）

```
┌─────────────────────────────────────────────────────────────────────────┐
│           6A 工作流 v2.0 - 轻量桌面端应用开发（Tauri + Superpowers）    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  Node 1        Node 2        Node 3          Node 4    Node 5    Node 6│
│  Analyze  →   Architect  →   Assemble     →  Automate  → Assess →Advance│
│  需求分析      产品架构       设计开发         自动化测试   质量评估  进阶优化│
│    ↓              ↓              ↓               ↓          ↓        ↓  │
│  需求分析师    产品经理      UI/UX设计师      质量QA     全角色    产品经理│
│                              桌面端工程师                          │
│  ⚡Brainstorm  ⚡Plan      ⚡TDD+Subagent   ⚡Test+Review ⚡Audit  ⚡复盘│
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

⚡ = Superpowers 技能注入点
```

### 各节点核心职责（增强版）

| 节点 | 角色 | Superpowers 技能 | 核心任务 | 文档输出 |
|------|------|------------------|----------|----------|
| **Analyze** | 需求分析师 | `brainstorming` | 需求澄清、桌面端特性分析 | 需求规格说明书.md |
| **Architect** | 产品经理 | `writing-plans` | PRD、技术选型、任务拆解 | PRD文档.md、技术方案.md、**实施计划.md** |
| **Assemble** | UI/UX设计师<br>+ 桌面端开发工程师 | `test-driven-development`<br>`subagent-driven-development`<br>`tauri-command-dev`<br>`systematic-debugging` | 设计稿、TDD开发（Rust+前端）、子代理并行 | 设计稿、HTML原型、功能代码、**测试代码** |
| **Automate** | 质量QA | `requesting-code-review`<br>`cross-platform-test`<br>`verification-before-completion` | 测试执行、跨平台测试、代码审查 | 测试计划.md、测试报告.md、**审查报告.md** |
| **Assess** | 全角色 | `finishing-a-development-branch`<br>`build-package-verify` | 质量评估、打包验证 | 质量评估报告.md |
| **Advance** | 产品经理 | 复盘优化 | 项目复盘、知识沉淀 | 项目复盘报告.md |

---

## 技术栈规范

### 为什么选择Tauri？

| 对比维度 | Tauri | Electron |
|----------|-------|----------|
| **包体积** | <10MB | >100MB |
| **内存占用** | 低（Rust后端） | 高（Node.js+Chromium） |
| **启动速度** | 快 | 较慢 |
| **安全性** | 高（Rust内存安全） | 中 |
| **前端技术** | 任意Web技术栈 | 任意Web技术栈 |
| **后端语言** | Rust | Node.js |
| **生态成熟度** | 快速发展中 | 非常成熟 |

### 默认技术栈（Tauri + Superpowers 增强版）

```
前端框架：Vue 3 + TypeScript
桌面框架：Tauri 2.x (Rust后端)
状态管理：Pinia
UI组件：Element Plus
本地存储：Tauri Store Plugin / SQLite
构建工具：Vite
tauri-cli：用于构建和打包

【Superpowers 新增】
测试框架（Rust）：cargo test + #[cfg(test)]
测试框架（前端）：Vitest / Jest
覆盖率工具：tarpaulin (Rust) / c8 (前端)
代码检查：cargo clippy (Rust) + ESLint (前端)
```

### Tauri架构优势

1. **前端无关**：可以使用任何前端框架（React/Vue/Svelte/Angular）
2. **Rust后端**：高性能、内存安全、线程安全
3. **系统API**：通过Rust直接调用系统API
4. **自动更新**：内置自动更新机制
5. **代码签名**：支持Windows/macOS代码签名

---

## 项目结构规范（Superpowers 增强版）

### Tauri项目结构

```
tauri-desktop-app/
├── src/                        # 前端源码目录
│   ├── components/             # Vue组件
│   │   └── __tests__/          # ⭐ 组件单元测试（新增）
│   ├── views/                  # 页面视图
│   ├── composables/            # 组合式函数(Hooks)
│   │   └── __tests__/          # ⭐ Hooks 单元测试（新增）
│   ├── stores/                 # Pinia状态管理
│   │   └── __tests__/          # ⭐ Store 单元测试（新增）
│   ├── utils/                  # 工具函数
│   │   └── __tests__/          # ⭐ 工具函数单元测试（新增）
│   ├── router/                 # Vue Router路由
│   ├── App.vue                 # 根组件
│   └── main.ts                 # 入口文件
├── src-tauri/                  # Tauri后端（Rust）
│   ├── src/
│   │   ├── main.rs             # 主入口
│   │   ├── lib.rs              # 库入口
│   │   ├── commands/           # Tauri命令
│   │   │   ├── mod.rs
│   │   │   ├── file.rs         # 文件操作
│   │   │   │   └── ⭐ #[cfg(test)] mod tests; （新增）
│   │   │   ├── window.rs       # 窗口控制
│   │   │   │   └── ⭐ #[cfg(test)] mod tests;
│   │   │   └── store.rs        # 数据存储
│   │   │       └── ⭐ #[cfg(test)] mod tests;
│   │   ├── services/           # 服务层
│   │   │   ├── mod.rs
│   │   │   ├── database.rs     # 数据库服务
│   │   │   │   └── ⭐ #[cfg(test)] mod tests;
│   │   │   └── updater.rs      # 自动更新
│   │   │       └── ⭐ #[cfg(test)] mod tests;
│   │   └── utils/              # 工具函数
│   │       └── ⭐ #[cfg(test)] mod tests;
│   ├── Cargo.toml              # Rust依赖
│   │   └── [dev-dependencies]  # ⭐ 测试依赖（新增）
│   tauri.conf.json             # Tauri配置
│   └── build.rs                # 构建脚本
├── public/                     # 静态资源
│   └── icons/                  # 应用图标
├── docs/                       # 项目文档
│   ├── 01-需求规格说明书.md
│   ├── 02-PRD文档.md
│   ├── 03-技术方案.md
│   ├── 04-实施计划.md          # ⭐ 新增（Writing-Plans 输出）
│   ├── 05-设计稿/
│   ├── 06-测试计划.md
│   ├── 07-审查报告.md          # ⭐ 新增（Code Review 输出）
│   └── 08-项目复盘.md
├── tests/                      # 测试文件（增强）
│   ├── unit/                   # 单元测试
│   │   ├── rust/               # Rust 后端单元测试
│   │   └── frontend/           # 前端单元测试
│   ├── integration/            # 集成测试（前后端联调）
│   │   └── tauri-commands/     # Tauri Command 集成测试
│   └── e2e/                    # 端到端测试
├── index.html
├── package.json
├── tsconfig.json
├── vite.config.ts              # Vite配置（含测试配置）
└── README.md
```

---

## 数字员工角色与任务匹配规则（Superpowers 增强版）

### 1. 需求分析师 (BA) ⚡ Brainstormer

**Superpowers 技能**：`brainstorming`

**触发关键词**：
- "分析需求"、"需求分析"、"调研"
- "用户画像"、"业务场景"
- "可行性分析"、"需求文档"
- "新项目启动"、"需求变更"

**任务特征**：
- 输入：业务诉求、用户痛点、市场机会
- 输出：需求规格说明书
- 节点：Analyze

**Tauri桌面端特殊关注点（Brainstorming 阶段必须确认）**：
- [ ] 离线使用场景？是否需要本地数据缓存？
- [ ] 本地数据存储需求？SQLite vs Tauri Store？
- [ ] 系统托盘需求？最小化行为？
- [ ] 快捷键需求？全局快捷键 vs 应用内快捷键？
- [ ] 自动更新机制？更新策略？
- [ ] 系统级功能需求？（文件操作、通知、剪贴板等）
- [ ] 多窗口需求？单窗口 vs 多窗口？
- [ ] 跨平台需求？Win/Mac/Linux 兼容性要求？

---

### 2. 产品经理 (PM) ⚡ Planner

**Superpowers 技能**：`writing-plans`

**触发关键词**：
- "PRD"、"产品文档"、"产品方案"
- "功能设计"、"功能规划"
- "优先级"、"路线图"
- "竞品分析"、"验收标准"

**任务特征**：
- 输入：需求规格说明书
- 输出：PRD文档、**实施计划**、技术选型建议
- 节点：Architect / Advance

**Tauri桌面端特殊关注点（Planning 阶段必须规划）**：

**Writing-Plans 输出示例**：
```markdown
## 实施计划：[Tauri桌面应用名称]

### Phase 1: 基础设施搭建
┌────────┬────────────────────┬────────┬──────┐
│ Task ID │ 任务名             │ 时间   │ 依赖 │
├────────┼────────────────────┼────────┼──────┤
│ T-001  │ Tauri项目初始化    │ 3min   │ 无   │
│ T-002  │ Rust基础Command骨架 │ 5min   │ T001 │
│ T-003  │ Vue3前端项目搭建   │ 5min   │ T001 │
│ T-004  │ 测试环境配置       │ 5min   │ T002 │
└────────┴────────────────────┴────────┴──────┘

### Phase 2: 核心功能开发
┌────────┬────────────────────┬────────┬──────┐
│ Task ID │ 任务名             │ 时间   │ 依赖 │
├────────┼────────────────────┼────────┼──────┤
│ T-005  │ 文件操作Command    │ 10min  │ T002 │
│ T-006  │ 窗口管理Command    │ 8min   │ T002 │
│ T-007  │ 本地存储Service    │ 10min  │ T002 │
│ T-008  │ 前端UI组件开发     │ 15min  │ T003 │
│ T-009  │ 前后端联调         │ 10min  │ T005-T008│
└────────┴────────────────────┴────────┴──────┘

每个 Task 必须包含：
- TDD 要求（RED/GREEN/REFACTOR）
- Rust 测试用例或前端测试用例
```

**Tauri 技术决策点**：
- 打包和分发策略（各平台安装包：MSI/DMG/AppImage）
- 版本更新机制设计（Tauri Updater 配置）
- 跨平台兼容性要求清单
- 代码签名策略（Windows Authenticode / Apple Notarization）

---

### 3. UI/UX设计师 + 桌面端开发工程师 (Designer + Dev) ⚡ TDD Developer

**Superpowers 技能**：
- `test-driven-development`（核心）
- `subagent-driven-development`
- `systematic-debugging`
- `tauri-command-dev`（Tauri专项）
- `frontend-backend-sync`（Tauri专项）

**触发关键词**：
- "设计"、"界面"、"UI"、"UX"
- "原型"、"线框图"、"视觉稿"
- "开发"、"编码"、"实现"
- "桌面端"、"窗口"、"菜单"
- "Tauri"、"Rust"、"Command"

**任务特征**：
- 输入：PRD文档、**实施计划**
- 输出：设计稿、HTML原型、可运行代码、**测试代码**
- 节点：Assemble

**TDD 开发工作流（Tauri 专项）**：

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🖥️ Tauri 桌面端 - TDD 开发模式
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

【Rust 后端 TDD 流程】

  Task: 实现 open_file_dialog Command

  Step 1: RED - 编写失败的 Rust 测试
  ┌─────────────────────────────────────────────┐
  // src-tauri/src/commands/file.rs (tests module)
  #[cfg(test)]
  mod tests {
      use super::*;

      #[test]
      fn test_open_file_dialog_returns_file_info() {
          // TODO: 测试 open_file_dialog 返回正确的 FileInfo
          // 当前预期：应返回包含 path 和 content 的结构体
      }
  }
  └─────────────────────────────────────────────
  → 运行 cargo test → ❌ 失败（函数不存在）

  Step 2: GREEN - 编写最少实现
  ┌─────────────────────────────────────────────
  #[command]
  pub async fn open_file_dialog() -> Result<Option<FileInfo>, String> {
      let path = rfd::AsyncFileDialog::new()
          .pick_file()
          .await;
      
      match path {
          Some(file) => {
              let content = fs::read_to_string(file.path())
                  .map_err(|e| e.to_string())?;
              Ok(Some(FileInfo { ... }))
          }
          None => Ok(None)
      }
  }
  └─────────────────────────────────────────────
  → 运行 cargo test → ✅ 通过

  Step 3: REFACTOR - 重构优化
  ├── 提取文件过滤器为参数
  ├── 添加错误日志记录
  └── 运行 cargo test + cargo clippy → ✅ 全部通过

【前端 TDD 流程】

  Task: 实现 useFile composable

  Step 1: RED - 编写失败的 Vitest 测试
  ┌─────────────────────────────────────────────
  // src/composables/__tests__/useFile.test.ts
  import { describe, it, expect, vi } from 'vitest'
  
  describe('useFile', () => {
      it('should call invoke when openFile is called', async () => {
          const { openFile } = useFile()
          vi.mocked(invoke).mockResolvedValue({ path: '/test.txt', content: 'hello' })
          
          const result = await openFile()
          expect(result).toEqual({ path: '/test.txt', content: 'hello' })
          expect(invoke).toHaveBeenCalledWith('open_file_dialog')
      })
  })
  └─────────────────────────────────────────────
  → 运行 npx vitest → ❌ 失败

  Step 2: GREEN - 编写最少实现
  ┌─────────────────────────────────────────────
  export function useFile() {
      const openFile = async (): Promise<FileInfo | null> => {
          return await invoke<FileInfo | null>('open_file_dialog')
      }
      return { openFile }
  }
  └─────────────────────────────────────────────
  → 运行 npx vitest → ✅ 通过

  Step 3: REFACTOR - 重构优化
  ├── 添加错误处理
  ├── 添加 loading 状态
  └── 运行 npx vitest → ✅ 全部通过

【前后端联调 TDD】

  Task: 验证文件打开完整流程

  Step 1: 编写集成测试
  ┌─────────────────────────────────────────────
  // tests/integration/tauri-commands/file.test.ts
  describe('File Operations Integration', () => {
      it('should complete full file open flow', async () => {
          // 1. 模拟用户点击打开按钮
          // 2. 验证 Tauri Command 被正确调用
          // 3. 验证前端状态正确更新
          // 4. 验证内容正确显示
      })
  })
  └─────────────────────────────────────────────

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Tauri桌面端特殊关注点（Assemble 阶段）**：
- [ ] 窗口管理功能（最小化到托盘、多窗口）
- [ ] 原生菜单设计（Menu Bar、Context Menu、系统托盘菜单）
- [ ] 快捷键设计（全局快捷键、应用快捷键）
- [ ] 系统通知集成（Tauri Notification API）
- [ ] 拖拽文件支持
- [ ] 前端与Rust后端通信（Tauri Commands）
- [ ] **✨ 每个 Tauri Command 都有对应的 Rust 单元测试**
- [ ] **✨ 每个前端 Composable/Store 都有对应的 Vitest 测试**

**子代理并行开发模式（Tauri）**：

```
主代理协调者
    │
    ├── 子代理 A: Rust Commands 开发
    │   ├── file.rs (TDD)
    │   ├── window.rs (TDD)
    │   └── store.rs (TDD)
    │
    ├── 子代理 B: 前端组件开发
    │   ├── Views (TDD)
    │   ├── Components (TDD)
    │   └── Composables (TDD)
    │
    └── 子代理 C: 联调测试（等 A、B 完成）
        ├── Integration Tests
        └── E2E Tests
```

---

### 4. 质量QA (QA) ⚡ Reviewer & Verifier

**Superpowers 技能**：
- `requesting-code-review`
- `cross-platform-test`
- `verification-before-completion`
- `build-package-verify`

**触发关键词**：
- "测试"、"测试用例"、"测试计划"
- "质量"、"QA"、"验收"
- "缺陷"、"Bug"、"回归"
- "自动化测试"、"性能测试"

**任务特征**：
- 输入：PRD、设计稿、可运行版本、测试代码
- 输出：测试计划、测试报告、**审查报告**
- 节点：Automate

**Tauri桌面端 QA 工作流（Superpowers 增强）**：

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔍 Tauri 桌面端 - Quality Assurance 模式
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

【Phase 1】双重代码审查

  维度A：Rust 后端审查
  ├── cargo clippy 通过无 warning？
  ├── cargo test 全部通过？
  ├── cargo fmt 格式正确？
  ├── Command 错误处理完善？
  └── 安全性检查（SQL注入、路径遍历等）

  维度B：前端审查
  ├── ESLint 通过无 error/warning？
  ├── TypeScript 类型检查通过？
  ├── Vitest 全部通过？
  ├── 测试覆盖率 > 80%？
  └── 代码结构清晰？

【Phase 2】跨平台兼容性测试
  ├── Windows 10/11 测试
  ├── macOS 12+ 测试
  ├── Linux (Ubuntu/Debian) 测试
  └── 记录平台差异问题

【Phase 3】Tauri 特殊测试
  ├── 安装/卸载流程测试（MSI/DMG/AppImage/deb）
  ├── 自动更新功能测试（Tauri Updater）
  ├── 离线功能测试
  ├── 性能测试（启动时间 < 1s，内存 < 100MB）
  └── 系统托盘/快捷键功能测试

【Phase 4】完成前验证（Verification-Before-Completion）
  - [ ] 所有 Rust 单元测试通过
  - [ ] 所有前端单元测试通过
  - [ ] 集成测试通过
  - [ ] 代码审查无 Critical 问题
  - [ ] 跨平台测试通过
  - [ ] 打包产物可用
  - [ ] 文档完整且准确

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Tauri桌面端特殊关注点（Automate 阶段）**：
- [ ] 跨平台兼容性测试（Windows/macOS/Linux）
- [ ] 安装/卸载流程测试（MSI/DMG/AppImage/deb）
- [ ] 自动更新测试（Tauri Updater）
- [ ] 离线功能测试
- [ ] 性能测试（启动时间 < 1s，内存占用 < 100MB）
- [ ] Rust后端单元测试（cargo test）
- [ ] Rust 代码质量（cargo clippy）
- [ ] **⭐ 代码审查已完成（双维度：Rust + 前端）**

---

### 5. 全角色评估 (Assess) ⚡ Finishing & Verify

**Superpowers 技能**：
- `finishing-a-development-branch`
- `build-package-verify`

**触发关键词**：
- "评估"、"评审"、"质量检查"
- "发布前检查"、"上线前评估"
- "验收"、"签字"
- "打包"、"构建"

**Tauri 桌面端 Assess 流程**：

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📦 Tauri 桌面端 - Assess & Package 模式
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

【Step 1】全量测试回归
  ├── cargo test --all-targets
  ├── npx vitest run --coverage
  └── E2E 测试套件

【Step 2】构建验证
  ├── cargo build --release
  ├── npm run build（前端生产构建）
  └── tauri build（各平台打包）

【Step 3】打包产物验证
  ├── Windows: MSI 安装包测试
  ├── macOS: DMG 安装包测试
  ├── Linux: AppImage/deb 测试
  ├── 文件大小检查（< 10MB 目标）
  └── 签名验证（如已配置）

【Step 4】分支收尾决策
  用户选择：
  ├── 合并到主分支
  ├── 创建 Release
  ├── 保留分支继续修改
  └── 丢弃所有更改

【Step 5】清理
  ├── Git Worktree 清理
  ├── 临时文件清理
  └── 输出变更报告

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Tauri开发规范（Superpowers 增强版）

### 前端与Rust通信（Tauri Commands）- 含 TDD 示例

```rust
// src-tauri/src/commands/file.rs
use tauri::command;
use std::fs;
use std::path::Path;

#[derive(Debug, serde::Serialize)]
pub struct FileInfo {
    path: String,
    content: String,
}

/// 打开文件对话框并读取文件
#[command]
pub async fn open_file_dialog() -> Result<Option<FileInfo>, String> {
    let path = rfd::AsyncFileDialog::new()
        .add_filter("Text", &["txt"])
        .add_filter("JSON", &["json"])
        .pick_file()
        .await;
    
    if let Some(file) = path {
        let path_str = file.path().to_string_lossy().to_string();
        let content = fs::read_to_string(file.path())
            .map_err(|e| e.to_string())?;
        
        Ok(Some(FileInfo {
            path: path_str,
            content,
        }))
    } else {
        Ok(None)
    }
}

/// 保存文件对话框
#[command]
pub async fn save_file_dialog(content: String, filename: String) -> Result<Option<String>, String> {
    let path = rfd::AsyncFileDialog::new()
        .set_file_name(&filename)
        .save_file()
        .await;
    
    if let Some(file) = path {
        fs::write(file.path(), content)
            .map_err(|e| e.to_string())?;
        Ok(Some(file.path().to_string_lossy().to_string()))
    } else {
        Ok(None)
    }
}

// ==================== TDD 测试模块 ====================
#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_file_info_struct_creation() {
        let info = FileInfo {
            path: "/test/path.txt".to_string(),
            content: "hello world".to_string(),
        };
        
        assert_eq!(info.path, "/test/path.txt");
        assert_eq!(info.content, "hello world");
    }

    #[tokio::test]
    async fn test_save_file_dialog_creates_file() {
        let tmp_dir = tempfile::tempdir().expect("Failed to create temp dir");
        let file_path = tmp_dir.path().join("test_output.txt");
        let file_name = "test_output.txt".to_string();
        let content = "test content".to_string();

        // 注意：此测试需要 mock rfd 或使用真实文件系统
        // 在实际项目中，建议提取文件操作逻辑以便测试
    }

    // TODO: 添加更多边界条件测试
    // - 空文件名
    // - 特殊字符文件名
    // - 权限不足情况
}
```

```typescript
// 前端调用Rust命令 (Vue 3 + TypeScript) - 含 TDD 测试
// src/utils/tauri.ts
import { invoke } from '@tauri-apps/api/core';
import { open, save } from '@tauri-apps/plugin-dialog';
import { writeTextFile } from '@tauri-apps/plugin-fs';

interface FileInfo {
  path: string;
  content: string;
}

export const openFile = async (): Promise<FileInfo | null> => {
  try {
    const result = await invoke<FileInfo | null>('open_file_dialog');
    return result;
  } catch (error) {
    console.error('打开文件失败:', error);
    throw error;
  }
};

export const saveFile = async (content: string, filename: string): Promise<string | null> => {
  try {
    const result = await invoke<string | null>('save_file_dialog', { 
      content, 
      filename 
    });
    return result;
  } catch (error) {
    console.error('保存文件失败:', error);
    throw error;
  }
};
```

```typescript
// src/utils/__tests__/tauri.test.ts - 前端 TDD 测试
import { describe, it, expect, vi, beforeEach } from 'vitest'

vi.mock('@tauri-apps/api/core', () => ({
    invoke: vi.fn()
}))

describe('tauri utils', () => {
    beforeEach(() => {
        vi.clearAllMocks()
    })

    describe('openFile', () => {
        it('should call invoke with correct command name', async () => {
            const { invoke } = await import('@tauri-apps/api/core')
            vi.mocked(invoke).mockResolvedValue({
                path: '/test/file.txt',
                content: 'file content'
            })

            const { openFile } = await import('../tauri')
            const result = await openFile()

            expect(invoke).toHaveBeenCalledWith('open_file_dialog')
            expect(result).toEqual({
                path: '/test/file.txt',
                content: 'file content'
            })
        })

        it('should throw error when invoke fails', async () => {
            const { invoke } = await import('@tauri-apps/api/core')
            vi.mocked(invoke).mockRejectedValue(new Error('Tauri error'))

            const { openFile } = await import('../tauri')
            
            await expect(openFile()).rejects.toThrow('打开文件失败')
        })
    })
})
```

### 窗口管理规范 - 含 TDD

```rust
// src-tauri/src/commands/window.rs
use tauri::{command, AppHandle, Manager};

#[command]
pub fn minimize_window(app: AppHandle) {
    if let Some(window) = app.get_webview_window("main") {
        let _ = window.minimize();
    }
}

#[command]
pub fn maximize_window(app: AppHandle) {
    if let Some(window) = app.get_webview_window("main") {
        if window.is_maximized().unwrap_or(false) {
            let _ = window.unmaximize();
        } else {
            let _ = window.maximize();
        }
    }
}

#[command]
pub fn close_window(app: AppHandle) {
    if let Some(window) = app.get_webview_window("main") {
        let _ = window.close();
    }
}

#[command]
pub fn toggle_fullscreen(app: AppHandle) {
    if let Some(window) = app.get_webview_window("main") {
        let is_fullscreen = window.is_fullscreen().unwrap_or(false);
        let _ = window.set_fullscreen(!is_fullscreen);
    }
}

#[command]
pub fn set_always_on_top(app: AppHandle, always_on_top: bool) {
    if let Some(window) = app.get_webview_window("main") {
        let _ = window.set_always_on_top(always_on_top);
    }
}

#[cfg(test)]
mod tests {
    // Window 操作通常需要 Tauri AppHandle mock
    // 建议在集成测试中验证
}
```

### 本地数据存储规范（Tauri Store）- 含 TDD

```rust
// src-tauri/src/commands/store.rs
use tauri::command;
use tauri::State;
use tauri_plugin_store::Store;
use serde_json::Value;

#[command]
pub fn get_store_value(store: State<'_, Store>, key: String) -> Option<Value> {
    store.get(&key)
}

#[command]
pub fn set_store_value(store: State<'_, Store>, key: String, value: Value) -> Result<(), String> {
    store.set(&key, value);
    store.save().map_err(|e| e.to_string())
}

#[command]
pub fn delete_store_value(store: State<'_, Store>, key: String) -> Result<(), String> {
    store.delete(&key);
    store.save().map_err(|e| e.to_string())
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn test_store_value_serialization() {
        let value = serde_json::json!({
            "theme": "dark",
            "language": "zh-CN"
        });
        
        assert_eq!(value["theme"], "dark");
        assert_eq!(value["language"], "zh-CN");
    }
}
```

### 系统托盘规范

```rust
// src-tauri/src/tray.rs
use tauri::{AppHandle, Manager, SystemTray, SystemTrayEvent, SystemTrayMenu, SystemTrayMenuItem, CustomMenuItem};

pub fn create_system_tray() -> SystemTray {
    let show = CustomMenuItem::new("show", "显示主窗口");
    let settings = CustomMenuItem::new("settings", "设置");
    let quit = CustomMenuItem::new("quit", "退出");
    
    let tray_menu = SystemTrayMenu::new()
        .add_item(show)
        .add_item(settings)
        .add_native_item(SystemTrayMenuItem::Separator)
        .add_item(quit);
    
    SystemTray::new().with_menu(tray_menu)
}

pub fn handle_system_tray_event(app: &AppHandle, event: SystemTrayEvent) {
    match event {
        SystemTrayEvent::LeftClick { .. } => {
            if let Some(window) = app.get_webview_window("main") {
                let _ = window.show();
                let _ = window.set_focus();
            }
        }
        SystemTrayEvent::MenuItemClick { id, .. } => match id.as_str() {
            "show" => {
                if let Some(window) = app.get_webview_window("main") {
                    let _ = window.show();
                    let _ = window.set_focus();
                }
            }
            "settings" => {
                if let Some(window) = app.get_webview_window("main") {
                    let _ = window.show();
                    let _ = window.eval("window.location.href = '/settings'");
                }
            }
            "quit" => {
                app.exit(0);
            }
            _ => {}
        },
        _ => {}
    }
}
```

### 自动更新规范（Tauri Updater）

```rust
// src-tauri/src/services/updater.rs
use tauri::AppHandle;
use tauri_plugin_updater::UpdaterExt;

pub async fn check_update(app: AppHandle) -> Result<(), Box<dyn std::error::Error>> {
    let updater = app.updater()?;
    
    if let Some(update) = updater.check().await? {
        update.download_and_install(|_chunk_length, _content_length| {}, || {}).await?;
        app.restart();
    }
    
    Ok(())
}
```

```typescript
// 前端更新检查 - 含测试
// src/utils/updater.ts
import { check } from '@tauri-apps/plugin-updater';
import { ask, message } from '@tauri-apps/plugin-dialog';

export const checkForUpdates = async () => {
  try {
    const update = await check();
    
    if (update) {
      const yes = await ask(
        `发现新版本 ${update.version}，是否现在下载？`,
        { title: '发现新版本', kind: 'info' }
      );
      
      if (yes) {
        await update.downloadAndInstall((event) => {
          switch (event.event) {
            case 'Started': console.log('开始下载更新...'); break;
            case 'Progress': console.log(`下载进度: ${event.data.chunkLength}`); break;
            case 'Finished': console.log('下载完成'); break;
          }
        });
        
        await message('更新已下载完成，应用将重启', { title: '更新完成' });
      }
    }
  } catch (error) {
    console.error('检查更新失败:', error);
  }
};
```

---

## Tauri配置规范

### tauri.conf.json配置

```json
{
  "productName": "YourApp",
  "version": "1.0.0",
  "identifier": "com.yourcompany.yourapp",
  "build": {
    "frontendDist": "../dist",
    "devUrl": "http://localhost:5173",
    "beforeDevCommand": "npm run dev",
    "beforeBuildCommand": "npm run build && npm run test"
  },
  "app": {
    "windows": [
      {
        "title": "YourApp",
        "width": 1200,
        "height": 800,
        "minWidth": 800,
        "minHeight": 600,
        "resizable": true,
        "fullscreen": false,
        "decorations": true,
        "transparent": false,
        "alwaysOnTop": false,
        "visible": false
      }
    ],
    "security": {
      "csp": null
    },
    "withGlobalTauri": true
  },
  "bundle": {
    "active": true,
    "targets": ["msi", "dmg", "appimage", "deb"],
    "icon": [
      "icons/32x32.png",
      "icons/128x128.png",
      "icons/128x128@2x.png",
      "icons/icon.icns",
      "icons/icon.ico"
    ],
    "windows": {
      "certificateThumbprint": null,
      "digestAlgorithm": "sha256",
      "timestampUrl": ""
    },
    "macOS": {
      "frameworks": [],
      "minimumSystemVersion": "10.13",
      "signingIdentity": null,
      "entitlements": null
    },
    "linux": {
      "appimage": {
        "bundleMediaFramework": false
      }
    }
  },
  "plugins": {
    "updater": {
      "active": true,
      "endpoints": [
        "https://releases.myapp.com/{{target}}/{{arch}}/{{current_version}}"
      ],
      "dialog": true,
      "pubkey": "YOUR_PUBLIC_KEY"
    },
    "store": {
      "freezeOnError": false
    }
  }
}
```

---

## 工作流执行规则（Superpowers 增强版）

### 规则0：Superpowers 四原则（最高优先级）

```
在任何时候，以下四条原则不可违反：

1. 测试驱动 (TDD)
   → Rust: 先写 #[test]，再写 impl
   → 前端: 先写 it()，再写实现
   → 违反时：立即停止，回到RED阶段

2. 系统性优先
   → 遵循 6A 工作流 + Tauri 开发规范
   → 违反时：回退到被跳过的步骤

3. 简化为上 (YAGNI)
   → 只做当前需要的 Tauri 功能
   → 违反时：删除过度设计的部分

4. 证据说话
   → cargo test 通过 + vitest 通过 + 审查通过 = 完成
   → 违反时：补充测试或修复审查问题
```

### 规则1：严格按照节点顺序执行

```
Analyze → Architect → Assemble → Automate → Assess → Advance
   ↓          ↓          ↓          ↓           ↓         ↓
 必须完成    必须完成    必须完成    必须完成     必须完成   必须完成
(Brainstorm)(Planning) (TDD)      (Review+Test) (Package)  (复盘)
 才能进入    才能进入    才能进入    才能进入     才能进入   才能进入
 下一阶段
```

### 规则2：TDD 强制执行原则（Tauri 专项）

**Rust 后端 TDD 要求**：
```
每个 Tauri Command 必须有对应的 #[cfg(test)] 测试模块
每个 Service 必须有对应的单元测试
每个 Utility 函数必须有对应的单元测试

开发顺序：
1. 编写 #[test] 测试函数（描述预期行为）
2. 运行 cargo test → 确认失败（RED）
3. 编写最少实现
4. 运行 cargo test → 确认通过（GREEN）
5. 运行 cargo clippy → 确认无警告
6. 重构优化（REFACTOR）
7. 再次运行 cargo test + cargo clippy → 确认全部通过
```

**前端 TDD 要求**：
```
每个 Composable 必须有对应的 .test.ts
每个 Store 必须有对应的 .test.ts
每个 Utility 函数必须有对应的 .test.ts

开发顺序：
1. 编写 Vitest 测试（describe/it/expect）
2. 运行 npx vitest → 确认失败（RED）
3. 编写最少实现
4. 运行 npx vitest → 确认通过（GREEN）
5. 运行 ESLint + TypeScript 检查
6. 重构优化（REFACTOR）
7. 再次运行全量测试 → 确认全部通过
```

### 规则3：开发即文档原则（增强版）

**强制要求**：
1. **同步开发**：Rust 代码开发 + 前端代码开发 + 测试编写 + 文档编写同步进行
2. **Command 完成即测试完成**：每完成一个 Tauri Command，对应的 Rust 测试 + 前端调用测试必须同时完成
3. **功能调整即全量更新**：任何功能调整/新增，必须同步更新相关文档和相关测试
4. **质量门禁**：Assemble 节点必须通过 **cargo test + vitest + 代码审查** 才能进入 Automate

### 规则4：每个节点必须人工决策 + 验证

```
节点执行 → Superpowers验证 → 输出成果 → 【等待人工决策】 → 用户确认 → 进入下一阶段
                ↓                              ↓
         verification-before-completion    用户拒绝
                ↓                              ↓
         - cargo test 通过？               返回当前节点重新执行
         - vitest 通过？
         - clippy/eslint 通过？
         - 代码审查通过？
         - 文档完整？
```

### 规则5：不允许跳过节点的场景

以下情况**严禁**跳过：
1. 新项目必须从 Analyze 开始（启用 Brainstorming）
2. 有需求变更必须回到 Analyze
3. 设计变更必须回到 Assemble
4. **Rust 测试不通过必须回到 Assemble**
5. **前端测试不通过必须回到 Assemble**
6. **代码审查有 Critical 问题必须回到 Assemble**
7. **跨平台测试不通过必须回到 Assemble**

### 规则6：允许跳过节点的场景

以下情况**可以**直接调用特定角色：
1. 已有明确需求，直接调用产品经理（启用 Writing-Plans）
2. 已有 PRD + 实施计划，直接调用开发工程师（启用 TDD 模式）
3. 已有可运行版本，直接调用 QA（启用 Code Review 模式）
4. 需要技术选型建议，直接调用产品经理

---

## 质量门禁标准（Superpowers 增强版）

### Assemble节点检查清单

#### Rust 后端检查
- [ ] `cargo check` 通过
- [ ] `cargo clippy` 通过（无 warning）
- [ ] `cargo fmt --check` 通过
- [ ] `cargo test` 全部通过
- [ ] **每个 Command 有对应测试模块**
- [ ] **测试覆盖核心逻辑路径**

#### 前端检查
- [ ] ESLint 通过（无 error/warning）
- [ ] TypeScript 类型检查通过
- [ ] **Vitest 全部通过**
- [ ] **测试覆盖率 > 80%**
- [ ] **每个 Composable/Store/Util 有对应测试**

#### Tauri 功能检查
- [ ] Tauri Commands 功能正常
- [ ] 窗口管理功能正常
- [ ] 本地数据存储功能正常
- [ ] UI 设计符合设计稿
- [ ] 前后端通信正常

### Automate节点检查清单
- [ ] **Rust 单元测试全部通过**
- [ ] **前端单元测试全部通过**
- [ ] **集成测试通过**
- [ ] **代码审查双维度通过（Rust + 前端）**
- [ ] **测试覆盖率达标**
- [ ] 安装/卸载流程测试通过（MSI/DMG/AppImage）
- [ ] 自动更新功能测试通过
- [ ] 离线功能测试通过
- [ ] 性能测试通过（启动时间 < 1s）
- [ ] 内存占用测试通过（< 100MB）
- [ ] 跨平台兼容性测试通过

### Assess节点检查清单
- [ ] 所有测试用例通过
- [ ] 代码审查通过（前端 + Rust）
- [ ] 文档完整且准确
- [ ] **各平台打包产物验证通过**
- [ ] **安装/卸载流程验证通过**
- [ ] 用户验收测试通过

---

## 用户指令识别表（增强版）

| 用户指令 | 识别结果 | 执行动作 | Superpowers 技能 |
|----------|----------|----------|----------------|
| "做一个桌面应用" | 新项目 | 启动完整6A工作流 | 全技能链 |
| "分析需求" | 需求分析 | 调用需求分析师 | `brainstorming` |
| "写PRD"/"帮我规划" | 产品设计 | 调用产品经理 | `writing-plans` |
| "技术选型" | 技术决策 | 调用产品经理（推荐Tauri） | `planning` |
| "设计界面" | 界面设计 | 调用UI/UX设计师 | `tdd` |
| "开发功能"/"写代码" | 功能开发 | 调用桌面端开发工程师 | `tdd` + `tauri-command-dev` |
| "有个bug"/"调试一下" | Bug修复 | 调用开发工程师 | `systematic-debugging` |
| "测试应用" | 测试 | 调用质量QA | `code-review` + `cross-platform-test` |
| "打包应用" | 构建分发 | 调用桌面端开发工程师 | `build-package-verify` |
| "审查代码" | 代码审查 | 调用质量QA | `requesting-code-review` |
| "完整项目" | 完整流程 | 启动完整6A工作流 | 全技能链 |

---

## 输出物标准检查（增强版）

### 每个节点的标准输出

| 节点 | 角色 | 必须输出 | Superpowers 验证要求 |
|------|------|----------|---------------------|
| Analyze | BA | 需求规格说明书.md | 含清晰验收标准（可用于TDD） |
| Architect | PM | PRD文档.md、技术方案.md、**实施计划.md** | Task拆解到2-5min级别 |
| Assemble | Designer + Dev | 设计稿、HTML原型、功能代码、**测试代码** | TDD完成 + cargo test通过 + vitest通过 |
| Automate | QA | 测试计划.md、测试报告.md、**审查报告.md** | 双维度审查 + 跨平台测试 + 覆盖率达标 |
| Assess | 全角色 | 质量评估报告.md | 全量验证 + 打包产物验证 |
| Advance | PM | 项目复盘报告.md | 含最佳实践沉淀 |

---

## 最佳实践提示（Tauri + Superpowers）

### 对开发者
1. **Rust 测试先行**：写 Command 前，先想好怎么测
2. **小 Command 原则**：每个 Command 做一件事，便于测试
3. **错误类型明确**：使用 String 或自定义 Error 类型，不要 unwrap
4. **前端测试同步**：每写一个 Composable，同时写测试
5. **跨平台意识**：开发时就考虑 Win/Mac/Linux 差异

### 反模式警告
```
❌ 写完 Command 再补测试
   ✅ 正确：先写 #[test]，再写 impl

❌ 前端直接调用 invoke 不做封装
   ✅ 正确：封装 Composable，方便测试 mock

❌ cargo clippy 有 warning 忽略不管
   ✅ 正确：clippy 零 warning 才能提交

❌ 只在 Windows 上测试
   ✅ 正确：至少测试目标平台的子集

❌ 不做前后端联调测试
   ✅ 正确：Integration Test 验证完整流程
```

---

**规则版本**：v2.0  
**适用工作流**：6A + Superpowers 增强（Analyze → Architect → Assemble → Automate → Assess → Advance）  
**默认架构**：Tauri 2.x (Rust + Vue 3 + TypeScript)  
**核心理念**：Superpowers 四原则（TDD、系统性、简化、证据）  
**数字员工数量**：5个（BA、PM、Designer、Dev、QA）  
**Superpowers 技能**：14+ 个核心技能 + Tauri 专项技能  
**更新日期**：2026-04-07

## 版本更新记录

| 版本 | 日期 | 更新内容 |
|------|------|----------|
| **v2.0** | **2026-04-07** | **重大升级：集成Superpowers理念，引入TDD（Rust+前端）、子代理开发、系统化调试、任务拆分、代码审查、跨平台测试等机制** |
| v1.1 | 2026-04-01 | 初始版本，定义6A工作流和Tauri开发规范 |
