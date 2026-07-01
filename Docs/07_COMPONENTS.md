# Diggr App — Page 2 组件清单

> 来源：Figma 文件 `PO5erXVEwn4zxWowyWEsiC`，Page 2
> 设计宽度：390px（移动端）
> 主题：黑胶唱片/音乐探索社交 App

---

## 目录
1. [Store Card — 商店卡片](#1-store-card)
2. [Album Card — 专辑卡片](#2-album-card)
3. [Search Pill — 搜索药丸](#3-search-pill)
4. [Tag — 标签](#4-tag)
5. [Bottom Navigation — 底部导航](#5-bottom-navigation)
6. [Match Badge — 匹配度徽章](#6-match-badge)
7. [Vinyl Pin — 地图标记](#7-vinyl-pin)
8. [Recent Find Card — 最近发现卡片](#8-recent-find-card)
9. [Filter Pills — 筛选条](#9-filter-pills)
10. [Top Header Bar — 顶部标题栏](#10-top-header-bar)
11. [Floating Content Card — 浮动内容面板](#11-floating-content-card)
12. [Segmented Control — 分段切换](#12-segmented-control)
13. [City List Item — 城市列表项](#13-city-list-item)
14. [Profile Stats Grid — 个人统计](#14-profile-stats-grid)
15. [New Arrival Card — 新到货卡片](#15-new-arrival-card)
16. [Store Identity Banner — 商店横幅](#16-store-identity-banner)
17. [Audio Waveform — 音频波形](#17-audio-waveform)
18. [Treasure Log Form — 收藏记录表单](#18-treasure-log-form)
19. [Sticky CTA Button — 底部固定按钮](#19-sticky-cta-button)
20. [Empty State Callout — 列表结束提示](#20-empty-state-callout)
21. [页面速览](#21-页面速览)

---

## 1. Store Card

**用途：** 展示唱片商店信息卡，出现在首页、城市搜索、商店预览、商店详情等多个页面。

```
┌──────────────────────────────────────┐
│ ┌──────┐                             │
│ │      │  Face Records               │
│ │ 96×96│  92% MATCH                  │
│ │      │  SHIBUYA, TOKYO             │
│ └──────┘  [City Pop] [Jazz] [Soul]   │
└──────────────────────────────────────┘
```

| 属性 | 值 |
|------|-----|
| 容器宽度 | 350px |
| 容器圆角 | 12px |
| 容器背景 | `#FFFFFF` |
| 店铺图片 | 96×96px |
| 匹配度标签 | 深色填充 Badge，字号 13px SemiBold |
| 位置信息 | 较小字号，灰色 |
| 类型标签 | 描边标签（[City Pop] [Jazz] [Soul]） |
| 出现屏幕 | Home、City Search、Store Preview、Store Detail |

---

## 2. Album Card

**用途：** 展示专辑封面，根据场景有 4 种尺寸变体。

| 变体 | 尺寸 | 场景 |
|------|------|------|
| Hero 大卡 | 192×192px | 专辑详情页封面 |
| 大卡 | 183×183px | 商店新到货区域 |
| 中卡 | 88×88px | 最近发现区（Recent Finds） |
| 小卡 | 64×64 / 80×80px | 个人主页收藏列表 |

**常见附加信息：** 专辑名、艺人名、价格、年份

---

## 3. Search Pill

**用途：** 全局搜索入口。

| 属性 | 值 |
|------|-----|
| 尺寸 | 350×56px |
| 圆角 | 全圆角（9999px / 胶囊形） |
| 背景 | `rgba(240, 237, 232, 0.7)` |
| 占位文字 | "Where to dig?" |
| 图标 | 左侧搜索图标 + 右侧筛选图标 |

---

## 4. Tag

**用途：** 标签，4 种视觉变体。

| 变体 | 样式 | 字号/字重 | 示例 |
|------|------|-----------|------|
| 深色填充 | 黑色(`#000`)背景，白色文字 | 13px SemiBold | "92% MATCH" |
| 浅色填充 | `#F0EDE8` 背景，黑色文字 | 13px Regular | "92% MATCH" |
| 描边标签 | 1px `#CFC4C5` 描边，透明底 | 较小字号 | "City Pop", "Jazz" |
| 黑色药丸 | `#000` 填充，白色文字 | Bold | "STORE", "ALBUM" |

---

## 5. Bottom Navigation

**用途：** 底部导航栏，固定于页面底部。

| 属性 | 值 |
|------|-----|
| 容器宽度 | 390px |
| 背景 | `rgba(252, 249, 244, 0.66)` + `backdrop-filter: blur(6px)` |
| 标签项 | Map / Explore / Bookmark / Person |
| 图标尺寸 | 48×48px，圆角 9999px |
| 布局 | 4 等分 |

---

## 6. Match Badge

**用途：** 显示商店/专辑与用户偏好的匹配度。

| 变体 | 尺寸 | 样式 | 使用场景 |
|------|------|------|----------|
| 大号黑底 | 约 94×25px | 黑底白字 SemiBold 13px | Store Card 内 |
| 中号浅底 | 约 63px 宽，hug 高 | `#F0EDE8` 底黑字 | 列表项 |
| 小号浅底 | 自适应宽度 | 2px/8px padding | 紧凑场景 |

---

## 7. Vinyl Pin

**用途：** 地图上的商店标记。

| 属性 | 值 |
|------|-----|
| 总尺寸 | 约 154.5×76px |
| 黑胶图标 | 圆形，约 33px 直径 |
| 标签容器 | 154.5×32px，圆角 9999px（胶囊形） |
| 样式示例 | 黑底白字："Face Records 92%" |
| 高亮示例 | 红底白字："Disk Union 96%" |

---

## 8. Recent Find Card

**用途：** 社交动态卡片，展示用户最近发现的唱片。

```
┌──────────────────────────────────────┐
│ ┌──────┐  Rumours                    │
│ │88×88 │  Fleetwood Mac              │
│ └──────┘                             │
│ ● L  ·  43min ago                   │
│ "Pristine copy found at Disk Union,  │
│  couldn't believe my luck..."        │
└──────────────────────────────────────┘
```

| 属性 | 值 |
|------|-----|
| 容器宽度 | 350px |
| 容器圆角 | 12px |
| 专辑图片 | 88×88px |
| 用户头像 | 20px 圆形 |
| 时间戳 | 灰色小字 |
| 引语 | 正文，可能有多行 |

---

## 9. Filter Pills

**用途：** 横向滚动筛选条。

| 属性 | 值 |
|------|-----|
| 布局 | 横向滚动（overflow-x: scroll） |
| 选项示例 | "TOKYO", "NEARBY", "FOR YOU", "GENRES", "Rate", "New Listing" |
| 样式 | 浅色描边胶囊形 |
| 选中态 | 深色填充药丸 |

---

## 10. Top Header Bar

**用途：** 页面顶部标题栏。

| 属性 | 值 |
|------|-----|
| 标题 | "Diggr" |
| 字体 | Libre Caslon Text Bold |
| 布局 | 居中标题 + 可选左右图标按钮 |

---

## 11. Floating Content Card

**用途：** 从底部上浮的白色内容面板，用于商店预览等场景。

| 属性 | 值 |
|------|-----|
| 顶部圆角 | 40px |
| 背景 | `#FFFFFF` |
| 阴影 | 有阴影层次 |
| 内容 | 可滚动 |

---

## 12. Segmented Control

**用途：** "STORE" / "ALBUM" 分类切换。

| 属性 | 值 |
|------|-----|
| 样式 | 黑底药丸形 |
| 选中态 | 黑色填充 + 白色文字 |
| 未选中态 | 透明/浅色 |
| 出现 | My Diggs 页面 |

---

## 13. City List Item

**用途：** 城市搜索列表中的城市项。

| 属性 | 值 |
|------|-----|
| 结构 | 圆形图标 + 城市名 + 商店数量 |
| 示例 | "Tokyo — 24 stores" |

---

## 14. Profile Stats Grid

**用途：** 用户个人主页统计区。

| 属性 | 值 |
|------|-----|
| 头像 | 96px 圆形 |
| 统计数字 | "52 DIGGS / 18 LOGS / 6 Cities" |
| 布局 | 水平 3 等分 |

---

## 15. New Arrival Card

**用途：** 商店新到货唱片卡片。

| 属性 | 值 |
|------|-----|
| 尺寸 | 209×290px |
| 内容 | 大封面图 + 日期 + 描述文字 |
| 圆角 | 12px |

---

## 16. Store Identity Banner

**用途：** 商店详情页顶部横幅。

| 属性 | 值 |
|------|-----|
| 内容 | 店名 + 地址 + 匹配度 Badge |
| 布局 | 店名大字 + 地址小字 + Badge |

---

## 17. Audio Waveform

**用途：** 专辑试听播放器界面。

| 属性 | 值 |
|------|-----|
| 元素 | 波形可视化 + 播放/暂停按钮 |
| 播放按钮 | 44px 黑色圆形按钮 |

---

## 18. Treasure Log Form

**用途：** 用户添加唱片收藏的表单。

| 元素 | 说明 |
|------|------|
| 图片上传 | 可添加唱片图片 |
| 条件选择 | 唱片品相选择（Mint/Near Mint/VG+ 等） |
| 评分 | 星级评分 |
| 备注 | 文字输入 |

---

## 19. Sticky CTA Button

**用途：** 底部固定操作按钮。

| 属性 | 值 |
|------|-----|
| 尺寸 | 390×56px |
| 背景 | 黑色 `#000` |
| 文字 | 白色 Bold，如 "SAVE" / "PLAN VISIT" |

---

## 20. Empty State Callout

**用途：** 列表滚动到底部时的提示。

| 属性 | 值 |
|------|-----|
| 文字 | "— End of current diggs —" |
| 样式 | 居中，灰色小字 |

---

## 21. 页面速览

Page 2 共包含 10 个屏幕，所有组件分布如下：

| 屏幕 | 主要组件 |
|------|----------|
| Home | Search Pill, Filter Pills, Store Card, Top Header, Bottom Nav |
| City Search | Search Pill, City List Item, Bottom Nav |
| Store Preview | Floating Content Card, Store Card, Vinyl Pin |
| Store Detail | Store Identity Banner, Album Card(大卡), New Arrival Card, Sticky CTA |
| Album Detail | Album Card(Hero), Audio Waveform, Tag |
| Explore | Search Pill, Vinyl Pin, Floating Content Card, Bottom Nav |
| My Diggs - Store | Segmented Control, Store Card, Bottom Nav |
| My Diggs - Album | Segmented Control, Album Card(中卡), Bottom Nav |
| Treasure Log | Treasure Log Form |
| Profile | Profile Stats Grid, Album Card(小卡), Bottom Nav |

---

## 设计 Token（来自 Figma Variables）

| Token | 值 | 用途 |
|-------|-----|------|
| 主背景色 | `#FCF9F4` | 页面背景 |
| 卡片背景 | `#FFFFFF` | 卡片 |
| 浅灰背景 | `#F0EDE8` | 浅色 Tag、Badge |
| 描边色 | `#CFC4C5` | 描边标签 |
| 黑色 | `#000000` | 主要文字、按钮 |
| 红色 | 高亮 Vinyl Pin |
| 模糊 | `backdrop-filter: blur(6px)` | Bottom Nav |
