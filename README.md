# 个人主页

一个使用 Vue 3 和 Vuesax Alpha 构建的现代响应式个人主页。

## 🌟 特性

- 💫 现代简洁的设计
- 🌓 支持亮色/暗色/跟随系统主题
- 🎨 流畅的动画和过渡效果
- 📱 完全响应式布局
- ⚡ 最小依赖，快速加载

## 🛠️ 技术栈

- Vue 3
- Vuesax Alpha
- Less
- Vite
- Vue Use Motion
- Vue3 Typed.js

## 🚀 快速开始

1. 克隆仓库:
```bash
git clone https://github.com/Honahec/homepage.git
cd homepage
```

2. 安装依赖:
```bash
pnpm install
```

3. 启动开发服务器:
```bash
pnpm dev
```

4. 构建生产版本:
```bash
pnpm build
```

## 📁 项目结构

```
src
├── assets # 静态资源
│ └── load.css # 加载动画样式
├── components # 组件
│ ├── AboutDialog.vue # 关于弹窗
│ ├── BackgroundGrid.vue # 背景网格
│ └── LoadingAnimation.vue # 加载动画
├── config # 配置文件
│ └── index.js # 站点配置、社交链接等
├── less # Less 样式
│ └── App.less # 全局样式
├── utils # 工具函数
│ └── theme.js # 主题管理
├── App.vue # 根组件
├── main.js # 入口文件
└── style.css # 全局 CSS 变量
```

## 🎨 自定义

### 主题配置

主题系统支持三种模式：亮色、暗色和跟随系统。颜色可以在 style.css 中自定义：

startLine: 1
endLine: 18

### 社交链接和站点配置

在 config/index.js 中编辑社交媒体链接和站点配置：

startLine: 1
endLine: 95

### 背景图片

在 App.vue 中替换背景图片 URL：

startLine: 5
endLine: 7

## 🙏 致谢

本项目基于 QNquenan 的 [homepage-for-vue3](https://github.com/QNquenan/homepage-for-vue3)。

在原项目基础上做了模块化处理。

## 🤝 贡献

1. Fork 本仓库
2. 创建你的特性分支 (`git checkout -b feature/amazing-feature`)
3. 提交你的更改 (`git commit -m '添加一些很棒的特性'`)
4. 推送到分支 (`git push origin feature/amazing-feature`)
5. 提交 Pull Request