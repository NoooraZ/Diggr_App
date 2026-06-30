# Diggr App — Page 2 组件 API

> 版本：v1.0 | 配套 `components.md` + `design-tokens.md`
> 组件总数：20 | 屏幕：10 个页面

---

## 目录

- [通用类型](#通用类型)
- [1. StoreCard — 商店卡片](#1-storecard)
- [2. AlbumCard — 专辑卡片](#2-albumcard)
- [3. SearchPill — 搜索药丸](#3-searchpill)
- [4. Tag — 标签](#4-tag)
- [5. BottomNav — 底部导航](#5-bottomnav)
- [6. MatchBadge — 匹配度徽章](#6-matchbadge)
- [7. VinylPin — 地图标记](#7-vinylpin)
- [8. RecentFindCard — 最近发现卡片](#8-recentfindcard)
- [9. FilterPills — 筛选条](#9-filterpills)
- [10. TopHeader — 顶部标题栏](#10-topheader)
- [11. FloatingSheet — 浮动内容面板](#11-floatingsheet)
- [12. SegmentedControl — 分段切换](#12-segmentedcontrol)
- [13. CityListItem — 城市列表项](#13-citylistitem)
- [14. ProfileStats — 个人统计](#14-profilestats)
- [15. NewArrivalCard — 新到货卡片](#15-newarrivalcard)
- [16. StoreBanner — 商店横幅](#16-storebanner)
- [17. AudioWaveform — 音频波形](#17-audiowaveform)
- [18. TreasureLogForm — 收藏记录表单](#18-treasurelogform)
- [19. StickyCTA — 底部固定按钮](#19-stickycta)
- [20. EmptyState — 列表结束提示](#20-emptystate)

---

## 通用类型

```typescript
// ---- 基础实体 ----
interface Store {
  id: string;
  name: string;
  imageUrl: string;
  matchPercent: number;
  city: string;
  neighborhood?: string;
  tags: string[];
}

interface Album {
  id: string;
  title: string;
  artist: string;
  coverUrl: string;
  year?: number;
  price?: string;
  label?: string;
}

interface User {
  id: string;
  displayName: string;
  avatarUrl: string;
}

// ---- 通用枚举 ----
type TagVariant = 'filled-dark' | 'filled-light' | 'outlined' | 'pill-dark';

type MatchBadgeSize = 'lg' | 'md' | 'sm';

type AlbumCardSize = 'hero' | 'lg' | 'md' | 'sm';

type VinylPinHighlight = 'default' | 'highlighted';

type NavTab = 'map' | 'explore' | 'bookmark' | 'person';

type FilterOption = {
  key: string;
  label: string;
};

type MediaCondition = 'mint' | 'near-mint' | 'vg-plus' | 'vg' | 'good' | 'fair';
```

---

## 1. StoreCard

商店信息卡片，用于列表展示。

```typescript
interface StoreCardProps {
  /** 商店数据 */
  store: Store;
  /** 点击卡片回调 */
  onPress?: (store: Store) => void;
  /** 是否显示匹配度 Badge，默认 true */
  showMatch?: boolean;
  /** 是否显示分类标签，默认 true */
  showTags?: boolean;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `store` | `Store` | ✅ | — | 商店实体 |
| `onPress` | `(store: Store) => void` | — | — | 点击跳转详情 |
| `showMatch` | `boolean` | — | `true` | 隐藏匹配度 |
| `showTags` | `boolean` | — | `true` | 隐藏标签行 |

**结构：**
```
[96×96 图]  [店名]
            [MatchBadge]
            [城市, 区域]
            [Tag] [Tag] [Tag]
```

**使用场景：** Home 列表、City Search 结果、Store Preview 面板内

---

## 2. AlbumCard

专辑封面卡片，4 种尺寸变体。

```typescript
interface AlbumCardProps {
  /** 专辑数据 */
  album: Album;
  /** 卡片尺寸变体 */
  size?: AlbumCardSize;           // 'hero' | 'lg' | 'md' | 'sm'
  /** 是否显示文字叠加层（仅在 hero/lg 下生效） */
  showOverlay?: boolean;
  /** 点击回调 */
  onPress?: (album: Album) => void;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `album` | `Album` | ✅ | — | 专辑实体 |
| `size` | `AlbumCardSize` | — | `'md'` | 变体尺寸 |
| `showOverlay` | `boolean` | — | `false` | 文字叠加 |
| `onPress` | `(album: Album) => void` | — | — | 点击 |

**尺寸矩阵：**
| size | 宽×高 | 圆角 | 场景 |
|------|--------|------|------|
| `hero` | 192×192 | 8px | 专辑详情页 |
| `lg` | 183×183 | 12px | New Arrival 网格 |
| `md` | 88×88 | 8px | Recent Find 列表 |
| `sm` | 64×64 / 80×80 | 4px | Profile 收藏网格 |

**状态：**
- `loading` — 灰色骨架屏占位
- `error` — 破损唱片图标占位
- `default` — 正常展示封面

---

## 3. SearchPill

全局搜索输入入口。

```typescript
interface SearchPillProps {
  /** 占位文字 */
  placeholder?: string;
  /** 当前输入值（受控模式） */
  value?: string;
  /** 点击时导航到搜索页，或聚焦输入 */
  onPress?: () => void;
  /** 文字变化（可编辑模式下） */
  onChangeText?: (text: string) => void;
  /** 点击右侧筛选图标 */
  onFilterPress?: () => void;
  /** 是否显示筛选图标，默认 true */
  showFilter?: boolean;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `placeholder` | `string` | — | `"Where to dig?"` | 占位文字 |
| `value` | `string` | — | — | 受控值 |
| `onPress` | `() => void` | — | — | 点击跳转 |
| `onChangeText` | `(text: string) => void` | — | — | 输入回调 |
| `onFilterPress` | `() => void` | — | — | 筛选回调 |
| `showFilter` | `boolean` | — | `true` | 隐藏筛选 |

---

## 4. Tag

标签组件，4 种视觉变体。

```typescript
interface TagProps {
  /** 标签文字 */
  label: string;
  /** 视觉变体 */
  variant?: TagVariant;           // 'filled-dark' | 'filled-light' | 'outlined' | 'pill-dark'
  /** 是否可点击 */
  onPress?: () => void;
  /** 选中态（用于可筛选标签） */
  selected?: boolean;
  /** 紧凑模式（减 padding） */
  compact?: boolean;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `label` | `string` | ✅ | — | 文字内容 |
| `variant` | `TagVariant` | — | `'filled-light'` | 视觉风格 |
| `onPress` | `() => void` | — | — | 可点击态 |
| `selected` | `boolean` | — | `false` | 选中高亮 |
| `compact` | `boolean` | — | `false` | 紧凑 padding |

**变体说明：**
| variant | 样式 | 示例 |
|---------|------|------|
| `filled-dark` | 黑底白字 SemiBold 13px | "92% MATCH" |
| `filled-light` | `#F0EDE8` 底黑字 | 轻量标签 |
| `outlined` | 1px `#CFC4C5` 透明底 | "City Pop" |
| `pill-dark` | 黑底白字 Bold | "STORE" |

---

## 5. BottomNav

底部固定导航栏。

```typescript
interface BottomNavProps {
  /** 当前激活标签 */
  activeTab: NavTab;
  /** 切换标签回调 */
  onTabChange: (tab: NavTab) => void;
  /** 标签配置（可覆盖默认图标/文字） */
  tabs?: BottomNavTab[];
}

interface BottomNavTab {
  key: NavTab;
  label: string;
  icon: ReactNode;
  /** Badge 数字（可选） */
  badge?: number;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `activeTab` | `NavTab` | ✅ | — | 当前页 |
| `onTabChange` | `(tab: NavTab) => void` | ✅ | — | 切换 |
| `tabs` | `BottomNavTab[]` | — | 默认 4 项 | 自定义标签 |

**默认标签：**
| key | label | 对应页面 |
|-----|-------|----------|
| `map` | Map | Explore 地图 |
| `explore` | Explore | Home |
| `bookmark` | Bookmark | My Diggs |
| `person` | Person | Profile |

---

## 6. MatchBadge

匹配度徽章。

```typescript
interface MatchBadgeProps {
  /** 匹配百分比（0-100） */
  percent: number;
  /** 尺寸变体 */
  size?: MatchBadgeSize;          // 'lg' | 'md' | 'sm'
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `percent` | `number` | ✅ | — | 0-100 |
| `size` | `MatchBadgeSize` | — | `'md'` | 尺寸 |

**尺寸对照：**
| size | 样式 | 字号 | 场景 |
|------|------|------|------|
| `lg` | 黑底白字 94×25px | 13px SemiBold | StoreCard |
| `md` | `#F0EDE8` 底黑字 63px 宽 | 13px Regular | 列表 |
| `sm` | 自适应 2px/8px padding | 11px Regular | 紧凑 |

---

## 7. VinylPin

地图上的唱片店标记。

```typescript
interface VinylPinProps {
  /** 商店名称 */
  storeName: string;
  /** 匹配度 */
  matchPercent: number;
  /** 高亮模式 */
  highlight?: VinylPinHighlight;  // 'default' | 'highlighted'
  /** 点击回调 */
  onPress?: () => void;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `storeName` | `string` | ✅ | — | 店名 |
| `matchPercent` | `number` | ✅ | — | 0-100 |
| `highlight` | `VinylPinHighlight` | — | `'default'` | 高亮态红底 |
| `onPress` | `() => void` | — | — | 点击弹出预览 |

**显示格式：** `"店名 百分比%"`，默认黑底白字，高亮红底(`#E23737`)白字。

---

## 8. RecentFindCard

社交动态卡片。

```typescript
interface RecentFindCardProps {
  /** 发现记录 */
  find: RecentFind;
  /** 点击回调 */
  onPress?: (find: RecentFind) => void;
  /** 点击用户头像 */
  onUserPress?: (user: User) => void;
  /** 点击专辑 */
  onAlbumPress?: (album: Album) => void;
}

interface RecentFind {
  id: string;
  album: Album;
  user: User;
  timestamp: string;              // ISO 8601
  quote: string;
  storeName?: string;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `find` | `RecentFind` | ✅ | — | 发现实体 |
| `onPress` | `(find: RecentFind) => void` | — | — | 卡片点击 |
| `onUserPress` | `(user: User) => void` | — | — | 头像点击 |
| `onAlbumPress` | `(album: Album) => void` | — | — | 专辑点击 |

**时间戳格式化：** 相对时间（"43min ago" / "2h ago" / "Yesterday"）

---

## 9. FilterPills

横向滚动筛选组件。

```typescript
interface FilterPillsProps {
  /** 选项列表 */
  options: FilterOption[];
  /** 当前选中的 key（单选） */
  selectedKey?: string;
  /** 选中变化回调 */
  onSelect: (key: string) => void;
  /** 是否允许取消选中 */
  allowDeselect?: boolean;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `options` | `FilterOption[]` | ✅ | — | 选项 |
| `selectedKey` | `string` | — | — | 当前选中 |
| `onSelect` | `(key: string) => void` | ✅ | — | 选择回调 |
| `allowDeselect` | `boolean` | — | `false` | 允许取消 |

**默认选项示例：**
```typescript
const defaultHomeFilters: FilterOption[] = [
  { key: 'tokyo', label: 'TOKYO' },
  { key: 'nearby', label: 'NEARBY' },
  { key: 'for-you', label: 'FOR YOU' },
  { key: 'genres', label: 'GENRES' },
  { key: 'rate', label: 'Rate' },
  { key: 'new-listing', label: 'New Listing' },
];
```

- 未选中：透明底 + `#CFC4C5` 描边
- 选中：黑底白字，`shadow-micro`

---

## 10. TopHeader

页面顶部标题栏。

```typescript
interface TopHeaderProps {
  /** 标题文字 */
  title?: string;
  /** 左侧图标按钮 */
  leftAction?: HeaderAction;
  /** 右侧图标按钮（可多个） */
  rightActions?: HeaderAction[];
  /** 是否透明背景（用于 Hero 覆盖） */
  transparent?: boolean;
}

interface HeaderAction {
  icon: 'back' | 'search' | 'filter' | 'more' | 'share' | 'menu';
  onPress: () => void;
  label?: string;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `title` | `string` | — | `"Diggr"` | 标题 |
| `leftAction` | `HeaderAction` | — | — | 返回等 |
| `rightActions` | `HeaderAction[]` | — | — | 右侧按钮 |
| `transparent` | `boolean` | — | `false` | Hero 透明 |

---

## 11. FloatingSheet

底部上浮面板，用于商店预览等。

```typescript
interface FloatingSheetProps {
  /** 面板内容 */
  children: ReactNode;
  /** 是否显示 */
  visible: boolean;
  /** 关闭回调 */
  onClose: () => void;
  /** 初始吸附高度（0-1，占屏幕比） */
  snapPoint?: number;
  /** 是否显示拖拽手柄 */
  showHandle?: boolean;
  /** 最大高度 */
  maxHeight?: number | string;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `children` | `ReactNode` | ✅ | — | 内容 |
| `visible` | `boolean` | ✅ | — | 显隐 |
| `onClose` | `() => void` | ✅ | — | 关闭 |
| `snapPoint` | `number` | — | `0.5` | 初始高度比 |
| `showHandle` | `boolean` | — | `true` | 拖拽手柄 |
| `maxHeight` | `number\|string` | — | `'90%'` | 最大高度 |

**样式：** 顶部圆角 40px，白色底，`shadow-heavy`

---

## 12. SegmentedControl

"STORE" / "ALBUM" 分段切换器。

```typescript
interface SegmentedControlProps {
  /** 分段选项 */
  segments: SegmentedOption[];
  /** 当前选中 */
  activeKey: string;
  /** 切换回调 */
  onChange: (key: string) => void;
}

interface SegmentedOption {
  key: string;
  label: string;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `segments` | `SegmentedOption[]` | ✅ | — | 选项 |
| `activeKey` | `string` | ✅ | — | 当前 |
| `onChange` | `(key: string) => void` | ✅ | — | 切换 |

**默认选项：**
```typescript
[
  { key: 'store', label: 'STORE' },
  { key: 'album', label: 'ALBUM' },
]
```

- 容器：`#F0EDE8` 底 + 9999px 圆角
- 选中：黑底白字 Bold（使用 `Tag variant="pill-dark"` 或独立动画过渡）

---

## 13. CityListItem

城市搜索结果行。

```typescript
interface CityListItemProps {
  /** 城市名 */
  cityName: string;
  /** 商店数量 */
  storeCount: number;
  /** 城市图标 URL */
  iconUrl?: string;
  /** 点击回调 */
  onPress: () => void;
}

// 也支持列表模式
interface CityListProps {
  cities: CityListItemProps[];
  onCityPress: (city: CityListItemProps) => void;
  /** 搜索过滤文本 */
  searchQuery?: string;
}
```

---

## 14. ProfileStats

用户统计区域。

```typescript
interface ProfileStatsProps {
  /** 用户 */
  user: User;
  /** 统计数据 */
  stats: {
    diggs: number;
    logs: number;
    cities: number;
  };
  /** 点击统计项 */
  onStatPress?: (key: 'diggs' | 'logs' | 'cities') => void;
  /** 是否可编辑头像 */
  editable?: boolean;
  /** 编辑头像回调 */
  onEditAvatar?: () => void;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `user` | `User` | ✅ | — | 用户信息 |
| `stats` | `{diggs, logs, cities}` | ✅ | — | 统计 |
| `onStatPress` | `(key) => void` | — | — | 点击跳转 |
| `editable` | `boolean` | — | `false` | 编辑模式 |
| `onEditAvatar` | `() => void` | — | — | 换头像 |

**布局：** 96px 头像 + 水平 3 等分统计数字

---

## 15. NewArrivalCard

商店新到货唱片卡片。

```typescript
interface NewArrivalCardProps {
  /** 专辑 */
  album: Album;
  /** 到货日期 */
  arrivalDate: string;
  /** 简短描述 */
  description?: string;
  /** 点击回调 */
  onPress?: (album: Album) => void;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `album` | `Album` | ✅ | — | 专辑 |
| `arrivalDate` | `string` | ✅ | — | 到货日期 |
| `description` | `string` | — | — | 描述 |
| `onPress` | `(album: Album) => void` | — | — | 点击 |

**尺寸：** 209×290px，圆角 12px

---

## 16. StoreBanner

商店详情页顶部横幅。

```typescript
interface StoreBannerProps {
  /** 商店数据 */
  store: Store;
  /** 背景图 URL */
  backgroundUrl?: string;
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `store` | `Store` | ✅ | — | 商店 |
| `backgroundUrl` | `string` | — | — | 背景图 |

**内容：** 店名(Libre Caslon Bold 24px) + 地址 + MatchBadge

---

## 17. AudioWaveform

专辑试听播放器。

```typescript
interface AudioWaveformProps {
  /** 音频 URL */
  audioUrl: string;
  /** 波形数据（采样点数组） */
  waveformData?: number[];
  /** 当前播放进度 0-1 */
  progress?: number;
  /** 是否正在播放 */
  isPlaying?: boolean;
  /** 播放/暂停回调 */
  onTogglePlay: () => void;
  /** 拖拽进度回调 */
  onSeek?: (progress: number) => void;
  /** 专辑信息 */
  albumInfo?: {
    title: string;
    artist: string;
    coverUrl: string;
  };
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `audioUrl` | `string` | ✅ | — | 音频 |
| `waveformData` | `number[]` | — | — | 波形 |
| `progress` | `number` | — | `0` | 进度 |
| `isPlaying` | `boolean` | — | `false` | 播放态 |
| `onTogglePlay` | `() => void` | ✅ | — | 切换 |
| `onSeek` | `(progress: number) => void` | — | — | 拖拽 |
| `albumInfo` | `object` | — | — | 专辑信息 |

**播放按钮：** 44px 黑色圆形，内嵌播放/暂停图标

---

## 18. TreasureLogForm

添加唱片收藏表单。

```typescript
interface TreasureLogFormProps {
  /** 提交回调 */
  onSubmit: (data: TreasureLogData) => void;
  /** 初始数据（编辑模式） */
  initialData?: Partial<TreasureLogData>;
  /** 是否正在提交 */
  isSubmitting?: boolean;
}

interface TreasureLogData {
  /** 专辑信息（可新建或搜索关联） */
  album?: Album;
  /** 唱片图片（用户拍照/上传） */
  images: File[];
  /** 唱片品相 */
  condition: MediaCondition;
  /** 购买价格 */
  price?: number;
  /** 评分 1-5 */
  rating: number;
  /** 备注 */
  notes: string;
  /** 购买商店 */
  storeName?: string;
  /** 购买日期 */
  purchaseDate?: string;
}
```

| 字段 | 类型 | 说明 |
|------|------|------|
| `album` | `Album` | 关联专辑 |
| `images` | `File[]` | 唱片照片 |
| `condition` | `MediaCondition` | 品相 |
| `price` | `number` | 价格 ¥ |
| `rating` | `number` | 1-5 星 |
| `notes` | `string` | 备注 |
| `storeName` | `string` | 购买商店 |
| `purchaseDate` | `string` | 日期 |

**品相枚举：**
```typescript
type MediaCondition = 'mint' | 'near-mint' | 'vg-plus' | 'vg' | 'good' | 'fair';
// 显示: Mint / Near Mint / VG+ / VG / Good / Fair
```

---

## 19. StickyCTA

底部固定操作按钮。

```typescript
interface StickyCTAProps {
  /** 按钮文字 */
  label: string;
  /** 点击回调 */
  onPress: () => void;
  /** 是否禁用 */
  disabled?: boolean;
  /** 加载中 */
  loading?: boolean;
  /** 次要操作（左侧文字按钮） */
  secondaryAction?: {
    label: string;
    onPress: () => void;
  };
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `label` | `string` | ✅ | — | "SAVE" |
| `onPress` | `() => void` | ✅ | — | 回调 |
| `disabled` | `boolean` | — | `false` | 置灰 |
| `loading` | `boolean` | — | `false` | 转圈 |
| `secondaryAction` | `object` | — | — | 次要按钮 |

**固定于底部，390×56px，黑底白字，`shadow-bottom`**

---

## 20. EmptyState

列表结束 / 空状态提示。

```typescript
interface EmptyStateProps {
  /** 提示文字 */
  message?: string;
  /** 类型 */
  type?: 'end-of-list' | 'empty' | 'error';
  /** 重试按钮（仅 error 类型） */
  onRetry?: () => void;
  /** 操作引导（仅 empty 类型） */
  action?: {
    label: string;
    onPress: () => void;
  };
}
```

| Prop | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `message` | `string` | — | 按类型 | 文字 |
| `type` | `'end-of-list' \| 'empty' \| 'error'` | — | `'end-of-list'` | 类型 |
| `onRetry` | `() => void` | — | — | 重试 |
| `action` | `object` | — | — | 操作按钮 |

**默认文案：**
| type | message |
|------|---------|
| `end-of-list` | "— End of current diggs —" |
| `empty` | "Nothing here yet" |
| `error` | "Something went wrong" |

---

## 组件依赖关系

```
TopHeader ──────────────────────────────────────────────┐
                                                        │
Home ──── SearchPill ─── FilterPills ─── StoreCard ──┐ │
                  │                       │           │ │
                  │                  MatchBadge   Tag  │ │
                  │                                    │ │
City Search ──── SearchPill ─── CityListItem           │ │
                                                        │ │
Store Preview ── FloatingSheet ─── StoreCard ─────────┘ │
        │                                                │
Store Detail ── StoreBanner ── NewArrivalCard ── StickyCTA
        │                       │
        │                  AlbumCard(lg)
        │
Album Detail ── AlbumCard(hero) ── AudioWaveform ── Tag
        │
Explore ──── SearchPill ─── VinylPin ─── FloatingSheet
        │
My Diggs ──── SegmentedControl ─── StoreCard / AlbumCard(md)
        │
Treasure Log ── TreasureLogForm
        │
Profile ──── ProfileStats ─── AlbumCard(sm)
        │
        └─── BottomNav ──────────────────（全局固定）
```

---

## 类型导出索引

```typescript
// 统一导出
export type {
  // 实体
  Store, Album, User, RecentFind,
  // 组件 Props
  StoreCardProps, AlbumCardProps, SearchPillProps,
  TagProps, BottomNavProps, MatchBadgeProps,
  VinylPinProps, RecentFindCardProps, FilterPillsProps,
  TopHeaderProps, FloatingSheetProps, SegmentedControlProps,
  CityListItemProps, ProfileStatsProps, NewArrivalCardProps,
  StoreBannerProps, AudioWaveformProps, TreasureLogFormProps,
  StickyCTAProps, EmptyStateProps,
  // 枚举 / 字面量
  TagVariant, MatchBadgeSize, AlbumCardSize, VinylPinHighlight,
  NavTab, FilterOption, MediaCondition, TreasureLogData,
  HeaderAction, BottomNavTab,
};
