# Diggr App — Page 2 设计 Token

> 来源：Figma 文件 `PO5erXVEwn4zxWowyWEsiC`，Page 2 GLOBAL_VARS
> 设计基座：390×874px 移动端
> 与 `components.md` 配套使用

---

## 目录

1. [色彩系统](#1-色彩系统)
2. [字体系统](#2-字体系统)
3. [阴影 & 模糊](#3-阴影--模糊)
4. [圆角](#4-圆角)
5. [间距 & 布局](#5-间距--布局)
6. [组件尺寸速查](#6-组件尺寸速查)
7. [CSS 变量建议](#7-css-变量建议)

---

## 1. 色彩系统

### 1.1 基础色板

| Token | Hex / RGBA | CSS 变量建议 | 用途 |
|-------|------------|-------------|------|
| 页面背景 | `#FCF9F4` | `--color-bg-page` | 全局页面底色 |
| 白色 | `#FFFFFF` | `--color-bg-card` | 卡片、面板背景 |
| 黑色 | `#000000` | `--color-fill-dark` | 深色按钮、深色标签、主文字 |
| 深棕 | `#1C1C19` | `--color-text-primary` | 一级文字 |
| 中灰 | `#4C4546` | `--color-text-secondary` | 二级文字 |
| 灰文字 | `#7E7576` | `--color-text-tertiary` | 三级文字（地址、时间戳） |
| 暗灰 | `#5E5E5B` | `--color-text-muted` | 弱化文字 |
| 灰蓝 | `#6B7280` | `--color-icon` | 图标色 |

### 1.2 浅色 / 背景系

| Token | 值 | CSS 变量建议 | 用途 |
|-------|-----|-------------|------|
| 浅灰卡 | `#F0EDE8` | `--color-bg-tag` | Tag / Badge 浅色底 |
| 极浅灰 | `#F6F3EE` | `--color-bg-surface` | 表面层级 |
| 浅灰 | `#EAE8E3` | `--color-bg-subtle` | 微妙背景 |
| 灰白 | `#E5E2DD` | `--color-border-light` | 浅分割线 |
| 半透页面色 80% | `rgba(252,249,244,0.8)` | `--color-overlay-page` | 渐变叠加 |
| 半透页面色 66% | `rgba(252,249,244,0.66)` | `--color-bg-nav` | Bottom Nav 背景 |
| 半透白 60% | `rgba(255,255,255,0.6)` | `--color-overlay-white` | 浅色叠加 |

### 1.3 描边 / 分割线

| Token | 值 | CSS 变量建议 | 用途 |
|-------|-----|-------------|------|
| 描边主色 | `#CFC4C5` | `--color-border` | Tag 描边、输入框边框 |
| 描边半透 50% | `rgba(207,196,197,0.5)` | `--color-border-soft` | 软分割 |
| 描边半透 30% | `rgba(207,196,197,0.3)` | `--color-border-light` | 轻分割 |
| 描边半透 20% | `rgba(207,196,197,0.2)` | `--color-border-subtle` | 极轻分割 |
| 暗半透 10% | `rgba(0,0,0,0.1)` | `--color-overlay-dark` | 暗色叠加 |
| 深灰半透 80% | `rgba(76,69,70,0.8)` | `--color-text-disabled` | 禁用态文字 |
| 灰半透 20% | `rgba(126,117,118,0.2)` | `--color-text-placeholder` | 占位符 |

### 1.4 强调 / 功能色

| Token | 值 | CSS 变量建议 | 用途 |
|-------|-----|-------------|------|
| 红色 | `#E23737` | `--color-accent-red` | 高亮 Vinyl Pin、提醒 |
| 黑色渐变 | `linear-gradient(180deg, rgba(0,0,0,0.35) 0%, #000 21%, #000 85%, rgba(0,0,0,0) 100%)` | `--gradient-hero` | Hero 区域渐变遮罩 |
| 上淡入 | `linear-gradient(0deg, rgba(252,249,244,0.8) 0%, rgba(252,249,244,0) 50%, rgba(252,249,244,0) 100%)` | `--gradient-fade-up` | 底部到中间淡入 |
| 水平分割线 | `linear-gradient(90deg, rgba(207,196,197,0) 0%, #CFC4C5 50%, rgba(207,196,197,0) 100%)` | `--gradient-divider` | 横向渐变分割线 |

### 1.5 颜色使用矩阵（按组件）

| 组件 | 背景 | 文字 | 描边 | 特殊 |
|------|------|------|------|------|
| Store Card | `#FFFFFF` | `#1C1C19` / `#7E7576` | — | 12px 圆角 |
| Album Card | — | — | — | 缩放图片 |
| Search Pill | `rgba(240,237,232,0.7)` | `#7E7576` | — | 9999px |
| Tag (深色) | `#000000` | `#FFFFFF` | — | 9999px |
| Tag (浅色) | `#F0EDE8` | `#000000` | — | 9999px |
| Tag (描边) | transparent | `#000000` | `#CFC4C5` 1px | 9999px |
| Bottom Nav | `rgba(252,249,244,0.66)` | — | — | backdrop-blur(6px) |
| Match Badge (黑) | `#000000` | `#FFFFFF` | — | 9999px |
| Match Badge (浅) | `#F0EDE8` | `#000000` | — | 9999px |
| Vinyl Pin | `#000000` / `#E23737` | `#FFFFFF` | — | — |
| Recent Find Card | `#FFFFFF` | `#1C1C19` / `#7E7576` | — | 12px 圆角 |
| Filter Pills | transparent | `#000000` | `#CFC4C5` | 选中态黑底 |
| Floating Card | `#FFFFFF` | — | — | 40px 顶圆角 |
| CTA Button | `#000000` | `#FFFFFF` | — | — |

---

## 2. 字体系统

### 2.1 字体族

| 用途 | Font Family | 分类 |
|------|-------------|------|
| UI 正文 / 标签 / 数字 | **Hanken Grotesk** | Sans-serif |
| 标题 / 品牌 / 引语 | **Libre Caslon Text** | Serif |

### 2.2 Hanken Grotesk（UI 字体）

| Token 名 | 字重 | 字号 | 行高 | 字间距 | 大小写 | 建议用途 |
|----------|------|------|------|--------|--------|----------|
| `text-xs` | Regular 400 | 9px | 13.5px | — | — | 极小标注 |
| `text-2xs` | Regular 400 | 10px | 15px | — | — | 辅助信息 |
| `text-2xs-up` | Regular 400 | 10px | 15px | 0.1em | UPPER | 大写标签 |
| `text-xs-up` | Bold 700 | 10px | 15px | -0.05em | UPPER | 加粗大写标签 |
| `text-2xs-center` | Regular 400 | 10px | 15px | — | — | 居中辅助字 |
| `text-2xs-italic` | Italic 400 | 10px | 15px | — | — | 斜体注释 |
| `text-xs-medium` | Medium 500 | 10px | 15px | — | — | 加粗小字 |
| `text-sm` | Regular 400 | 11px | 15px | — | — | 说明文字 |
| `text-sm-medium` | Medium 500 | 11px | 14px | — | — | 标签文字 |
| `text-sm-up` | Medium 500 | 11px | 14px | 0.05em | UPPER | 大写标签中号 |
| `text-sm-italic` | Italic 400 | 11px | 14px | — | — | 斜体说明 |
| `text-sm-17` | Regular 400 | 11px | 17.88px | — | — | 宽松行高 |
| `text-base-sm` | Medium 500 | 12px | 14px | 0.05em | — | 紧凑标签 |
| `text-base` | Regular 400 | 13px | 18px | 0.0615em | TITLE | 正文/列表 |
| `text-base-semibold` | SemiBold 600 | 13px | 16px | 0.05em | — | Match Badge |
| `text-base-semibold-up` | SemiBold 600 | 13px | 16px | 0.1em | UPPER | 大写 Badge |
| `text-base-semibold-2` | SemiBold 600 | 13px | 16px | 0.05em | UPPER | 标签强调 |
| `text-md` | Regular 400 | 14px | 20px | — | — | 列表文字 |
| `text-md-wide` | Regular 400 | 14px | 20px | 0.0429em | — | 列表宽间距 |
| `text-md-up` | Regular 400 | 14px | 24px | 0.1143em | UPPER | 分类标题 |
| `text-lg` | Regular 400 | 16px | 24px | — | — | 正文 |
| `text-lg-center` | Regular 400 | 16px | 24px | — | — | 居中正文 |
| `text-lg-16` | Regular 400 | 16px | 16px | 0.0406em | — | 紧凑正文 |
| `text-lg-up` | Regular 400 | 16px | 24px | 0.05em | UPPER | 导航标签 |
| `text-lg-wide` | Regular 400 | 16px | 24px | 0.05em | UPPER | 大写宽间距 |
| `text-xl` | Regular 400 | 16px | 16px | 0.0406em | — | 数字展示 |

### 2.3 Libre Caslon Text（标题 / 品牌字体）

| Token 名 | 字重 | 字号 | 行高 | 字间距 | 建议用途 |
|----------|------|------|------|--------|----------|
| `heading-sm` | Regular 400 | 16px | 27px | — | 引语 / 副标题 |
| `heading-sm-medium` | Medium 500 | 14px | 24px | — | 小标题 |
| `heading-md` | Medium 500 | 16px | 24px | — | 中标题 |
| `heading-md-center` | Medium 500 | 16px | 24px | — | 居中标题 |
| `heading-md-27` | Medium 500 | 16px | 27px | — | 宽松行高标题 |
| `heading-base` | Regular 400 | 16px | 20px | — | 紧凑标题 |
| `heading-lg` | Bold 600 | 20px | 28px | — | 大标题 |
| `heading-lg-center` | Bold 600 | 20px | 28px | — | 居中大标题 |
| `heading-xl` | Bold 700 | 20px | 25px | — | 紧凑大标题 |
| `heading-xl-28` | Bold 700 | 20px | 28px | — | 大标题宽松 |
| `heading-2xl` | Medium 500 | 20px | 28px | — | 超大副标 |
| `heading-3xl` | Bold 700 | 24px | 32px | — | 页面标题 |
| `heading-4xl` | Bold 700 | 28px | 36px | -0.0429em | Hero 标题 |

### 2.4 字体大小综述

```
        ┌── 28px  Hero 标题 (Libre Caslon Bold)
        │
        ├── 24px  页面标题 (Libre Caslon Bold)
        │
        ├── 20px  大标题 (Libre Caslon Bold 600/700)
        │
        ├── 16px  正文 / 中标题 (Hanken Grotesk / Libre Caslon Medium)
        │
 12px ──├── 14px  列表文字 (Hanken Grotesk)
 14px ──┤
        ├── 13px  Badge / 标签 (Hanken Grotesk SemiBold)
        │
        ├── 12px  紧凑标签 (Hanken Grotesk Medium)
        │
        ├── 11px  说明文字 (Hanken Grotesk Regular/Italic)
        │
        ├── 10px  辅助信息 (Hanken Grotesk)
        │
        └──  9px  极小标注 (Hanken Grotesk)
```

---

## 3. 阴影 & 模糊

| Token 名 | 值 | 建议用途 |
|----------|-----|----------|
| Shadow 微 | `0px 1px 2px 0px rgba(0,0,0,0.05)` | 药丸标签、滤镜 |
| Shadow 轻 1 | `0px 2px 4px -2px rgba(0,0,0,0.1), 0px 4px 6px -1px rgba(0,0,0,0.1)` | Vinyl Pin 标签 |
| Shadow 轻 2 | `0px 4px 20px 0px rgba(0,0,0,0.03)` | 轻卡片 |
| Shadow 中 | `0px 4px 6px -4px rgba(0,0,0,0.1), 0px 10px 15px -3px rgba(0,0,0,0.1)` | 黑胶图标投影 |
| Shadow 重 | `0px 8px 10px -6px rgba(0,0,0,0.1), 0px 20px 25px -5px rgba(0,0,0,0.1)` | 浮动卡片 |
| Shadow 强 | `0px 10px 30px 0px rgba(0,0,0,0.05)` | 底部操作区 |
| Shadow 底栏 | `0px -8px 30px 0px rgba(0,0,0,0.08)` | Bottom Nav 上投影 |
| Blur 导航 | `backdrop-filter: blur(6px)` | Bottom Nav 玻璃效果 |

**阴影层级示意（低→高）：**

```
Shadow 微       → Filter Pills
Shadow 轻 1/2   → Vinyl Pin, 轻卡片
Shadow 中       → 图标元素
Shadow 重       → Floating Content Card
Shadow 强       → Sticky CTA 区域
Shadow 底栏     → Bottom Navigation (向上)
```

---

## 4. 圆角

| Token | 值 | 用途 |
|-------|-----|------|
| `radius-none` | 0 | 全宽元素 |
| `radius-sm` | 4px | 小元素 |
| `radius-md` | 8px | 图像容器 |
| `radius-lg` | 12px | Store Card, Recent Find Card, New Arrival Card |
| `radius-xl` | 20px | 中等圆角面板 |
| `radius-2xl` | 40px | Floating Content Card（顶部） |
| `radius-full` | 9999px | Search Pill, Tag, Badge, Vinyl Pin 标签, Bottom Nav 图标 |

---

## 5. 间距 & 布局

### 5.1 屏幕网格

| 属性 | 值 |
|------|-----|
| 屏幕宽度 | 390px |
| 屏幕高度 | 874px / 874.25px |
| 水平内边距 | 20px（390 − 350）/2 |
| 内容区宽度 | 350px |

### 5.2 常用间距

| Token | 值 | 场景 |
|-------|-----|------|
| `space-2xs` | 2px | 紧凑间距 |
| `space-xs` | 4px | 图标与文字间距 |
| `space-sm` | 8px | Tag padding, 列表项间隙 |
| `space-md` | 12px | Tag 横向 padding |
| `space-lg` | 16px | 卡片内边距、Filter Pill |
| `space-xl` | 20px | 页面安全区、Store Banner |
| `space-2xl` | 24px | 大间距 |
| `space-3xl` | 128px | 页面底部留白（避开 Bottom Nav） |

### 5.3 弹性布局模式

| Token | 属性 | 场景 |
|-------|------|------|
| `layout-row-center` | `flex-direction: row; justify-content: center; align-items: center` | 图标容器 (48×48) |
| `layout-row-hug` | `flex-direction: row; padding: 8px; justify-content: center; align-items: center` | Vinyl Pin 图标区 |
| `layout-col-stretch` | `flex-direction: column; align-self: stretch; align-items: stretch` | 列表内容区 |
| `layout-col-center` | `flex-direction: column; padding: 8px 16px; justify-content: center; align-items: center` | 按钮/标签 |
| `layout-row-space` | `flex-direction: row; padding: 20px; justify-content: space-between; align-items: center` | 顶部导航栏 |
| `layout-page` | `flex-direction: column; padding-bottom: 128px; align-items: stretch` | 页面容器 |

---

## 6. 组件尺寸速查

| 组件 | 宽度 | 高度 | 特殊 |
|------|------|------|------|
| 屏幕 | 390px | 874px | 固定 |
| 内容区 | 350px | — | 自适应 |
| Search Pill | 350px | 56px | 9999px |
| Store Card | 350px | 自适应 | 12px |
| Album Hero | 192px | 192px | — |
| Album 大卡 | 183px | 183px | — |
| Album 中卡 | 88px | 88px | — |
| Album 小卡 | 64px / 80px | 64px / 80px | — |
| Vinyl Pin | 154.5px | 76px | — |
| Vinyl 圆标 | 33px | 33px | 9999px |
| Vinyl 标签 | 154.5px | 32px | 9999px |
| Bottom Nav 图标 | 48px | 48px | 9999px |
| CTA Button | 390px | 56px | — |
| New Arrival Card | 209px | 290px | 12px |
| 个人头像（大） | 96px | 96px | 9999px |
| 个人头像（小） | 20px | 20px | 9999px |
| 播放按钮 | 44px | 44px | 9999px |
| 分割线 | — | 0.5px | — |

---

## 7. CSS 变量建议

将以上 Token 转为 Tailwind 或原生 CSS 变量，建议以下命名：

```css
:root {
  /* === 色彩 === */
  --color-bg-page:       #FCF9F4;
  --color-bg-card:       #FFFFFF;
  --color-bg-tag:        #F0EDE8;
  --color-bg-surface:    #F6F3EE;
  --color-bg-subtle:     #EAE8E3;
  --color-bg-nav:        rgba(252, 249, 244, 0.66);
  --color-fill-dark:     #000000;
  --color-fill-red:      #E23737;

  --color-text-primary:  #1C1C19;
  --color-text-secondary:#4C4546;
  --color-text-tertiary: #7E7576;
  --color-text-muted:    #5E5E5B;
  --color-text-inverse:  #FFFFFF;

  --color-border:        #CFC4C5;
  --color-border-soft:   rgba(207, 196, 197, 0.5);
  --color-border-light:  rgba(207, 196, 197, 0.3);
  --color-border-subtle: rgba(207, 196, 197, 0.2);

  --color-overlay-page:  rgba(252, 249, 244, 0.8);
  --color-overlay-dark:  rgba(0, 0, 0, 0.1);

  /* === 字体 === */
  --font-ui:       'Hanken Grotesk', sans-serif;
  --font-display:  'Libre Caslon Text', serif;

  /* === 圆角 === */
  --radius-sm:     4px;
  --radius-md:     8px;
  --radius-lg:     12px;
  --radius-xl:     20px;
  --radius-2xl:    40px;
  --radius-full:   9999px;

  /* === 阴影 === */
  --shadow-micro:  0px 1px 2px 0px rgba(0, 0, 0, 0.05);
  --shadow-light:  0px 2px 4px -2px rgba(0, 0, 0, 0.1),
                   0px 4px 6px -1px rgba(0, 0, 0, 0.1);
  --shadow-medium: 0px 4px 6px -4px rgba(0, 0, 0, 0.1),
                   0px 10px 15px -3px rgba(0, 0, 0, 0.1);
  --shadow-heavy:  0px 8px 10px -6px rgba(0, 0, 0, 0.1),
                   0px 20px 25px -5px rgba(0, 0, 0, 0.1);
  --shadow-bottom: 0px -8px 30px 0px rgba(0, 0, 0, 0.08);

  /* === 模糊 === */
  --blur-nav:      blur(6px);

  /* === 间距 === */
  --space-xs:      4px;
  --space-sm:      8px;
  --space-md:      12px;
  --space-lg:      16px;
  --space-xl:      20px;
  --space-2xl:     24px;
  --space-3xl:     128px;

  /* === 屏幕 === */
  --screen-width:  390px;
  --content-width: 350px;
  --screen-height: 874px;
}
