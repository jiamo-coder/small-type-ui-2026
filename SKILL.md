---
name: small-type-ui-2026
description: 先问清关键需求，再审计、设计或升级企业后台、Pad 作业台、移动 App、企业官网、数据报表和信息可视化界面，使其遵循“2026 小字号 UI 2.0”；已有系统默认只读审计，仅在确认范围后实施。
---

# 2026 小字号 UI 2.0

```text
Design Standard: 2026 小字号 UI 2.0
Standard ID: small-type-ui-2026
Version: 2.11.0
```

以稳定模板、清晰层级和可验证的减法减少 UI 随机性。先读取事实，只问会改变设计的决策；不得把简洁误解为删除风险、权限、证据或错误恢复。

## 每次调用：同步规范

只从以下固定可信清单读取最新版：

```text
https://raw.githubusercontent.com/jiamo-coder/small-type-ui-2026/main/latest.json
```

1. 校验 HTTPS、主机 `raw.githubusercontent.com`、标准 ID、版本及资源 SHA-256。
2. 优先读取 `resources.designMethod`、`resources.uiQualityRules`、`resources.designSystem`、`resources.tokens` 和 `resources.templatePatterns`；只按任务平台读取 Website、Web Shell、Mobile、Tablet、Motion、Icon 或品牌资源。
3. 远端失败、字段异常或哈希不符时，使用本地 [references/ui-design-method.md](references/ui-design-method.md)、[assets/ui-quality-rules.json](assets/ui-quality-rules.json)、[references/design-system.md](references/design-system.md)、[assets/tokens.json](assets/tokens.json) 和 [assets/template-patterns.json](assets/template-patterns.json)，并明确标注“离线快照 `small-type-ui-2026@2.11.0`”。
4. 动态同步只更新设计规则，不授权修改产品代码、安装依赖、访问凭证或跨仓库写入。

## 工作闭环

```text
读取项目 → 自适应问需求 → 确认 Design Read → 固定模板选型 → 做减法 →
设计/审计 → 确认后实施 → 自动质量检查
```

### 1. 先读取，后提问

读取仓库说明、现有页面、组件、样式、截图、业务文档和可见状态。禁止询问能够自行发现的事实。

- 资料充分：不提问，直接输出紧凑 `Design Read`。
- 缺少会改变结构、范围、权限或验收的决定：每轮只问 1–3 个问题，每题给出推荐答案及影响。
- 只有新系统、需求明显模糊或用户明确要求深度访谈时才多轮追问。

进入设计前必须明确主要用户、首要任务、平台设备、对象与状态、关键操作、不可改范围和成功标准。完整格式与 UI-ready 判定读取 [references/ui-design-method.md](references/ui-design-method.md)。

### 2. 判断模式

- **新设计**：输出 Design Read，用户确认后才交付方案或原型。
- **已有系统**：默认只读，生成 `UI_2_AUDIT.md` 后停止；未经确认不得改产品代码。
- **已确认实施**：只实施已确认的 P0/P1 页面与组件，保留后台接口、业务规则、权限、数据结构和技术栈。

### 3. 确定性选模板

按 `平台 → 页面目标 → 对象规模 → 操作频率 → 证据/审核要求` 选择一个主模板，最多增加一个支持模板。模板约束信息顺序和交互闭环，不是业务数据合同，不得随机生成布局或把多个完整工作台堆在一页。

Website 读取 [references/website-standard.md](references/website-standard.md)；带侧栏 Web 工作台读取 [references/web-application-shell.md](references/web-application-shell.md)；Mobile、Tablet、动效、产品 Logo 和第三方品牌仅在相关时读取对应 references/assets。

### 4. 先做减法

每个可见元素必须至少服务于：`页面上下文 / 用户决策 / 业务行动 / 状态风险 / 数据证据 / 可访问性`。否则删除、合并或降级。

检查身份、数据、操作、容器、说明和装饰六类重复。不得删除对象身份、范围与时间、风险结论、数据新鲜度、权限上下文、证据来源、错误恢复、必要字段帮助及法律安全信息。

审计每项发现使用：

```text
屏幕上看到什么 → 给用户造成什么成本 → 删除或调整什么 → 保护哪些内容
```

## 审计交付

`UI_2_AUDIT.md` 必须包含：

1. 需求完整度与 Design Read。
2. 页面到主/支持模板的映射及不可照搬部分。
3. 减法机会与受保护内容。
4. 固定素材一致性：字体、图标、侧栏、顶栏、边距、组件状态和动效。
5. P0/P1/P2、影响页面、用户成本、迁移风险及验收方法。

P0 包含核心任务或上下文丢失、响应式不可用、假按钮、风险/权限/更新时间被隐藏、固定应用外壳严重漂移。P1 包含重复页头、重复 KPI/CTA、错误字号图标、局部间距和组件状态不完整。审计结束后停止，不修改代码。

## 实施边界

1. 只改确认的前端范围，优先复用现有组件与设计令牌。
2. 不新增后台接口、权限、数据字段、遥测、远程字体、网络资源或第三方依赖。
3. 不存在的通知、搜索、提交、联系、证据或成功状态必须隐藏、禁用或明确标记原型，不得伪造。
4. 加载、空、无结果、错误、权限不足、过期、成功恢复和组件 Default/Hover/Focus/Active/Disabled/Loading/Error/Success 状态必须完整。
5. 运行项目最快相关检查、`validate-ui-standard.mjs`（若项目包含）、Lint、生产构建和与平台匹配的响应式验收。

## 不可降级的固定值

- Web 侧栏：216px 展开、68px 折叠、248px 移动抽屉；菜单最多 8 个中文字符；折叠按钮及四态响应读取 Web Shell 参考。
- Web 顶栏：64px，顺序为面包屑、搜索、通知、身份、退出；内容左/右 28/16px，模块间距 12px。
- 固定顶栏已表达页面身份时，不再重复英文眉题、大标题和用途介绍；首屏直接进入状态、筛选、任务或简易可视化。
- Web 正文 14/22px，Mobile 正文 16/24px，所有可见文字不低于 12px；字重仅 400/500/600/700。
- 通用图标 24×24、1.75px 线宽；导航 20px、顶栏 18px；纯图标操作热区至少 44px 并有可访问名称。
- 企业后台、Mobile 和 Tablet 使用固定框架；Website 不继承工作台外壳，但仍遵守减法、真实性、响应式与 WCAG 2.2 AA。
- 颜色不是唯一状态编码；未知、缺失、过期和失败不得按零或正常处理。
- 动效有明确目的才使用，UI 最长 280ms，禁止 `transition: all`；减少动态效果时移除位移、缩放、视差和过冲。

## 交付

- 新设计：已确认 Design Read 后的结构、模板、状态、令牌、交互与可实现原型。
- 审计：`UI_2_AUDIT.md` 与简短结论。
- 实施：已确认改动、验证结果和仍需业务确认事项。
- 使用远端规范时报告实际版本；回退时同时报告离线快照版本。
