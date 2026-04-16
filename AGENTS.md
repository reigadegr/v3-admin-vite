# 仓库指南

## 项目结构与模块组织
本仓库是单体纯前端项目，基于 Vue 3 + Vite + TypeScript，不包含 `front/`、`backend/` 等子项目。

- `src/`：核心业务代码，包含页面、布局、路由、Pinia、插件、通用组件、组合式函数与接口封装。
- `tests/`：Vitest 测试文件，按功能模块组织，使用 `*.test.ts` 命名。
- `public/`：构建时原样拷贝的静态资源。
- `types/`：全局类型声明。

静态资源主要位于 `public/` 与 `src/common/assets/`。

## 构建、测试与开发命令
所有前端命令都在仓库根目录执行：

- `pnpm i` 安装依赖。
- `pnpm dev` 启动本地 Vite 开发服务器。
- `pnpm build` 执行类型检查并构建生产版本。
- `pnpm build:staging` 执行类型检查并构建预发版本。
- `pnpm preview` 预览构建产物。
- `pnpm lint` 运行 ESLint 并自动修复可修复问题。
- `pnpm test` 运行 Vitest 测试。

## 代码风格与命名规范
项目使用空格缩进并保持 2 空格，与根目录 `.editorconfig` 保持一致。

- Vue 单文件组件优先使用 `<script setup lang="ts">`。
- 组件文件优先使用 PascalCase 命名。
- 组合式函数、工具函数、变量与普通函数使用 camelCase 命名。
- 与接口契约保持一致的字段名应保留既有命名方式；若后端接口使用 snake_case，则不要擅自改为 camelCase。
- 样式与格式问题以 ESLint 结果为准，提交前应运行 `pnpm lint`。

## 测试规范
前端测试位于 `tests/`，使用 Vitest 和 `*.test.ts` 命名。

- 当页面交互、路由守卫、组合式函数、状态管理或 API 封装行为发生变化时，应新增或更新对应测试。
- 若改动影响 UI 逻辑，至少覆盖关键状态分支或核心交互。

## 提交说明
提交时必须遵循约定式提交（Conventional Commits）。

提交标题必须完整，并且标题使用中文。

提交正文的第一行必须是提交标题的英文翻译。

提交正文的主要内容必须采用中英逐句对照的写法，先中文，下一行对应英文，逐句成对出现。

提交信息必须包含 DCO。

DCO 中的姓名和邮箱必须从本地 git 配置获取，不得手写、不得使用占位符、不得替换为其他身份。

获取 DCO 身份时，使用以下命令读取本地配置：

```bash
git config user.name
git config user.email
```

生成 `Signed-off-by` 时，必须直接使用上面两个命令的输出结果。
