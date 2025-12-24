# SoloBlog Frontend

SoloBlog 前端项目是一个基于 **Nuxt 3** (Vue 3) 构建的现代化 SSR (服务端渲染) 博客应用。项目高度还原了稀土掘金 (Juejin) 的 UI 设计，旨在提供沉浸式的阅读体验和高效的创作者服务。

## 🏗 技术栈

- **框架**: [Nuxt 3](https://nuxt.com/) (基于 Vue 3)
- **UI 组件库**: [TDesign Vue Next](https://tdesign.tencent.com/vue-next) (腾讯开源企业级 UI)
- **语言**: TypeScript
- **构建工具**: Vite
- **Markdown 渲染**: ByteMD (支持 GFM, Highlight.js)
- **状态管理**: Nuxt Composables (基于 Vue Reactivity)
- **图标库**: TDesign Icons

## 🏛 系统架构与设计

### 1. 页面路由架构 (`pages/`)

利用 Nuxt 的文件系统路由，构建了清晰的页面结构：

- **首页 (`/`)**: 综合文章流，包含推荐、最新、热榜等分类，采用左-中-右三栏布局。
- **文章详情页 (`/article/:id`)**:
  - **SSR 渲染**: 确保 SEO 友好。
  - **沉浸式阅读**: 集成 ByteMD Viewer 渲染 Markdown 内容。
  - **互动区**: 悬浮点赞/评论/分享面板，右侧目录导航。
- **小册中心 (`/booklet`)**:
  - 展示付费课程列表，支持多维度筛选（后端/前端/AI）。
  - 包含课程封面、作者信息、价格与优惠展示。
- **创作者中心 (`/creator`)**:
  - **独立布局**: 使用 `layouts/creator.vue`，提供侧边栏管理菜单。
  - **功能**: 数据仪表盘（可视化图表）、内容管理、创作任务奖励。
- **认证体系**:
  - 基于 `TDesign Dialog` 的弹窗式登录/注册流程，不打断用户浏览。

### 2. 组件化设计 (`components/`)

- **通用组件**:
  - `AppHeader`: 全局顶部导航，集成搜索、创作者入口、用户菜单及登录/注册弹窗触发器。
  - `LoginDialog` / `RegisterDialog`: 封装完善的认证交互组件。
- **业务组件**:
  - 复用性高的 UI 模块，如文章卡片、小册卡片等。

### 3. 布局系统 (`layouts/`)

- **Default Layout**: 适用于前台浏览页面（首页、文章页），包含通用的 Header 和 Footer。
- **Creator Layout**: 专为后台管理设计，左侧固定导航栏，右侧内容区，提供沉浸式管理体验。

### 4. 核心逻辑复用 (`composables/`)

- **`useAuth`**: 封装用户认证逻辑（登录、注册、退出、用户信息获取），管理全局用户状态。
- **`useFetch`**: 利用 Nuxt 内置的数据请求钩子与后端 API 通信。

## 📂 目录结构说明

```
frontend/
├── assets/             # 静态资源 (CSS/Images)
├── components/         # Vue 组件 (Header, Dialogs)
├── composables/        # 组合式函数 (useAuth)
├── layouts/            # 页面布局模板
├── pages/              # 页面路由视图
│   ├── article/        # 文章详情
│   ├── booklet/        # 小册页面
│   ├── creator/        # 创作者中心
│   └── index.vue       # 首页
├── plugins/            # Nuxt 插件 (TDesign)
└── nuxt.config.ts      # 项目配置
```

## 🚀 启动说明

1.  **安装依赖**:
    ```bash
    npm install
    ```
2.  **启动开发服务器**:
    ```bash
    npm run dev
    ```
    服务默认运行在 `http://localhost:3000`。

## 🎨 特色功能

- **深度定制 UI**: 1:1 还原掘金风格，包括配色、间距、阴影等细节。
- **响应式设计**: 适配桌面端与移动端展示。
- **Markdown 支持**: 专业的代码高亮与 Markdown 渲染支持。
- **交互体验**: 
  - 弹窗式登录，体验流畅。
  - 创作者中心数据可视化面板。
