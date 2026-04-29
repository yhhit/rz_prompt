# APP软件 UI参数（50套）

## 生成目标

生成50套APP软件UI参数。界面应适合移动端首页、列表、表单、个人中心、设置页、卡片页等通用结构，不包含具体业务逻辑。

## 风格要求

- 移动端友好，控件尺寸舒适。
- 可使用更大的圆角、更柔和的留白和卡片结构。
- 色彩可比后台软件更亲和，但不能幼稚、游戏化或过度艺术化。
- 避免强大屏风、复杂背景纹理。

## 推荐风格方向

1. 明亮移动卡片风
2. iOS 分组列表风
3. Android Material 容器风
4. 底部导航卡片风
5. 大标题列表风
6. 浅玻璃移动风
7. 青绿效率卡片风
8. 暖灰分组表单风
9. 米白墨绿列表风
10. 奶白深棕轻卡片风
11. 紫色点缀节制风
12. 冷灰橙色工具风
13. 平板双栏风
14. 深色移动工具风

## 技术栈 / 渲染范式优先规则

- Rendering Paradigm: `Mobile native app`
- UI Framework: `iOS SwiftUI/UIKit / Android Material 3`
- Component Language: `navigation bar, tab bar, list cell, card container, bottom sheet, segmented control, chips`
- Native Control Level: `medium / high`
- CSS Styling Level: `medium`

## OS / Era 使用规则

- 推荐 OS Family: `iOS / Android`
- 推荐 OS Era: `iOS 15/16/17`、`Android 11/12/13/14`、`Android 12+ Material You`
- 少量可用: `iPadOS / Android Tablet`，用于平板端轻办公或轻工具
- 避免: `Windows/macOS 桌面软件`、`Web后台`、`Industrial HMI`、`Windows XP/7/10/11 桌面气质`
- OS Visual Traits: `移动端大圆角卡片、底部导航、分组列表、轻浮层、Material组件或iOS柔和层次`
- No Title Bar: `不要桌面操作系统标题栏、不要窗口控制按钮；必须保持移动端 iOS/Android 应用结构`

## 平台 / OS / 控件 / 避免项

- Platform Style: `现代移动应用`，可偏 `iOS` 或 `Android / Material` 当前时代气质
- OS / Era: 优先 `iOS 15/16/17`、`Android 11/12/13/14`，避免老式移动端视觉
- Control Style: `移动端卡片`、`底部导航`、`列表`、`表单`、`移动交互控件`
- Avoid: 不要生成 `Web后台`、`桌面专业软件`、`PLC/HMI工控屏`、`数据大屏`、`复杂表格密集页`、`老式移动系统界面`

## 参数生成模板

### 参数模板
- OS Family: `iOS / Android / iPadOS / Android Tablet`
- Rendering Paradigm: `Mobile native app`
- UI Framework: `iOS SwiftUI/UIKit / Android Material 3`
- Component Language: `navigation bar, tab bar, list cell, card container, bottom sheet, segmented control, chips`
- Native Control Level: `medium / high`
- CSS Styling Level: `medium; mobile component polish, not desktop Web CSS`
- OS Era: `iOS 15/16/17 / Android 11/12/13/14 / Android 12+ Material You`
- OS Visual Traits: `移动端大圆角卡片、底部导航、分组列表、轻浮层、Material组件或iOS柔和层次`
- No Title Bar: `不要桌面操作系统标题栏、不要窗口控制按钮；必须保持移动端 iOS/Android 应用结构`
- Colors: bg `#...`, surface `#...`, text `#...`, primary `#...`, accent `#...`, border `#...`
- Typography: sans; scale `12/14/16/24` 或 `14/16/22/34`; weights `400/500/600/700`
- Shape: radius `12/14/16/18/24`; controls `40–48h`
- Stroke: 1px subtle; focus/active state soft
- Depth: soft card shadow / none / glass light
- Layout: mobile card / bottom action / list-first / spacious sections
- Icon: outline `1.5px`; rounded friendly
- Motion: `180–240ms`; soft fade+slide
- Texture: none 或 1% noise，玻璃浅色少量使用

## 差异化规则

每套至少变化以下4项：

- 主色与辅助色
- 卡片圆角
- 背景暖冷
- 控件高度
- 阴影强度
- 列表或卡片密度
- 图标风格
- 动效节奏


## 少量套数强差异化规则

当某个大类下只有 6–10 套真实参数时，不能只做同一骨架的配色变化；每套都必须像不同软件。生成时优先遵守以下硬约束：

- 每套必须有不同的 `Target Viewport / UI Scale`：例如手机 390×844、平板 1366×1024、桌面 1440×900、工作站 1920×1080、HMI 1024×768、双屏/超宽 2560×1440。
- 每套必须有明确的 `First-glance Signature`：用户第一眼能看到的差异，例如大标题手机卡片、硬边框工控按钮、深色终端、Ribbon 工具栏、三维视口、图表矩阵、浮动小窗。
- 每套必须拉开 `Component Scale`：有的整体控件很小很密，有的按钮和列表很大，有的中等办公密度，有的触控大字号。
- 每套必须拉开背景与容器语言：纯白/浅灰/米色/深蓝/黑灰/玻璃/硬边框/网格底/终端底，不允许连续多套都是白底卡片。
- 每套至少在 `目标分辨率、整体缩放、背景颜色、容器形态、导航骨架、控件密度、字体尺度、边框/阴影` 中变化 5 项以上。
- 如果两套同属浅色风，必须一个偏冷灰硬边框，一个偏暖色大留白，或者一个高密度表格，一个大控件卡片，不能只换主色。

## 推荐配色池

- bg `#FFFFFF`, surface `#F8FAFC`, text `#0F172A`, primary `#2563EB`, accent `#10B981`, border `#E2E8F0`
- bg `#F8FAFC`, surface `#FFFFFF`, text `#0F172A`, primary `#16A34A`, accent `#0EA5E9`, border `#E2E8F0`
- bg `#FFFFFF`, surface `#F8FAFC`, text `#0F172A`, primary `#0F766E`, accent `#F59E0B`, border `#E2E8F0`
- bg `#F6F7FB`, surface `rgba(255,255,255,.70)`, text `#0F172A`, primary `#2563EB`, accent `#06B6D4`, border `rgba(15,23,42,.08)`
- bg `#FAF8F3`, surface `#FFFFFF`, text `#1C1917`, primary `#166534`, accent `#B45309`, border `#E7E5E4`
- bg `#FFFFFF`, surface `#F1F5F9`, text `#0F172A`, primary `#7C3AED`, accent `#2563EB`, border `#E2E8F0`

## 数量建议

- 明亮移动卡片：6套
- iOS 分组列表：5套
- Android Material 容器：5套
- 底部导航卡片：4套
- 大标题列表：4套
- 浅玻璃移动：4套
- 青绿效率卡片：4套
- 暖灰分组表单：4套
- 米白墨绿列表：3套
- 奶白深棕轻卡片：3套
- 紫色点缀节制：3套
- 冷灰橙色工具：2套
- 平板双栏：2套
- 深色移动工具：1套

---

## UI参数区

### APP软件 UI参数 001：iOS 当前时代清爽卡片风
- Visual Differentiation: `与同类其他套相比，第一眼必须呈现“iOS large-title + white rounded summary cards + bottom TabBar, very clean and airy”，不是只换颜色`
- Target Viewport / UI Scale: `Phone 390×844 @1x; large mobile scale; 48–56h touch controls; generous safe-area spacing`
- First-glance Signature: `iOS large-title + white rounded summary cards + bottom TabBar, very clean and airy`
- Background & Surface Language: `cool off-white mobile background with floating cards`
- Component Scale: `large mobile scale; 48–56h touch controls; generous safe-area spacing`
- Subtype: `现代移动APP / iOS气质 / 信息列表与快捷入口`
- Rendering Paradigm: `Mobile native app`
- UI Framework: `iOS SwiftUI/UIKit / Android Material 3`
- Component Language: `navigation bar, tab bar, list cell, card container, bottom sheet, segmented control, chips`
- Native Control Level: `medium / high`
- CSS Styling Level: `medium; mobile component polish, not desktop Web CSS`
- Platform / OS: `iOS 16+ / iOS 17 时代移动应用气质`
- OS Family: `按 Platform / OS 判断：Web / Windows / macOS / Linux / iOS / Android / Industrial HMI`
- OS Visual Traits: `遵循本文件 OS / Era 使用规则，匹配对应系统年代的控件、圆角、边框、密度与层次`
- No Title Bar: `不要桌面操作系统标题栏、不要窗口控制按钮；保持 iOS/Android 移动应用结构`
- Controls: `大圆角卡片`、`底部导航`、`分组列表`、`轻量搜索栏`、`浮层操作`
- Avoid: 不要像Web后台、桌面软件、PLC/HMI、数据大屏、复杂表格页
- Colors: bg `#F7F8FA`, surface `#FFFFFF`, text `#111827`, primary `#0F766E`, accent `#F59E0B`, border `rgba(17,24,39,.08)`
- Typography: sans; scale `13/15/20/32`; weights `400/500/600/700`; lineHeight `1.45–1.62`
- Shape: radius `18/24/28`; controls `48h`
- Stroke: 1px faint; active ring `rgba(15,118,110,.16)`
- Depth: soft card shadow `0 10 24 rgba(17,24,39,.06)`
- Layout: top summary card + grouped list + bottom tab bar
- Icon: outline `1.5px`; rounded mobile symbols
- Motion: `220ms`; soft fade+6px slide
- Texture: none

### APP软件 UI参数 002：Android Material 稳定组件风
- Visual Differentiation: `与同类其他套相比，第一眼必须呈现“Android Material top app bar + tonal containers + chips + bottom navigation”，不是只换颜色`
- Target Viewport / UI Scale: `Phone 412×915 @1x; medium mobile scale; 44–48h Material controls; compact vertical feed`
- First-glance Signature: `Android Material top app bar + tonal containers + chips + bottom navigation`
- Background & Surface Language: `warm beige Material surface, tonal cards`
- Component Scale: `medium mobile scale; 44–48h Material controls; compact vertical feed`
- Subtype: `现代移动APP / Android Material / 设置与队列列表`
- Rendering Paradigm: `Mobile native app`
- UI Framework: `iOS SwiftUI/UIKit / Android Material 3`
- Component Language: `navigation bar, tab bar, list cell, card container, bottom sheet, segmented control, chips`
- Native Control Level: `medium / high`
- CSS Styling Level: `medium; mobile component polish, not desktop Web CSS`
- Platform / OS: `Android 12+ / Material You 克制气质`
- OS Family: `按 Platform / OS 判断：Web / Windows / macOS / Linux / iOS / Android / Industrial HMI`
- OS Visual Traits: `遵循本文件 OS / Era 使用规则，匹配对应系统年代的控件、圆角、边框、密度与层次`
- No Title Bar: `不要桌面操作系统标题栏、不要窗口控制按钮；保持 iOS/Android 移动应用结构`
- Controls: `Material卡片`、`顶部应用栏`、`FAB弱化版`、`分段筛选`、`列表项`
- Avoid: 不要像桌面工具、后台系统、工控屏、老式Android界面
- Colors: bg `#F5F3EF`, surface `#FFFFFF`, text `#1F2937`, primary `#3F6212`, accent `#EA580C`, border `#E7E5E4`
- Typography: sans; scale `12/14/18/28`; weights `400/500/600`; lineHeight `1.42–1.58`
- Shape: radius `16/20`; controls `44h`
- Stroke: 1px subtle; selected container `rgba(63,98,18,.12)`
- Depth: tiny `0 3 10 rgba(0,0,0,.05)`
- Layout: app bar + filter chips + vertical cards + bottom navigation
- Icon: outline `1.5px`; Material-like rounded
- Motion: `200ms`; standard ease
- Texture: none

### APP软件 UI参数 003：移动端深色专业应用风
- Visual Differentiation: `与同类其他套相比，第一眼必须呈现“black/navy mobile dark mode + glowing status chips + bottom action bar”，不是只换颜色`
- Target Viewport / UI Scale: `Phone 390×844 dark mode; large mobile scale; 46–52h controls; dark compact cards`
- First-glance Signature: `black/navy mobile dark mode + glowing status chips + bottom action bar`
- Background & Surface Language: `deep navy background with elevated dark cards`
- Component Scale: `large mobile scale; 46–52h controls; dark compact cards`
- Subtype: `现代移动APP / 深色模式 / 专业工具型移动界面`
- Rendering Paradigm: `Mobile native app`
- UI Framework: `iOS SwiftUI/UIKit / Android Material 3`
- Component Language: `navigation bar, tab bar, list cell, card container, bottom sheet, segmented control, chips`
- Native Control Level: `medium / high`
- CSS Styling Level: `medium; mobile component polish, not desktop Web CSS`
- Platform / OS: `iOS/Android 当前时代深色模式`
- OS Family: `按 Platform / OS 判断：Web / Windows / macOS / Linux / iOS / Android / Industrial HMI`
- OS Visual Traits: `遵循本文件 OS / Era 使用规则，匹配对应系统年代的控件、圆角、边框、密度与层次`
- No Title Bar: `不要桌面操作系统标题栏、不要窗口控制按钮；保持 iOS/Android 移动应用结构`
- Controls: `深色卡片`、`分组表单`、`底部操作栏`、`状态标签`、`轻量弹层`
- Avoid: 不要像工业监控大屏、桌面控制台、游戏HUD、复杂后台
- Colors: bg `#0F172A`, surface `#182235`, text `#E5E7EB`, primary `#14B8A6`, accent `#F59E0B`, border `rgba(255,255,255,.10)`
- Typography: sans; scale `13/15/20/30`; weights `400/500/600`; lineHeight `1.42–1.58`
- Shape: radius `16/20`; controls `46h`
- Stroke: 1px subtle; active border `rgba(20,184,166,.28)`
- Depth: soft dark `0 14 34 rgba(0,0,0,.35)`
- Layout: compact mobile dashboard + grouped settings + bottom action bar
- Icon: outline `1.5px`; rounded
- Motion: `210ms`; fade+4px slide
- Texture: none

---

### APP软件 UI参数 004：Android Material 容器风
- Visual Differentiation: `与同类其他套相比，第一眼必须呈现“single-column Material cards + prominent FAB + rounded bottom sheet”，不是只换颜色`
- Target Viewport / UI Scale: `Phone 360×800 @1x; very large touch scale; oversized 52–60h controls; low density`
- First-glance Signature: `single-column Material cards + prominent FAB + rounded bottom sheet`
- Background & Surface Language: `pale lavender/white tonal container background`
- Component Scale: `very large touch scale; oversized 52–60h controls; low density`
- Rendering Paradigm: `Mobile native app`
- UI Framework: `Android Material 3`
- Component Language: `top app bar, navigation bar, card container, chips, bottom sheet, list cell`
- Native Control Level: `high`
- CSS Styling Level: `medium`
- OS Family: `Android`
- OS Era: `Android 13/14 Material You`
- OS Visual Traits: `大圆角色彩容器、顶部栏、底部导航、轻量动效`
- No Title Bar: `不要桌面操作系统标题栏、不要窗口控制按钮`
- Skeleton Type: `顶部应用栏 + 内容卡片流 + 底部导航 + 底部浮层`
- Navigation Pattern: `TopAppBar + NavigationBar + modal bottom sheet`
- Panel Composition: `顶部栏 / 大卡片 / 分组列表 / chips / 底部导航`
- Interaction Density: `中低`
- Control Style: `Material 3 容器、chips、列表单元、底部浮层、FAB`
- Avoid: `不要桌面软件、多栏后台、HMI屏、表格密集页`
- Colors: bg `#F8FAFC`, surface `#FFFFFF`, text `#0F172A`, primary `#6750A4`, accent `#0F766E`, border `#E2E8F0`
- Typography: sans; scale `12/14/18/28`; weights `400/500/600`; lineHeight `1.45–1.6`
- Shape: radius `18/24/28`; controls `48h`
- Stroke: 1px faint; active container `rgba(103,80,164,.12)`
- Depth: soft tonal elevation
- Layout: single-column mobile; bottom navigation fixed
- Icon: rounded Material symbols
- Motion: `220ms`; soft material transition
- Texture: none

### APP软件 UI参数 005：iOS 分组列表风
- Visual Differentiation: `与同类其他套相比，第一眼必须呈现“iOS Settings-like grouped list + search field + sheet overlay”，不是只换颜色`
- Target Viewport / UI Scale: `Phone 430×932 @1x; comfortable iOS scale; large titles; sparse grouped cells`
- First-glance Signature: `iOS Settings-like grouped list + search field + sheet overlay`
- Background & Surface Language: `system light gray background with flat white grouped cells`
- Component Scale: `comfortable iOS scale; large titles; sparse grouped cells`
- Rendering Paradigm: `Mobile native app`
- UI Framework: `iOS SwiftUI/UIKit`
- Component Language: `navigation bar, grouped list, large title, segmented control, sheet, tab bar`
- Native Control Level: `high`
- CSS Styling Level: `medium`
- OS Family: `iOS`
- OS Era: `iOS 16/17`
- OS Visual Traits: `大标题、分组列表、轻灰背景、底部Tab、柔和浮层`
- No Title Bar: `不要桌面操作系统标题栏、不要窗口控制按钮`
- Skeleton Type: `大标题导航 + 分组列表 + 底部Tab + 轻浮层`
- Navigation Pattern: `NavigationStack + TabBar + sheet`
- Panel Composition: `大标题 / 分组列表 / 卡片摘要 / 底部导航`
- Interaction Density: `中低`
- Control Style: `iOS 分组列表、分段控件、搜索栏、sheet、TabBar`
- Avoid: `不要桌面标题栏、不要浏览器壳、不要后台侧栏、不要工控屏`
- Colors: bg `#F2F2F7`, surface `#FFFFFF`, text `#1D1D1F`, primary `#007AFF`, accent `#34C759`, border `rgba(60,60,67,.18)`
- Typography: sans; scale `13/15/20/34`; weights `400/500/600/700`; lineHeight `1.45–1.62`
- Shape: radius `14/18/22`; controls `44–50h`
- Stroke: hairline separators
- Depth: none / subtle floating sheet
- Layout: grouped list; safe-area spacing; bottom tabs
- Icon: SF Symbols-like outline
- Motion: `200ms`; native slide
- Texture: none

### APP软件 UI参数 006：平板双栏浅色风
- Visual Differentiation: `与同类其他套相比，第一眼必须呈现“iPad/Android tablet three-pane split with navigation rail and detail pane”，不是只换颜色`
- Target Viewport / UI Scale: `Tablet 1366×1024 landscape; tablet scale; 46h controls; medium density split view`
- First-glance Signature: `iPad/Android tablet three-pane split with navigation rail and detail pane`
- Background & Surface Language: `wide light canvas with separated side rail`
- Component Scale: `tablet scale; 46h controls; medium density split view`
- Rendering Paradigm: `Mobile native app`
- UI Framework: `iPadOS SwiftUI / Android Tablet Material`
- Component Language: `split view, navigation rail, list cell, detail pane, floating sheet`
- Native Control Level: `medium / high`
- CSS Styling Level: `medium`
- OS Family: `iPadOS / Android Tablet`
- OS Era: `iPadOS 16+ / Android Tablet Material 3`
- OS Visual Traits: `平板双栏、侧边导航、详情面板、触控留白`
- No Title Bar: `不要桌面操作系统标题栏、不要窗口控制按钮`
- Skeleton Type: `左侧导航栏 + 中央列表 + 右详情面板`
- Navigation Pattern: `split view + navigation rail + floating sheet`
- Panel Composition: `导航栏 / 列表区 / 详情面板 / 操作浮层`
- Interaction Density: `中`
- Control Style: `平板双栏、列表单元、详情卡片、浮层控件`
- Avoid: `不要桌面窗口标题栏、不要Web后台、不要密集表格页`
- Colors: bg `#F7F8FA`, surface `#FFFFFF`, text `#111827`, primary `#2563EB`, accent `#F59E0B`, border `#E5E7EB`
- Typography: sans; scale `13/15/20/30`; weights `400/500/600`; lineHeight `1.45–1.58`
- Shape: radius `16/20/24`; controls `46h`
- Stroke: 1px subtle
- Depth: soft card `0 8 20 rgba(17,24,39,.06)`
- Layout: tablet split view; medium whitespace
- Icon: outline `1.5px`; rounded
- Motion: `210ms`; fade+slide
- Texture: none
