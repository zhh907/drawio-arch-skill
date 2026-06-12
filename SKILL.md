---
name: drawio-arch
description: "Generate professional draw.io (.drawio) diagrams. 17 types, 5 themes, 4-layer business standard model, automated layout, quality checklist."
trigger: /drawio-arch
---

# /drawio-arch

Generate production-quality draw.io diagrams. Output is `.drawio` XML that opens directly in draw.io (app.diagrams.net).

## ⚠️ Invocation Rules

1. `--help`/`-h` → print Usage and stop.
2. `all` → ask theme confirmation, then generate all 17 types in `doc/arch/drawio/`.
3. Single type → confirm **theme** (default: ocean-blue), then generate.
4. `audit <file>` → check every item in Quality rules.
5. `fix <file>` → identify and fix all layout/color/content issues.
6. No arguments → **immediately ask**: diagram type + theme. Do NOT read files before confirmation.

**★ Pre-generation mandatory flow**:
1. Check "必须包含内容" table for the target type → collect project info accordingly
2. **余量分配法算坐标** → plan all node positions before XML; rightmost edge == container edge (0px error)
3. **反向算高度** → content → container → BG_BOARD → canvasHeight. Never pre-set fixed canvas height
4. **Verify**: no overlap, rightmost aligns, bottom blank < 40px, container blank < 10%
5. **Count cells** → below minimum → add content. Never output sparse diagrams

## Usage

```
/drawio-arch [type] [desc]            # Single diagram
/drawio-arch all                      # All 17 types
/drawio-arch audit <file.drawio>      # Quality audit
/drawio-arch fix <file.drawio>        # Fix layout
/drawio-arch theme <ocean-blue|dark-night|forest-green|sunset-orange|monochrome>
```

Keywords: `system` `business` `topology` `dataflow` `component` `sequence` `er` `network` `class` `activity` `state` `api-map` `wireframe` `org-chart` `mindmap` `timeline` `comparison` `custom`

### 17 File Set

| # | File | keyword | Description |
|---|------|---------|-------------|
| 01 | 系统架构图 | system | 分层系统架构（网关/服务/数据/基础设施） |
| 02 | 业务架构图 | business | 业务能力地图（4 层标准模型） |
| 03 | 部署拓扑图 | topology | K8s/服务器部署拓扑 |
| 04 | 数据流图 | dataflow | 核心数据流向 |
| 05 | 组件依赖图 | component | 模块间依赖关系 |
| 06 | 时序图 | sequence | 核心接口调用时序 |
| 07 | ER图 | er | 数据库实体关系 |
| 08 | 网络拓扑图 | network | VPC/子网/负载均衡 |
| 09 | 类图 | class | 核心类继承和接口实现 |
| 10 | 活动图 | activity | 核心业务流程 |
| 11 | 状态机图 | state | 订单/任务状态流转 |
| 12 | API地图 | api-map | 全部 API 端点总览 |
| 13 | 线框图 | wireframe | 核心页面布局 |
| 14 | 组织架构图 | org-chart | 团队/角色结构 |
| 15 | 思维导图 | mindmap | 项目知识体系 |
| 16 | 排期路线图 | timeline | 版本规划和里程碑 |
| 17 | 方案对比图 | comparison | Before/After、A/B |

---

## 4-Layer Business Standard Model ★

> All chart types use this 4-layer model for content organization. Other charts (system/topology) adjust layer naming by type.

| 层 | 中文名 / English | 职责 | 典型内容 |
|----|-----------------|------|---------|
| **L1** | 核心业务能力域 / Core | 平台**能做什么** | 行情/策略/信号/AI预测/技术分析/资讯 |
| **L2** | 支撑业务能力 / Supporting | **跨域通用能力**（横切） | 通知/推送/报表/可观测性 |
| **L3** | 通用业务能力 / Common | **平台基础**（谁用、用什么对象） | 用户认证/后台管理/业务对象 |
| **L4** | 关键业务流程 / Process | **端到端流程**横切 L1+L2+L3 | 数据采集/信号推送/AI分析 |

### 配色

| 层 | 底色 | 域头 | 子能力 |
|----|------|------|--------|
| L1 核心 | `#E3F2FD` | `#1E88E5` 实心白字 | `#E3F2FD` + `#0D47A1` 文字 |
| L2 支撑 | `#E8F5E9` | `#43A047` 实心白字 | `#E8F5E9` + `#1B5E20` 文字 |
| L3 通用 | `#FFF8E1` | `#FF8A65` 实心白字 | `#FFF3E0` + `#4E342E` 文字 |
| L4 流程 | `#E3F2FD` | `#FFFFFF` + `#1565C0` 描边 | 6 步流水线 |

流程节点三色：业务步骤 `#1E88E5` | 异步/外部 `#43A047` | 存储 `cylinder3` + `#0D47A1` | 入口/出口 `#0D47A1`

跨层关系：L1→L2（实线）、L1→L3（实线）、L2→L3（实线）、L4 横切

### 反模式（4 层通用）

| ❌ | ✅ |
|----|-----|
| 客户触点混进 L1 | L1 只放业务能力 |
| "数据库"作为子能力 | 存储出现在 L4 流程节点 |
| 业务对象散落各域 | 独立成 L3 子域 |
| 缺 L4 流程 | 底部 2-3 个端到端流程 |
| 流程节点单色 | 三色区分（蓝/绿/深蓝） |
| 单语标签 | 强制双语：中文 + 英文 |
| 能力数 < 50 | 推荐 60-90 |
| 域头浅色填充 | 域头必须实心 M1，子能力浅色 M4 |

---

## Themes

默认 **ocean-blue**。切换时替换所有 `fillColor`/`strokeColor`/`fontColor`。

### Ocean Blue (default)

| Token | Hex | 用途 |
|-------|-----|------|
| PRIMARY_DARK | `#0D47A1` | 标题栏、基础设施 |
| PRIMARY | `#1565C0` | 图层标题 |
| PRIMARY_MID | `#1E88E5` | 核心模块填充 |
| PRIMARY_LIGHT | `#90CAF9` | 描边、连接线 |
| PRIMARY_BG | `#E3F2FD` | 容器背景 |
| ACCENT | `#43A047` | 二级模块（绿） |
| ACCENT_BG | `#E8F5E9` | 强调色背景 |
| ACCENT_TEXT | `#2E7D32` | 强调色文字 |
| NEUTRAL_BG | `#F0F4F8` | 画布背景 |
| NEUTRAL_BOARD | `#E8EEF4` | 底板背景 |
| NEUTRAL_ALT | `#F5F7FA` | 备用容器 |
| NEUTRAL_BORDER | `#CFD8DC` | 底板边框 |
| NEUTRAL_STROKE | `#B0BEC5` | 二级描边 |
| NEUTRAL_TEXT | `#455A64` | 正文文字 |
| WHITE | `#FFFFFF` | 深色上的文字 |

### Theme 2-5

| 主题 | 主色 | 强调色 | 适用 |
|------|------|--------|------|
| Dark Night | `#0D1B2A` | `#E0A458` | 演示、暗色文档 |
| Forest Green | `#1B5E20` | `#00897B` | DevOps、健康 |
| Sunset Orange | `#BF360C` | `#FFB300` | 路线图、营销 |
| Monochrome | `#212121` | `#37474F` | 打印、正式报告 |

---

## Audience & Must-Include

**核心原则**：一张图一个受众，业务术语和技术术语不混用，分层即分责。

| # | keyword | 受众 | 必须包含内容 | 禁区 |
|---|---------|------|------------|------|
| 1 | system | 技术 | 用户层+接入(Nginx/Gateway)+业务服务+中间件(Redis/MQ)+数据(MySQL/ES)+基础设施(K8s)+监控日志 | ❌业务描述 |
| 2 | business | 业务 | 业务域+业务模块+业务能力+业务流程+上下游关系 | ❌技术术语/端口 |
| 3 | topology | 运维 | 入口+LB+K8s集群+服务器+服务实例+DB+缓存+中间件+第三方 | ❌业务能力/代码 |
| 4 | dataflow | 架构师 | 数据源+采集+处理+存储+分析+输出层+流向箭头 | ❌纯业务描述 |
| 5 | component | 开发 | 核心模块+公共组件+SDK+第三方+依赖方向 | ❌业务能力 |
| 6 | sequence | 开发 | 参与对象+调用顺序+请求响应+同步/异步+异常流程 | ❌无关系统 |
| 7 | er | 开发/DBA | 实体表+字段+PK+FK+1:1/1:N/N:M关系 | ❌业务流程 |
| 8 | network | 运维 | Internet+VPC+子网+安全组+LB+NAT+服务器+DB | ❌业务能力 |
| 9 | class | 开发 | 类名+属性+方法+继承+接口实现+聚合+组合 | ❌业务描述 |
| 10 | activity | 业务+技术 | 开始+步骤+判断+分支+结束 | 混合时标泳道 |
| 11 | state | 开发 | 状态节点+转换+触发事件+终止状态 | ❌无关实体 |
| 12 | api-map | 开发/前端 | 服务分组+接口名+请求方式+URL+依赖 | ❌实现细节 |
| 13 | wireframe | 产品/设计 | Header+菜单+导航+内容区+表格+表单+按钮+弹窗 | ❌技术实现 |
| 14 | org-chart | 管理层 | 部门+岗位+上下级+角色职责 | ❌技术组件 |
| 15 | mindmap | 全员 | 中心主题+一级+二级+关联关系 | 按领域组织 |
| 16 | timeline | 管理层 | 时间轴+里程碑+版本+交付物+负责人+风险 | ❌技术细节 |
| 17 | comparison | 全员 | Before/After 双栏+维度+差异+结论 | - |

对内对外标记：External=ACCENT/M3描边 | Internal=PRIMARY/M1实心 | Infra=PRIMARY_DARK/M5 | 3rd Party=ACCENT_BG+虚线

---

## Style Reference

Base: `html=1;rounded=1;arcSize=6;whiteSpace=wrap;`

**★ html=1 强制**：所有节点 style 必须含 `html=1`。value 中换行用 `&lt;br/&gt;`，加粗用 `fontStyle=1` 或 `&lt;b&gt;`，禁止 Markdown 或未转义 HTML。

### Typography

| Level | Size | Style | Color | 用途 |
|-------|------|-------|-------|------|
| H1 Title | 18-22px | bold | WHITE | 图表主标题 |
| H2 Layer | 11-13px | bold | PRIMARY | 图层标题 |
| H3 Module | 10-11px | bold | WHITE/PRIMARY | 模块标签 |
| H4 Detail | 8-9px | normal | PRIMARY/ACCENT | 技术细节 |

### Module Styles (base: `html=1;rounded=1;arcSize=6;whiteSpace=wrap;`)

| ID | Name | 样式 |
|----|------|------|
| M1 | Primary | `fillColor={PRIMARY_MID};strokeColor=none;fontColor={WHITE}` |
| M2 | Secondary | `fillColor={ACCENT};strokeColor=none;fontColor={WHITE}` |
| M3 | Outlined | `fillColor={WHITE};strokeColor={PRIMARY_LIGHT};fontColor={PRIMARY}` |
| M4 | Light Fill | `fillColor={PRIMARY_BG};strokeColor={PRIMARY_LIGHT};fontColor={NEUTRAL_TEXT}` |
| M5 | Infra | `fillColor={PRIMARY_DARK};strokeColor=none;fontColor={WHITE}` |
| M6 | Database | `shape=cylinder3;size=10;fillColor={PRIMARY_DARK};fontColor={WHITE}` |
| M7 | Decision | `rhombus;fillColor={ACCENT};fontColor={WHITE}` |
| M8 | Actor | `shape=mxgraph.basic.smiley;fillColor={PRIMARY_BG};strokeColor={PRIMARY_LIGHT}` |

### Container Styles

| ID | Name | 样式 |
|----|------|------|
| C1 | Layer | `swimlane;html=1;fillColor={PRIMARY_BG};strokeColor={PRIMARY_LIGHT};startSize=36;container=1` |
| C2 | Sub | `swimlane;html=1;fillColor={NEUTRAL_ALT};strokeColor={NEUTRAL_STROKE};startSize=28` |
| C3 | Nested | `swimlane;html=1;fillColor={WHITE};strokeColor={NEUTRAL_BORDER};startSize=22` |
| C4 | Board | `swimlane;html=1;fillColor={NEUTRAL_BOARD};strokeColor=#CFD8DC;startSize=0;horizontal=0` |

**★ 防遮挡规则**：
- `horizontal=1`（标题在顶部）：`startSize` = 标题栏高度，子节点 y >= startSize + 10
  - C1: y>=46 | C2: y>=38 | C3: y>=32
- `horizontal=0`（标题在左侧）：`startSize` = 标题列宽度，子节点 x >= startSize + 10
  - **填充宽度必须减去标题占位**：`availableWidth = containerWidth - startSize - 2*padding - (N-1)*gap`

### Connector Styles

| 类型 | 样式 |
|------|------|
| 有向箭头 | `edgeStyle=orthogonalEdgeStyle;rounded=1;strokeColor={PRIMARY_LIGHT};endArrow=block;endFill=1` |
| 强调色 | 同上 `strokeColor={ACCENT}` |
| 双向 | + `startArrow=block;startFill=1` |
| 虚线(异步) | + `dashed=1;dashPattern=8 4` |
| 缓存命中(绿) | `strokeColor=#43A047;strokeWidth=2` |
| 缓存未命中(红) | `strokeColor=#E53935;strokeWidth=2;dashed=1` |

出入点：左右 `exitX=1;exitY=0.5;entryX=0;entryY=0.5` | 上下 `exitX=0.5;exitY=1;entryX=0.5;entryY=0`

---

## Layout Formulas ★★★

### Canvas Fill Rules

```
规则1: BG_BOARD_W = canvasWidth - 40
规则2: layer_W = BG_BOARD_W - 20
规则3: 同行模块均分，余量分配，右边缘齐平
规则4: BG_BOARD_H = titleBar(48) + sum(layer_H) + gaps + legend(80) + 20
规则5: canvasHeight = BG_BOARD_H + 40（反向精确适配）
规则6: 容器H = 精确适配内容（startSize + 2*P + contentH），无空洞
规则7: 子模块W = layer_W - titleOffset - 2*P（见下方公式），禁止仅占50%
```

### ★ 余量分配法（宽度铺满）

```
P=12 (padding), G=6 (gap)

// ★ titleOffset 根据 horizontal 属性决定
titleOffset = (horizontal==0) ? startSize : 0

available  = layer_W - titleOffset - 2*P - (N-1)*G
baseModule = floor(available / N)
remainder  = available - baseModule * N

module_W[i] = baseModule + (i < remainder ? 1 : 0)
x[i]        = titleOffset + P + sum(module_W[0..i-1]) + i * G

验证: x[N-1] + module_W[N-1] == layer_W - P  // 严格齐平
```

### 高度自适应

```
// 反向计算：内容 → 容器 → 画布
swimlane_H = startSize + 2*P + N*(child_H + child_gap) - child_gap
bgBoard_H  = titleBar(48) + sum(layer_H) + (N_layers-1)*10 + legend(80) + 2*P
canvasH    = bgBoard_H + 40
```

### 专用布局

```
// 双行模块: H=42, 主标签 y+4/h18/fontSize10/bold, 技术标签 y+22/h16/fontSize8
// 时序图: laneWidth = (canvasW-2*margin)/N, messageY = startY+i*step
// ER图: entityW=200, fieldH=24, entityH=32+N*fieldH
```

### 坐标规划（生成前必做）

```
Step 1: 定 canvasWidth（2000/2400 by type）
Step 2: bgBoard_W = canvasWidth - 40
Step 3: 规划层数和每层节点
Step 4: 余量分配法算宽度（注意 horizontal=0 时 x 起点偏移 startSize）
Step 5: 验证 node_W >= 80（过窄拆行或增大 canvas）
Step 6: 反向算高度，canvasHeight 精确适配
Step 7: 算所有 x,y 坐标
Step 8: 验证无重叠（所有节点对无矩形交集）
Step 9: 验证铺满（右边缘齐平，底部空白<40px）
Step 10: 验证通过后写 XML

失败处理: 过窄→增大canvas | 重叠→增大层高 | 不满→余量分配法重算 | 底部空白→反向高度
```

---

## Anti-Overlap & Content Density ★★★

> **最高优先级**，违反任何一条即不合规。

### Anti-Overlap

```
硬约束: 同级间距>=4px(紧凑)/8px(宽松) | 层间>=12px | 节点与容器边>=8px
        父容器完全包含子节点 | 文本不溢出 | 连线不穿节点(orthogonal绕行)

自检: 按 y 排序 → child[i].y+h+gap <= child[i+1].y
      按 x 排序 → child[j].x+w+gap <= child[j+1].x
```

### Content Density

| Type | mxCell≥ | 内容节点≥ | Notes |
|------|---------|----------|-------|
| system | 200 | 35 | 每层≥5，共6层 |
| business | 300 | 60 | L1每domain≥6，共6domain |
| topology | 200 | 30 | 每服务器≥3+数据 |
| dataflow | 200 | 30 | 每层≥5，共6层 |
| component | 300 | 40 | 每zone≥10 |
| sequence | 150 | 7actor+12msg | +ALT框 |
| er | 200 | 12×5fields | |
| network | 180 | 25 | 每子网≥5 |
| class | 200 | 15 classes | |
| activity | 180 | 15 nodes+3判断 | |
| state | 120 | 8state+10trans | |
| api-map | 200 | 8×4=32端点 | |
| wireframe | 300 | 30 widgets | |
| org-chart | 150 | 12 roles | |
| mindmap | 150 | 7×4=28 | |
| timeline | 200 | 4×5=20 | |
| comparison | 150 | 6 dims | |

补充规则：双行标签(中文+英文) | 技术栈标注 | 版本号 | 数据格式(连接线) | 副本数 | 底部说明块

---

## 17 Type Quick Reference

### Per-Type Canvas & Layers

| Type | Canvas | Layers |
|------|--------|--------|
| system | 2000×auto | L1 Client(#FF8A65) → L2 Access(#1E88E5描边) → L3 App(#1E88E5实心) → L4 MW(#43A047) → L5 Data(#0D47A1圆柱) → L6 Infra(#0D47A1) |
| business | 2400×auto | 4层模型（L1核心/L2支撑/L3通用/L4流程），见4层标准模型章节 |
| topology | 1900×auto | L1 Traffic(#FF8A65) → L2 LB(#1E88E5描边) → L3 App(#1E88E5实心) → L4 Data(#0D47A1圆柱) → L5 DevOps(#43A047) |
| dataflow | 2200×auto | L1 Sources(M5) → L2 Ingestion(M1) → L3 Processing(M1) → L4 Cache(M6绿) → L5 Storage(M6深) → L6 Consumers(M2) |
| component | 1800×auto | Z1 External(M3描边) → Z2 Adapters(M1) → Z3 Core(M1) → Z4 Infra(M5) |
| sequence | 1600×auto | 纵向生命线+横向消息箭头，5-7 actor |
| er | 1600×800 | 实体盒子+字段列表+关系线(1:N/N:M/0..1) |
| network | 2000×auto | L1 Public(#E3F2FD) → L2 App(#E8F5E9) → L3 Data(#FFF3E0) → L4 Mgmt(#ECEFF1) |
| class | 1600×800 | 三段式：类名/属性/方法+关系线 |
| activity | 1600×600 | Start→Activities→Decisions→Fork/Join→End |
| state | 1200×600 | States+Transitions+Initial/Final |
| api-map | 2000×auto | 按 Controller 分组，标注 method+path |
| wireframe | 1400×900 | Header/Sidebar/Main/Footer+交互组件 |
| org-chart | 1600×auto | CEO→VP→Director→Manager→IC |
| mindmap | 1600×auto | Central→Main(5-7)→Sub |
| timeline | 2000×auto | Q1-Q4 时间轴+里程碑(菱形)+任务条 |
| comparison | 1800×auto | 左右双栏，每行一维度 |

底板统一样式: `swimlane;html=1;fillColor=#F0F4F8;strokeColor=#CFD8DC;startSize=0;container=1`

### Per-Type Anti-Patterns

**通用反模式**（所有类型）：
- ❌单层<4节点 → 补充子模块 | ❌数据库未用圆柱 → `cylinder3` | ❌容器空白>10% → 余量分配法
- ❌节点重叠 → 坐标规划后再写XML | ❌底部大片空白 → 反向高度计算

**特定反模式**：

| Type | ❌ 避免 | ✅ 正确 |
|------|---------|---------|
| system | 混合业务术语 | 技术组件(platform-web:BarController) |
| system | 缺L6基础设施 | 必须含监控/日志/CI/CD |
| business | 技术术语(Spring/MySQL) | 只用业务术语(K线图表分析) |
| business | 缺L4流程 | L4必须2-3个端到端 |
| business | 无数据来源说明 | 底部标注"基于N个Controller" |
| topology | 缺副本数/服务器规格 | 标xN副本+CPU/内存/磁盘 |
| topology | DB未区分主从 | 主库深色+从库浅色 |
| topology | 无L1外部流量 | 必须含CDN/DNS/WAF |
| dataflow | 箭头无数据格式 | 标JSON/Protobuf/gzip |
| dataflow | 缺L6消费层 | 必须含客户端/推送/可视化 |
| component | 循环依赖未标注 | 红虚线标 |
| component | 缺版本/包名 | 标com.erayt.x.y v3.0.0 |
| sequence | 无返回消息 | 同步必须画返回虚线箭头 |
| sequence | 无激活框/缺alt分支 | 生命线激活框+alt区分 |
| er | 字段无PK/FK | PK加粗PRIMARY，FK斜体ACCENT |
| er | 关系线无基数 | 标1/N/N:M |
| network | 无VPC边界 | 外层VPC swimlane框 |
| network | 无安全组规则 | 标注入站/出站端口 |
| class | 缺可见性符号 | +public/-private/#protected |
| class | 继承箭头方向反 | extends实线空心三角，implements虚线 |
| activity | 无Start/End | 实心圆=Start，圆环=End |
| activity | 缺条件分支 | M7菱形+[condition] |
| state | 无Initial/Final | 实心圆/圆环 |
| state | 转换缺事件/守卫 | 标[event]/[guard]//action |
| api-map | HTTP方法未标色 | GET蓝/POST绿/PUT橙/DELETE红 |
| api-map | 接口缺路径前缀 | 标context-path |
| wireframe | 混入技术实现 | 不画Spring/MySQL |
| wireframe | 无响应式说明 | 标桌面/平板/手机断点 |
| org-chart | 缺人数/职责 | 标headcount+responsibility |
| mindmap | 主分支>9 | 控制在5-7 |
| timeline | 无责任人/版本 | 标owner+v3.0.0/状态 |
| comparison | 维度不一致/无优劣标识 | 左右对应+✓/✗/⚠+底部推荐 |

---

## Technical Notes

1. **画布尺寸**：宽度预设、高度反向自适应。pageHeight 在内容计算完毕后精确设置。
2. **背景**：禁止单色填白，用浅色底板 `#F0F4F8`。
3. **节点ID**：语义化命名（`L1_client_web` 而非 `node1`）。
4. **html=1**：所有 mxCell style 必须包含 `html=1`，value 中 HTML 必须 XML 转义。
5. **swimlane 防遮挡**：horizontal=1 → 子节点 y>=startSize+10；horizontal=0 → 子节点 x>=startSize+10，宽度减 startSize。
6. **端口标注**：仅在 topology/network 两种图标注，其他图禁止。
7. **兼容性**：避免 mxGraph 高级特性（Custom Shape、Stencil）。

## File Output

```
位置: doc/arch/drawio/{NN}-{name}.drawio
格式: UTF-8 XML
结构: mxfile → mxGraphModel(pageWidth/pageHeight) → root → mxCell[0,1] → bg底板 → title → 层容器+子模块 → edges
```

---

**最后更新**: 2026-06-11（v2.1.0 精简版）
