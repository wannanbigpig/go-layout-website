<template>
  <div class="website">
    <!-- 导航栏 -->
    <header :class="['navbar', { scrolled: isScrolled }]">
      <div class="nav-container">
        <div class="logo" @click="scrollTo('home')">
          <div class="logo-icon">
            <div class="logo-square"></div>
          </div>
          <span class="logo-text">Gin Layout</span>
        </div>
        
        <nav class="nav-links desktop-nav">
          <a @click="scrollTo('features')" class="nav-link">特性</a>
          <a @click="scrollTo('architecture')" class="nav-link">架构</a>
          <a @click="scrollTo('quickstart')" class="nav-link">快速开始</a>
          <a @click="scrollTo('demo')" class="nav-link">演示</a>
        </nav>
        
        <div class="nav-actions">
          <a href="https://github.com/wannanbigpig/gin-layout" target="_blank" class="github-btn desktop-only">
            <svg viewBox="0 0 24 24" fill="currentColor" class="github-icon">
              <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
            </svg>
            <span>Star</span>
          </a>
          <button class="mobile-menu-btn" @click="mobileMenuOpen = !mobileMenuOpen">
            <span></span>
            <span></span>
            <span></span>
          </button>
        </div>
      </div>
      
      <!-- 移动端菜单 -->
      <transition name="slide">
        <div v-if="mobileMenuOpen" class="mobile-menu">
          <a @click="scrollTo('features'); mobileMenuOpen = false" class="mobile-nav-link">特性</a>
          <a @click="scrollTo('architecture'); mobileMenuOpen = false" class="mobile-nav-link">架构</a>
          <a @click="scrollTo('quickstart'); mobileMenuOpen = false" class="mobile-nav-link">快速开始</a>
          <a @click="scrollTo('demo'); mobileMenuOpen = false" class="mobile-nav-link">演示</a>
          <a href="https://github.com/wannanbigpig/gin-layout" target="_blank" class="mobile-nav-link github-mobile">
            <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
            GitHub
          </a>
        </div>
      </transition>
    </header>

    <!-- Hero 区域 -->
    <section id="home" class="hero">
      <div class="hero-bg">
        <div class="gradient-orb orb-1"></div>
        <div class="gradient-orb orb-2"></div>
        <div class="gradient-orb orb-3"></div>
        <div class="grid-overlay"></div>
      </div>
      
      <div class="hero-content">
        <div class="hero-badge">
          <span class="badge-dot"></span>
          <span>v2.0 现已发布</span>
        </div>
        
        <h1 class="hero-title">
          <span class="title-line">构建企业级</span>
          <span class="title-line highlight">Go 后台系统</span>
          <span class="title-line">从未如此简单</span>
        </h1>
        
        <p class="hero-description">
          Gin Layout 是一个开箱即用的 Go 语言后台管理脚手架，
          集成用户管理、RBAC 权限、动态菜单、操作日志等核心功能，
          让您专注于业务逻辑，快速交付高质量产品。
        </p>
        
        <div class="hero-cta">
          <button @click="scrollTo('quickstart')" class="btn btn-primary">
            <span>开始使用</span>
            <svg class="btn-arrow" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M5 12h14M12 5l7 7-7 7"/>
            </svg>
          </button>
          <a href="https://github.com/wannanbigpig/gin-layout" target="_blank" class="btn btn-secondary">
            <svg viewBox="0 0 24 24" fill="currentColor" class="btn-github">
              <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
            </svg>
            <span>GitHub</span>
          </a>
        </div>
        
        <div class="hero-stats">
          <div class="stat">
            <div class="stat-value">10+</div>
            <div class="stat-label">核心模块</div>
          </div>
          <div class="stat-divider"></div>
          <div class="stat">
            <div class="stat-value">100%</div>
            <div class="stat-label">开源免费</div>
          </div>
          <div class="stat-divider"></div>
          <div class="stat">
            <div class="stat-value">生产级</div>
            <div class="stat-label">代码质量</div>
          </div>
        </div>
      </div>
      
      <div class="hero-scroll">
        <div class="scroll-indicator"></div>
        <span>向下滚动</span>
      </div>
    </section>

    <!-- 特性网格 -->
    <section id="features" class="features">
      <div class="container">
        <div class="section-header">
          <span class="section-tag">核心特性</span>
          <h2 class="section-title">为高效开发而生</h2>
          <p class="section-desc">精心设计的每一个功能，都经过生产环境验证</p>
        </div>
        
        <div class="features-grid">
          <div class="feature-card" v-for="(feature, index) in features" :key="index">
            <div class="feature-icon-wrapper">
              <div class="feature-icon-bg"></div>
              <el-icon :size="28" class="feature-icon"><component :is="feature.iconName" /></el-icon>
            </div>
            <h3 class="feature-title">{{ feature.title }}</h3>
            <p class="feature-desc">{{ feature.description }}</p>
            <ul class="feature-list">
              <li v-for="item in feature.items" :key="item">{{ item }}</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- 技术架构 -->
    <section id="architecture" class="architecture">
      <div class="container">
        <div class="section-header">
          <span class="section-tag">技术栈</span>
          <h2 class="section-title">现代化的技术选型</h2>
          <p class="section-desc">采用业界最佳实践，确保系统稳定高效</p>
        </div>
        
        <div class="tech-showcase">
          <div class="tech-category">
            <h4 class="tech-category-title">后端技术</h4>
            <div class="tech-items">
              <div class="tech-item" v-for="tech in backendTech" :key="tech.name">
                <div class="tech-logo" :style="{ background: tech.gradient }">
                  <el-icon :size="24"><component :is="tech.iconName" /></el-icon>
                </div>
                <div class="tech-info">
                  <span class="tech-name">{{ tech.name }}</span>
                  <span class="tech-desc">{{ tech.desc }}</span>
                </div>
              </div>
            </div>
          </div>
          
          <div class="tech-category">
            <h4 class="tech-category-title">前端技术</h4>
            <div class="tech-items">
              <div class="tech-item" v-for="tech in frontendTech" :key="tech.name">
                <div class="tech-logo" :style="{ background: tech.gradient }">
                  <el-icon :size="24"><component :is="tech.iconName" /></el-icon>
                </div>
                <div class="tech-info">
                  <span class="tech-name">{{ tech.name }}</span>
                  <span class="tech-desc">{{ tech.desc }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 快速开始 -->
    <section id="quickstart" class="quickstart">
      <div class="container">
        <div class="section-header">
          <span class="section-tag">快速开始</span>
          <h2 class="section-title">5 分钟运行项目</h2>
          <p class="section-desc">简单的步骤，快速上手</p>
        </div>
        
        <div class="code-showcase">
          <div class="code-tabs">
            <button 
              :class="['code-tab', { active: activeTab === 'backend' }]"
              @click="activeTab = 'backend'"
            >
              <span class="tab-icon">🔧</span>
              <span>后端</span>
            </button>
            <button 
              :class="['code-tab', { active: activeTab === 'frontend' }]"
              @click="activeTab = 'frontend'"
            >
              <span class="tab-icon">🎨</span>
              <span>前端</span>
            </button>
            <button 
              :class="['code-tab', { active: activeTab === 'docker' }]"
              @click="activeTab = 'docker'"
            >
              <span class="tab-icon">🐳</span>
              <span>Docker</span>
            </button>
          </div>
          
          <div class="code-content">
            <div class="code-header">
              <div class="code-dots">
                <span class="dot red"></span>
                <span class="dot yellow"></span>
                <span class="dot green"></span>
              </div>
              <span class="code-title">{{ codeTitles[activeTab] }}</span>
              <button class="copy-btn" @click="copyCode">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <rect x="9" y="9" width="13" height="13" rx="2" ry="2"></rect>
                  <path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"></path>
                </svg>
              </button>
            </div>
            <pre class="code-block"><code v-html="highlightedCode"></code></pre>
          </div>
        </div>
      </div>
    </section>

    <!-- 演示 -->
    <section id="demo" class="demo">
      <div class="container">
        <div class="demo-wrapper">
          <div class="demo-content">
            <span class="section-tag">在线演示</span>
            <h2 class="section-title">亲身体验</h2>
            <p class="section-desc">完整的管理后台功能，即刻体验</p>
            
            <div class="demo-credentials">
              <div class="credential-item">
                <span class="credential-label">演示地址</span>
                <a href="https://x-l-admin.wannanbigpig.com" target="_blank" class="credential-value link">
                  x-l-admin.wannanbigpig.com
                </a>
              </div>
              <div class="credential-item">
                <span class="credential-label">用户名</span>
                <code class="credential-value">super_admin</code>
              </div>
              <div class="credential-item">
                <span class="credential-label">密码</span>
                <code class="credential-value">123456</code>
              </div>
            </div>
            
            <a href="https://x-l-admin.wannanbigpig.com" target="_blank" class="btn btn-primary btn-large">
              <span>立即体验</span>
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/>
                <polyline points="15 3 21 3 21 9"/>
                <line x1="10" y1="14" x2="21" y2="3"/>
              </svg>
            </a>
          </div>
          
          <div class="demo-preview">
            <div class="preview-mockup">
              <div class="mockup-header">
                <div class="mockup-dots">
                  <span class="dot"></span>
                  <span class="dot"></span>
                  <span class="dot"></span>
                </div>
              </div>
              <div class="mockup-content">
                <div class="mockup-sidebar"></div>
                <div class="mockup-main">
                  <div class="mockup-topbar"></div>
                  <div class="mockup-body">
                    <div class="mockup-card"></div>
                    <div class="mockup-card"></div>
                    <div class="mockup-card"></div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 页脚 -->
    <footer class="footer">
      <div class="container">
        <div class="footer-content">
          <div class="footer-brand">
            <div class="footer-logo">
              <div class="logo-square"></div>
              <span>Gin Layout</span>
            </div>
            <p class="footer-desc">让 Go 后台开发更简单</p>
          </div>
          
          <div class="footer-links">
            <div class="footer-column">
              <h5>资源</h5>
              <a href="https://github.com/wannanbigpig/gin-layout" target="_blank">GitHub</a>
              <a href="https://github.com/wannanbigpig/go-admin-ui" target="_blank">前端仓库</a>
            </div>
            <div class="footer-column">
              <h5>链接</h5>
              <a @click="scrollTo('features')">特性</a>
              <a @click="scrollTo('quickstart')">文档</a>
              <a @click="scrollTo('demo')">演示</a>
            </div>
          </div>
        </div>
        
        <div class="footer-bottom">
          <p>© 2024 Gin Layout. Open source under MIT License.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import { 
  User, Lock, Menu, Connection, Setting, Document,
  DataAnalysis, Monitor, Grid, Cpu
} from '@element-plus/icons-vue'

const isScrolled = ref(false)
const mobileMenuOpen = ref(false)
const activeTab = ref('backend')

const features = [
  {
    icon: 'User',
    iconName: 'User',
    title: '用户管理',
    description: '完整的用户生命周期管理',
    items: ['CRUD 操作', '批量导入导出', '多条件筛选', '状态管理']
  },
  {
    icon: 'Lock',
    iconName: 'Lock',
    title: '权限控制',
    description: '基于 Casbin 的 RBAC',
    items: ['细粒度权限', '角色继承', '权限缓存', '动态授权']
  },
  {
    icon: 'Menu',
    iconName: 'Menu',
    title: '菜单管理',
    description: '动态路由配置',
    items: ['多级菜单', '按钮权限', '外链支持', '多语言']
  },
  {
    icon: 'Connection',
    iconName: 'Connection',
    title: '部门管理',
    description: '树形组织架构',
    items: ['无限层级', '部门用户', '数据权限', '组织统计']
  },
  {
    icon: 'Setting',
    iconName: 'Setting',
    title: '角色管理',
    description: '灵活的角色系统',
    items: ['角色配置', '权限分配', '角色继承', '批量授权']
  },
  {
    icon: 'Document',
    iconName: 'Document',
    title: '日志审计',
    description: '完整的操作记录',
    items: ['登录日志', '请求日志', '操作审计', '数据分析']
  }
]

const backendTech = [
  { name: 'Go', desc: '1.21+', icon: 'Code', iconName: 'Cpu', gradient: 'linear-gradient(135deg, #00ADD8, #005f73)' },
  { name: 'Gin', desc: 'Web 框架', icon: 'Server', iconName: 'Cpu', gradient: 'linear-gradient(135deg, #0091EA, #0056b3)' },
  { name: 'MySQL', desc: '数据存储', icon: 'Database', iconName: 'DataAnalysis', gradient: 'linear-gradient(135deg, #4479A1, #2c5270)' },
  { name: 'Redis', desc: '缓存队列', icon: 'Cpu', iconName: 'Cpu', gradient: 'linear-gradient(135deg, #DC382D, #9b2c2c)' }
]

const frontendTech = [
  { name: 'Vue 3', desc: '前端框架', icon: 'Monitor', iconName: 'Monitor', gradient: 'linear-gradient(135deg, #42B883, #2d7a55)' },
  { name: 'Element Plus', desc: 'UI 组件库', icon: 'Grid', iconName: 'Grid', gradient: 'linear-gradient(135deg, #409EFF, #2b6cb0)' },
  { name: 'Vite', desc: '构建工具', icon: 'Vite', iconName: 'Cpu', gradient: 'linear-gradient(135deg, #646CFF, #4338ca)' },
  { name: 'TypeScript', desc: '类型安全', icon: 'TS', iconName: 'Cpu', gradient: 'linear-gradient(135deg, #3178C6, #1e4a7a)' }
]

const codeExamples = {
  backend: `# 克隆项目
git clone https://github.com/wannanbigpig/gin-layout.git
cd gin-layout

# 安装依赖
go mod tidy

# 配置数据库 (编辑 config.yaml)
# 运行迁移
go run cmd/gin-layout/main.go command init-system -c config.yaml

# 启动服务
go run cmd/gin-layout/main.go service -c config.yaml

# 访问 http://localhost:9001`,
  frontend: `# 克隆项目
git clone https://github.com/wannanbigpig/go-admin-ui.git
cd go-admin-ui

# 安装依赖
npm install

# 启动开发服务器
npm run dev

# 构建生产版本
npm run build`,
  docker: `# 使用 Docker Compose 一键启动
docker-compose up -d

# 查看日志
docker-compose logs -f

# 停止服务
docker-compose down`
}

const codeTitles = {
  backend: 'terminal — backend',
  frontend: 'terminal — frontend',
  docker: 'terminal — docker'
}

const highlightedCode = computed(() => {
  const code = codeExamples[activeTab.value]
  return code
    .replace(/(#.*)/g, '<span class="code-comment">$1</span>')
    .replace(/(git|go|npm|docker|cd)/g, '<span class="code-command">$1</span>')
    .replace(/(https?:\/\/[^\s]+)/g, '<span class="code-url">$1</span>')
})

const copyCode = () => {
  navigator.clipboard.writeText(codeExamples[activeTab.value])
}

const scrollTo = (id) => {
  const element = document.getElementById(id)
  if (element) {
    const headerOffset = 70
    const elementPosition = element.getBoundingClientRect().top
    const offsetPosition = elementPosition + window.pageYOffset - headerOffset
    window.scrollTo({ top: offsetPosition, behavior: 'smooth' })
  }
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
/* ========== CSS 变量 ========== */
.website {
  --color-bg: #0a0a0f;
  --color-bg-secondary: #12121a;
  --color-bg-card: #1a1a25;
  --color-text: #ffffff;
  --color-text-secondary: #a0a0b0;
  --color-text-muted: #6b6b80;
  --color-primary: #6366f1;
  --color-primary-light: #818cf8;
  --color-accent: #22d3ee;
  --color-success: #10b981;
  --color-border: #2a2a3a;
  --shadow-sm: 0 2px 8px rgba(0, 0, 0, 0.3);
  --shadow-md: 0 4px 16px rgba(0, 0, 0, 0.4);
  --shadow-lg: 0 10px 40px rgba(0, 0, 0, 0.5);
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-xl: 24px;
  
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'PingFang SC', 'Microsoft YaHei', sans-serif;
  background: var(--color-bg);
  color: var(--color-text);
  overflow-x: hidden;
}

/* ========== 通用 ========== */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
}

.section-header {
  text-align: center;
  margin-bottom: 60px;
}

.section-tag {
  display: inline-block;
  padding: 6px 16px;
  background: linear-gradient(135deg, rgba(99, 102, 241, 0.2), rgba(34, 211, 238, 0.2));
  border: 1px solid var(--color-border);
  border-radius: 20px;
  font-size: 13px;
  color: var(--color-primary-light);
  margin-bottom: 16px;
}

.section-title {
  font-size: clamp(28px, 5vw, 42px);
  font-weight: 700;
  margin-bottom: 12px;
  background: linear-gradient(135deg, #fff, #a0a0b0);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.section-desc {
  font-size: 16px;
  color: var(--color-text-secondary);
  max-width: 500px;
  margin: 0 auto;
}

/* ========== 按钮 ========== */
.btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 14px 28px;
  border-radius: var(--radius-md);
  font-size: 15px;
  font-weight: 500;
  text-decoration: none;
  transition: all 0.3s;
  cursor: pointer;
  border: none;
}

.btn-primary {
  background: linear-gradient(135deg, var(--color-primary), var(--color-primary-light));
  color: white;
  box-shadow: 0 4px 15px rgba(99, 102, 241, 0.4);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(99, 102, 241, 0.5);
}

.btn-secondary {
  background: var(--color-bg-card);
  color: var(--color-text);
  border: 1px solid var(--color-border);
}

.btn-secondary:hover {
  background: var(--color-bg-secondary);
  border-color: var(--color-primary);
}

.btn-large {
  padding: 16px 32px;
  font-size: 16px;
}

/* ========== 导航栏 ========== */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 20px 0;
  transition: all 0.3s;
}

.navbar.scrolled {
  background: rgba(10, 10, 15, 0.9);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--color-border);
  padding: 12px 0;
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  display: flex;
  align-items: center;
  gap: 12px;
  cursor: pointer;
}

.logo-icon {
  width: 36px;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.logo-square {
  width: 24px;
  height: 24px;
  background: linear-gradient(135deg, var(--color-primary), var(--color-accent));
  border-radius: 6px;
  transform: rotate(45deg);
}

.logo-text {
  font-size: 20px;
  font-weight: 700;
  color: var(--color-text);
}

.nav-links {
  display: flex;
  gap: 8px;
}

.nav-link {
  padding: 10px 20px;
  color: var(--color-text-secondary);
  text-decoration: none;
  border-radius: var(--radius-sm);
  transition: all 0.3s;
  cursor: pointer;
  background: transparent;
  border: none;
  font-size: 15px;
}

.nav-link:hover {
  color: var(--color-text);
  background: var(--color-bg-card);
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 16px;
}

.github-btn {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 10px 20px;
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-sm);
  color: var(--color-text);
  text-decoration: none;
  transition: all 0.3s;
}

.github-btn:hover {
  border-color: var(--color-primary);
  background: var(--color-bg-secondary);
}

.github-icon {
  width: 20px;
  height: 20px;
}

.mobile-menu-btn {
  display: none;
  flex-direction: column;
  gap: 5px;
  padding: 8px;
  background: transparent;
  border: none;
  cursor: pointer;
}

.mobile-menu-btn span {
  width: 24px;
  height: 2px;
  background: var(--color-text);
  transition: all 0.3s;
}

.mobile-menu {
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background: var(--color-bg-secondary);
  border-bottom: 1px solid var(--color-border);
  padding: 16px 24px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.mobile-nav-link {
  padding: 14px 16px;
  color: var(--color-text-secondary);
  text-decoration: none;
  border-radius: var(--radius-sm);
  transition: all 0.3s;
  display: flex;
  align-items: center;
  gap: 12px;
}

.mobile-nav-link:hover {
  color: var(--color-text);
  background: var(--color-bg-card);
}

.github-mobile svg {
  width: 20px;
  height: 20px;
}

.slide-enter-active,
.slide-leave-active {
  transition: all 0.3s ease;
}

.slide-enter-from,
.slide-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

/* ========== Hero 区域 ========== */
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
  padding: 120px 24px 80px;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  inset: 0;
  overflow: hidden;
}

.gradient-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.5;
  animation: float 20s infinite ease-in-out;
}

.orb-1 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, var(--color-primary) 0%, transparent 70%);
  top: -200px;
  left: -100px;
}

.orb-2 {
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, var(--color-accent) 0%, transparent 70%);
  bottom: -100px;
  right: -50px;
  animation-delay: -7s;
}

.orb-3 {
  width: 200px;
  height: 200px;
  background: radial-gradient(circle, #a855f7 0%, transparent 70%);
  top: 50%;
  right: 20%;
  animation-delay: -14s;
}

@keyframes float {
  0%, 100% { transform: translate(0, 0) scale(1); }
  25% { transform: translate(30px, -30px) scale(1.1); }
  50% { transform: translate(-20px, 20px) scale(0.9); }
  75% { transform: translate(20px, 30px) scale(1.05); }
}

.grid-overlay {
  position: absolute;
  inset: 0;
  background-image: 
    linear-gradient(rgba(255, 255, 255, 0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.03) 1px, transparent 1px);
  background-size: 60px 60px;
}

.hero-content {
  position: relative;
  z-index: 10;
  text-align: center;
  max-width: 900px;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: 20px;
  font-size: 13px;
  color: var(--color-text-secondary);
  margin-bottom: 24px;
}

.badge-dot {
  width: 8px;
  height: 8px;
  background: var(--color-success);
  border-radius: 50%;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%, 100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.5; transform: scale(1.2); }
}

.hero-title {
  font-size: clamp(36px, 8vw, 72px);
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 24px;
}

.title-line {
  display: block;
  background: linear-gradient(135deg, #fff 0%, #a0a0b0 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.title-line.highlight {
  background: linear-gradient(135deg, var(--color-primary-light), var(--color-accent) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-description {
  font-size: clamp(16px, 3vw, 18px);
  line-height: 1.8;
  color: var(--color-text-secondary);
  max-width: 650px;
  margin: 0 auto 40px;
}

.hero-cta {
  display: flex;
  gap: 16px;
  justify-content: center;
  flex-wrap: wrap;
  margin-bottom: 48px;
}

.btn-arrow {
  width: 18px;
  height: 18px;
  transition: transform 0.3s;
}

.btn-primary:hover .btn-arrow {
  transform: translateX(4px);
}

.btn-github {
  width: 20px;
  height: 20px;
}

.hero-stats {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 24px;
  flex-wrap: wrap;
}

.stat {
  text-align: center;
}

.stat-value {
  font-size: 32px;
  font-weight: 700;
  background: linear-gradient(135deg, var(--color-primary-light), var(--color-accent));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.stat-label {
  font-size: 13px;
  color: var(--color-text-muted);
  margin-top: 4px;
}

.stat-divider {
  width: 1px;
  height: 40px;
  background: var(--color-border);
}

.hero-scroll {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  color: var(--color-text-muted);
  font-size: 13px;
}

.scroll-indicator {
  width: 24px;
  height: 40px;
  border: 2px solid var(--color-border);
  border-radius: 12px;
  position: relative;
}

.scroll-indicator::after {
  content: '';
  position: absolute;
  top: 8px;
  left: 50%;
  transform: translateX(-50%);
  width: 4px;
  height: 8px;
  background: var(--color-text-muted);
  border-radius: 2px;
  animation: scroll 2s infinite;
}

@keyframes scroll {
  0%, 100% { opacity: 1; top: 8px; }
  50% { opacity: 0.3; top: 16px; }
}

/* ========== 特性区域 ========== */
.features {
  padding: 100px 0;
  background: var(--color-bg-secondary);
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 24px;
}

.feature-card {
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: 32px;
  transition: all 0.3s;
}

.feature-card:hover {
  border-color: var(--color-primary);
  transform: translateY(-4px);
  box-shadow: var(--shadow-lg);
}

.feature-icon-wrapper {
  position: relative;
  width: 56px;
  height: 56px;
  margin-bottom: 20px;
}

.feature-icon-bg {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(99, 102, 241, 0.3), rgba(34, 211, 238, 0.3));
  border-radius: var(--radius-md);
  transform: rotate(45deg);
}

.feature-icon {
  position: relative;
  color: var(--color-primary-light);
}

.feature-title {
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 8px;
}

.feature-desc {
  font-size: 14px;
  color: var(--color-text-secondary);
  margin-bottom: 16px;
}

.feature-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.feature-list li {
  padding: 6px 12px;
  background: var(--color-bg-secondary);
  border-radius: var(--radius-sm);
  font-size: 13px;
  color: var(--color-text-muted);
}

/* ========== 技术架构 ========== */
.architecture {
  padding: 100px 0;
  background: var(--color-bg);
}

.tech-showcase {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 40px;
}

.tech-category-title {
  font-size: 16px;
  font-weight: 600;
  color: var(--color-text-secondary);
  margin-bottom: 20px;
  padding-bottom: 12px;
  border-bottom: 1px solid var(--color-border);
}

.tech-items {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.tech-item {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 16px;
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  transition: all 0.3s;
}

.tech-item:hover {
  border-color: var(--color-primary);
  transform: translateX(4px);
}

.tech-logo {
  width: 44px;
  height: 44px;
  border-radius: var(--radius-sm);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.tech-logo .el-icon {
  color: white;
}

.tech-info {
  display: flex;
  flex-direction: column;
}

.tech-name {
  font-weight: 600;
  color: var(--color-text);
}

.tech-desc {
  font-size: 13px;
  color: var(--color-text-muted);
}

/* ========== 快速开始 ========== */
.quickstart {
  padding: 100px 0;
  background: var(--color-bg-secondary);
}

.code-showcase {
  max-width: 800px;
  margin: 0 auto;
}

.code-tabs {
  display: flex;
  gap: 8px;
  margin-bottom: 16px;
}

.code-tab {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 12px 20px;
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-sm);
  color: var(--color-text-secondary);
  cursor: pointer;
  transition: all 0.3s;
}

.code-tab.active {
  background: var(--color-primary);
  border-color: var(--color-primary);
  color: white;
}

.tab-icon {
  font-size: 16px;
}

.code-content {
  background: #1e1e2e;
  border-radius: var(--radius-lg);
  overflow: hidden;
  border: 1px solid var(--color-border);
}

.code-header {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 12px 16px;
  background: #181825;
  border-bottom: 1px solid var(--color-border);
}

.code-dots {
  display: flex;
  gap: 6px;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.dot.red { background: #ff5f56; }
.dot.yellow { background: #ffbd2e; }
.dot.green { background: #27ca40; }

.code-title {
  font-size: 13px;
  color: var(--color-text-muted);
  flex: 1;
}

.copy-btn {
  padding: 6px;
  background: transparent;
  border: none;
  color: var(--color-text-muted);
  cursor: pointer;
  transition: color 0.3s;
}

.copy-btn:hover {
  color: var(--color-text);
}

.copy-btn svg {
  width: 18px;
  height: 18px;
}

.code-block {
  padding: 24px;
  overflow-x: auto;
  margin: 0;
}

.code-block code {
  font-family: 'Fira Code', 'JetBrains Mono', monospace;
  font-size: 14px;
  line-height: 1.8;
  color: #e0e0e0;
}

.code-comment { color: #6b7280; }
.code-command { color: #60a5fa; }
.code-url { color: #34d399; text-decoration: underline; }

/* ========== 演示区域 ========== */
.demo {
  padding: 100px 0;
  background: var(--color-bg);
}

.demo-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}

.demo-content .section-tag,
.demo-content .section-title,
.demo-content .section-desc {
  text-align: left;
  margin-left: 0;
}

.demo-credentials {
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: 24px;
  margin: 32px 0;
}

.credential-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 0;
  border-bottom: 1px solid var(--color-border);
}

.credential-item:last-child {
  border-bottom: none;
  padding-bottom: 0;
}

.credential-item:first-child {
  padding-top: 0;
}

.credential-label {
  font-size: 14px;
  color: var(--color-text-muted);
}

.credential-value {
  font-size: 14px;
  color: var(--color-text);
}

.credential-value.link {
  color: var(--color-primary-light);
  text-decoration: none;
}

.credential-value code {
  background: var(--color-bg-secondary);
  padding: 4px 10px;
  border-radius: var(--radius-sm);
  font-family: 'Fira Code', monospace;
}

.preview-mockup {
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  overflow: hidden;
  box-shadow: var(--shadow-lg);
}

.mockup-header {
  padding: 12px 16px;
  background: #181825;
  border-bottom: 1px solid var(--color-border);
}

.mockup-dots {
  display: flex;
  gap: 6px;
}

.mockup-dots .dot {
  background: #3f3f5f;
}

.mockup-content {
  display: flex;
  height: 400px;
}

.mockup-sidebar {
  width: 80px;
  background: #181825;
  border-right: 1px solid var(--color-border);
}

.mockup-main {
  flex: 1;
  display: flex;
  flex-direction: column;
}

.mockup-topbar {
  height: 50px;
  background: #181825;
  border-bottom: 1px solid var(--color-border);
}

.mockup-body {
  flex: 1;
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.mockup-card {
  flex: 1;
  background: #181825;
  border-radius: var(--radius-sm);
  border: 1px solid var(--color-border);
}

/* ========== 页脚 ========== */
.footer {
  padding: 60px 0 30px;
  background: var(--color-bg-secondary);
  border-top: 1px solid var(--color-border);
}

.footer-content {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 40px;
  margin-bottom: 40px;
}

.footer-logo {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}

.footer-logo .logo-square {
  width: 28px;
  height: 28px;
}

.footer-logo span {
  font-size: 20px;
  font-weight: 700;
}

.footer-desc {
  font-size: 14px;
  color: var(--color-text-muted);
}

.footer-links {
  display: flex;
  gap: 60px;
}

.footer-column h5 {
  font-size: 14px;
  font-weight: 600;
  color: var(--color-text);
  margin-bottom: 16px;
}

.footer-column a {
  display: block;
  padding: 6px 0;
  color: var(--color-text-muted);
  text-decoration: none;
  font-size: 14px;
  transition: color 0.3s;
}

.footer-column a:hover {
  color: var(--color-primary-light);
}

.footer-bottom {
  padding-top: 30px;
  border-top: 1px solid var(--color-border);
  text-align: center;
}

.footer-bottom p {
  font-size: 13px;
  color: var(--color-text-muted);
}

/* ========== 响应式 ========== */
@media (max-width: 1024px) {
  .demo-wrapper {
    grid-template-columns: 1fr;
    gap: 40px;
  }
  
  .demo-content .section-header {
    text-align: center;
  }
  
  .demo-content .section-tag,
  .demo-content .section-title,
  .demo-content .section-desc {
    text-align: center;
    margin-left: auto;
    margin-right: auto;
  }
}

@media (max-width: 768px) {
  .desktop-nav,
  .github-btn.desktop-only,
  .desktop-only {
    display: none !important;
  }
  
  .mobile-menu-btn {
    display: flex;
  }
  
  .navbar {
    padding: 16px 0;
  }
  
  .hero {
    padding: 100px 16px 60px;
  }
  
  .hero-cta {
    flex-direction: column;
    align-items: center;
  }
  
  .hero-cta .btn {
    width: 100%;
    max-width: 300px;
    justify-content: center;
  }
  
  .hero-stats {
    gap: 16px;
  }
  
  .stat-divider {
    display: none;
  }
  
  .features-grid {
    grid-template-columns: 1fr;
  }
  
  .tech-showcase {
    grid-template-columns: 1fr;
  }
  
  .code-tabs {
    overflow-x: auto;
  }
  
  .footer-content {
    flex-direction: column;
    gap: 30px;
  }
  
  .footer-links {
    gap: 40px;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 26px;
  }
  
  .feature-card {
    padding: 24px 20px;
  }
  
  .code-block {
    padding: 16px;
    font-size: 13px;
  }
}
</style>
