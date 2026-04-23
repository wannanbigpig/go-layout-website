# Gin Layout Website

Gin Layout 项目官网 - 基于 Vue 3 + Vite + Element Plus 构建

## 在线访问

- 官网：https://www.wannanbigpig.com
- 演示环境：https://x-l-admin.wannanbigpig.com
- 后端仓库：https://github.com/wannanbigpig/gin-layout
- 前端仓库：https://github.com/wannanbigpig/go-admin-ui

## 技术栈

- Vue 3 - 渐进式 JavaScript 框架
- Vite - 下一代前端构建工具
- Element Plus - 基于 Vue 3 的组件库

## 本地开发

```bash
# 安装依赖
npm install

# 启动开发服务器
npm run dev

# 构建生产版本
npm run build

# 预览生产构建
npm run preview
```

## 项目结构

```
gin-layout-website/
├── src/
│   ├── App.vue          # 主组件
│   └── main.js          # 入口文件
├── index.html           # HTML 模板
├── package.json         # 项目配置
├── vite.config.js       # Vite 配置
└── README.md            # 项目说明
```

## 部署

构建后的文件位于 `dist` 目录，可部署到任意静态文件服务器。

```bash
# 构建
npm run build

# 复制 dist 目录到服务器
scp -r dist/* user@server:/var/www/gin-layout-website/
```

## 许可证

MIT License

## 作者

wannanbigpig
