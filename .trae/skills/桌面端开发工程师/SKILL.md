---
name: "桌面端开发工程师"
description: "专门开发轻量桌面端应用（Tauri架构），负责核心功能实现、窗口管理、前后端通信、本地存储、自动更新等功能开发。Invoke when user needs to develop desktop app features with Tauri, implement window management, Rust commands, local storage, or auto-update functionality."
---

# 桌面端开发工程师

> 版本：v2.0 | 日期：2026-04-07 | 工作流节点：Assemble | 增强：Superpowers 技能体系

## 角色定位

负责基于Tauri架构的轻量桌面端应用核心功能开发，包括：
- 前端开发（React/Vue + TypeScript）
- Rust后端开发（Tauri Commands）
- 窗口管理
- 前后端通信（Tauri Commands）
- 本地数据存储（Tauri Store）
- 自动更新机制（Tauri Updater）
- 打包与分发配置

**Superpowers 技能标注：** TDD开发 + 系统化调试 + 子代理并行开发 + 代码审查 + 完成前验证

## Superpowers 技能体系

```
┌─────────────────────────────────────────────────────────────┐
│        桌面端开发工程师 - Superpowers 技能树                 │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ⚡test-driven-development (TDD)                            │
│  │  RED → GREEN → REFACTOR                                 │
│  │  Rust: #[cfg(test)] mod tests                           │
│  │  前端: Vitest vi.mock                                   │
│  │                                                         │
│  ⚡systematic-debugging                                     │
│  │  4步调试法（问题表征 → 假设生成 → 假设验证 → 根因定位）    │
│  │                                                         │
│  ⚡subagent-driven-development                              │
│  │  子代理并行开发（Rust Commands / 前端组件 / 联调测试）     │
│  │                                                         │
│  ⚡requesting-code-review                                   │
│  │  双维度代码审查（Rust clippy + ESLint）                  │
│  │                                                         │
│  ⚡verification-before-completion                           │
│  │  完成前验证清单                                          │
│  │                                                         │
│  ⚡using-git-worktrees                                      │
│  │  Git工作树隔离开发                                       │
│  │                                                         │
│  ⚡finishing-a-development-branch                           │
│  │  分支收尾流程                                            │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### ⚡test-driven-development (TDD)

测试驱动开发，遵循 RED → GREEN → REFACTOR 循环：

- **Rust 后端**：先写 `#[cfg(test)] mod tests`，再写实现
- **前端**：先写 Vitest 测试用例（`vi.mock`），再写 Composable/Store
- **核心原则**：每完成一个 Tauri Command，对应的 Rust 测试 + 前端调用测试必须同时完成

### ⚡systematic-debugging

4步系统化调试法：

1. **问题表征**：精确描述 Bug 现象、复现步骤、期望行为 vs 实际行为
2. **假设生成**：列出所有可能的原因，按可能性排序
3. **假设验证**：用最小可复现用例逐一验证假设
4. **根因定位**：确认根因后修复，并编写回归测试防止复发

### ⚡subagent-driven-development

子代理并行开发模式，将开发任务拆分为可并行的子任务：

- **子代理 A**：Rust Commands 开发（TDD 模式）
- **子代理 B**：前端组件开发（TDD 模式）
- **子代理 C**：联调测试（等待 A、B 完成后执行）

### ⚡requesting-code-review

双维度代码审查：

- **Rust 维度**：`cargo clippy` 零 warning、`cargo fmt` 格式正确、Command 错误处理完善
- **前端维度**：ESLint 无 error/warning、TypeScript 类型检查通过、测试覆盖率 > 80%

### ⚡verification-before-completion

完成前验证清单：

- [ ] 所有 Rust 单元测试通过
- [ ] 所有前端单元测试通过
- [ ] cargo clippy 零 warning
- [ ] ESLint 零 error/warning
- [ ] 代码审查通过
- [ ] 功能测试通过

### ⚡using-git-worktrees

Git 工作树隔离开发，每个功能分支使用独立的 Git Worktree，避免分支切换导致的环境冲突。

### ⚡finishing-a-development-branch

分支收尾流程：全量测试回归 → 构建验证 → 打包产物验证 → 用户决策（合并/Release/继续修改/丢弃）

## 技术栈

```
前端框架：Vue 3 + TypeScript
桌面框架：Tauri 2.x (Rust后端)
状态管理：Pinia
UI组件：Element Plus
本地存储：Tauri Store Plugin / SQLite
构建工具：Vite
tauri-cli：用于构建和打包

【Superpowers 增强测试工具】
测试框架（Rust）：cargo test + #[cfg(test)]
测试框架（前端）：Vitest / Jest
覆盖率工具：tarpaulin (Rust) / c8 (前端)
代码检查：cargo clippy (Rust) + ESLint (前端)
```

## 触发条件

**关键词：**
- "开发"、"实现"、"编码"
- "桌面端"、"窗口"、"菜单"
- "Tauri"、"Rust"、"命令"
- "自动更新"、"打包"

**场景：**
- 需要开发Tauri桌面应用功能
- 需要配置窗口管理
- 需要实现Rust Commands
- 需要配置自动更新
- 需要打包应用

## 核心能力

### 1. 项目初始化

```bash
# 创建Tauri项目
npm create tauri-app@latest

# 或使用cargo
cargo install create-tauri-app
cargo create-tauri-app

# 安装依赖
cd tauri-app
npm install

# 安装常用插件
npm install @tauri-apps/plugin-dialog @tauri-apps/plugin-fs
npm install @tauri-apps/plugin-store @tauri-apps/plugin-updater
```

### 2. 前端与Rust通信（Tauri Commands）

```rust
// src-tauri/src/commands/file.rs
use tauri::command;
use std::fs;

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
        
        Ok(Some(FileInfo { path: path_str, content }))
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
        fs::write(file.path(), content).map_err(|e| e.to_string())?;
        Ok(Some(file.path().to_string_lossy().to_string()))
    } else {
        Ok(None)
    }
}
```

```typescript
// 前端调用Rust命令 (Vue 3 + TypeScript)
// src/utils/tauri.ts
import { invoke } from '@tauri-apps/api/core';
import { open, save } from '@tauri-apps/plugin-dialog';
import { readTextFile, writeTextFile } from '@tauri-apps/plugin-fs';

interface FileInfo {
  path: string;
  content: string;
}

// 调用Rust命令
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
    const result = await invoke<string | null>('save_file_dialog', { content, filename });
    return result;
  } catch (error) {
    console.error('保存文件失败:', error);
    throw error;
  }
};

// 使用Tauri插件（推荐方式）
export const openFileWithPlugin = async (): Promise<{ path: string; content: string } | null> => {
  const selected = await open({
    multiple: false,
    filters: [{ name: 'Text', extensions: ['txt', 'json'] }]
  });
  if (selected) {
    const content = await readTextFile(selected as string);
    return { path: selected as string, content };
  }
  return null;
};

export const saveFileWithPlugin = async (content: string, suggestedFilename?: string): Promise<string | null> => {
  const filePath = await save({
    defaultPath: suggestedFilename,
    filters: [{ name: 'Text', extensions: ['txt'] }]
  });
  if (filePath) {
    await writeTextFile(filePath, content);
  }
  return filePath;
};
```

#### TDD 示例：Rust Commands 测试

```rust
// src-tauri/src/commands/file.rs (TDD 测试模块)
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

    #[test]
    fn test_file_info_serialization() {
        let info = FileInfo {
            path: "/test/path.json".to_string(),
            content: r#"{"key": "value"}"#.to_string(),
        };
        
        let json = serde_json::to_string(&info).unwrap();
        let deserialized: FileInfo = serde_json::from_str(&json).unwrap();
        
        assert_eq!(deserialized.path, info.path);
        assert_eq!(deserialized.content, info.content);
    }

    #[test]
    fn test_file_info_empty_content() {
        let info = FileInfo {
            path: "/test/empty.txt".to_string(),
            content: "".to_string(),
        };
        
        assert_eq!(info.path, "/test/empty.txt");
        assert!(info.content.is_empty());
    }

    #[test]
    fn test_file_info_special_characters() {
        let info = FileInfo {
            path: "/test/文件.txt".to_string(),
            content: "你好世界\n换行\t制表符".to_string(),
        };
        
        assert_eq!(info.path, "/test/文件.txt");
        assert!(info.content.contains('\n'));
        assert!(info.content.contains('\t'));
    }
}
```

#### TDD 示例：前端 Vitest 测试

```typescript
// src/utils/__tests__/tauri.test.ts
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

        it('should return null when user cancels dialog', async () => {
            const { invoke } = await import('@tauri-apps/api/core')
            vi.mocked(invoke).mockResolvedValue(null)

            const { openFile } = await import('../tauri')
            const result = await openFile()

            expect(result).toBeNull()
        })

        it('should throw error when invoke fails', async () => {
            const { invoke } = await import('@tauri-apps/api/core')
            vi.mocked(invoke).mockRejectedValue(new Error('Tauri error'))

            const { openFile } = await import('../tauri')
            
            await expect(openFile()).rejects.toThrow()
        })
    })

    describe('saveFile', () => {
        it('should call invoke with content and filename', async () => {
            const { invoke } = await import('@tauri-apps/api/core')
            vi.mocked(invoke).mockResolvedValue('/test/saved.txt')

            const { saveFile } = await import('../tauri')
            const result = await saveFile('test content', 'saved.txt')

            expect(invoke).toHaveBeenCalledWith('save_file_dialog', {
                content: 'test content',
                filename: 'saved.txt'
            })
            expect(result).toBe('/test/saved.txt')
        })

        it('should return null when user cancels save dialog', async () => {
            const { invoke } = await import('@tauri-apps/api/core')
            vi.mocked(invoke).mockResolvedValue(null)

            const { saveFile } = await import('../tauri')
            const result = await saveFile('content', 'file.txt')

            expect(result).toBeNull()
        })
    })
})
```

### 3. 窗口管理

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

#[command]
pub fn show_window(app: AppHandle) {
    if let Some(window) = app.get_webview_window("main") {
        let _ = window.show();
        let _ = window.set_focus();
    }
}

#[command]
pub fn hide_window(app: AppHandle) {
    if let Some(window) = app.get_webview_window("main") {
        let _ = window.hide();
    }
}
```

```typescript
// 前端窗口控制 (Vue Composable)
// src/composables/useWindow.ts
import { invoke } from '@tauri-apps/api/core';
import { getCurrentWindow } from '@tauri-apps/api/window';

export const useWindow = () => {
  const appWindow = getCurrentWindow();

  const minimize = () => appWindow.minimize();
  const maximize = () => appWindow.toggleMaximize();
  const close = () => appWindow.close();
  const toggleFullscreen = () => invoke('toggle_fullscreen');
  const setAlwaysOnTop = (value: boolean) => invoke('set_always_on_top', { alwaysOnTop: value });
  const show = () => appWindow.show();
  const hide = () => appWindow.hide();

  return { minimize, maximize, close, toggleFullscreen, setAlwaysOnTop, show, hide };
};
```

#### TDD 示例：前端 useWindow Composable 测试

```typescript
// src/composables/__tests__/useWindow.test.ts
import { describe, it, expect, vi, beforeEach } from 'vitest'

vi.mock('@tauri-apps/api/core', () => ({
    invoke: vi.fn()
}))

vi.mock('@tauri-apps/api/window', () => ({
    getCurrentWindow: vi.fn(() => ({
        minimize: vi.fn().mockResolvedValue(undefined),
        toggleMaximize: vi.fn().mockResolvedValue(undefined),
        close: vi.fn().mockResolvedValue(undefined),
        show: vi.fn().mockResolvedValue(undefined),
        hide: vi.fn().mockResolvedValue(undefined),
    }))
}))

describe('useWindow', () => {
    beforeEach(() => {
        vi.clearAllMocks()
    })

    it('should provide all window control functions', async () => {
        const { useWindow } = await import('../useWindow')
        const windowControls = useWindow()

        expect(typeof windowControls.minimize).toBe('function')
        expect(typeof windowControls.maximize).toBe('function')
        expect(typeof windowControls.close).toBe('function')
        expect(typeof windowControls.toggleFullscreen).toBe('function')
        expect(typeof windowControls.setAlwaysOnTop).toBe('function')
        expect(typeof windowControls.show).toBe('function')
        expect(typeof windowControls.hide).toBe('function')
    })

    it('should call invoke for toggleFullscreen', async () => {
        const { invoke } = await import('@tauri-apps/api/core')
        vi.mocked(invoke).mockResolvedValue(undefined)

        const { useWindow } = await import('../useWindow')
        const { toggleFullscreen } = useWindow()
        await toggleFullscreen()

        expect(invoke).toHaveBeenCalledWith('toggle_fullscreen')
    })

    it('should call invoke with correct params for setAlwaysOnTop', async () => {
        const { invoke } = await import('@tauri-apps/api/core')
        vi.mocked(invoke).mockResolvedValue(undefined)

        const { useWindow } = await import('../useWindow')
        const { setAlwaysOnTop } = useWindow()
        await setAlwaysOnTop(true)

        expect(invoke).toHaveBeenCalledWith('set_always_on_top', { alwaysOnTop: true })
    })
})
```

### 4. 本地数据存储

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
```

```typescript
// 前端存储使用 (Pinia)
// src/stores/appStore.ts
import { defineStore } from 'pinia';
import { Store } from '@tauri-apps/plugin-store';

const store = new Store('store.bin');

interface AppSettings {
  theme: 'light' | 'dark' | 'system';
  language: string;
  windowBounds: {
    width: number;
    height: number;
    x?: number;
    y?: number;
  };
}

export const useAppStore = defineStore('app', {
  state: () => ({
    settings: null as AppSettings | null,
    recentFiles: [] as string[],
  }),

  actions: {
    async loadSettings() {
      this.settings = await store.get<AppSettings>('settings');
    },

    async saveSettings(settings: AppSettings) {
      await store.set('settings', settings);
      await store.save();
      this.settings = settings;
    },

    async loadRecentFiles() {
      this.recentFiles = (await store.get<string[]>('recentFiles')) || [];
    },

    async addRecentFile(filePath: string) {
      const filtered = this.recentFiles.filter(f => f !== filePath);
      filtered.unshift(filePath);
      const newFiles = filtered.slice(0, 10);
      await store.set('recentFiles', newFiles);
      await store.save();
      this.recentFiles = newFiles;
    },

    async clearRecentFiles() {
      await store.set('recentFiles', []);
      await store.save();
      this.recentFiles = [];
    }
  }
});
```

#### TDD 示例：Rust Store 测试

```rust
// src-tauri/src/commands/store.rs (TDD 测试模块)
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

    #[test]
    fn test_store_value_nested_object() {
        let value = serde_json::json!({
            "windowBounds": {
                "width": 1200,
                "height": 800,
                "x": 100,
                "y": 100
            }
        });
        
        assert_eq!(value["windowBounds"]["width"], 1200);
        assert_eq!(value["windowBounds"]["height"], 800);
    }

    #[test]
    fn test_store_value_array() {
        let value = serde_json::json!([
            "/path/file1.txt",
            "/path/file2.txt",
            "/path/file3.txt"
        ]);
        
        assert_eq!(value.as_array().unwrap().len(), 3);
        assert_eq!(value[0], "/path/file1.txt");
    }

    #[test]
    fn test_store_value_null_handling() {
        let value: Value = Value::Null;
        
        assert!(value.is_null());
    }
}
```

#### TDD 示例：前端 Pinia Store 测试

```typescript
// src/stores/__tests__/appStore.test.ts
import { describe, it, expect, vi, beforeEach } from 'vitest'
import { setActivePinia, createPinia } from 'pinia'

vi.mock('@tauri-apps/plugin-store', () => ({
    Store: vi.fn().mockImplementation(() => ({
        get: vi.fn().mockResolvedValue(null),
        set: vi.fn().mockResolvedValue(undefined),
        save: vi.fn().mockResolvedValue(undefined),
        delete: vi.fn().mockResolvedValue(undefined),
    }))
}))

describe('appStore', () => {
    beforeEach(() => {
        setActivePinia(createPinia())
        vi.clearAllMocks()
    })

    it('should initialize with default state', async () => {
        const { useAppStore } = await import('../appStore')
        const store = useAppStore()

        expect(store.settings).toBeNull()
        expect(store.recentFiles).toEqual([])
    })

    it('should add recent file and limit to 10', async () => {
        const { useAppStore } = await import('../appStore')
        const store = useAppStore()

        for (let i = 0; i < 15; i++) {
            await store.addRecentFile(`/path/file${i}.txt`)
        }

        expect(store.recentFiles.length).toBe(10)
        expect(store.recentFiles[0]).toBe('/path/file14.txt')
    })

    it('should deduplicate recent files', async () => {
        const { useAppStore } = await import('../appStore')
        const store = useAppStore()

        await store.addRecentFile('/path/file.txt')
        await store.addRecentFile('/path/other.txt')
        await store.addRecentFile('/path/file.txt')

        expect(store.recentFiles.length).toBe(2)
        expect(store.recentFiles[0]).toBe('/path/file.txt')
    })

    it('should clear all recent files', async () => {
        const { useAppStore } = await import('../appStore')
        const store = useAppStore()

        await store.addRecentFile('/path/file.txt')
        await store.clearRecentFiles()

        expect(store.recentFiles).toEqual([])
    })
})
```

### 5. 系统托盘

```rust
// src-tauri/src/lib.rs
use tauri::{AppHandle, Manager};
use tauri::menu::{Menu, MenuItem};
use tauri::tray::TrayIconBuilder;

pub fn setup_tray(app: &mut tauri::App) -> Result<(), Box<dyn std::error::Error>> {
    let show_i = MenuItem::with_id(app, "show", "显示主窗口", true, None::<&str>)?;
    let settings_i = MenuItem::with_id(app, "settings", "设置", true, None::<&str>)?;
    let quit_i = MenuItem::with_id(app, "quit", "退出", true, None::<&str>)?;
    
    let menu = Menu::with_items(app, &[&show_i, &settings_i, &quit_i])?;
    
    TrayIconBuilder::new()
        .icon(app.default_window_icon().unwrap().clone())
        .menu(&menu)
        .on_menu_event(|app, event| match event.id.as_ref() {
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
        })
        .on_tray_icon_event(|tray, event| {
            if let tauri::tray::TrayIconEvent::Click { .. } = event {
                let app = tray.app_handle();
                if let Some(window) = app.get_webview_window("main") {
                    let _ = window.show();
                    let _ = window.set_focus();
                }
            }
        })
        .build(app)?;
    
    Ok(())
}
```

### 6. 自动更新

```rust
// src-tauri/src/lib.rs
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
// 前端更新检查
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
            case 'Started':
              console.log('开始下载更新...');
              break;
            case 'Progress':
              console.log(`下载进度: ${event.data.chunkLength}`);
              break;
            case 'Finished':
              console.log('下载完成');
              break;
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

#### TDD 示例：前端 updater 工具测试

```typescript
// src/utils/__tests__/updater.test.ts
import { describe, it, expect, vi, beforeEach } from 'vitest'

vi.mock('@tauri-apps/plugin-updater', () => ({
    check: vi.fn()
}))

vi.mock('@tauri-apps/plugin-dialog', () => ({
    ask: vi.fn(),
    message: vi.fn()
}))

describe('updater utils', () => {
    beforeEach(() => {
        vi.clearAllMocks()
    })

    it('should do nothing when no update available', async () => {
        const { check } = await import('@tauri-apps/plugin-updater')
        vi.mocked(check).mockResolvedValue(undefined)

        const { checkForUpdates } = await import('../updater')
        await checkForUpdates()

        const { ask } = await import('@tauri-apps/plugin-dialog')
        expect(ask).not.toHaveBeenCalled()
    })

    it('should ask user when update is available', async () => {
        const { check } = await import('@tauri-apps/plugin-updater')
        const mockUpdate = {
            version: '2.0.0',
            downloadAndInstall: vi.fn().mockResolvedValue(undefined),
        }
        vi.mocked(check).mockResolvedValue(mockUpdate as any)

        const { ask } = await import('@tauri-apps/plugin-dialog')
        vi.mocked(ask).mockResolvedValue(false)

        const { checkForUpdates } = await import('../updater')
        await checkForUpdates()

        expect(ask).toHaveBeenCalledWith(
            '发现新版本 2.0.0，是否现在下载？',
            { title: '发现新版本', kind: 'info' }
        )
        expect(mockUpdate.downloadAndInstall).not.toHaveBeenCalled()
    })

    it('should download and install when user confirms', async () => {
        const { check } = await import('@tauri-apps/plugin-updater')
        const mockUpdate = {
            version: '2.0.0',
            downloadAndInstall: vi.fn().mockResolvedValue(undefined),
        }
        vi.mocked(check).mockResolvedValue(mockUpdate as any)

        const { ask, message } = await import('@tauri-apps/plugin-dialog')
        vi.mocked(ask).mockResolvedValue(true)

        const { checkForUpdates } = await import('../updater')
        await checkForUpdates()

        expect(mockUpdate.downloadAndInstall).toHaveBeenCalled()
        expect(message).toHaveBeenCalledWith(
            '更新已下载完成，应用将重启',
            { title: '更新完成' }
        )
    })

    it('should handle check update error gracefully', async () => {
        const { check } = await import('@tauri-apps/plugin-updater')
        vi.mocked(check).mockRejectedValue(new Error('Network error'))

        const consoleSpy = vi.spyOn(console, 'error').mockImplementation(() => {})

        const { checkForUpdates } = await import('../updater')
        await checkForUpdates()

        expect(consoleSpy).toHaveBeenCalledWith('检查更新失败:', expect.any(Error))
        consoleSpy.mockRestore()
    })
})
```

### 7. 主入口配置

```rust
// src-tauri/src/lib.rs
use tauri::{AppHandle, Manager};

#[cfg_attr(mobile, tauri::mobile_entry_point)]
pub fn run() {
    tauri::Builder::default()
        .plugin(tauri_plugin_store::Builder::new().build())
        .plugin(tauri_plugin_dialog::init())
        .plugin(tauri_plugin_fs::init())
        .plugin(tauri_plugin_updater::Builder::new().build())
        .plugin(tauri_plugin_shell::init())
        .invoke_handler(tauri::generate_handler![
            commands::file::open_file_dialog,
            commands::file::save_file_dialog,
            commands::window::minimize_window,
            commands::window::maximize_window,
            commands::window::close_window,
            commands::window::toggle_fullscreen,
            commands::window::set_always_on_top,
            commands::store::get_store_value,
            commands::store::set_store_value,
            commands::store::delete_store_value,
        ])
        .setup(|app| {
            // 设置系统托盘
            setup_tray(app)?;
            
            // 检查更新
            let handle = app.handle().clone();
            tauri::async_runtime::spawn(async move {
                if let Err(e) = check_update(handle).await {
                    eprintln!("检查更新失败: {}", e);
                }
            });
            
            Ok(())
        })
        .run(tauri::generate_context!())
        .expect("error while running tauri application");
}
```

```rust
// src-tauri/src/main.rs
#![cfg_attr(not(debug_assertions), windows_subsystem = "windows")]

fn main() {
    tauri_desktop_app_lib::run();
}
```

## 系统化调试（⚡ systematic-debugging）

### 4步调试法

当遇到 Bug 或异常行为时，严格按照以下 4 步执行：

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔍 系统化调试 - 4步法（Tauri 桌面端专用）
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Step 1: 问题表征（Characterize）
├── 精确描述 Bug 现象
├── 记录复现步骤（1-2-3...）
├── 明确期望行为 vs 实际行为
├── 确认影响范围（Rust后端 / 前端 / 前后端通信）
└── 收集错误日志（cargo 日志 / DevTools Console）

Step 2: 假设生成（Hypothesize）
├── 列出所有可能原因，按可能性排序
├── 常见 Tauri 问题假设：
│   ├── Command 参数类型不匹配？
│   ├── Rust serde 序列化/反序列化问题？
│   ├── 前端 invoke 调用参数名错误？
│   ├── 异步操作未正确 await？
│   ├── Tauri 权限配置缺失？
│   ├── 文件路径跨平台差异？
│   └── 状态管理竞态条件？
└── 每个假设标注验证方法

Step 3: 假设验证（Test Hypotheses）
├── 用最小可复现用例逐一验证
├── Rust 端验证：
│   ├── cargo test 运行相关测试
│   ├── 添加临时 println! 日志
│   └── cargo clippy 检查潜在问题
├── 前端验证：
│   ├── DevTools Console 检查网络/日志
│   ├── Vue DevTools 检查状态
│   └── 添加临时 console.log 日志
└── 通信验证：
    ├── 确认 invoke 命令名一致
    └── 确认参数序列化格式一致

Step 4: 根因定位（Root Cause）
├── 确认根因后编写修复
├── 编写回归测试防止复发
│   ├── Rust: #[cfg(test)] 新增测试用例
│   └── 前端: Vitest 新增测试用例
├── 运行 cargo test + npx vitest 确认全部通过
└── 记录 Bug 原因和修复方案

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 常见 Tauri 调试场景

| 场景 | 可能原因 | 调试方法 |
|------|----------|----------|
| Command 调用返回错误 | 参数类型/名称不匹配 | 检查 Rust 函数签名与前端 invoke 参数 |
| 文件操作失败 | 路径跨平台差异 | 使用 PathBuf 代替字符串拼接 |
| 窗口操作无响应 | AppHandle 获取失败 | 检查窗口标识符是否正确 |
| Store 读写异常 | Store 未正确初始化 | 确认 tauri_plugin_store 已注册 |
| 前端状态不同步 | 异步操作竞态 | 检查 await 是否遗漏 |
| 打包后功能异常 | CSP 或权限限制 | 检查 tauri.conf.json 权限配置 |

## 子代理并行开发模式（⚡ subagent-driven-development）

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🚀 Tauri 桌面端 - 子代理并行开发模式
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

主代理（协调者）
    │
    ├── 分析实施计划，拆分为独立子任务
    │
    ├── 子代理 A: Rust Commands 开发（TDD 模式）
    │   ├── Task: 文件操作 Commands
    │   │   ├── RED: 编写 #[cfg(test)] 测试
    │   │   ├── GREEN: 实现 open_file_dialog / save_file_dialog
    │   │   └── REFACTOR: 提取公共逻辑，clippy 通过
    │   │
    │   ├── Task: 窗口管理 Commands
    │   │   ├── RED: 编写 #[cfg(test)] 测试
    │   │   ├── GREEN: 实现 minimize/maximize/close 等命令
    │   │   └── REFACTOR: 统一错误处理，clippy 通过
    │   │
    │   └── Task: 存储 Commands
    │       ├── RED: 编写 #[cfg(test)] 测试
    │       ├── GREEN: 实现 get/set/delete_store_value
    │       └── REFACTOR: 优化序列化逻辑，clippy 通过
    │
    ├── 子代理 B: 前端组件开发（TDD 模式）
    │   ├── Task: Composables 开发
    │   │   ├── RED: 编写 Vitest 测试（vi.mock）
    │   │   ├── GREEN: 实现 useFile / useWindow
    │   │   └── REFACTOR: 添加 loading/error 状态
    │   │
    │   ├── Task: Pinia Stores 开发
    │   │   ├── RED: 编写 Vitest 测试
    │   │   ├── GREEN: 实现 appStore / fileStore
    │   │   └── REFACTOR: 优化持久化逻辑
    │   │
    │   └── Task: UI 组件开发
    │       ├── RED: 编写组件测试
    │       ├── GREEN: 实现页面和组件
    │       └── REFACTOR: 优化交互和样式
    │
    └── 子代理 C: 联调测试（等待 A、B 完成）
        ├── 集成测试: Tauri Commands 完整流程
        ├── 跨平台测试: Windows/macOS/Linux 兼容性
        └── 性能测试: 启动时间、内存占用

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

并行开发注意事项：
1. 子代理 A 和 B 可同时启动，互不阻塞
2. 子代理 C 必须等待 A 和 B 完成后启动
3. 每个子代理完成后必须运行对应测试
4. 主代理负责合并和最终集成验证
```

## 工作流程

### Step 1: 理解需求
- 阅读PRD文档和技术方案
- 明确功能范围和技术选型
- 确认开发优先级

### Step 2: 项目初始化

```bash
# 创建Tauri项目（Vue模板）
npm create tauri-app@latest

# 选择以下配置：
# - Project name: my-tauri-app
# - Identifier: com.yourcompany.myapp
# - Frontend template: Vue
# - UI flavor: TypeScript

# 进入项目目录
cd my-tauri-app

# 安装依赖
npm install

# 安装Element Plus
npm install element-plus @element-plus/icons-vue

# 安装Pinia
npm install pinia

# 安装Vue Router
npm install vue-router@4

# 安装Tauri插件
npm install @tauri-apps/plugin-dialog @tauri-apps/plugin-fs
npm install @tauri-apps/plugin-store @tauri-apps/plugin-updater
npm install @tauri-apps/plugin-shell

# 安装测试工具（Superpowers 增强）
npm install -D vitest @vue/test-utils happy-dom
npm install -D @vitest/coverage-v8

# 启动开发服务器
npm run tauri dev
```

### Step 3: TDD 核心功能开发（⚡ Superpowers 增强）

每个功能模块遵循 RED → GREEN → REFACTOR 循环：

**RED 阶段：编写失败的测试**
```bash
# Rust: 编写 #[cfg(test)] 测试模块
# 前端: 编写 Vitest 测试用例（vi.mock）
# 运行测试确认失败
cargo test                    # Rust 测试
npx vitest run                # 前端测试
```

**GREEN 阶段：编写最少实现**
```bash
# 实现功能代码（仅满足测试通过）
# 运行测试确认通过
cargo test                    # Rust 测试
npx vitest run                # 前端测试
```

**REFACTOR 阶段：重构优化**
```bash
# 优化代码结构、提取公共逻辑
# 运行全量检查确认无回归
cargo test                    # Rust 测试
cargo clippy                  # Rust 代码质量
cargo fmt --check             # Rust 格式检查
npx vitest run                # 前端测试
npx eslint .                  # 前端代码质量
```

开发内容：
- 前端开发（Vue 3组件、页面）
- Rust后端开发（Tauri Commands）
- 前后端通信实现

### Step 4: 功能测试
- 前端单元测试（Vitest）
- Rust单元测试（`cargo test`）
- 集成测试
- 跨平台测试

### Step 5: 打包配置
- 配置`tauri.conf.json`
- 设置多平台打包（MSI/DMG/AppImage）
- 配置自动更新（Tauri Updater）

## 输出物

1. **源代码**
   - `src/` - 前端代码（Vue 3 + TypeScript）
   - `src/components/` - Vue组件
   - `src/views/` - 页面视图
   - `src/composables/` - 组合式函数
   - `src/composables/__tests__/` - Composables 单元测试
   - `src/stores/` - Pinia状态管理
   - `src/stores/__tests__/` - Store 单元测试
   - `src/utils/` - 工具函数
   - `src/utils/__tests__/` - 工具函数单元测试
   - `src-tauri/src/` - Rust后端代码
   - `src-tauri/src/commands/` - Tauri Commands
   - `src-tauri/src/services/` - Rust服务层
   - `src-tauri/src/utils/` - Rust工具函数

2. **配置文件**
   - `package.json` - 前端依赖
   - `src-tauri/Cargo.toml` - Rust依赖
   - `src-tauri/tauri.conf.json` - Tauri配置
   - `vite.config.ts` - Vite配置

3. **测试文件（Superpowers 增强）**
   - `src/**/__tests__/*.test.ts` - 前端单元测试
   - `src-tauri/src/**/tests` - Rust 单元测试模块
   - `tests/integration/` - 集成测试
   - `tests/e2e/` - 端到端测试

4. **文档**
   - `README.md` - 项目说明
   - `DEVELOPMENT.md` - 开发文档
   - `CHANGELOG.md` - 更新日志

## 检查清单

### 基础检查
- [ ] 项目结构符合Tauri规范
- [ ] 前端代码通过 ESLint / TypeScript 检查
- [ ] Rust代码通过 cargo check / clippy 检查
- [ ] Tauri Commands功能正常
- [ ] 窗口管理功能正常
- [ ] 本地存储功能正常
- [ ] 自动更新配置完成
- [ ] 跨平台兼容性测试通过
- [ ] 打包产物验证通过

### Superpowers 增强检查（⚡）
- [ ] 每个Rust Command有对应#[cfg(test)]测试
- [ ] 每个前端Composable有对应Vitest测试
- [ ] 每个Pinia Store有对应Vitest测试
- [ ] 每个前端工具函数有对应Vitest测试
- [ ] cargo clippy无warning
- [ ] cargo fmt格式正确
- [ ] ESLint无error/warning
- [ ] TypeScript类型检查通过
- [ ] 测试覆盖率>80%
- [ ] 所有Rust单元测试通过（cargo test）
- [ ] 所有前端单元测试通过（npx vitest）
- [ ] 集成测试通过
- [ ] 代码审查通过（双维度：Rust + 前端）

## 反模式警告

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚠️  Tauri 开发常见反模式（Superpowers 警告）
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

❌ 写完Command再补测试
   ✅ 正确：先写 #[test]，再写 impl

❌ 前端直接调用invoke不封装
   ✅ 正确：封装Composable，方便测试mock

❌ cargo clippy有warning忽略不管
   ✅ 正确：clippy零warning才提交

❌ 只在Windows上测试就认为跨平台OK
   ✅ 正确：至少验证目标平台的兼容性

❌ 不做前后端联调测试
   ✅ 正确：集成测试验证完整流程

❌ Rust代码中大量unwrap()
   ✅ 正确：使用 ? 操作符或 map_err 提供明确错误信息

❌ 前端Composable没有loading/error状态
   ✅ 正确：统一封装异步状态管理

❌ Store数据未做类型约束
   ✅ 正确：使用TypeScript接口定义数据结构

❌ 跳过REFACTOR阶段直接进入下一个Task
   ✅ 正确：每次TDD循环必须完成 RED→GREEN→REFACTOR

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

## 最佳实践

1. **安全性**
   - 使用Tauri的安全模型（前端与后端隔离）
   - 验证所有Command输入参数
   - 使用Tauri的权限系统

2. **性能**
   - 利用Rust的高性能处理耗时任务
   - 前端使用虚拟列表、懒加载
   - 优化打包体积

3. **用户体验**
   - 窗口状态记忆
   - 优雅的启动/退出
   - 系统托盘支持
   - 自动更新提示

4. **开发效率**
   - 使用Tauri的HMR热更新
   - 前端和Rust并行开发
   - 使用cargo watch自动编译

5. **测试驱动（⚡ Superpowers 增强）**
   - Rust: 每个Command先写 `#[cfg(test)]` 测试模块
   - 前端: 每个Composable/Store先写 Vitest 测试
   - 遵循 RED → GREEN → REFACTOR 循环
   - 测试覆盖率目标 > 80%
   - cargo clippy 零 warning 标准

6. **系统化调试（⚡ Superpowers 增强）**
   - 遇到Bug严格遵循4步调试法
   - 先表征问题，再生成假设，逐一验证
   - 每个修复必须附带回归测试
   - 记录Bug原因和修复方案，积累调试经验

7. **代码质量（⚡ Superpowers 增强）**
   - Rust: cargo clippy + cargo fmt 作为提交前必须检查
   - 前端: ESLint + TypeScript strict mode
   - 每个功能模块完成后进行代码审查
   - 使用 Git Worktree 隔离功能分支开发

## 版本更新记录

| 版本 | 日期 | 更新内容 |
|------|------|----------|
| **v2.0** | **2026-04-07** | **重大升级：集成Superpowers技能体系，新增TDD开发流程（Rust+前端Vitest）、系统化调试4步法、子代理并行开发模式、双维度代码审查、完成前验证清单、反模式警告** |
| v1.1 | 2026-04-01 | 初始版本，定义桌面端开发工程师角色和Tauri开发规范 |
