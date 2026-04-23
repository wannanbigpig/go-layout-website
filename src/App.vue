<template>
  <div class="website">
    <!-- 导航栏 -->
    <el-header class="header">
      <div class="header-content">
        <div class="logo">
          <el-icon :size="28" color="#409EFF"><Platform /></el-icon>
          <span>Gin Layout</span>
        </div>
        <el-menu mode="horizontal" :ellipsis="false" class="nav-menu">
          <el-menu-item index="home" @click="scrollTo('home')">首页</el-menu-item>
          <el-menu-item index="features" @click="scrollTo('features')">特性</el-menu-item>
          <el-menu-item index="quickstart" @click="scrollTo('quickstart')">快速开始</el-menu-item>
          <el-menu-item index="demo" @click="scrollTo('demo')">演示</el-menu-item>
        </el-menu>
        <div class="header-actions">
          <el-button type="primary" @click="openGithub">
            <el-icon><Star /></el-icon>
            GitHub
          </el-button>
        </div>
      </div>
    </el-header>

    <!-- 首页 Hero -->
    <section id="home" class="hero">
      <div class="hero-content">
        <h1 class="hero-title">Gin Layout</h1>
        <p class="hero-subtitle">基于 Gin 框架的企业级 Go 语言后台管理脚手架</p>
        <p class="hero-description">
          开箱即用的后台管理系统模板，集成用户管理、角色权限、菜单管理、部门管理等功能，
          帮助您快速完成业务开发
        </p>
        <div class="hero-actions">
          <el-button type="primary" size="large" @click="scrollTo('quickstart')">
            <el-icon><Rocket /></el-icon>
            快速开始
          </el-button>
          <el-button size="large" @click="openGithub">
            <el-icon><Star /></el-icon>
            查看源码
          </el-button>
        </div>
        <div class="hero-stats">
          <div class="stat-item">
            <el-icon :size="24"><Code /></el-icon>
            <span>Go 1.21+</span>
          </div>
          <div class="stat-item">
            <el-icon :size="24"><Monitor /></el-icon>
            <span>Vue 3 + Element Plus</span>
          </div>
          <div class="stat-item">
            <el-icon :size="24"><Database /></el-icon>
            <span>MySQL + Redis</span>
          </div>
          <div class="stat-item">
            <el-icon :size="24"><Lock /></el-icon>
            <span>JWT + Casbin</span>
          </div>
        </div>
      </div>
    </section>

    <!-- 特性 -->
    <section id="features" class="features">
      <div class="section-container">
        <h2 class="section-title">核心特性</h2>
        <p class="section-subtitle">功能完善、易于扩展、开箱即用</p>
        <el-row :gutter="30" class="feature-grid">
          <el-col :xs="24" :sm="12" :md="8" v-for="feature in features" :key="feature.title">
            <div class="feature-card">
              <div class="feature-icon">
                <el-icon :size="40">{{ feature.icon }}</el-icon>
              </div>
              <h3>{{ feature.title }}</h3>
              <p>{{ feature.description }}</p>
            </div>
          </el-col>
        </el-row>
      </div>
    </section>

    <!-- 技术栈 -->
    <section class="tech-stack">
      <div class="section-container">
        <h2 class="section-title">技术栈</h2>
        <el-row :gutter="20" class="tech-grid">
          <el-col :xs="12" :sm="8" :md="4" v-for="tech in techStack" :key="tech.name">
            <div class="tech-card">
              <el-icon :size="36" :color="tech.color">{{ tech.icon }}</el-icon>
              <span>{{ tech.name }}</span>
            </div>
          </el-col>
        </el-row>
      </div>
    </section>

    <!-- 快速开始 -->
    <section id="quickstart" class="quickstart">
      <div class="section-container">
        <h2 class="section-title">快速开始</h2>
        <p class="section-subtitle">只需几步即可运行项目</p>
        <el-tabs class="code-tabs">
          <el-tab-pane label="后端">
            <div class="code-block">
              <pre><code># 克隆项目
git clone https://github.com/wannanbigpig/gin-layout.git
cd gin-layout

# 安装依赖
go mod tidy

# 配置数据库（编辑 config.yaml）
# 运行迁移
go run cmd/gin-layout/main.go command init-system -c config.yaml

# 启动服务
go run cmd/gin-layout/main.go service -c config.yaml

# 访问 http://localhost:9001</code></pre>
            </div>
          </el-tab-pane>
          <el-tab-pane label="前端">
            <div class="code-block">
              <pre><code># 克隆项目
git clone https://github.com/wannanbigpig/go-admin-ui.git
cd go-admin-ui

# 安装依赖
npm install

# 启动开发服务器
npm run dev

# 构建生产版本
npm run build</code></pre>
            </div>
          </el-tab-pane>
          <el-tab-pane label="Docker">
            <div class="code-block">
              <pre><code># 使用 Docker Compose 一键启动
docker-compose up -d

# 查看日志
docker-compose logs -f

# 停止服务
docker-compose down</code></pre>
            </div>
          </el-tab-pane>
        </el-tabs>
      </div>
    </section>

    <!-- 演示 -->
    <section id="demo" class="demo">
      <div class="section-container">
        <h2 class="section-title">在线演示</h2>
        <p class="section-subtitle">体验完整的管理后台功能</p>
        <div class="demo-info">
          <el-card class="demo-card">
            <template #header>
              <div class="demo-header">
                <span>演示环境</span>
                <el-tag type="success">可用</el-tag>
              </div>
            </template>
            <div class="demo-content">
              <div class="demo-item">
                <span class="label">管理后台：</span>
                <el-link type="primary" href="https://x-l-admin.wannanbigpig.com" target="_blank">
                  https://x-l-admin.wannanbigpig.com
                </el-link>
              </div>
              <div class="demo-item">
                <span class="label">用户名：</span>
                <el-tag>super_admin</el-tag>
              </div>
              <div class="demo-item">
                <span class="label">密码：</span>
                <el-tag>123456</el-tag>
              </div>
            </div>
            <el-button type="primary" class="demo-btn" href="https://x-l-admin.wannanbigpig.com" target="_blank">
              立即体验
              <el-icon><Right /></el-icon>
            </el-button>
          </el-card>
        </div>
      </div>
    </section>

    <!-- 页脚 -->
    <footer class="footer">
      <div class="footer-content">
        <div class="footer-links">
          <el-link href="https://github.com/wannanbigpig/gin-layout" target="_blank">GitHub</el-link>
          <el-divider direction="vertical" />
          <el-link href="https://github.com/wannanbigpig/go-admin-ui" target="_blank">前端仓库</el-link>
          <el-divider direction="vertical" />
          <el-link href="https://x-l-admin.wannanbigpig.com" target="_blank">演示环境</el-link>
        </div>
        <p class="copyright">
          © 2024 Gin Layout. Made with ❤️ by wannanbigpig
        </p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const features = ref([
  {
    icon: 'User',
    title: '用户管理',
    description: '完善的用户 CRUD 功能，支持批量操作、导入导出'
  },
  {
    icon: 'Lock',
    title: '权限管理',
    description: '基于 Casbin 的 RBAC 权限控制，支持细粒度权限'
  },
  {
    icon: 'Menu',
    title: '菜单管理',
    description: '动态路由配置，支持多级菜单、按钮权限'
  },
  {
    icon: 'Connection',
    title: '部门管理',
    description: '树形组织结构，支持多级部门管理'
  },
  {
    icon: 'Setting',
    title: '角色管理',
    description: '灵活的角色配置，支持角色继承'
  },
  {
    icon: 'Document',
    title: '日志审计',
    description: '完整的操作日志记录，支持登录日志、请求日志'
  }
])

const techStack = ref([
  { name: 'Go', icon: 'DataLine', color: '#00ADD8' },
  { name: 'Gin', icon: 'Cpu', color: '#0091EA' },
  { name: 'Vue 3', icon: 'Monitor', color: '#42B883' },
  { name: 'Element Plus', icon: 'Grid', color: '#409EFF' },
  { name: 'MySQL', icon: 'Database', color: '#4479A1' },
  { name: 'Redis', icon: 'FolderOpened', color: '#DC382D' },
  { name: 'JWT', icon: 'Key', color: '#000000' },
  { name: 'Casbin', icon: 'Lock', color: '#4CAF50' }
])

const scrollTo = (id) => {
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
}

const openGithub = () => {
  window.open('https://github.com/wannanbigpig/gin-layout', '_blank')
}
</script>

<style scoped>
.website {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
}

/* 导航栏 */
.header {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.1);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
}

.header-content {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 60px;
  padding: 0 20px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 20px;
  font-weight: bold;
  color: #333;
}

.nav-menu {
  border: none;
  background: transparent;
}

.nav-menu .el-menu-item {
  font-size: 15px;
}

.header-actions {
  display: flex;
  gap: 10px;
}

/* Hero 区域 */
.hero {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  min-height: 600px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  color: white;
  padding: 100px 20px 60px;
}

.hero-content {
  max-width: 800px;
}

.hero-title {
  font-size: 56px;
  margin-bottom: 20px;
  font-weight: 700;
}

.hero-subtitle {
  font-size: 24px;
  margin-bottom: 16px;
  opacity: 0.95;
}

.hero-description {
  font-size: 16px;
  margin-bottom: 30px;
  opacity: 0.9;
  line-height: 1.8;
}

.hero-actions {
  display: flex;
  gap: 16px;
  justify-content: center;
  margin-bottom: 40px;
}

.hero-stats {
  display: flex;
  gap: 30px;
  justify-content: center;
  flex-wrap: wrap;
}

.stat-item {
  display: flex;
  align-items: center;
  gap: 8px;
  background: rgba(255, 255, 255, 0.2);
  padding: 12px 20px;
  border-radius: 8px;
}

/* 通用区域样式 */
.section-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 60px 20px;
}

.section-title {
  text-align: center;
  font-size: 36px;
  margin-bottom: 12px;
  color: #333;
}

.section-subtitle {
  text-align: center;
  font-size: 16px;
  color: #666;
  margin-bottom: 40px;
}

/* 特性区域 */
.features {
  background: #f8f9fa;
}

.feature-grid {
  margin-top: 40px;
}

.feature-card {
  background: white;
  padding: 30px;
  border-radius: 12px;
  text-align: center;
  transition: transform 0.3s, box-shadow 0.3s;
  height: 100%;
}

.feature-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.feature-icon {
  color: #409EFF;
  margin-bottom: 16px;
}

.feature-card h3 {
  font-size: 18px;
  margin-bottom: 12px;
  color: #333;
}

.feature-card p {
  font-size: 14px;
  color: #666;
  line-height: 1.6;
}

/* 技术栈区域 */
.tech-stack {
  background: white;
}

.tech-grid {
  margin-top: 40px;
}

.tech-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  padding: 20px;
  background: #f8f9fa;
  border-radius: 8px;
  font-weight: 500;
}

/* 快速开始区域 */
.quickstart {
  background: #f8f9fa;
}

.code-tabs {
  margin-top: 40px;
  background: #1e1e1e;
  border-radius: 8px;
  overflow: hidden;
}

.code-tabs :deep(.el-tabs__header) {
  background: #2d2d2d;
  margin: 0;
}

.code-tabs :deep(.el-tabs__item) {
  color: #fff;
}

.code-tabs :deep(.el-tabs__item.is-active) {
  color: #409EFF;
}

.code-block {
  padding: 20px;
  overflow-x: auto;
}

.code-block pre {
  margin: 0;
  color: #d4d4d4;
  font-family: 'Fira Code', 'Consolas', monospace;
  font-size: 14px;
  line-height: 1.6;
}

.code-block code {
  font-family: inherit;
}

/* 演示区域 */
.demo {
  background: white;
}

.demo-info {
  display: flex;
  justify-content: center;
  margin-top: 40px;
}

.demo-card {
  max-width: 500px;
  width: 100%;
}

.demo-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.demo-content {
  display: flex;
  flex-direction: column;
  gap: 16px;
  margin-bottom: 20px;
}

.demo-item {
  display: flex;
  align-items: center;
  gap: 12px;
}

.demo-item .label {
  color: #666;
  min-width: 80px;
}

.demo-btn {
  width: 100%;
}

/* 页脚 */
.footer {
  background: #1a1a2e;
  color: #fff;
  padding: 30px 20px;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
}

.footer-links {
  margin-bottom: 16px;
}

.footer-links .el-link {
  color: #fff;
}

.footer-links .el-link:hover {
  color: #409EFF;
}

.copyright {
  opacity: 0.7;
  font-size: 14px;
}

/* 响应式 */
@media (max-width: 768px) {
  .hero-title {
    font-size: 36px;
  }
  
  .hero-subtitle {
    font-size: 18px;
  }
  
  .hero-actions {
    flex-direction: column;
  }
  
  .header-content {
    flex-wrap: wrap;
  }
  
  .nav-menu {
    order: 3;
    width: 100%;
    margin-top: 10px;
  }
}
</style>
