# 开发指南

## 项目架构

- **多上下文扩展**：支持 background、popup、options、content script、devtools、side panel 和 offscreen 页面。
- **文件路由**：UI 路由从 `src/ui/*/pages` 自动注册。
- **组合式与模块化**：使用 Vue 3 Composition API、Pinia 状态管理，以及用于国际化、主题、存储等的组合式函数。
- **UI**：使用 Nuxt/UI v3 和 shadcn-vue 组件库，样式使用 Tailwind CSS 4。
- **WebExtension 工具**：使用 `webext-bridge` 和 `webextension-polyfill` 实现浏览器 API 兼容性。

## 文件结构

- `src/assets/`：全局资源（CSS、图片）
- `src/background/`：后台脚本（生命周期、安装/更新逻辑）
- `src/components/`：共享 Vue 组件
- `src/composables/`：Vue 组合式函数（hooks）
- `src/content-script/`：内容脚本（DOM 注入、页面交互）
- `src/devtools/`、`src/offscreen/`、`src/side-panel/`：专用扩展上下文
- `src/stores/`：Pinia 状态管理
- `src/types/`：TypeScript 类型定义
- `src/ui/`：UI 入口（popup、options、setup 等）
- `src/utils/`：共享工具（路由、i18n、pinia 等）

## 设计原则

- **类型安全**：全面使用严格模式的 TypeScript。
- **组合式 API**：使用 `<script setup>` 和组合式函数实现逻辑复用。
- **自动导入**：函数、状态管理和组件自动导入。
- **单一职责**：每个文件/文件夹都有明确、专注的用途。
- **最小样板代码**：偏好简洁、可读的代码。

## 代码规范

- 使用 TypeScript 和 Vue 3 Composition API。
- 使用 ESLint 和 Prettier 强制代码风格。
- 使用 Pinia 管理状态，Vue Router 处理导航。
- 新增 UI 页面放在 `src/ui/<context>/pages/`。
- 使用组合式函数处理跨领域关注点（主题、i18n、存储）。
- 优雅处理错误；在 background/content 脚本中使用 `console.info` 记录日志。

## 最佳实践

- 保持组件小而专注。
- 使用文件路由管理 UI。
- 优先使用组合式函数实现共享逻辑。
- 在 Chrome 和 Firefox 中测试。
- 使用 shadcn-vue 实现可访问、可定制的 UI 组件。