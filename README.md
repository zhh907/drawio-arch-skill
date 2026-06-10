# drawio-arch-skill

[English](#english) | [中文](#中文)

---

## English

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) Skill for generating professional draw.io architecture diagrams with a unified design system.

### Features

- **16 Diagram Types** — covers the full project lifecycle
- **5 Color Themes** — Ocean Blue, Dark Night, Forest Green, Sunset Orange, Monochrome
- **Automated Layout** — fill formulas for uniform module distribution
- **Quality Checklist** — 28 items across 5 dimensions for self-verification
- **8 Module Styles** — primary, secondary, outlined, database, decision, actor, etc.
- **4 Container Levels** — layer, sub-container, nested, board

### Diagram Types

| # | Type | Command | Description |
|---|------|---------|-------------|
| 01 | System Architecture | `system` | Layered system architecture |
| 02 | Business Architecture | `business` | Business capability map |
| 03 | Deployment Topology | `topology` | K8s / server deployment |
| 04 | Data Flow | `dataflow` | Data flow from input to output |
| 05 | Component Diagram | `component` | Module dependency graph |
| 06 | Sequence Diagram | `sequence` | API call sequences |
| 07 | ER Diagram | `er` | Entity-relationship diagram |
| 08 | Network Topology | `network` | VPC / subnet / load balancer |
| 09 | Class Diagram | `class` | Class inheritance and interfaces |
| 10 | Activity Diagram | `activity` | Business process / algorithm flow |
| 11 | State Machine | `state` | State transitions |
| 12 | API Map | `api-map` | All API endpoints overview |
| 13 | Wireframe | `wireframe` | Page layout prototype |
| 14 | Org Chart | `org-chart` | Team / role structure |
| 15 | Mindmap | `mindmap` | Tech stack / knowledge map |
| 16 | Timeline | `timeline` | Project roadmap and milestones |
| -- | Comparison | `comparison` | Before/After or A/B comparison |

### Color Themes

| Theme | Style | Best For |
|-------|-------|----------|
| Ocean Blue (default) | Professional, calm | Enterprise architecture, technical docs |
| Dark Night | Dark mode, modern | Presentations, social media |
| Forest Green | Natural, eco | DevOps dashboards, health tech |
| Sunset Orange | Warm, energetic | Product roadmaps, startup pitches |
| Monochrome | Minimal, print-friendly | Print documents, academic papers |

### Installation

```bash
# 1. Clone this repository
git clone https://github.com/zhh907/drawio-arch-skill.git

# 2. Copy the skill to your Claude Code skills directory
mkdir -p ~/.claude/skills/drawio-arch
cp drawio-arch-skill/SKILL.md ~/.claude/skills/drawio-arch/SKILL.md

# 3. Restart Claude Code (or start a new session)
# The skill is now available via /drawio-arch
```

### Usage

```
# Generate a single diagram
/drawio-arch system A three-tier web app: Nginx → Spring Boot → MySQL
/drawio-arch er User, Order, Product entity relationships
/drawio-arch sequence Login to order placement call chain

# Generate all 16 diagrams for a project
/drawio-arch all

# Choose a theme
/drawio-arch topology K8s cluster deployment --theme dark-night
/drawio-arch dataflow Data pipeline --theme forest-green

# Audit or fix existing diagrams
/drawio-arch audit 01-system-architecture.drawio
/drawio-arch fix 03-deployment-topology.drawio
```

### Design System

The skill defines a complete design system with parameterized color tokens. All module, container, and connector styles reference theme tokens (e.g., `{PRIMARY_MID}`, `{ACCENT}`), so switching themes only requires swapping the palette — layout and typography rules stay the same.

See [SKILL.md](./SKILL.md) for the complete specification.

---

## 中文

一个 [Claude Code](https://docs.anthropic.com/en/docs/claude-code) Skill，用于生成专业级 draw.io 架构图，内置统一设计系统。

### 特性

- **16 种图表类型** — 覆盖项目全生命周期
- **5 套配色主题** — 海洋蓝、暗夜、森林绿、日落橙、单色
- **自动布局** — 均分填充公式，模块等宽等距
- **质量检查清单** — 28 项检查，覆盖 5 个维度
- **8 种模块样式** — 核心模块、二级模块、描边、数据库、决策、角色等
- **4 级容器** — 图层容器、子容器、嵌套容器、全局底板

### 图表类型

| # | 类型 | 命令 | 说明 |
|---|------|------|------|
| 01 | 系统架构图 | `system` | 分层系统架构 |
| 02 | 业务架构图 | `business` | 业务能力地图 |
| 03 | 部署拓扑图 | `topology` | K8s / 服务器部署 |
| 04 | 数据流图 | `dataflow` | 从输入到输出的数据流向 |
| 05 | 组件依赖图 | `component` | 模块间依赖关系 |
| 06 | 时序图 | `sequence` | 接口调用时序 |
| 07 | ER 图 | `er` | 实体关系图 |
| 08 | 网络拓扑图 | `network` | VPC / 子网 / 负载均衡 |
| 09 | 类图 | `class` | 类继承和接口实现 |
| 10 | 活动图 | `activity` | 业务流程 / 算法步骤 |
| 11 | 状态机图 | `state` | 状态流转 |
| 12 | API 地图 | `api-map` | 全部 API 端点总览 |
| 13 | 线框图 | `wireframe` | 页面布局原型 |
| 14 | 组织架构图 | `org-chart` | 团队 / 角色结构 |
| 15 | 思维导图 | `mindmap` | 技术栈 / 知识体系 |
| 16 | 排期路线图 | `timeline` | 版本规划和里程碑 |
| -- | 方案对比图 | `comparison` | Before/After 或 A/B 对比 |

### 配色主题

| 主题 | 风格 | 适用场景 |
|------|------|---------|
| 海洋蓝（默认） | 专业沉稳 | 企业架构、技术文档 |
| 暗夜 | 暗黑现代 | 演示汇报、社交媒体 |
| 森林绿 | 自然生态 | DevOps 仪表盘、健康科技 |
| 日落橙 | 温暖活力 | 产品路线图、创业路演 |
| 单色 | 极简 | 打印文档、学术论文 |

### 安装

```bash
# 1. 克隆仓库
git clone https://github.com/zhh907/drawio-arch-skill.git

# 2. 复制 Skill 到 Claude Code 的 skills 目录
mkdir -p ~/.claude/skills/drawio-arch
cp drawio-arch-skill/SKILL.md ~/.claude/skills/drawio-arch/SKILL.md

# 3. 重启 Claude Code 或开启新会话
# 输入 /drawio-arch 即可使用
```

### 使用方式

```
# 生成单张图表
/drawio-arch system 金融量化平台微服务架构
/drawio-arch er 订单、用户、商品实体关系
/drawio-arch sequence 用户登录到下单的完整调用链路

# 一键生成项目全部 16 种图表
/drawio-arch all

# 选择主题
/drawio-arch topology K8s集群部署 --theme dark-night
/drawio-arch dataflow 数据管道 --theme forest-green

# 审计或修复已有图表
/drawio-arch audit 01-系统架构图.drawio
/drawio-arch fix 03-部署拓扑图.drawio
```

### 设计系统

Skill 定义了一套完整的设计系统，所有模块、容器和连接线的样式通过参数化色标（如 `{PRIMARY_MID}`、`{ACCENT}`）引用主题色值。切换主题只需替换色板，布局和排版规则完全不变。

核心规则：
- 所有模块：`rounded=1;arcSize=6`
- 所有容器：swimlane + `container=1`
- 同行模块间距统一（4px 或 8px）
- 5 级排版层级（H1-H5）
- 28 项质量检查清单

完整规范见 [SKILL.md](./SKILL.md)。

---

## Examples / 示例

[`examples/`](./examples/) 目录包含 5 套主题的完整示例，共 33 个文件：

| Theme / 主题 | Files | Diagrams |
|-------------|-------|----------|
| [ocean-blue](./examples/ocean-blue/) | 16 | 全部 16 种图表类型 |
| [dark-night](./examples/dark-night/) | 5 | 架构图、数据流、拓扑、组件 + 截图 |
| [forest-green](./examples/forest-green/) | 4 | 架构图、数据流、拓扑、组件 |
| [sunset-orange](./examples/sunset-orange/) | 4 | 架构图、数据流、拓扑、组件 |
| [monochrome](./examples/monochrome/) | 4 | 架构图、数据流、拓扑、组件 |

> 所有 `.drawio` 文件可直接用 [draw.io](https://app.diagrams.net) 打开。

## Project Structure / 项目结构

```
drawio-arch-skill/
├── SKILL.md                    # Skill 核心 — 完整设计系统规范
├── README.md                   # 本文件
├── LICENSE                     # MIT
└── examples/                   # 示例图表
    ├── ocean-blue/             # 海洋蓝主题（16 种图表）
    ├── dark-night/             # 暗夜主题 + 截图
    ├── forest-green/           # 森林绿主题
    ├── sunset-orange/          # 日落橙主题
    └── monochrome/             # 单色主题
```

## Requirements / 环境要求

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI
- [draw.io](https://app.diagrams.net) to open generated `.drawio` files

## License

[MIT](./LICENSE)
