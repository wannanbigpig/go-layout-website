<template>
  <div class="website">
    <!-- 导航栏 -->
    <el-header class="header">
      <div class="header-content">
        <div class="logo" @click="scrollTo('home')">
          <el-icon :size="28" color="#409EFF"><Platform /></el-icon>
          <span class="logo-text">Gin Layout</span>
        </div>
        
        <!-- PC 端菜单 -->
        <el-menu mode="horizontal" :ellipsis="false" class="nav-menu desktop-menu">
          <el-menu-item index="home" @click="scrollTo('home')">首页</el-menu-item>
          <el-menu-item index="features" @click="scrollTo('features')">特性</el-menu-item>
          <el-menu-item index="quickstart" @click="scrollTo('quickstart')">快速开始</el-menu-item>
          <el-menu-item index="demo" @click="scrollTo('demo')">演示</el-menu-item>
        </el-menu>
        
        <div class="header-actions">
          <el-button type="primary" @click="openGithub" class="desktop-only">
            <el-icon><Star /></el-icon>
            GitHub
          </el-button>
          <!-- 移动端菜单按钮 -->
          <el-button class="mobile-menu-btn" @click="mobileMenuVisible = true">
            <el-icon><Menu /></el-icon>
          </el-button>
        </div>
      </div>
    </el-header>

    <!-- 移动端侧边菜单 -->
    <el-drawer v-model="mobileMenuVisible" direction="rtl" size="70%" class="mobile-drawer">
      <template #header>
        <div class="drawer-header">
          <el-icon :size="24" color="#409EFF"><Platform /></el-icon>
          <span>Gin Layout</span>
        </div>
      </template>
      <el-menu class="mobile-nav-menu">
        <el-menu-item index="home" @click="scrollTo('home'); mobileMenuVisible = false">
          <el-icon><Home /></el-icon>
          <span>首页</span>
        </el-menu-item>
        <el-menu-item index="features" @click="scrollTo('features'); mobileMenuVisible = false">
          <el-icon><Grid /></el-icon>
          <span>特性</span>
        </el-menu-item>
        <el-menu-item index="quickstart" @click="scrollTo('quickstart'); mobileMenuVisible = false">
          <el-icon><Rocket /></el-icon>
          <span>快速开始</span>
        </el-menu-item>
        <el-menu-item index="demo" @click="scrollTo('demo'); mobileMenuVisible = false">
          <el-icon><Monitor /></el-icon>
          <span>演示</span>
        </el-menu-item>
        <el-menu-item @click="openGithub; mobileMenuVisible = false">
          <el-icon><Star /></el-icon>
          <span>GitHub</span>
        </el-menu-item>
      </el-menu>
    </el-drawer>

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
            <el-icon :size="20"><Code /></el-icon>
            <span>Go 1.21+</span>
          </div>
          <div class="stat-item">
            <el-icon :size="20"><Monitor /></el-icon>
            <span>Vue 3 + Element Plus</span>
          </div>
          <div class="stat-item">
            <el-icon :size="20"><Database /></el-icon>
            <span>MySQL + Redis</span>
          </div>
          <div class="stat-item">
            <el-icon :size="20"><Lock /></el-icon>
            <span>JWT + Casbin</span>
          </div>
        </div>
      </div>
      <!-- 装饰性背景 -->
      <div class="hero-bg-circle hero-bg-1"></div>
      <div class="hero-bg-circle hero-bg-2"></div>
      <div class="hero-bg-circle hero-bg-3"></div>
    </section>

    <!-- 特性 -->
    <section id="features" class="features">
      <div class="section-container">
        <h2 class="section-title">核心特性</h2>
        <p class="section-subtitle">功能完善、易于扩展、开箱即用</p>
        <el-row :gutter="20" class="feature-grid">
          <el-col :xs="24" :sm="12" :md="8" v-for="feature in features" :key="feature.title">
            <div class="feature-card">
              <div class="feature-icon">
                <el-icon :size="36">{{ feature.icon }}</el-icon>
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
        <p class="section-subtitle">现代化的技术选型，高效稳定</p>
        <el-row :gutter="16" class="tech-grid">
          <el-col :xs="6" :sm="8" :md="4" :lg="3" v-for="tech in techStack" :key="tech.name">
            <div class="tech-card">
              <el-icon :size="28" :color="tech.color">{{ tech.icon }}</el-icon>
              <span class="tech-name">{{ tech.name }}</span>
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
        <el-tabs class="code-tabs" type="border-card">
          <el-tab-pane label="后端">
            <div class="code-block">
              <pre><code><span class="comment"># 克隆项目</span>
git clone https://github.com/wannanbigpig/gin-layout.git
cd gin-layout

<span class="comment"># 安装依赖</span>
go mod tidy

<span class="comment"># 配置数据库（编辑 config.yaml）</span>
<span class="comment"># 运行迁移</span>
go run cmd/gin-layout/main.go command init-system -c config.yaml

<span class="comment"># 启动服务</span>
go run cmd/gin-layout/main.go service -c config.yaml

<span class="comment"># 访问 http://localhost:9001</span></code></pre>
            </div>
          </el-tab-pane>
          <el-tab-pane label="前端">
            <div class="code-block">
              <pre><code><span class="comment"># 克隆项目</span>
git clone https://github.com/wannanbigpig/go-admin-ui.git
cd go-admin-ui

<span class="comment"># 安装依赖</span>
npm install

<span class="comment"># 启动开发服务器</span>
npm run dev

<span class="comment"># 构建生产版本</span>
npm run build</code></pre>
            </div>
          </el-tab-pane>
          <el-tab-pane label="Docker">
            <div class="code-block">
              <pre><code><span class="comment"># 使用 Docker Compose 一键启动</span>
docker-compose up -d

<span class="comment"># 查看日志</span>
docker-compose logs -f

<span class="comment"># 停止服务</span>
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
                <el-tag type="success" size="small">可用</el-tag>
              </div>
            </template>
            <div class="demo-content">
              <div class="demo-item">
                <span class="label">管理后台：</span>
                <el-link type="primary" href="https://x-l-admin.wannanbigpig.com" target="_blank" class="demo-link">
                  https://x-l-admin.wannanbigpig.com
                </el-link>
              </div>
              <div class="demo-item">
                <span class="label">用户名：</span>
                <el-tag size="small">super_admin</el-tag>
              </div>
              <div class="demo-item">
                <span class="label">密码：</span>
                <el-tag size="small">123456</el-tag>
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
          <el-divider direction="vertical" class="desktop-only" />
          <el-link href="https://github.com/wannanbigpig/go-admin-ui" target="_blank">前端仓库</el-link>
          <el-divider direction="vertical" class="desktop-only" />
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

const mobileMenuVisible = ref(false)

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
  { name: 'JWT', icon: 'Key', color: '#333333' },
  { name: 'Casbin', icon: 'Lock', color: '#4CAF50' }
])

const scrollTo = (id) => {
  const element = document.getElementById(id)
  if (element) {
    const headerOffset = 60
    const elementPosition = element.getBoundingClientRect().top
    const offsetPosition = elementPosition + window.pageYOffset - headerOffset

    window.scrollTo({
      top: offsetPosition,
      behavior: 'smooth'
    })
  }
}

const openGithub = () => {
  window.open('https://github.com/wannanbigpig/gin-layout', '_blank')
}
</script>

<style scoped>
/* CSS 变量定义 */
.website {
  --header-height: 60px;
  --primary-color: #409EFF;
  --gradient-start: #667eea;
  --gradient-end: #764ba2;
  --text-primary: #333333;
  --text-secondary: #666666;
  --bg-light: #f8f9fa;
  --bg-white: #ffffff;
  --shadow-sm: 0 2px 8px rgba(0, 0, 0, 0.08);
  --shadow-md: 0 4px 16px rgba(0, 0, 0, 0.12);
  --shadow-lg: 0 10px 40px rgba(0, 0, 0, 0.15);
  
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, 'PingFang SC', 'Microsoft YaHei', sans-serif;
  overflow-x: hidden;
}

/* ==================== 导航栏 ==================== */
.header {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: var(--shadow-sm);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  height: var(--header-height);
}

.header-content {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
  padding: 0 16px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 18px;
  font-weight: 600;
  color: var(--text-primary);
  cursor: pointer;
  transition: opacity 0.2s;
}

.logo:hover {
  opacity: 0.8;
}

.logo-text {
  font-weight: 700;
}

.nav-menu {
  border: none;
  background: transparent;
}

.nav-menu :deep(.el-menu-item) {
  font-size: 15px;
  padding: 0 20px;
  border: none !important;
}

.nav-menu :deep(.el-menu-item:hover),
.nav-menu :deep(.el-menu-item.is-active) {
  background: transparent !important;
  color: var(--primary-color);
}

.header-actions {
  display: flex;
  align-items: center;
  gap: 12px;
}

.mobile-menu-btn {
  display: none;
  padding: 8px;
  border: none;
  background: transparent;
}

/* ==================== Hero 区域 ==================== */
.hero {
  background: linear-gradient(135deg, var(--gradient-start) 0%, var(--gradient-end) 100%);
  min-height: 600px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  color: white;
  padding: calc(var(--header-height) + 60px) 20px 60px;
  position: relative;
  overflow: hidden;
}

.hero-content {
  max-width: 800px;
  position: relative;
  z-index: 10;
}

.hero-title {
  font-size: clamp(36px, 8vw, 56px);
  margin-bottom: 16px;
  font-weight: 800;
  letter-spacing: -1px;
}

.hero-subtitle {
  font-size: clamp(18px, 4vw, 24px);
  margin-bottom: 12px;
  opacity: 0.95;
  font-weight: 500;
}

.hero-description {
  font-size: clamp(14px, 3vw, 16px);
  margin-bottom: 28px;
  opacity: 0.9;
  line-height: 1.8;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.hero-actions {
  display: flex;
  gap: 16px;
  justify-content: center;
  margin-bottom: 40px;
  flex-wrap: wrap;
}

.hero-stats {
  display: flex;
  gap: 12px;
  justify-content: center;
  flex-wrap: wrap;
}

.stat-item {
  display: flex;
  align-items: center;
  gap: 6px;
  background: rgba(255, 255, 255, 0.15);
  padding: 10px 16px;
  border-radius: 20px;
  font-size: 14px;
  backdrop-filter: blur(10px);
}

/* Hero 背景装饰 */
.hero-bg-circle {
  position: absolute;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
}

.hero-bg-1 {
  width: 300px;
  height: 300px;
  top: -100px;
  left: -100px;
}

.hero-bg-2 {
  width: 200px;
  height: 200px;
  bottom: 50px;
  right: -50px;
}

.hero-bg-3 {
  width: 150px;
  height: 150px;
  top: 50%;
  right: 20%;
}

/* ==================== 通用区域样式 ==================== */
.section-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 60px 20px;
}

.section-title {
  text-align: center;
  font-size: clamp(28px, 5vw, 36px);
  margin-bottom: 12px;
  color: var(--text-primary);
  font-weight: 700;
}

.section-subtitle {
  text-align: center;
  font-size: clamp(14px, 3vw, 16px);
  color: var(--text-secondary);
  margin-bottom: 40px;
}

/* ==================== 特性区域 ==================== */
.features {
  background: var(--bg-light);
}

.feature-grid {
  margin-top: 30px;
}

.feature-card {
  background: var(--bg-white);
  padding: 28px 20px;
  border-radius: 12px;
  text-align: center;
  transition: transform 0.3s, box-shadow 0.3s;
  height: 100%;
  box-shadow: var(--shadow-sm);
}

.feature-card:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-md);
}

.feature-icon {
  color: var(--primary-color);
  margin-bottom: 16px;
}

.feature-card h3 {
  font-size: 17px;
  margin-bottom: 10px;
  color: var(--text-primary);
  font-weight: 600;
}

.feature-card p {
  font-size: 14px;
  color: var(--text-secondary);
  line-height: 1.7;
}

/* ==================== 技术栈区域 ==================== */
.tech-stack {
  background: var(--bg-white);
}

.tech-grid {
  margin-top: 30px;
}

.tech-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  padding: 20px 12px;
  background: var(--bg-light);
  border-radius: 10px;
  transition: transform 0.2s;
}

.tech-card:hover {
  transform: translateY(-3px);
}

.tech-name {
  font-size: 13px;
  font-weight: 500;
  color: var(--text-primary);
}

/* ==================== 快速开始区域 ==================== */
.quickstart {
  background: var(--bg-light);
}

.code-tabs {
  margin-top: 30px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: var(--shadow-md);
}

.code-tabs :deep(.el-tabs__header) {
  background: #2d2d2d;
  margin: 0;
  padding: 0 10px;
}

.code-tabs :deep(.el-tabs__item) {
  color: #fff;
  font-size: 14px;
  padding: 0 20px;
  height: 46px;
  line-height: 46px;
}

.code-tabs :deep(.el-tabs__item.is-active) {
  color: var(--primary-color);
  background: #1e1e1e;
}

.code-block {
  padding: 20px;
  overflow-x: auto;
  background: #1e1e1e;
}

.code-block pre {
  margin: 0;
  color: #d4d4d4;
  font-family: 'Fira Code', 'Consolas', 'Monaco', monospace;
  font-size: 13px;
  line-height: 1.8;
  white-space: pre-wrap;
  word-wrap: break-word;
}

.code-block .comment {
  color: #6a9955;
}

/* ==================== 演示区域 ==================== */
.demo {
  background: var(--bg-white);
}

.demo-info {
  display: flex;
  justify-content: center;
  margin-top: 30px;
}

.demo-card {
  max-width: 480px;
  width: 100%;
  border-radius: 12px;
  box-shadow: var(--shadow-md);
}

.demo-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.demo-content {
  display: flex;
  flex-direction: column;
  gap: 14px;
  margin-bottom: 20px;
}

.demo-item {
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
}

.demo-item .label {
  color: var(--text-secondary);
  font-size: 14px;
  min-width: 80px;
}

.demo-link {
  word-break: break-all;
  font-size: 14px;
}

.demo-btn {
  width: 100%;
}

/* ==================== 页脚 ==================== */
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
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 8px;
}

.footer-links .el-link {
  color: #fff;
  font-size: 14px;
}

.footer-links .el-link:hover {
  color: var(--primary-color);
}

.copyright {
  opacity: 0.7;
  font-size: 13px;
}

/* ==================== 响应式设计 ==================== */

/* 平板端 (768px - 1024px) */
@media (max-width: 1024px) {
  .section-container {
    padding: 50px 16px;
  }
  
  .hero {
    min-height: 500px;
  }
  
  .hero-stats {
    gap: 8px;
  }
  
  .stat-item {
    padding: 8px 12px;
    font-size: 13px;
  }
}

/* 移动端 (≤ 768px) */
@media (max-width: 768px) {
  .desktop-menu {
    display: none;
  }
  
  .mobile-menu-btn {
    display: inline-flex;
  }
  
  .desktop-only {
    display: none !important;
  }
  
  .header-content {
    padding: 0 12px;
  }
  
  .logo-text {
    font-size: 16px;
  }
  
  .hero {
    padding: calc(var(--header-height) + 40px) 16px 40px;
    min-height: auto;
    padding-bottom: 50px;
  }
  
  .hero-title {
    margin-bottom: 12px;
  }
  
  .hero-subtitle {
    margin-bottom: 10px;
  }
  
  .hero-description {
    margin-left: 0;
    margin-right: 0;
  }
  
  .hero-actions {
    flex-direction: column;
    gap: 12px;
    margin-bottom: 30px;
  }
  
  .hero-actions .el-button {
    width: 100%;
    max-width: 280px;
  }
  
  .hero-stats {
    gap: 8px;
  }
  
  .stat-item {
    padding: 6px 12px;
    font-size: 12px;
  }
  
  .section-container {
    padding: 40px 16px;
  }
  
  .section-title {
    margin-bottom: 10px;
  }
  
  .section-subtitle {
    margin-bottom: 30px;
  }
  
  .feature-grid {
    margin-top: 20px;
  }
  
  .feature-card {
    padding: 24px 16px;
    margin-bottom: 16px;
  }
  
  .feature-card h3 {
    font-size: 16px;
  }
  
  .feature-card p {
    font-size: 13px;
  }
  
  .tech-grid {
    margin-top: 20px;
  }
  
  .tech-card {
    padding: 16px 8px;
    margin-bottom: 12px;
  }
  
  .tech-card :deep(.el-icon) {
    margin-bottom: 4px;
  }
  
  .tech-name {
    font-size: 12px;
  }
  
  .code-tabs :deep(.el-tabs__item) {
    padding: 0 12px;
    font-size: 13px;
  }
  
  .code-block {
    padding: 16px;
  }
  
  .code-block pre {
    font-size: 12px;
  }
  
  .demo-card {
    margin: 0 8px;
  }
  
  .demo-item .label {
    min-width: 70px;
    font-size: 13px;
  }
  
  .footer-links {
    flex-direction: column;
    gap: 12px;
  }
  
  .footer-links .el-divider {
    display: none;
  }
}

/* 小屏幕手机 (≤ 480px) */
@media (max-width: 480px) {
  .hero-stats {
    flex-direction: column;
    align-items: center;
    gap: 10px;
  }
  
  .stat-item {
    width: 100%;
    max-width: 200px;
    justify-content: center;
  }
  
  .section-title {
    font-size: 24px;
  }
  
  .section-subtitle {
    font-size: 13px;
  }
  
  .feature-card {
    padding: 20px 14px;
  }
  
  .feature-icon :deep(.el-icon) {
    font-size: 32px !important;
  }
}

/* ==================== 动画效果 ==================== */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.feature-card {
  animation: fadeInUp 0.6s ease-out backwards;
}

.feature-card:nth-child(1) { animation-delay: 0.1s; }
.feature-card:nth-child(2) { animation-delay: 0.2s; }
.feature-card:nth-child(3) { animation-delay: 0.3s; }
.feature-card:nth-child(4) { animation-delay: 0.4s; }
.feature-card:nth-child(5) { animation-delay: 0.5s; }
.feature-card:nth-child(6) { animation-delay: 0.6s; }

/* 移动端抽屉样式 */
.mobile-drawer :deep(.el-drawer__header) {
  margin-bottom: 20px;
  padding-bottom: 15px;
  border-bottom: 1px solid #eee;
}

.drawer-header {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 18px;
  font-weight: 600;
  color: var(--text-primary);
}

.mobile-nav-menu {
  border: none;
}

.mobile-nav-menu :deep(.el-menu-item) {
  height: 50px;
  line-height: 50px;
  font-size: 15px;
  border-radius: 8px;
  margin-bottom: 8px;
}

.mobile-nav-menu :deep(.el-menu-item:hover) {
  background: var(--bg-light);
}

.mobile-nav-menu :deep(.el-icon) {
  margin-right: 12px;
}
</style>
