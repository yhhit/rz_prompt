# UI 参数与生图提示词笔记

## 速查总纲：当前最重要规则

本项目的 UI 参数不能只靠 `Colors / Typography / Shape / Depth / Motion` 这类 CSS Design Token 描述。否则不同软件类型会被模型统一生成成精细化 Web/CSS 产品稿。

后续参数优先级应为：

1. 软件类型与子类型
2. `Rendering Paradigm`：Web 应用 / 移动原生 / 桌面原生 / 工程上位机 / HMI-SCADA / 专业创作工具
3. `UI Framework`：React/Vue/Ant Design、SwiftUI/UIKit、Android Material、WPF/WinForms/MFC/Qt、WinCC/SCADA Runtime 等
4. `Component Language`：该框架真实常见组件，如 Ribbon、TreeView、PropertyGrid、SCADA alarm banner、Material BottomSheet 等
5. `Native Control Level`：原生控件强度
6. `CSS Styling Level`：允许多强的 CSS / Web 精修感
7. `OS / Era`：系统年代气质
8. `Window Frame / Title Bar` 或 `No Title Bar`
9. 页面骨架、导航结构、分区关系
10. 颜色、字体、圆角、描边、阴影、图标、动效

### 高优先级字段模板

后续每类 UI 参数模板建议在颜色、圆角、阴影之前加入：

```text
- Rendering Paradigm: `...`
- UI Framework: `...`
- Component Language: `...`
- Native Control Level: `none / low / medium / high / very high / industrial controls`
- CSS Styling Level: `none / very low / low / medium / high`
- OS Family: `...`
- OS Era: `...`
- OS Visual Traits: `...`
- Window Frame / Title Bar 或 No Title Bar: `...`
```

这些字段优先于 `Colors / Shape / Depth / Motion`。

### 风格字段不得混入业务场景

`Rendering Paradigm / UI Framework / Component Language / Native Control Level / CSS Styling Level` 只描述渲染方式、技术栈、控件体系和视觉实现层级，不描述具体业务场景。

允许写：

- `Web application`
- `React/Vue, Ant Design / Element Plus`
- `form controls, data table, pagination, drawer, modal, tabs`
- `WPF / WinForms / Qt / AppKit`
- `tree view, tab control, property pane, status bar`
- `Industrial HMI / SCADA runtime`
- `alarm banner, status lamp, trend chart, parameter grid`

不应写在这些字段里的内容：

- 具体业务词：客户、订单、财务、CRM、OA、市场报告等
- 具体场景词：会议、项目、知识库、串口调试、固件升级、设备维护等
- 具体功能流程：审批、报表生成、数据采集、烧录、巡检等

这些内容应放到：

- `Software Type`
- `Subtype`
- `Skeleton Type`
- `Navigation Pattern`
- `Panel Composition`
- `Control Style`
- 示例标题或具体示例参数

也就是说：风格字段管“像什么技术/框架/控件”，业务字段管“做什么场景/功能”。

### CSS 风格占比不是全禁，而是按类型分配

| 软件类型 | 推荐渲染范式 | UI 框架 / 技术语言 | CSS Styling Level |
|---|---|---|---|
| APP软件 | Mobile native app | iOS SwiftUI/UIKit, Android Material 3 | medium |
| 办公软件-桌面端 | Native desktop office software | WPF, WinForms, AppKit, SwiftUI, Office Ribbon | none/low |
| 办公软件-Web协作端 | Desktop web collaboration app | Electron-like Web app, React document editor | medium |
| 工具软件 | Desktop utility | WinForms, WPF, Qt, GTK | low |
| 嵌入式软件 | Engineering desktop utility | Qt Widgets, MFC, WinForms, WPF | very low |
| 工业控制系统 | HMI/SCADA/engineering workstation | WinCC, SCADA Runtime, Qt Industrial, MFC/WPF | none/very low |
| 监控软件 | Monitoring terminal / station control | SCADA terminal, Qt, WPF, controlled Web terminal | low/very low |
| 数据分析系统-Web BI | Web BI analytics platform | React/Vue charts, ECharts, BI dashboard | medium/high |
| 数据分析系统-桌面工作台 | Desktop analytics workstation | Qt, WPF, Java Swing-like tool | low |
| 建模软件 | Professional desktop modeling software | Qt, WPF, C++ desktop UI, OpenGL viewport | low |
| 设计软件 | Professional creative tool | AppKit, Qt, Electron-like design tool | medium |

### 标题栏规则

#### 办公软件
- 办公软件允许且通常应该出现操作系统标题栏、窗口控制按钮或桌面应用窗口框架。
- Windows 桌面办公软件应能出现顶部标题栏、最小化/最大化/关闭按钮、Ribbon 或命令栏。
- macOS 办公软件应能出现左上红黄绿窗口按钮、融合工具栏或半透明侧栏。
- Web 协作办公可以有浏览器/Electron 容器，但不能因此变成纯 SaaS 卡片页。

#### 其他类型
- 除办公软件外，其他类型不要为了体现 OS / Era 而刻意加入系统标题栏或窗口控制按钮。
- APP 软件尤其不能出现桌面标题栏。
- 工控/HMI/监控类应优先体现设备终端、站控界面、上位机工具或触摸屏结构。
- 管理系统、数据分析、设计、建模、工具、嵌入式等类型的 OS / Era 主要体现在控件、边框、密度、面板、导航和组件语言上。


### 管理系统归档规则

- `管理系统-200套.md` 已归档到 `归档/UI参数/管理系统-200套.md`。
- 后续不要再生成管理系统、管理后台、企业后台、SaaS 后台、后台表格管理类 UI 参数。
- 当前可继续生成的类型以 `UI参数/` 目录下未归档文件为准。
- 若其他分类的 `Avoid` 中提到“不要像管理系统/后台管理系统”，这是作为排除项保留，不代表继续生成管理系统风格。

### UI 参数区规范化规则

- 每个分类文件只保留一个 `## UI参数区`，所有真实可用参数统一放在该区域下。
- 删除旧的中间示例分组标题，例如 `更准确的...参数示例`、`重新示例参数`、`扩展差异化参数（第一批）`、`首批示例参数`。
- 规则区中的模板标题统一写成 `### 参数模板`，不要写成 `### 某分类 UI参数 X`，避免和真实参数混淆。
- 真实参数标题统一格式：`### 分类名 UI参数 001：主题名`，按每个分类独立连续编号。
- 新增参数时继续追加到 `## UI参数区` 末尾，并按当前分类最后编号递增。

### 办公软件最新结论

办公软件不能只写“现代桌面/浏览器办公工具”，否则容易生成精细 Web/CSS 风。

需要拆成两类：

1. 桌面办公软件型：
   - `Rendering Paradigm`: `native desktop office software`
   - `UI Framework`: `WPF / WinForms / AppKit / SwiftUI / Office Ribbon`
   - `Component Language`: `title bar, ribbon toolbar, tree view, document editor, property pane, status bar`
   - `CSS Styling Level`: `none / low`
2. Web 协作办公型：
   - `Rendering Paradigm`: `desktop web collaboration app / Electron-like app`
   - `UI Framework`: `React document editor / collaborative workspace`
   - `CSS Styling Level`: `medium`

若目标是桌面办公软件，应避免：`SaaS cards`、`CSS shadow`、`Dribbble UI`、`large rounded cards`、`browser-like web dashboard`。

### 工控 / 嵌入式 / 监控最新结论

这些类型几乎不能靠 CSS Design Token 描述。

- 工业控制系统：优先 `HMI / SCADA Runtime / WinCC / Qt Industrial`，`CSS Styling Level` 应为 `none / very low`。
- 嵌入式软件：优先 `Qt Widgets / MFC / WinForms / WPF 工程工具`，`CSS Styling Level` 应为 `very low`。
- 监控软件：优先 `站控终端 / 值守终端 / SCADA监控端 / Qt监控端`，`CSS Styling Level` 应为 `low / very low`。

### 后续修改 UI 参数文件时的执行顺序

1. 先补 `Rendering Paradigm / UI Framework / Component Language / Native Control Level / CSS Styling Level`。
2. 再补 `OS Family / OS Era / OS Visual Traits`。
3. 再处理 `Window Frame / Title Bar` 或 `No Title Bar`。
4. 再改 `Skeleton Type / Navigation Pattern / Panel Composition`。
5. 最后才调整 `Colors / Typography / Shape / Stroke / Depth / Icon / Motion`。

### 2026-04-29 工控低分辨率与低文字密度修正

用户继续反馈：工控类文字和表格太密集、缺少独创性，并且分辨率虽然变多但整体偏高。已再次调整 `UI参数/工业控制系统-100套.md`：

- 分辨率策略从“扩大到高分/超宽”改为“低分辨率和中低分辨率优先”。新增 `320×240`、`400×240`、`480×272`、`480×320`、`640×360`、`720×480`、`854×480`、`960×540`、`1024×576`、`1152×720` 等低/中低分辨率。
- 规则要求：100 套至少覆盖 28 种分辨率；低于 `1280×800` 不少于 45 套；`1920×1080` 及以上合计不超过 18 套；`2560` 宽度及以上不超过 8 套。
- 每 10 套至少 7 种分辨率，且至少 5 套低于 `1280×800`；相邻两套宽或高至少一项差异 ≥160px，避免分辨率只小幅变化。
- 新增低文字量规则：100 套中至少 55 套应为低文字量/低表格量；HMI/触摸屏端禁止高密度表格作为主体；工程上位机每 10 套最多 3 套高密表格。
- 新增独创性规则：每套必须有明显 `First-glance Signature`，优先使用环形仪表盘、设备剖面、管线流程图、九宫格大按钮、棋盘式状态灯、纵向柜门面板、急停控制面板、模块槽位图、横向警示跑马条等。
- 已把现有 001–013 示例从高分辨率/高密表格改成低分辨率、少文字、图形化面板示例，例如 `400×240` 四按钮 HMI、`480×272` 小宽屏警示面板、`640×360` 物理按钮面板、`272×480` 竖向柜门面板、`800×480` 模块槽位 HMI、`960×540` 双仪表联机控制、`1024×576` 低分参数旋钮面板等。

用户反馈工控类当前色彩和分辨率区别仍不够明显，生成结果容易集中在白色、深蓝色、深灰色，分辨率也只在常规桌面尺寸附近小幅变化。已调整 `UI参数/工业控制系统-100套.md`：

- 工控类不追求花哨色彩，但必须使用更宽的“合理工业配色族”，包括冷灰、银灰、暖米灰、砂岩米色、浅青灰、钢蓝灰、设备灰、灰绿旧式面板、石墨灰、海军蓝、深青灰、暗橄榄、深棕黑灰等。
- 新增强制规则：连续 3 套不得使用同一种背景族；相邻参数分辨率不能只差几十像素；浅色要拉开冷暖/边框/密度，深色要拉开色相。
- 新增工控目标分辨率梯度：`640×480`、`800×480`、`1024×600`、`1366×1024`、`1680×1050`、`1920×1200`、`2048×1152`、`2560×1080`、`3440×1440`、`3840×2160`、`600×1024`、`2×1920×1080` 等。
- 100 套生成时至少覆盖 16 种不同分辨率/画布形态；每 10 套至少 5 种分辨率，并包含 HMI、桌面上位机、站控/超宽中的多个类型。
- 已把已有 001–013 示例参数的 `Target Viewport / UI Scale` 和 `Colors` 实际拉开，避免示例继续诱导模型只生成白/深蓝/深灰和小幅分辨率差异。

已对 `UI参数/` 下 10 个类型文件做第一轮全量重构：

- `管理系统-200套.md`
- `APP软件-50套.md`
- `办公软件-50套.md`
- `工业控制系统-100套.md`
- `嵌入式软件-50套.md`
- `监控软件-50套.md`
- `数据分析系统-100套.md`
- `建模软件-50套.md`
- `工具软件-50套.md`
- `设计软件-50套.md`

重构内容：

1. 每个文件新增 `## 技术栈 / 渲染范式优先规则`。
2. 每个参数模板新增：
   - `Rendering Paradigm`
   - `UI Framework`
   - `Component Language`
   - `Native Control Level`
   - `CSS Styling Level`
3. 每个首批示例 / 重新示例参数同步补充上述字段。
4. 保持标题栏规则：
   - `办公软件-50套.md` 保留 `Window Frame / Title Bar`。
   - 其他 9 个类型保留 `No Title Bar`。
5. 已做结构校验：10 个文件均存在新章节、模板新字段和对应标题栏规则。
6. 已检查诊断：10 个 UI 参数文件无诊断问题。

### 2026-04-28 风格字段清理记录

用户强调“不要在风格里加业务场景”。已完成清理：

- `Rendering Paradigm / UI Framework / Component Language / Native Control Level / CSS Styling Level` 只保留渲染范式、框架、控件语言、原生控件等级、CSS占比。
- 从这些字段中移除或泛化具体业务/场景词，例如文档、协作、对象配置、对象操作、进度流程、连接控制、监控总览、分析平台等。
- 业务场景仍可保留在 `Software Type` 或必要的生成目标说明中；但 UI 参数示例中的风格名、`Subtype / Platform Style / Skeleton Type / Navigation Pattern / Panel Composition / Control Style / Layout / OS / Era` 应尽量使用结构、控件、布局、密度语言。
- 已全量清洗 10 个 UI 参数文件中的示例标题和关键字段，把业务化名称改成纯 UI 骨架/控件描述。
- 后续新增示例时，标题优先写 `三栏目录编辑风`、`分组卡片面板风`、`高密度参数表风`、`深色多面板视口风` 这类 UI 结构名，不写 `会议项目协作风`、`对象操作风`、`客户管理风` 这类业务场景名。
- 已删除遗留的 `首批示例参数` 段落，避免旧示例与重构后的 `重新示例参数` 混用。目前保留重构后的示例段落和各类型专门示例段落。

### 2026-04-28 主题数量扩展记录

已在有较大风格差异的基础上扩展各分类下的推荐主题数量，并同步调整 `数量建议`：

- `管理系统-200套.md`：16 个主题，总数 200 套。
- `数据分析系统-100套.md`：16 个主题，总数 100 套。
- `工业控制系统-100套.md`：18 个主题，总数 100 套。
- 其余 50 套分类文件：各 14 个主题，总数均为 50 套。

主题命名原则：

- 使用 UI 结构、视觉差异、控件密度、骨架语言命名。
- 例如：`三栏目录编辑风`、`高密度参数表风`、`深色多面板视口风`、`浅色图表网格风`。
- 避免业务场景命名，例如：会议项目、客户管理、对象操作、市场报告等。
- 每个分类的 `数量建议` 总数必须与文件名中的套数一致。

### 2026-04-28 第一批差异化参数生成记录

已为 `UI参数/` 下 10 个分类文件分别追加 `扩展差异化参数（第一批）`：

- 每个分类先追加 3 套 `E001–E003`。
- 本轮不追求一次达到文件名套数要求，优先验证差异化质量。
- 每套参数必须在以下维度至少拉开 3–5 项差异：
  - `Rendering Paradigm`
  - `UI Framework`
  - `Component Language`
  - `Native Control Level`
  - `CSS Styling Level`
  - `OS Family / OS Era / OS Visual Traits`
  - `Window Frame / Title Bar` 或 `No Title Bar`
  - `Skeleton Type`
  - `Navigation Pattern`
  - `Panel Composition`
  - `Interaction Density`
  - `Control Style`
  - `Colors / Typography / Shape / Stroke / Depth / Layout`
- 差异化优先级高于数量补齐；后续可按同一方式追加第二批、第三批。

### 2026-04-29 少量套数强差异化规则

用户要求每个大类下不到 10 套参数时，也要一眼看出完全不一样，不能只是同一套界面换配色。已完成本轮增强：

- `UI参数/` 下 9 个现用分类文件均新增 `## 少量套数强差异化规则`。
- 每套真实参数均补充：
  - `Visual Differentiation`
  - `Target Viewport / UI Scale`
  - `First-glance Signature`
  - `Background & Surface Language`
  - `Component Scale`
- `完整提示词` 已同步补充参数池前置强约束，并为 83 套参数补充上述差异化字段。
- 后续新增/修改 UI 参数时，必须优先拉开以下维度，而不是先改颜色：
  1. 目标分辨率：手机、平板、桌面、工作站、HMI、超宽/多屏。
  2. 整体缩放：24–28h 高密度小控件、32–38h 常规桌面、48–72h 触控大控件。
  3. 首屏识别物：Ribbon、终端、硬边框工控按钮、三维视口、图表矩阵、浮动小窗、移动底部导航等。
  4. 背景容器语言：纯白、浅灰、米色、深蓝、黑灰、玻璃、网格底、终端底、硬边框灰底。
  5. 布局骨架：单列手机、平板双栏、三栏办公、左右分屏、中央视口、多面板工作站、HMI 大按钮面板。
- 如果两套都是浅色，必须强制一个高密度硬边框/表格化，另一个大留白卡片/大按钮化，避免白底卡片同质化。

### 2026-04-29 工控端类型区分记录

用户要求工控类标注区分“触摸屏面板端”和“上位机”。已完成：

- `UI参数/工业控制系统-100套.md` 新增 `## 工控端类型区分规则`。
- 工控参数模板新增 `Industrial Terminal Type` 字段。
- 13 套工业控制系统真实参数均补充：
  - `Industrial Terminal Type`
  - `Terminal Distinction`
- `完整提示词` 中 13 套工业控制系统参数已同步补充端类型字段，并在开头新增工控端类型强约束。

端类型分为四类：

1. `触摸屏面板端 / HMI Panel`
   - 设备本机屏、嵌入式工控触摸屏、WinCC Runtime 运行画面。
   - 典型特征：800×480、1024×600、1024×768、1280×720 横屏，大按钮、大字号、状态灯、硬边框、单屏/分页操作。
   - 不应出现工程树、复杂菜单、高密度表格、SaaS侧栏。
2. `工程上位机 / Engineering Workstation`
   - Windows/Linux 桌面工程配置、PLC 参数配置、点表映射、组态编辑。
   - 典型特征：1366×768、1440×900、1600×900、1920×1080，小控件、高密度表格、对象树、属性栏、工具栏、底部日志。
3. `SCADA站控监视端 / Station Monitoring Console`
   - 控制室监控终端、站控工作站、趋势警示监视。
   - 典型特征：1920×1080 或更宽，趋势图、警示条、状态摘要、监控总览、事件列表，控件中等偏大但不是 HMI 大按钮。
4. `维护调试上位机 / Maintenance Workstation`
   - 工程维护软件、联机调试、双栏操作日志。
   - 典型特征：左右/三栏面板、操作按钮、参数输入、日志控制台、状态标签。

判断优先级：

- 出现 HMI、Touch、800×480、1024×600、1024×768、大按钮、现场操作屏，标为触摸屏面板端。
- 出现 Engineering、PLC 参数、点表、组态、对象树、属性栏、高密度表格，标为工程上位机。
- 出现 Station、SCADA、趋势、警示、监控总览，标为 SCADA站控监视端。
- 出现维护、调试、双栏操作日志，标为维护调试上位机。

---

## 工业控制系统 / PLC / HMI / SCADA 提示原则

- 对于“工业控制系统”这一类，不要只写成泛化的工业后台风格。
- 如果目标更接近真实工控软件，应明确告诉生图模型：
  - `PLC风格界面`
  - `HMI风格界面`
  - `SCADA风格界面`
  - `设备调试维护界面`
- 由于生图模型较强，只要提示词中明确写出 `PLC/HMI/SCADA`，通常就能自动理解这类界面的典型气质与布局特征。
- 因此后续生成工业控制系统 UI 参数时，应优先在提示层明确子类型，而不是只写“工业控制系统”。

### HMI 提示词踩坑记录

- 仅写 `HMI industrial touchscreen interface`、`工业HMI触摸屏界面`、`工控触摸屏软件界面`、`工业设备操作屏风格`，模型可能会跑偏成“现代云控工业后台 / 工业SaaS平台”。
- 典型跑偏表现：
  - 深蓝色现代后台
  - 顶部图标导航
  - 左侧Web侧边栏菜单
  - 卡片式模块
  - 云平台名称、在线状态、系统设置
  - 视觉更像工业互联网平台，而不是设备触摸屏
- 如果要更像传统 HMI/PLC 触摸屏，需要强制加入：
  - `not web dashboard`
  - `not cloud platform`
  - `no sidebar navigation`
  - `no top icon navigation bar`
  - `flat gray industrial panel`
  - `hard bordered rectangular panels`
  - `large physical-machine buttons`
  - `Siemens WinCC / HMI panel style`
  - `operator panel screen, device local screen`
  - `low decorative design, utilitarian industrial UI`
- 正向描述要从“现代工业控制系统”改成“设备本机操作屏 / 工业触摸屏终端 / 西门子 WinCC 式 HMI 面板”。

## 工控界面常见视觉特征

- 功能区硬分割明显
- 小圆角或中小圆角
- 边框清晰，阴影较弱
- 信息密度偏高
- 强调状态区、参数区、控制区、告警区
- 常用深灰、蓝灰、石墨、墨绿、琥珀、青绿等克制配色
- 避免游戏HUD、赛博霓虹、大屏炫光

## 其他系统类型与操作系统风格考虑

当前生成策略默认采用“现代软件界面”思路，而不是强绑定某个具体操作系统视觉规范。

后续生成时需要有意识区分：

### 管理系统
- 更接近现代 Web 后台 / 桌面管理端
- 可参考现代浏览器后台、企业 SaaS、现代桌面应用风格
- 不应明显像老式 Windows XP / Win7 控制台

### 工业控制系统
- 更接近工业触控屏、工控上位机、HMI、SCADA
- 可适当带有桌面工控软件气质
- 不应过分 Web SaaS 化

### 数据分析系统
- 更接近现代 Web 分析平台、BI 工具、专业数据看板
- 可少量参考桌面分析软件布局，但主视觉仍应现代

### 建模软件
- 更接近专业桌面软件风格
- 要考虑多面板、工具栏、属性栏、画布区这些更像桌面应用的结构
- 可以有 Windows / macOS 专业工具软件的气质，但不直接复制具体系统外观

### 工具软件
- 可以偏桌面工具或现代轻量 Web 工具
- 要根据软件名判断更像桌面端还是浏览器端工具

### 嵌入式软件
- 更接近设备配置工具、串口工具、调试工具、上位机控制软件
- 通常偏桌面控制端，而不是纯互联网后台

### 办公软件
- 更接近现代办公套件、协作工具、文档工具
- 可以轻微参考 Windows / macOS 办公软件习惯
- 必须带有操作系统窗口标题栏或桌面应用窗口框架
- Windows 办公软件可使用顶部标题栏、窗口控制按钮、应用标题/搜索/工具区
- macOS 办公软件可使用左上红黄绿窗口按钮、融合式工具栏或半透明侧栏
- 不直接做成某一系统原生样式

### 其他类型标题栏规则
- 除办公软件外，其他 UI 参数类型不强制要求操作系统标题栏。
- 数据分析系统、设计软件、建模软件、工具软件、嵌入式软件、监控软件、工业控制系统、APP软件，不应为了体现 OS / Era 而刻意加入系统标题栏或窗口控制按钮。
- 这些类型的 OS / Era 主要体现在控件风格、圆角、边框、密度、面板结构、触控方式和平台气质上，而不是标题栏。
- APP软件尤其不能出现桌面系统标题栏。
- 工控/HMI/监控类应优先体现设备终端、站控界面、上位机工具或触摸屏结构，不要被标题栏弱化其类型特征。

### 设计软件
- 更接近专业创作类桌面软件
- 需要明显考虑桌面软件气质，尤其是多面板和画布中心结构
- 可参考现代设计工具，而非纯 Web 表单后台

### 监控软件
- 更接近监控台、站控系统、值守界面、实时监视系统
- 往往偏桌面监控终端或大屏控制端，但仍需克制

### APP软件
- 默认应理解为移动端应用风格
- 需要显式考虑 iOS / Android 时代的现代移动 UI 气质
- 但不应直接复制系统原生组件外观

### 2026-04-29 参数分隔符批量导入记录

用户需要将参数批量导入其他软件，已在相邻真实 UI 参数块之间插入独立分隔符：

```text
---参数分隔符---
```

处理范围：

- `UI参数/` 下 9 个现用分类文件。
- `完整提示词`。
- `总体`。
- `归档/总体-归档前含管理系统`。

维护规则：

- 分隔符只放在两个真实参数标题之间，即 `### ... UI参数 001：...` 与下一套 `### ... UI参数 002：...` 之间。
- 每两个相邻参数之间只能有 1 个 `---参数分隔符---`，避免重复插入。
- 参数模板标题（例如 `### 参数模板`、`### 管理系统 UI参数 X`）不是可导入真实参数，不需要分隔符。
- 后续新增真实参数时，应在上一套参数结束后、下一套标题前补 1 个分隔符，保证批量导入工具可按该字符串切分。

## 后续生成建议

- 先判断软件更像：`Web后台`、`桌面软件`、`工控上位机/HMI`、`移动APP`。
- 再在提示词中明确写出对应平台气质，而不仅是写功能分类。
- 如果希望生图模型更准，应在提示词里加入：
  - `现代Web后台风格`
  - `现代桌面专业软件风格`
  - `PLC/HMI/SCADA风格`
  - `现代移动APP风格`
- 这样比单纯写“管理系统 / 工具软件 / 工业控制系统”更稳定。

## 技术栈 / 渲染范式 / CSS 风格占比规则

不能所有 UI 参数都用同一种 `Colors / Typography / Shape / Depth / Motion` 的 CSS Design Token 语言描述，否则生图模型容易全部生成精细化 Web/CSS 风格。

后续应先确定：

1. `Rendering Paradigm`：Web 应用 / 移动原生 / 桌面原生 / 工程上位机 / HMI-SCADA / 专业创作工具
2. `UI Framework`：React/Vue/Ant Design、SwiftUI/UIKit、Android Material、WPF/WinForms/MFC/Qt、WinCC/SCADA Runtime 等
3. `Component Language`：使用该框架真实常见的组件语言，而不是只写颜色和圆角
4. `CSS Styling Level`：该类型允许多强的 CSS / Web 精修感

### 一、CSS 风格不是全禁，而是按类型分配

#### 适合较高 CSS / Web 精修感的类型
- 管理系统：本质是 Web 后台，适合 `React/Vue + Ant Design/Element Plus` 风格，CSS Styling Level 可为 `high`。
- Web 协作类办公软件：如果明确是 Web 协作工具，可用 `desktop web application / Electron-like app`，CSS Styling Level 可为 `medium`。
- Web BI 数据分析系统：适合图表卡片、筛选器、指标卡、数据表格，CSS Styling Level 可为 `medium/high`。
- APP软件：不是桌面 CSS，但可使用移动框架组件精修感，如 `SwiftUI / Material 3`，CSS Styling Level 应理解为移动组件风格，通常 `medium`。

#### 桌面软件中 CSS 比例应明显降低的类型
- 办公软件桌面端：优先 `WPF / WinForms / AppKit / SwiftUI / Office Ribbon`，CSS Styling Level 通常 `low` 或 `none`。
- 工具软件：优先 `WinForms / WPF / Qt / GTK`，CSS Styling Level 通常 `low`。
- 建模软件：优先 `Qt / WPF / C++ desktop UI`，CSS Styling Level 通常 `low`。
- 设计软件：可有一定现代精致感，但应是 `专业创作工具 / canvas + inspector + layer panel`，不是 SaaS 后台；CSS Styling Level 通常 `medium`。

#### 几乎不应使用 CSS Web 风格的类型
- 工业控制系统：优先 `HMI / SCADA Runtime / WinCC / 工控上位机 / Qt Industrial`，CSS Styling Level 应为 `none` 或 `very low`。
- 嵌入式软件：优先 `Qt Widgets / WinForms / WPF / MFC 工程工具`，CSS Styling Level 应为 `very low`。
- 监控软件：优先 `站控终端 / 值守终端 / SCADA监控端 / Qt监控端`，CSS Styling Level 应为 `low` 或 `very low`。

### 二、推荐字段

后续模板建议在颜色、圆角、阴影之前加入以下高优先级字段：

```text
- Rendering Paradigm: `...`
- UI Framework: `...`
- Component Language: `...`
- Native Control Level: `none / low / medium / high / very high`
- CSS Styling Level: `none / very low / low / medium / high`
```

这些字段优先于 `Colors / Shape / Depth / Motion`，用于决定界面到底像 Web、原生桌面、移动端、工控终端还是专业创作软件。

### 三、各类型推荐默认值

| 软件类型 | Rendering Paradigm | UI Framework / 技术语言 | CSS Styling Level |
|---|---|---|---|
| APP软件 | Mobile native app | iOS SwiftUI/UIKit, Android Material 3 | medium |
| 办公软件-桌面端 | Native desktop office software | WPF, WinForms, AppKit, SwiftUI, Office Ribbon | none/low |
| 办公软件-Web协作端 | Desktop web collaboration app | Electron-like Web app, React document editor | medium |
| 工具软件 | Desktop utility | WinForms, WPF, Qt, GTK | low |
| 嵌入式软件 | Engineering desktop utility | Qt Widgets, MFC, WinForms, WPF | very low |
| 工业控制系统 | HMI/SCADA/engineering workstation | WinCC, SCADA Runtime, Qt Industrial, MFC/WPF | none/very low |
| 监控软件 | Monitoring terminal / station control | SCADA terminal, Qt, WPF, controlled Web terminal | low/very low |
| 数据分析系统-Web BI | Web BI analytics platform | React/Vue charts, ECharts, BI dashboard | medium/high |
| 数据分析系统-桌面工作台 | Desktop analytics workstation | Qt, WPF, Java Swing-like tool | low |
| 建模软件 | Professional desktop modeling software | Qt, WPF, C++ desktop UI, OpenGL viewport | low |
| 设计软件 | Professional creative tool | AppKit, Qt, Electron-like design tool | medium |

### 四、描述语言示例

#### Web 管理系统
```text
- Rendering Paradigm: `web application`
- UI Framework: `React/Vue admin dashboard, Ant Design / Element Plus`
- Component Language: `filter form, data table, pagination, drawer, modal, tabs`
- Native Control Level: `none`
- CSS Styling Level: `high`
```

#### Windows 桌面办公软件
```text
- Rendering Paradigm: `native Windows desktop software screenshot`
- UI Framework: `WPF / WinForms desktop application with Office-style Ribbon`
- Component Language: `native title bar, ribbon toolbar, tree view, document editor, property pane, status bar`
- Native Control Level: `very high`
- CSS Styling Level: `none`
```

#### 嵌入式调试工具
```text
- Rendering Paradigm: `engineering desktop utility`
- UI Framework: `Qt Widgets / MFC / WinForms engineering tool`
- Component Language: `serial port selector, parameter grid, tab control, device tree, log console, status bar`
- Native Control Level: `high`
- CSS Styling Level: `very low`
```

#### 工业 HMI / SCADA
```text
- Rendering Paradigm: `industrial HMI / SCADA runtime`
- UI Framework: `Siemens WinCC / SCADA Runtime / Qt Industrial Panel`
- Component Language: `alarm banner, status lamp, process panel, control button, trend chart, equipment mimic diagram`
- Native Control Level: `industrial controls`
- CSS Styling Level: `none`
```

## 操作系统类型 / 版本 / 控件风格层

平台气质只能决定第一层大方向，真正影响界面细节的还有：

1. 操作系统类型
2. 操作系统版本年代
3. 控件风格体系
4. 输入方式（鼠标键盘 / 触控 / 工控触摸屏）

后续生成提示词时，应该把“平台气质”和“OS风格层”拆开描述。

### 一、为什么必须考虑 OS 风格层

即使同样是“桌面软件”或“工控软件”，不同操作系统与年代会导致明显差异：

- 窗口结构不同
- 工具栏样式不同
- 按钮、输入框、表格、树组件风格不同
- 圆角大小不同
- 阴影、描边、分隔线习惯不同
- 图标风格不同
- 明暗模式成熟度不同

所以后续不能只写：
- `桌面软件风格`
- `专业软件风格`

更应补充：
- `接近 Windows 10/11 时代桌面专业软件`
- `接近 macOS Big Sur / Sonoma 时代专业创作工具`
- `接近现代 Linux 工业控制终端风格`
- `接近 Android 工控触摸屏 HMI 风格`

### 二、可用的 OS 风格层分类

#### 1. Windows 桌面软件气质
适合：建模软件、工具软件、办公软件、嵌入式上位机、部分工业控制系统

可继续区分：
- `Windows XP / Windows 7 时代`：更传统、更硬朗、控件边框和分隔线更明显，适合少量旧式工程软件、工控上位机、嵌入式调试工具、设备配置工具；可以使用，但应控制比例，避免所有软件都变旧。
- `Windows 7 时代`：更硬朗、分隔明显、拟桌面工具感更强，适合工程/设备类软件的旧式专业感。
- `Windows 10 时代`：更扁平、清晰、理性、适合多数专业软件。
- `Windows 11 时代`：圆角更明显、留白更多、层次更柔和。

提示词建议：
- 如果需要现代专业桌面感，优先写 `Windows 10/11 时代专业软件界面`。
- 如果需要旧式工程感、传统上位机感、工控配置软件感，可以少量写 `Windows 7 时代工程软件界面`。
- 如果需要更老的设备配套软件、传统调试工具、早期上位机感，可以极少量写 `Windows XP/Windows 7 时代工程软件气质`，但要避免过度拟物、过厚渐变和明显过时的低质感。
- 不应把 XP/Win7 气质用于管理系统、办公软件、APP、现代Web分析平台这类本应现代化的类型。

#### 2. macOS 专业软件气质
适合：设计软件、建模软件、办公软件、部分高端工具软件

可继续区分：
- `Catalina / Big Sur 时代`：现代、清爽、分层自然
- `Monterey / Ventura / Sonoma 时代`：更成熟的圆角、侧边栏、半透明层次

提示词建议：
- 可写 `macOS 现代专业创作软件风格`
- 注意不要把所有软件都做成苹果原生 app 外观，只借鉴气质、布局和控件精度

#### 3. Linux / 工控终端气质
适合：工业控制系统、监控软件、嵌入式软件、上位机工具

特点：
- 更理性
- 更强调分区和稳定性
- 常见小圆角、清晰边框、较少装饰
- 更像设备控制终端，而不是互联网产品

提示词建议：
- 可写 `现代 Linux 工控上位机界面`
- 或 `工业控制终端 UI，偏桌面控制软件气质`

#### 4. 工控触摸屏 / HMI 终端气质
适合：PLC/HMI/SCADA、产线控制、人机操作屏

特点：
- 更重触控可读性
- 按钮更大
- 状态色更明确
- 功能区硬分割
- 控件偏规则化
- 不追求 Web 卡片感

提示词建议：
- 直接写 `HMI触控屏界面`
- `PLC触摸屏控制界面`
- `SCADA站控画面`

#### 5. 移动操作系统气质
适合：APP软件

可继续区分：
- `iOS 风格气质`：更克制、细腻、留白感强、层次柔和
- `Android / Material 风格气质`：结构更明确、组件感更强、色彩更稳定

提示词建议：
- `现代 iOS 风格移动应用界面气质`
- `现代 Android / Material 风格移动应用界面气质`
- 不直接复制原生组件，但要遵循该系统时代的控件语言

### 三、控件风格会直接影响生成结果

除了 OS 类型和版本，还应明确控件本身偏哪种风格：

- `传统桌面控件风格`
- `现代扁平控件风格`
- `半原生专业软件控件风格`
- `工控触屏按钮 + 参数面板风格`
- `现代SaaS表格/筛选器/卡片控件风格`
- `移动端卡片 + Tab + Bottom sheet 风格`

这会影响：
- Button 外观
- Input 外观
- Table/Grid 外观
- Tabs 外观
- Tree / Sidebar 外观
- Dialog / Drawer 外观
- 状态灯/告警块/仪表控件风格

### 四、后续提示词推荐写法

建议以后用四层结构描述：

1. `软件类型`
2. `平台气质`
3. `操作系统/时代`
4. `控件风格`

例如：

- `工业控制系统，PLC/HMI风格，现代Linux工控终端或工控触摸屏时代，规则化控制面板控件风格`
- `建模软件，现代桌面专业软件风格，Windows 10/11 时代，多面板工具栏与属性栏控件风格`
- `设计软件，现代专业创作软件风格，macOS Big Sur / Sonoma 时代，精细半透明面板与细线图标控件风格`
- `管理系统，现代 Web 后台风格，接近 Windows 11 时代的企业软件审美，现代 SaaS 表格和筛选器控件风格`
- `APP 软件，现代移动应用风格，偏 iOS 或 Android 当前时代，移动端卡片与底部导航控件风格`

### 五、当前项目的实际使用建议

- 管理系统：默认 `现代Web后台 + Windows 10/11 审美 + SaaS控件风格`
- 工业控制系统：默认 `PLC/HMI/SCADA + Linux工控终端或工控触摸屏 + 规则化工控控件`
- 数据分析系统：默认 `现代分析平台 + Web/桌面混合气质 + 图表分析控件`
- 建模软件：默认 `现代桌面专业软件 + Windows/macOS 近代版本 + 多面板控件`
- 工具软件：默认 `桌面工具或轻Web工具 + Windows 10/11 审美 + 紧凑工具控件`
- 嵌入式软件：默认 `上位机/调试工具 + Windows/Linux 工程软件气质 + 参数面板控件`
- 办公软件：默认 `现代办公套件 + Windows/macOS 当前时代 + 文档/列表/协作控件`
- 设计软件：默认 `专业创作桌面软件 + macOS/Windows 现代版本 + 画布中心控件体系`
- 监控软件：默认 `监控终端/站控系统 + Linux/Windows 工控终端气质 + 状态监看控件`
- APP软件：默认 `现代移动端 + iOS/Android 当前时代 + 移动组件体系`

### 六、旧式 OS 年代的使用规则

用户允许使用 `Windows 7`、`2010年前桌面软件气质`，少量也允许 `Windows XP`。

但这类旧式 OS 年代不是通用默认值，而是作为某些类型的少量变体使用：

#### 适合使用 Win7 / XP 气质的类型
- 工业控制系统：旧式工控上位机、PLC配置软件、早期设备调试软件。
- 嵌入式软件：串口工具、烧录工具、调试工具、设备配置工具。
- 工具软件：传统桌面小工具、批处理工具、系统维护工具。
- 建模软件：少量传统 CAD / 工程建模工具。
- 监控软件：少量传统值守终端或站控软件。

#### 不适合使用 Win7 / XP 气质的类型
- APP软件：移动端必须走 iOS/Android 年代，不应出现 Windows 桌面感。
- 设计软件：除非特别做旧，否则应优先 macOS/Windows 10/11 专业创作气质。
- 办公软件：默认现代办公套件，不建议用 XP/Win7 老办公感。
- 管理系统：默认现代 Web 后台，不建议用 XP/Win7 老后台，除非要做传统企业内网系统。
- 数据分析系统：默认现代 Web/专业分析工具，不建议明显 Win7/XP。

#### 使用比例建议
- 工业控制系统、嵌入式软件、工具软件：可保留 `10%–20%` 的旧式 Windows 变体。
- 建模软件、监控软件：可保留 `5%–10%` 的旧式工程变体。
- 管理系统、办公软件、设计软件、数据分析系统：通常不超过 `5%`，多数情况下不使用。
- APP软件：不使用 Windows XP/7/10/11 风格，除非明确是桌面端而不是移动端。

#### 旧式 OS 的提示写法

推荐：
- `Windows 7 时代工程软件界面`
- `Windows XP/Windows 7 时代设备调试工具气质`
- `传统 Windows 桌面上位机界面`
- `2010年前后工业控制软件气质`
- `传统桌面工具控件，硬边框、小圆角、清晰分隔线`

避免：
- `老旧低质感界面`
- `过时软件截图`
- `Windows XP 蓝绿主题强拟物`
- `厚重渐变按钮和廉价阴影`

也就是说，可以借用旧式 OS 的结构和控件密度，但不要生成粗糙、低质量、过时审美的界面。

## 各系统类型必须避免生成的错误方向

## OS / Era 系统版本矩阵

本矩阵用于控制生成界面的操作系统年代气质。后续 UI 参数中应尽量把 `OS / Era` 写清楚，不要只写“现代软件”。

### 1. Windows XP / Windows 7 时代

#### 适合的软件类型
- 工业控制系统：PLC配置、工控上位机、旧式站控、设备控制软件。
- 嵌入式软件：串口工具、烧录工具、固件升级、调试诊断、寄存器配置。
- 工具软件：传统小工具、批处理工具、维护工具、转换工具。
- 建模软件：少量传统 CAD、工程建模、参数化工具。
- 监控软件：少量传统值守终端、站控终端。

#### 视觉特征
- 硬边框明显。
- 分隔线清晰。
- 控件密度较高。
- 工具栏和菜单栏更传统。
- 树控件、表格、属性面板更像桌面软件。
- 圆角小或无圆角。
- 阴影少，层级靠边框和分割线表达。

#### 使用限制
- 可以少量使用，但不要泛滥。
- 不要把界面做成低质量、廉价、粗糙、过时截图感。
- 不要过度使用 XP 蓝绿主题、厚重渐变、强拟物按钮。
- 不建议用于现代管理系统、办公软件、数据分析系统、设计软件、APP。

#### 推荐写法
- `Windows 7 时代工程软件界面`
- `Windows XP/Windows 7 时代设备调试工具气质`
- `传统 Windows 桌面上位机界面`
- `2010年前后工业控制软件气质`
- `传统桌面工具控件，硬边框、小圆角、清晰分隔线`

---

### 2. Windows 10 时代

#### 适合的软件类型
- 管理系统
- 工业控制系统
- 嵌入式软件
- 工具软件
- 建模软件
- 数据分析系统
- 监控软件
- 办公软件
- 设计软件

#### 视觉特征
- 扁平、理性、清晰。
- 控件边框明确但不过度老旧。
- 圆角较小。
- 信息密度可中高。
- 工具栏、表格、面板、属性栏都比较稳定。
- 适合专业软件和企业软件。

#### 使用限制
- 是桌面专业软件和工程软件的安全默认值。
- 如果是移动 APP，不应使用 Windows 10 气质。
- 如果是设计软件，Windows 10 可用，但不要做成普通后台。

#### 推荐写法
- `Windows 10 时代专业桌面软件`
- `Windows 10 工程软件界面`
- `Windows 10 企业管理端审美`
- `Windows 10 上位机工具软件气质`

---

### 3. Windows 11 时代

#### 适合的软件类型
- 管理系统
- 办公软件
- 数据分析系统
- 工具软件
- 设计软件
- 建模软件
- 少量现代工控/嵌入式上位机

#### 视觉特征
- 圆角更明显。
- 留白更舒适。
- 阴影更柔和。
- 卡片和面板层次更现代。
- 适合现代企业软件、办公软件、轻量工具。

#### 使用限制
- 用在工控、嵌入式、监控时要谨慎，容易变成现代平台化/SaaS化。
- 不适合传统 HMI、PLC 现场屏、老式工程上位机。

#### 推荐写法
- `Windows 11 时代企业软件审美`
- `Windows 11 现代桌面工具软件`
- `Windows 11 时代办公套件气质`
- `Windows 11 专业桌面软件界面`

---

### 4. macOS Big Sur / Monterey / Ventura / Sonoma 时代

#### 适合的软件类型
- 设计软件
- 建模软件
- 办公软件
- 部分数据分析系统
- 部分高端工具软件

#### 视觉特征
- 圆角更大。
- 侧边栏更柔和。
- 工具栏更融合。
- 半透明和毛玻璃更自然。
- 图标更细、更精致。
- 层次更轻，视觉更高级。

#### 使用限制
- 不适合工控 HMI、PLC、嵌入式调试工具、传统监控终端。
- 不要把所有软件都做成苹果原生 app 外观，只借鉴气质、布局和控件精度。

#### 推荐写法
- `macOS Big Sur 时代专业软件气质`
- `macOS Ventura/Sonoma 时代专业创作工具`
- `macOS Sonoma 时代办公应用气质`
- `macOS 近代专业桌面软件界面`

---

### 5. Linux 工程桌面 / 工控终端

#### 适合的软件类型
- 工业控制系统
- 嵌入式软件
- 监控软件
- 工具软件
- 建模软件
- 数据分析工作台

#### 视觉特征
- 理性、克制、工程化。
- 分区明确。
- 边框清晰。
- 装饰少。
- 信息密度偏高。
- 更像设备控制端、工程工具或监控终端。

#### 使用限制
- 不适合办公软件、移动 APP、偏消费级的软件。
- 不要做成黑客终端或命令行全屏，除非子类型明确是日志/控制台工具。

#### 推荐写法
- `现代 Linux 工程桌面软件`
- `Linux 工控终端气质`
- `Linux/Windows 工程工具混合气质`
- `工业控制终端 UI，偏桌面控制软件气质`

---

### 6. Industrial HMI / WinCC Runtime / 工控触摸屏时代

#### 适合的软件类型
- 工业控制系统
- 少量嵌入式板载终端
- 少量监控站控终端

#### 视觉特征
- 灰底或深灰底。
- 硬边框矩形分区。
- 大按钮。
- 状态灯。
- 告警条。
- 参数读数。
- 单屏操作为主。
- 少导航、少层级、少装饰。

#### 使用限制
- 不要出现 Web 后台侧边栏。
- 不要出现顶部互联网图标导航。
- 不要出现云平台首页。
- 不要出现 SaaS 卡片总览。
- 不要出现移动 App 底部 Tab。

#### 推荐写法
- `WinCC Runtime 风格操作员面板`
- `设备本机触摸屏 HMI`
- `传统工业 HMI 操作屏`
- `PLC machine local touchscreen panel`
- `flat gray industrial panel, hard bordered rectangular controls`

---

### 7. iOS 14 / 15 / 16 / 17 时代

#### 适合的软件类型
- APP软件
- 移动办公
- 移动工具
- 移动表单/设置/个人中心

#### 视觉特征
- 大圆角卡片。
- 分组列表。
- 底部导航。
- 大标题。
- 轻浮层、Bottom Sheet。
- 层次柔和。
- iOS 16/17 更成熟、更细腻。

#### 使用限制
- 不要用于桌面软件、工控软件、管理后台、建模软件。
- 不要直接复制系统原生界面，只借鉴移动 UI 气质。

#### 推荐写法
- `iOS 16+ 当前时代移动应用气质`
- `iOS 17 时代移动卡片界面`
- `现代 iOS 分组列表与底部导航控件`
- `iOS 风格移动应用，但不直接复制系统原生界面`

---

### 8. Android 10 / 11 / 12 / 13 / 14 时代

#### 适合的软件类型
- APP软件
- 移动工具
- 移动设置页
- Android 平板轻办公/轻工具
- 少量设备终端界面

#### 视觉特征
- Android 10/11：Material Design 2，组件规则、顶部栏/FAB/卡片明显。
- Android 12+：Material You，圆角更大、色彩容器更明显、组件更柔和。
- Android 13/14：延续 Material You，更成熟、更系统化。

#### 使用限制
- 不要用于普通桌面软件、Web后台、专业建模工具、传统工控上位机。
- 如果用于设备终端，要明确是 `Android 工控触摸屏终端`，不要变成消费级手机 APP。

#### 推荐写法
- `Android 12+ / Material You 克制气质`
- `Android 10/11 Material Design 工具型应用`
- `Android Tablet 工具软件界面`
- `Android 工控触摸屏终端，非消费级手机APP`

---

### 9. 不同软件类型推荐 OS / Era 总表

| 软件类型 | 推荐 OS / Era | 少量可用 | 避免 |
|---|---|---|---|
| 管理系统 | 现代 Web、Windows 10/11 企业软件 | 少量传统企业内网 Win7 | XP 老后台、移动 OS、HMI |
| 工业控制系统 | Win7/Win10 工控上位机、Linux 工控终端、WinCC/HMI | 少量 XP/Win11 工程端 | iOS/Android 消费端、SaaS Web、macOS 玻璃风 |
| 嵌入式软件 | Win7/Win10/Win11 工程工具、Linux 工程工具 | 少量 XP、设备终端 | 移动消费 App、云平台后台 |
| 监控软件 | Linux/Windows 工控终端、Win10/Win11 值守端 | 少量 Win7 站控 | 移动 OS、macOS 创作风、赛博大屏 |
| 数据分析系统 | 现代 Web、Windows 10/11 专业分析 | 少量 macOS 分析工具 | XP/Win7 老控件、HMI、移动 App |
| 建模软件 | Windows 10/11、macOS 近代、Linux 工程桌面 | 少量 Win7 工程/CAD | Web 后台、移动 OS、HMI |
| 工具软件 | Win7/Win10/Win11、现代轻 Web、Linux 工程 | 少量 XP、macOS 小工具 | HMI、移动内容 App、复杂后台 |
| 办公软件 | Windows 11、macOS Ventura/Sonoma、现代 Web 协作 | 少量 Win10 | XP/Win7 老办公、工控/监控终端 |
| 设计软件 | macOS Big Sur+、Windows 10/11 专业创作 | 少量现代 Web 创作工具 | Win7/XP、工控/监控气质 |
| APP软件 | iOS 15/16/17、Android 11/12/13/14 | iPadOS / Android Tablet | Windows/macOS 桌面、Web后台、HMI |


后续生成每一种类型的 UI 参数时，除了写“应该像什么”，还必须写清楚“绝对不要像什么”。否则模型容易把不同系统做成同一种泛化 Web UI，或生成与软件类型不匹配的界面。

### 1. 管理系统必须避免

- 避免生成成游戏界面、营销官网、艺术展板、可视化大屏。
- 避免过度像移动 APP。
- 避免像 PLC/HMI 工控屏。
- 避免像设计软件的画布工具界面。
- 避免老式 2010 年前后台系统风格，如厚重渐变按钮、强拟物控件。
- 避免大量蓝紫科技风驾驶舱。

推荐负向提示：
`不要生成游戏HUD、数据大屏、移动APP首页、PLC触控屏、设计工具画布、老式后台系统。`

### 2. 工业控制系统必须避免

- 避免生成成普通 Web SaaS 后台。
- 避免生成成互联网管理系统、CRM、OA、财务后台。
- 避免生成成炫酷数据大屏或赛博朋克监控屏。
- 避免生成成手机 APP。
- 避免生成成艺术化工业插画界面。
- 避免过多玻璃拟态、漂浮卡片、大留白。

应更接近：`PLC / HMI / SCADA / 工控上位机 / 设备控制屏`。

推荐负向提示：
`不要生成普通SaaS后台、互联网管理系统、手机APP、游戏HUD、赛博朋克大屏、艺术化看板。`

### 3. 数据分析系统必须避免

- 避免生成成纯监控大屏或炫酷驾驶舱。
- 避免生成成工控 PLC/HMI 操作屏。
- 避免生成成普通表单后台，没有分析感。
- 避免生成成移动 APP。
- 避免生成成设计软件/建模软件的画布界面。
- 避免图表过度装饰、霓虹、发光网格过多。

推荐负向提示：
`不要生成PLC控制屏、手机APP、纯后台表单、游戏化大屏、过度发光驾驶舱、设计软件画布。`

### 4. 建模软件必须避免

- 避免生成成普通 Web 后台或管理系统。
- 避免生成成数据看板、大屏驾驶舱。
- 避免生成成办公文档软件。
- 避免生成成移动 APP。
- 避免生成成 HMI 触控屏。
- 避免缺少画布、工具栏、属性面板、多面板结构。

应更接近：`专业桌面软件 / CAD / 建模工具 / 多面板工作区`。

推荐负向提示：
`不要生成普通后台、数据大屏、移动APP、HMI触控屏、办公文档界面、营销网页。`

### 5. 工具软件必须避免

- 避免生成成复杂管理系统后台。
- 避免生成成大屏看板或监控台。
- 避免生成成游戏工具界面。
- 避免生成成艺术化创作软件。
- 避免生成成内容型移动 APP。
- 避免过度复杂的多模块业务系统。

应更接近：`轻量桌面工具 / 小型Web工具 / 设置转换处理工具`。

推荐负向提示：
`不要生成复杂后台、大屏驾驶舱、游戏界面、艺术创作软件、内容APP、业务流程系统。`

### 6. 嵌入式软件必须避免

- 避免生成成普通互联网后台。
- 避免生成成管理系统、CRM、OA。
- 避免生成成炫酷可视化大屏。
- 避免生成成消费级移动 APP。
- 避免生成成纯 PLC/HMI 现场屏，除非子类型明确为板载终端或轻量 HMI。
- 避免过度玻璃化、艺术化、营销化。

应更接近：`设备配置工具 / 调试诊断工具 / 上位机控制软件 / 固件升级工具 / 串口通信工具`。

推荐负向提示：
`不要生成互联网后台、CRM/OA、炫酷大屏、消费级APP、纯PLC触控屏、营销网页。`

### 7. 办公软件必须避免

- 避免生成成后台管理系统。
- 避免生成成工控屏、监控屏、大屏驾驶舱。
- 避免生成成设计/建模专业工具界面。
- 避免生成成游戏或娱乐 APP。
- 避免过度暗黑、过度科技、过度工业。
- 避免视觉太花影响长时间使用。

应更接近：`文档/协作/列表/日程/轻量表格/办公套件`。

推荐负向提示：
`不要生成工控屏、监控大屏、游戏界面、设计软件画布、复杂后台、强科技暗黑界面。`

### 8. 设计软件必须避免

- 避免生成成普通后台管理系统。
- 避免生成成数据分析看板。
- 避免生成成 HMI/PLC 工控屏。
- 避免生成成普通移动 APP。
- 避免生成成办公文档列表页。
- 避免只出现卡片和表单，缺少画布/工具栏/属性面板。

应更接近：`专业创作工具 / 画布中心 / 多面板 / 图层或属性控制区`。

推荐负向提示：
`不要生成普通后台、数据大屏、HMI触控屏、移动APP、办公文档页、纯表单卡片界面。`

### 9. 监控软件必须避免

- 避免生成成普通管理后台。
- 避免生成成 PLC/HMI 操作屏，除非子方向明确为站控终端。
- 避免生成成移动 APP。
- 避免生成成设计软件、建模软件。
- 避免过度游戏 HUD、赛博霓虹、科幻雷达屏。
- 避免只有静态表格而没有状态监看感。

应更接近：`监控终端 / 值守界面 / 状态面板 / 趋势图 / 告警列表`。

推荐负向提示：
`不要生成普通后台、移动APP、设计工具、建模工具、游戏HUD、赛博朋克大屏、纯表格页面。`

### 10. APP软件必须避免

- 避免生成成 Web 后台管理系统。
- 避免生成成桌面专业软件。
- 避免生成成工控 PLC/HMI 屏。
- 避免生成成数据大屏。
- 避免生成成复杂表格密集界面。
- 避免生成成老式 Android 或老式 iOS 风格。

应更接近：`现代 iOS / Android 移动应用界面`。

推荐负向提示：
`不要生成Web后台、桌面软件、PLC/HMI屏、数据大屏、复杂表格页、老式移动系统界面。`

## 骨架误判与结构性禁忌

这次项目中发现，模型的误判不只发生在配色和控件层，更大量发生在“页面骨架层”。

也就是说，很多软件一旦出现错误的结构骨架，即使颜色、按钮、字体调整得再像，也会被看成另一种软件类型。

因此后续生成时，除了控制风格、配色、OS、控件外，还必须控制：

1. 页面骨架
2. 主导航形式
3. 分区关系
4. 操作重心位置
5. 是否允许出现某种典型结构

### 工业控制系统的典型骨架禁忌

工业控制系统尤其要避免出现以下结构，否则极容易被看成云平台后台：

- 左侧 SaaS 侧边栏导航
- 顶部互联网平台图标导航
- 顶部 + 左侧双重后台导航
- 云平台首页结构
- 大量卡片宫格概览首页
- 用户中心 / 云服务 / 系统首页 / 平台总览这类互联网平台结构
- 底部移动 Tab 导航

真正偏 PLC / HMI / SCADA / 工控上位机的结构，更应该是：

- 单屏操作区
- 顶部状态条 + 中央控制区
- 左树 + 中表 + 右属性
- 中央机架/模块图 + 下方点位/参数表
- 趋势区 + 告警区 + 状态区
- 页签式参数/监控/诊断页面
- 设备本机运行画面，而不是平台型首页

### 其他类型也有各自不应出现的骨架

不同类型不仅要避免“错误风格”，还要避免“错误结构骨架”。

#### 管理系统不应出现
- 设备本机单屏 HMI 骨架
- 大按钮操作屏骨架
- 机架/模块硬件中心骨架
- 画布中心设计软件骨架
- 移动端底部 Tab 主导骨架

#### 数据分析系统不应出现
- 纯配置表单后台骨架
- PLC/HMI 单屏控制骨架
- 画布中心创作骨架
- 移动端信息流骨架

#### 建模软件不应出现
- SaaS 后台左侧菜单 + 表格中心骨架
- 大屏看板骨架
- 工控触摸屏大按钮骨架
- 纯列表办公软件骨架

#### 工具软件不应出现
- 复杂后台多层业务骨架
- 大屏监控台骨架
- 专业设计画布中心骨架
- 消费内容型 APP 骨架

#### 嵌入式软件不应出现
- SaaS 管理平台骨架
- 纯 PLC/HMI 现场大按钮骨架（除非是板载终端子类）
- 数据可视化大屏骨架
- 消费级移动 APP 骨架

#### 办公软件不应出现
- 工控操作屏骨架
- SCADA / 监控站控骨架
- 专业设计画布中心骨架
- 复杂 CRM/ERP 后台骨架过重的结构

#### 设计软件不应出现
- 互联网后台骨架
- 纯数据看板骨架
- PLC/HMI 单屏操作骨架
- 普通办公列表骨架

#### 监控软件不应出现
- 普通后台表格中心骨架
- 移动 APP 骨架
- 创作型画布中心骨架
- 工控现场大按钮操作屏骨架（除非就是站控操作终端）

#### APP软件不应出现
- Web 后台左侧菜单骨架
- 桌面专业软件多面板骨架
- 工控本机操作屏骨架
- 大屏监控骨架
- 超高密度表格中心骨架

## 不同类型不能共用一套参数骨架模板

这是本次项目最重要的发现之一：

- 不能先做一套通用 UI 参数模板，再通过改颜色、改按钮、改文案去适配所有软件类型。
- 因为真正决定“像不像”的，往往不是颜色，而是骨架。

后续应按类型分别维护不同的“参数骨架模板”，至少要分为：

1. `Web后台骨架`
2. `桌面专业软件骨架`
3. `工控/HMI/SCADA骨架`
4. `嵌入式上位机/调试工具骨架`
5. `办公协作骨架`
6. `设计/建模画布骨架`
7. `监控值守骨架`
8. `移动APP骨架`

也就是说，参数结构不应只包含：
- Colors
- Typography
- Shape
- Stroke
- Depth
- Layout
- Icon
- Motion
- Texture

还应增加更高一层的：
- `Skeleton Type`
- `Navigation Pattern`
- `Panel Composition`
- `Interaction Density`
- `Forbidden Structure`

## 后续生成时的骨架层写法建议

建议以后每套参数至少写成以下结构：

- `Software Type`: 软件类型
- `Subtype`: 子类型
- `Platform Style`: 平台气质
- `OS / Era`: 操作系统与时代
- `Skeleton Type`: 页面骨架类型
- `Navigation Pattern`: 导航样式
- `Panel Composition`: 分区方式
- `Control Style`: 控件风格
- `Avoid`: 风格与结构双重禁止项
- `UI Params`: 配色、字体、形态、描边、层次、动效等参数

## 工控类补充发现

工控类的差异化空间，相比管理系统、APP、设计软件更小。

因此工控类不应主要靠以下维度拉差异：
- 奇怪背景色
- 大圆角变化
- 材质变化
- 花哨动效
- 装饰性图标

工控类真正可用的差异化维度主要是：
- 子类型
- 页面骨架
- 操作场景
- 平台/年代
- 深浅体系
- 状态色策略
- 信息密度
- 参数区/控制区/告警区/趋势区的组织方式

因此后续在工控系统中，即使做 50 套、100 套，也不应被理解成 100 套完全自由发挥的视觉方案，而应理解成：

- 多种工控子类型
- 多种合理骨架
- 多种工程软件时代感
- 多种控制场景下的参数变体

## 负向约束使用规则

后续每生成一套 UI 参数，都应同时包含：

1. 正向类型定位：说明它应该像什么。
2. 平台/OS/控件定位：说明它属于什么平台与控件体系。
3. 负向类型约束：说明它绝对不要像什么。

推荐结构：

- `Software Type`: 当前系统类型
- `Subtype`: 子类型，如 PLC/HMI、设备配置、现代Web后台、桌面建模工具
- `Platform / OS`: 平台和操作系统时代
- `Control Style`: 控件风格
- `Avoid`: 明确列出不要生成的错误类型
- `UI Params`: 颜色、字体、布局、控件、动效等参数

### 2026-04-29 参数分隔符批量导入记录

用户需要将参数批量导入其他软件，已在相邻真实 UI 参数块之间插入独立分隔符：

```text
---参数分隔符---
```

处理范围：

- `UI参数/` 下 9 个现用分类文件。
- `完整提示词`。
- `总体`。
- `归档/总体-归档前含管理系统`。

维护规则：

- 分隔符只放在两个真实参数标题之间，即 `### ... UI参数 001：...` 与下一套 `### ... UI参数 002：...` 之间。
- 每两个相邻参数之间只能有 1 个 `---参数分隔符---`，避免重复插入。
- 参数模板标题（例如 `### 参数模板`、`### 管理系统 UI参数 X`）不是可导入真实参数，不需要分隔符。
- 后续新增真实参数时，应在上一套参数结束后、下一套标题前补 1 个分隔符，保证批量导入工具可按该字符串切分。

