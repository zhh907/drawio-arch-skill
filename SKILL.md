---
name: drawio-arch
description: "Generate professional draw.io (.drawio) diagrams with a multi-theme design system. Supports 16 diagram types covering the full project lifecycle: architecture, topology, flow, ER, sequence, component, network, class, activity, state, API map, wireframe, org-chart, timeline, comparison, mindmap. 5 color themes. Automated layout and quality checklist."
trigger: /drawio-arch
---

# /drawio-arch

Generate production-quality draw.io diagrams. Output is `.drawio` XML that opens directly in draw.io (app.diagrams.net).

## ⚠️ What You Must Do When Invoked (READ FIRST)

1. If `--help` or `-h`, print the **Usage** section below and stop immediately. Do NOT run any commands, do NOT detect files, do NOT default path to `.`.
2. If `all` is specified (e.g. `/drawio-arch all`), generate ALL 16 diagram types for the project. Ask user to confirm theme first. Each diagram goes to a separate file.
3. If a single diagram type is specified, ask the user to confirm **theme** (default: ocean-blue) then generate that one type.
4. If `audit <file>`, read the file and check every item in the **Quality Checklist**. Report all violations with exact element IDs and line numbers.
5. If `fix <file>`, read the file, identify all layout/color/content issues against the design system, and fix them. Re-verify after fixing.
6. If invoked without arguments, **immediately ask**: diagram type + theme preference. Do NOT start searching or reading any files before getting user confirmation.

## Usage

```
/drawio-arch                                                        # Interactive — pick type and theme
/drawio-arch all                                                    # 生成全部 16 种图表
/drawio-arch system <desc>                                          # 分层系统架构图
/drawio-arch business <desc>                                        # 业务能力地图
/drawio-arch topology <desc>                                        # 部署拓扑/集群架构
/drawio-arch dataflow <desc>                                        # 数据流向图
/drawio-arch component <desc>                                       # 组件依赖关系图
/drawio-arch sequence <desc>                                        # 时序交互图
/drawio-arch er <desc>                                              # 实体关系图（ER）
/drawio-arch network <desc>                                         # 网络拓扑（VPC/子网/负载均衡）
/drawio-arch class <desc>                                           # 类图/接口继承关系
/drawio-arch activity <desc>                                        # 活动图/业务流程
/drawio-arch state <desc>                                           # 状态机图
/drawio-arch api-map <desc>                                         # API 接口地图
/drawio-arch wireframe <desc>                                       # 页面线框图/布局原型
/drawio-arch org-chart <desc>                                       # 组织架构图/团队结构
/drawio-arch mindmap <desc>                                         # 思维导图/知识图谱
/drawio-arch timeline <desc>                                        # 项目排期/路线图
/drawio-arch comparison <desc>                                      # 方案对比（Before/After、A/B）
/drawio-arch custom <desc>                                          # 自定义布局
/drawio-arch audit <file.drawio>                                    # 质量审计
/drawio-arch fix <file.drawio>                                      # 修复布局/配色/内容问题
/drawio-arch theme <ocean-blue|dark-night|forest-green|sunset-orange|monochrome>   # 切换主题
```

### Full Project Diagram Set / 项目完整图表集

When `all` is specified, generate these 16 files in order:

```
01-系统架构图.drawio         system        系统分层架构（网关/服务/数据/基础设施）
02-业务架构图.drawio         business      业务能力地图（按领域分层）
03-部署拓扑图.drawio         topology      K8s/服务器部署拓扑
04-数据流图.drawio           dataflow      核心数据流向（从输入到输出）
05-组件依赖图.drawio         component     模块间依赖关系
06-时序图.drawio             sequence      核心接口调用时序
07-ER图.drawio               er            数据库实体关系
08-网络拓扑图.drawio         network       VPC/子网/安全组/负载均衡
09-类图.drawio               class         核心类继承和接口实现
10-活动图.drawio             activity      核心业务流程（下单/支付/回调）
11-状态机图.drawio           state         订单/任务/工单状态流转
12-API地图.drawio            api-map       全部 API 端点总览
13-线框图.drawio             wireframe     核心页面布局原型
14-组织架构图.drawio         org-chart     团队/角色/权限结构
15-思维导图.drawio           mindmap       项目知识体系/技术栈全景
16-排期路线图.drawio         timeline      版本规划和里程碑
```

## Themes / 主题色板

五套内置主题，每套 15 个语义化 token。选一个主题后，所有模块/容器/连接线自动替换对应色值，布局和排版规则不变。

### Theme 1: Ocean Blue (default) — 专业沉稳

适用场景：企业架构、系统设计、技术文档

| Token | Hex | 用途 |
|-------|-----|------|
| `PRIMARY_DARK` | `#0D47A1` | 标题栏、基础设施节点 |
| `PRIMARY` | `#1565C0` | 图层标题、主文字色 |
| `PRIMARY_MID` | `#1E88E5` | 核心模块填充 |
| `PRIMARY_LIGHT` | `#90CAF9` | 描边、连接线 |
| `PRIMARY_BG` | `#E3F2FD` | 容器背景 |
| `ACCENT` | `#43A047` | 二级模块填充（绿色） |
| `ACCENT_BG` | `#E8F5E9` | 强调色背景 |
| `ACCENT_TEXT` | `#2E7D32` | 强调色文字 |
| `NEUTRAL_BG` | `#F0F4F8` | 画布背景 |
| `NEUTRAL_BOARD` | `#E8EEF4` | 底板背景 |
| `NEUTRAL_ALT` | `#F5F7FA` | 备用容器背景 |
| `NEUTRAL_BORDER` | `#CFD8DC` | 底板边框 |
| `NEUTRAL_STROKE` | `#B0BEC5` | 二级描边 |
| `NEUTRAL_TEXT` | `#455A64` | 正文文字 |
| `WHITE` | `#FFFFFF` | 深色上的文字、白色填充 |

### Theme 2: Dark Night — 暗黑现代

适用场景：演示汇报、社交媒体、暗色主题文档

| Token | Hex | 用途 |
|-------|-----|------|
| `PRIMARY_DARK` | `#0D1B2A` | 标题栏、底板背景 |
| `PRIMARY` | `#1B2838` | 图层标题 |
| `PRIMARY_MID` | `#415A77` | 核心模块填充 |
| `PRIMARY_LIGHT` | `#778DA9` | 描边、连接线 |
| `PRIMARY_BG` | `#1B2838` | 容器背景 |
| `ACCENT` | `#E0A458` | 二级模块（暖金色） |
| `ACCENT_BG` | `#2A1F0E` | 强调色背景 |
| `ACCENT_TEXT` | `#E0A458` | 强调色文字 |
| `NEUTRAL_BG` | `#0D1B2A` | 画布背景 |
| `NEUTRAL_BOARD` | `#162032` | 底板背景 |
| `NEUTRAL_ALT` | `#1B2838` | 备用容器背景 |
| `NEUTRAL_BORDER` | `#415A77` | 底板边框 |
| `NEUTRAL_STROKE` | `#778DA9` | 二级描边 |
| `NEUTRAL_TEXT` | `#C8D0DA` | 正文文字 |
| `WHITE` | `#E8EEF4` | 深色上的文字 |

### Theme 3: Forest Green — 自然生态

适用场景：DevOps 仪表盘、健康/生物科技、可持续发展

| Token | Hex | 用途 |
|-------|-----|------|
| `PRIMARY_DARK` | `#1B5E20` | 标题栏、基础设施 |
| `PRIMARY` | `#2E7D32` | 图层标题 |
| `PRIMARY_MID` | `#43A047` | 核心模块填充 |
| `PRIMARY_LIGHT` | `#81C784` | 描边、连接线 |
| `PRIMARY_BG` | `#E8F5E9` | 容器背景 |
| `ACCENT` | `#00897B` | 二级模块（青色） |
| `ACCENT_BG` | `#E0F2F1` | 强调色背景 |
| `ACCENT_TEXT` | `#00695C` | 强调色文字 |
| `NEUTRAL_BG` | `#F1F8E9` | 画布背景 |
| `NEUTRAL_BOARD` | `#E8F5E9` | 底板背景 |
| `NEUTRAL_ALT` | `#F5F7FA` | 备用容器背景 |
| `NEUTRAL_BORDER` | `#A5D6A7` | 底板边框 |
| `NEUTRAL_STROKE` | `#81C784` | 二级描边 |
| `NEUTRAL_TEXT` | `#33691E` | 正文文字 |
| `WHITE` | `#FFFFFF` | 深色上的文字 |

### Theme 4: Sunset Orange — 温暖活力

适用场景：产品路线图、营销技术、创业路演

| Token | Hex | 用途 |
|-------|-----|------|
| `PRIMARY_DARK` | `#BF360C` | 标题栏、基础设施 |
| `PRIMARY` | `#D84315` | 图层标题 |
| `PRIMARY_MID` | `#F4511E` | 核心模块填充 |
| `PRIMARY_LIGHT` | `#FF8A65` | 描边、连接线 |
| `PRIMARY_BG` | `#FBE9E7` | 容器背景 |
| `ACCENT` | `#FFB300` | 二级模块（琥珀色） |
| `ACCENT_BG` | `#FFF8E1` | 强调色背景 |
| `ACCENT_TEXT` | `#FF8F00` | 强调色文字 |
| `NEUTRAL_BG` | `#FFF3E0` | 画布背景 |
| `NEUTRAL_BOARD` | `#FBE9E7` | 底板背景 |
| `NEUTRAL_ALT` | `#FFF8E1` | 备用容器背景 |
| `NEUTRAL_BORDER` | `#FFCCBC` | 底板边框 |
| `NEUTRAL_STROKE` | `#FFAB91` | 二级描边 |
| `NEUTRAL_TEXT` | `#4E342E` | 正文文字 |
| `WHITE` | `#FFFFFF` | 深色上的文字 |

### Theme 5: Monochrome — 极简单色

适用场景：打印文档、正式报告、学术论文

| Token | Hex | 用途 |
|-------|-----|------|
| `PRIMARY_DARK` | `#212121` | 标题栏、基础设施 |
| `PRIMARY` | `#424242` | 图层标题 |
| `PRIMARY_MID` | `#616161` | 核心模块填充 |
| `PRIMARY_LIGHT` | `#9E9E9E` | 描边、连接线 |
| `PRIMARY_BG` | `#F5F5F5` | 容器背景 |
| `ACCENT` | `#37474F` | 二级模块 |
| `ACCENT_BG` | `#ECEFF1` | 强调色背景 |
| `ACCENT_TEXT` | `#263238` | 强调色文字 |
| `NEUTRAL_BG` | `#FAFAFA` | 画布背景 |
| `NEUTRAL_BOARD` | `#F5F5F5` | 底板背景 |
| `NEUTRAL_ALT` | `#EEEEEE` | 备用容器背景 |
| `NEUTRAL_BORDER` | `#E0E0E0` | 底板边框 |
| `NEUTRAL_STROKE` | `#BDBDBD` | 二级描边 |
| `NEUTRAL_TEXT` | `#424242` | 正文文字 |
| `WHITE` | `#FFFFFF` | 深色上的文字 |

## Typography / 排版层级

All text uses `align=center;verticalAlign=middle;whiteSpace=wrap;` as base.

| Level | Size | Style | Color Token | 用途 |
|-------|------|-------|-------------|------|
| H1 Title | 18-22px | `fontStyle=1` | `WHITE` | 图表主标题 |
| H2 Layer | 11-13px | `fontStyle=1` | `PRIMARY` | 图层/容器标题 |
| H3 Module | 10-11px | `fontStyle=1` | `WHITE` or `PRIMARY` | 模块标签 |
| H4 Detail | 8-9px | default | `PRIMARY` or `ACCENT_TEXT` | 技术细节、子说明 |
| H5 Micro | 7px | `fontStyle=1` | `PRIMARY` | 端口号、微型标签 |

## Module Styles / 模块样式

Replace `{TOKEN}` with hex values from the chosen theme. Base style for all modules: `rounded=1;arcSize=6;whiteSpace=wrap;align=center;verticalAlign=middle;`

### M1 — Primary Module / 核心模块

```
rounded=1;arcSize=6;fillColor={PRIMARY_MID};strokeColor=none;fontColor={WHITE};fontSize=10;fontStyle=1;whiteSpace=wrap;align=center;verticalAlign=middle;
```

### M2 — Secondary Module / 二级模块（强调色）

```
rounded=1;arcSize=6;fillColor={ACCENT};strokeColor=none;fontColor={WHITE};fontSize=10;fontStyle=1;whiteSpace=wrap;align=center;verticalAlign=middle;
```

### M3 — Outlined Module / 描边模块

```
rounded=1;arcSize=6;fillColor={WHITE};strokeColor={PRIMARY_LIGHT};strokeWidth=1;fontColor={PRIMARY};fontSize=8;whiteSpace=wrap;align=center;verticalAlign=middle;
```

### M4 — Light Fill Module / 浅色模块

```
rounded=1;arcSize=6;fillColor={PRIMARY_BG};strokeColor={PRIMARY_LIGHT};strokeWidth=1;fontColor={NEUTRAL_TEXT};fontSize=8;whiteSpace=wrap;align=center;verticalAlign=middle;
```

### M5 — Infra Module / 基础设施模块（深色）

```
rounded=1;arcSize=6;fillColor={PRIMARY_DARK};strokeColor=none;fontColor={WHITE};fontSize=9;fontStyle=1;whiteSpace=wrap;align=center;verticalAlign=middle;
```

### M6 — Database / Storage / 数据库（圆柱）

```
shape=cylinder3;size=10;fillColor={PRIMARY_DARK};strokeColor=none;fontColor={WHITE};fontSize=9;fontStyle=1;whiteSpace=wrap;align=center;verticalAlign=middle;
```

### M7 — Decision / Gateway / 决策网关（菱形）

```
rhombus;fillColor={ACCENT};strokeColor=none;fontColor={WHITE};fontSize=9;fontStyle=1;whiteSpace=wrap;align=center;verticalAlign=middle;
```

### M8 — Actor / User / 用户角色

```
shape=mxgraph.basic.smiley;fillColor={PRIMARY_BG};strokeColor={PRIMARY_LIGHT};strokeWidth=2;fontColor={PRIMARY};fontSize=9;whiteSpace=wrap;align=center;
```

## Container Styles / 容器样式

### C1 — Layer Container / 图层容器

```
swimlane;fillColor={PRIMARY_BG};strokeColor={PRIMARY_LIGHT};strokeWidth=2;fontColor={PRIMARY};fontSize=11;fontStyle=1;rounded=1;arcSize=6;horizontal=1;collapsible=0;startSize=22;spacingLeft=8;container=1;
```

### C2 — Sub-Container / 子容器（服务分组）

```
swimlane;fillColor={NEUTRAL_ALT};strokeColor={NEUTRAL_STROKE};strokeWidth=2;fontColor={PRIMARY};fontSize=10;fontStyle=1;rounded=1;arcSize=6;horizontal=1;collapsible=0;startSize=20;spacingLeft=6;container=1;
```

### C3 — Nested Container / 嵌套容器（Pod/副本集）

```
swimlane;fillColor={WHITE};strokeColor={NEUTRAL_BORDER};strokeWidth=1;fontColor={NEUTRAL_TEXT};fontSize=8;fontStyle=1;rounded=1;arcSize=6;horizontal=1;collapsible=0;startSize=16;container=1;
```

### C4 — Board Container / 全局底板（根容器）

```
swimlane;fillColor={NEUTRAL_BOARD};strokeColor={NEUTRAL_BORDER};strokeWidth=2;rounded=1;arcSize=4;startSize=0;horizontal=0;container=1;collapsible=0;
```

## Connector Styles / 连接线样式

### Directed Arrow / 有向箭头（主色）

```
edgeStyle=orthogonalEdgeStyle;rounded=1;orthogonalLoop=1;jettySize=auto;strokeColor={PRIMARY_LIGHT};strokeWidth=2;endArrow=block;endFill=1;
```

### Directed Arrow / 有向箭头（强调色）

```
edgeStyle=orthogonalEdgeStyle;rounded=1;orthogonalLoop=1;jettySize=auto;strokeColor={ACCENT};strokeWidth=2;endArrow=block;endFill=1;
```

### Bidirectional Arrow / 双向箭头

```
edgeStyle=orthogonalEdgeStyle;rounded=1;orthogonalLoop=1;jettySize=auto;strokeColor={PRIMARY_LIGHT};strokeWidth=2;endArrow=block;endFill=1;startArrow=block;startFill=1;
```

### Dashed Arrow / 虚线箭头（异步/可选）

```
edgeStyle=orthogonalEdgeStyle;rounded=1;orthogonalLoop=1;jettySize=auto;strokeColor={PRIMARY_LIGHT};strokeWidth=2;dashed=1;dashPattern=8 4;endArrow=block;endFill=1;
```

### Exit/Entry Points / 出入点

- Left-to-right: `exitX=1;exitY=0.5;entryX=0;entryY=0.5;`
- Top-to-bottom: `exitX=0.5;exitY=1;entryX=0.5;entryY=0;`

## Layout Formulas / 布局计算公式

### Module Fill (Single Row) / 单行均分

```
availableWidth = W - 2 * P - (N - 1) * G
moduleWidth    = floor(availableWidth / N)
x_i            = P + i * (moduleWidth + G)
```

Standard: `P = 12`, `G = 4` (紧凑) or `G = 8` (宽松).

### Module Fill (Multiple Rows) / 多行均分

```
rowHeight = moduleHeight + rowGap     // standard: 26 + 6 = 32
totalHeight = startSize + R * rowHeight + bottomPadding
y_row = startSize + padding + row * rowHeight
x_col = padding + col * (moduleWidth + gap)
```

### Two-Line Module / 双行模块（标签+详情）

```
Module height: 42px
Primary label: y + 4, height 18, fontSize 10, bold, {WHITE}
Tech detail:   y + 22, height 16, fontSize 8, {PRIMARY_LIGHT}
```

### Sequence Layout / 时序图布局

```
laneWidth = (canvasWidth - 2 * margin) / N_actors
messageY = startY + i * verticalStep
arrowY = messageY + lifelineOffset
```

### ER Layout / ER 图布局

```
entityWidth = 200
fieldHeight = 24
entityHeight = headerHeight(32) + N_fields * fieldHeight
x_entity = grid_col * (entityWidth + hGap) + margin
y_entity = grid_row * (entityHeight + vGap) + margin
```

## Diagram Types / 图表类型（16 种）

### Type 1: System Architecture / 系统架构图 (system)

纵向分层堆叠，每层为 C1 容器。

```
Canvas: 2000 x (48 + N_layers * 120)
Layout: Title bar → L1 → L2 → ... → Ln
Modules: M1 (核心服务), M2 (二级服务), M5 (基础设施)
Connectors: 可选，层间连接
```

### Type 2: Business Architecture / 业务架构图 (business)

宽层多模块，6-10 层。

```
Canvas: 2000 x (48 + N_layers * 100)
Layout: 同 system，但层更矮，模块更紧凑
Modules: M1, M2, M3 (子能力)
```

### Type 3: Deployment Topology / 部署拓扑图 (topology)

左右分区，不同环境/区域。

```
Canvas: 1900 x calculated
Layout: L1 (外部接入) → L2 (网关) → L3 (应用集群) → L4 (数据层) → L5 (运维监控)
Sub-containers: C2 (服务器组), C3 (Pod)
Modules: M1, M2, M5, M6 (数据库)
```

### Type 4: Data Flow / 数据流图 (dataflow)

左侧图例 + 流向通道，箭头表示数据方向。

```
Canvas: 2000 x calculated
Left: 图例面板 (C1, 160px)
Main: 流程节点 (M1, M5, M6) 通过有向箭头连接
Labels: 箭头上的标签（如"行情数据"、"WebSocket推送"）
```

### Type 5: Component Diagram / 组件依赖图 (component)

节点和边展示依赖关系。

```
Canvas: 1600 x 1200 (or auto-fit)
Layout: 自由布局或网格，无严格分层
Nodes: M1 (内部组件), M3 (外部 API), M6 (数据库)
Edges: 有向箭头表示依赖方向
Groups: C2 表示限界上下文
```

### Type 6: Sequence Diagram / 时序图 (sequence)

纵向生命线 + 横向消息箭头。

```
Canvas: 1600 x calculated
Lifelines: 纵向虚线，每个参与者一条
Messages: 生命线间的横向箭头
Activation boxes: 生命线上的小矩形（高度=持续时间）
Self-calls: 折回同一生命线的箭头
Alt/loop frames: 包裹消息组的圆角矩形
```

Lifeline style:
```
dashed=1;dashPattern=5 5;strokeColor={PRIMARY_LIGHT};strokeWidth=1;endArrow=none;
```

### Type 7: ER Diagram / 实体关系图 (er)

实体盒子 + 字段列表 + 关系线。

```
Canvas: Auto-fit (min 1600x800)
Entities: C1 容器内含字段行
  Header: 实体名 (H2, PRIMARY fill)
  Fields: M3 行 (field_name : type)
  PK: 加粗, PRIMARY 色
  FK: 斜体, ACCENT 色
Relations: 连线 + 鸦脚记法或 Chen 记法
Cardinality labels: "1", "N", "1..*", "0..1"
```

### Type 8: Network Topology / 网络拓扑图 (network)

VPC/子网布局。

```
Canvas: 2000 x 1200
Regions: C1 容器 (VPC, 可用区)
Subnets: C2 容器嵌套在 Region 内
Nodes: M1 (服务器), M5 (路由器), M6 (存储)
Connectors: 实线=有线, 虚线=VPN/隧道
Labels: IP 范围、端口号、协议
Zone colors: 不同可用区用不同 PRIMARY_BG 深浅区分
```

### Type 9: Class Diagram / 类图 (class)

类继承、接口实现、关联关系。

```
Canvas: Auto-fit (min 1600x800)
Classes: C1 容器，三段式（类名/属性/方法）
  Header: 类名 (H3, PRIMARY fill), abstract 用斜体
  Attributes: M3 行 (visibility name: Type)
  Methods: M3 行 (visibility name(params): ReturnType)
Inheritance: 实线 + 空心三角箭头 (extends)
Implementation: 虚线 + 空心三角箭头 (implements)
Association: 实线箭头 + 基数标签
Composition: 实线 + 实心菱形
```

### Type 10: Activity Diagram / 活动图 (activity)

业务流程/算法步骤。

```
Canvas: Auto-fit (min 1600x600)
Start: M7 (菱形) 或 实心圆
Activities: M1 (圆角矩形), 纵向或横向排列
Decisions: M7 (菱形) 分支, 带 [condition] 标签
Fork/Join: 粗横线 (平行条) 表示并发
End: M7 (菱形) 或 圆环
Swimlanes: C2 容器表示不同角色/系统
Flow: 有向箭头连接各步骤
```

### Type 11: State Machine / 状态机图 (state)

状态流转。

```
Canvas: Auto-fit (min 1200x600)
States: M1 (圆角矩形), 内含 state name
  Sub-states: C3 嵌套容器
Initial: 实心圆
Final: 圆环 (圆内实心圆)
Transitions: 有向箭头 + [event]/guard/action 标签
Self-transition: 折回箭头
Composite states: C2 容器含多个子状态
```

### Type 12: API Map / API 接口地图 (api-map)

全部 API 端点总览。

```
Canvas: 2000 x calculated
Layout: 按模块分组的网格
Groups: C2 容器 (每个 Controller/Resource 一组)
Endpoints: M1 (GET), M2 (POST), M4 (PUT/PATCH), M5 (DELETE)
  每个端点显示: method + path + 简短描述
HTTP method color coding:
  GET  → M1 (PRIMARY_MID)
  POST → M2 (ACCENT)
  PUT  → M4 (light fill)
  DELETE → M5 (dark)
Version prefix: 作为组标题的一部分
```

### Type 13: Wireframe / 线框图 (wireframe)

页面布局原型。

```
Canvas: 1440 x 900 (desktop) or 375 x 812 (mobile)
Layout: 浏览器/设备外框 (C4)
Header: M5 (导航栏)
Sidebar: C2 (侧边栏)
Content area: C1 主内容区
Components: M3 (按钮), M4 (输入框), M1 (卡片)
Annotations: M3 标注组件名称和功能
Grid: 使用 12 列网格系统对齐
```

### Type 14: Org Chart / 组织架构图 (org-chart)

团队/角色/权限结构。

```
Canvas: Auto-fit (min 1600x600)
Layout: 树形层级，自上而下
Nodes: M1 (团队), M2 (角色), M3 (个人)
Connectors: 直线或折线，无箭头（汇报关系）
Levels: 部门 → 团队 → 角色 → 职责
Labels: 节点内显示 名称 + 职位/职责
```

### Type 15: Mindmap / 思维导图 (mindmap)

知识体系/技术栈全景。

```
Canvas: 2000 x 1200
Center: M1 (核心主题，大尺寸)
Branches: 从中心向外辐射的曲线
  Level 1: M1 (主分支，PRIMARY fill)
  Level 2: M3 (子分支)
  Level 3: M4 (叶子节点)
Connectors: curved=1;strokeColor={PRIMARY_LIGHT};
Layout: 放射状分布，4-8 个主方向
```

Mindmap connector style:
```
edgeStyle=elbowEdgeStyle;elbow=vertical;curved=1;rounded=1;strokeColor={PRIMARY_LIGHT};strokeWidth=2;endArrow=none;exitX=1;exitY=0.5;entryX=0;entryY=0.5;
```

### Type 16: Timeline / Roadmap / 排期路线图 (timeline)

横向泳道 + 时间列。

```
Canvas: 2000 x calculated
Columns: 时间段（周/月/季度）
Rows: 团队、模块或工作流
Bars: M1 填充=进行中, M4=计划中
Milestones: M7 (菱形) 标注关键日期
Today line: 当前日期的纵向虚线
```

### Type 17: Comparison / 方案对比图 (comparison)

左右并排面板，Before/After 或 A/B 对比。

```
Canvas: 2000 x calculated
Layout: 2-3 个面板并排
Panel: C2 容器 + 标签
Items: M3 行 + 勾选/叉号或数值
Divider: 面板间的纵向分割线
Header: 面板标题（如 "Before", "After"）
```

## Content Rules / 内容规则

### MUST / 必须遵守

- All text MUST be in the user's primary language
- Layer names MUST use "L1 / L2 / L3..." prefix for clear ordering
- Every swimlane MUST have `container=1`
- All elements MUST use `rounded=1;arcSize=6` (BG_BOARD uses `arcSize=4`)
- Title bar: 36-48px, title text centered
- Module gaps MUST be uniform within a row (4px or 8px)
- All colors MUST come from the chosen theme — NO random colors

### MUST NOT / 禁止事项

- NO version numbers anywhere (v3.0, v1.2.0, etc.)
- NO "迭代版" / "Beta" / "Draft" / "规划" labels
- NO decorative English text without information value
- NO duplicate elements or overlapping panels
- NO inconsistent module widths within the same row
- NO text concatenation bugs (e.g., "LabelLabel" from bad generation)

### Naming Conventions / 命名规范

- Element IDs: hierarchical prefixes (`L1`, `L2`, `L1_M1`, `L1_M1_T`, `L1_M1_D`)
- Layer value: `"L{n} {Name}"` (e.g., `"L1 网络入口层"`)
- Module value: Component name only, no extra decoration

## Generation Workflow / 生成流程

### Step 1: Confirm / 确认需求

Ask user: diagram type + theme (default: ocean-blue) + output path.

### Step 2: Plan Layout / 规划布局

1. Count layers/entities/actors and content per group
2. Calculate canvas size:
   ```
   canvasHeight = titleBar(48) + sum(groupHeights) + gaps + margin(20)
   canvasWidth  = 2000 (standard) or auto-fit
   ```
3. Calculate positions using fill formulas
4. Verify no overlaps — every element's bounding box must not intersect another

### Step 3: Generate XML / 生成 XML

1. File header + mxGraphModel with theme's `NEUTRAL_BG` as canvas `background`
2. BG_BOARD (C4 style with theme colors)
3. Title bar: `fillColor={PRIMARY_DARK}`, title text centered
4. Layers/entities/actors as containers
5. Modules at calculated positions
6. Connectors between elements
7. Legend panel if applicable

### Step 4: Self-Check / 自检

Run every item in the **Quality Checklist** before writing the file. Fix all violations before output.

## Quality Checklist / 质量检查清单

### Layout / 布局
- [ ] Same-row modules have identical width (同行模块等宽)
- [ ] Gaps are uniform: 4px or 8px (间距统一)
- [ ] No overlaps or elements extending beyond parent (无遮挡/无溢出)
- [ ] Bottom edges horizontally aligned where appropriate (底部水平对齐)
- [ ] Left/right margins consistent across groups (左右边距一致)
- [ ] Canvas fits all content with ~20px margin (画布适配内容)

### Typography / 排版
- [ ] Title is H1: 18px bold (主标题)
- [ ] Layer headers are H2: 11-13px bold (图层标题)
- [ ] Module labels are H3: 10-11px (模块标签)
- [ ] No text concatenation bugs (无文字拼接 bug)
- [ ] Text fits within element bounds (文字不溢出)

### Colors / 色彩
- [ ] All colors from the chosen theme palette (颜色来自选定主题)
- [ ] Module fills match semantic role: primary/secondary/infra (模块填充语义匹配)
- [ ] Container backgrounds consistent (容器背景一致)
- [ ] No random or off-theme colors (无随机色)

### Content / 内容
- [ ] No version numbers (无版本号)
- [ ] No decorative English text (无英文装饰文字)
- [ ] No "迭代版" / "规划" labels (无规划标签)
- [ ] All text in user's primary language (使用用户主语言)
- [ ] Layer IDs follow L1, L2, L3... (图层编号规范)
- [ ] No duplicate elements (无重复元素)

### Structure / 结构
- [ ] BG_BOARD exists as root container with C4 style (底板容器存在)
- [ ] All layers are swimlane containers with `container=1` (图层为 swimlane)
- [ ] All modules are children of their container (模块属于正确容器)
- [ ] Connector source/target IDs are valid and exist (连接线引用有效)
- [ ] XML is well-formed: all tags closed, attributes quoted (XML 格式正确)

## File Output / 文件输出

- Default directory: `doc/arch/drawio/`
- Naming: descriptive (e.g., `01-系统架构图.drawio`)
- Always write a COMPLETE, VALID `.drawio` XML file
- Never output partial XML — the file must be openable in draw.io

## Technical Notes / 技术说明

- `parent="1"` = direct child of root. `parent="BG_BOARD"` = child of BG_BOARD.
- `startSize` = header height in px. `startSize=0` = no visible header.
- `horizontal=1` = child elements flow left-to-right. `horizontal=0` = top-to-bottom.
- Use `grid-size="10"` for snap-to-grid alignment.
- All coordinates are absolute within the parent container.
- Modules MUST use `parent="LAYER_ID"` to be visually contained in their layer.
