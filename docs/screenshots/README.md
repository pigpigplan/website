# 官网功能截图（预留目录）

对应 `website/index.html` →「操作说明」中的三个核心模块：

| 模块 | 章节 | 目录/文件名前缀 |
|---|---|---|
| 封面 | §1 First Launch / 首次启动 / 首次啟動 / 初回起動 / 첫 실행 / Erster Start / Premier lancement / Primer inicio | `cover` |
| 财务 | §3 Finance / 财务 / 財務 / 家計 / 가계부 / Finanzen / Finances / Finanzas | `finance` |
| 健康 | §4 Health / 健康 / Gesundheit / Santé / Salud | `health` |
| 相册 | §5 Simple Album / 简易相册 / 簡易相簿 / 簡易アルバム / 간편 앨범 / Einfaches Album / Album simple / Álbum simple | `album` |

每个语言共 13 张：财务 5 张、健康 5 张、相册 3 张；另有 **1 张可选封面**（见下节）。固定顺序与后缀：

| 视图 | 后缀 | 拍什么 |
|---|---|---|
| 主页 | `-home.jpg` | 模块首页 / 主面板（有真实示例数据，不要空白页） |
| 录入 | `-entry.jpg` | 新增或编辑流程（语音待确认卡、录入表单、相册添加/筛选均可） |
| 录入 2 | `-entry-2.jpg` | 第二张录入效果（只给财务、健康；相册没有） |
| 查询 | `-query.jpg` | 第一张查询条件 + 结果（搜索、筛选结果、计划问答、趋势/报表） |
| 查询 2 | `-query-2.jpg` | 第二张查询效果（只给财务、健康；相册没有） |

## 路径规则

```text
website/screenshots/<语言>/<模块>-<视图>.jpg
```

- `<语言>`：`en`、`zh-Hans`、`zh-Hant`、`ja`、`ko`、`de`、`fr`、`es`
- `<模块>`：`finance`、`health`、`album`
- `<视图>`：`home`、`entry`、`query`；财务/健康另有 `entry-2`、`query-2`
- 扩展名必须是小写 `.jpg`；语言代码大小写必须一致（`zh-Hans` / `zh-Hant`）。

## 封面图（可选 · 每个语言 1 张）

封面图单独命名，不带 `<模块>-<视图>`，显示在「操作说明 → §1 首次启动」正文下方（App 封面 / 总览页截图）：

```text
website/screenshots/<语言>/cover.jpg    ← 优先：按语言各放一张
website/screenshots/cover.jpg           ← 兜底：只放一张、所有语言共用
```

- 页面先找 `screenshots/<语言>/cover.jpg`；该语言目录没有这张图时，自动回退到 `screenshots/cover.jpg`（一张通用封面即可）；两张都没有才显示预留路径虚线框。
- 封面不需要 8 个语言都补齐也能上线：先放一张 `screenshots/cover.jpg`，之后想精细区分语言再逐语言补 `cover.jpg`。
- 建议用 App 封面页（同时能看到天气 / 交通地图 / ETA 与页签），遮掉真实姓名、地址与状态栏隐私信息。

## 真机截图（`screenshots/devices/`）

营销页（`website/marketing.html`）的「真机截图」小节用这一组图，**不是**上面的操作说明图：

```text
website/screenshots/devices/<语言>/iphone_<视图>.jpg
```

| 设备 | `<视图>` | 页面位置 | 生成宽度 |
|---|---|---|---|
| iPhone Pro Max | `promax_portrait` | 竖屏 | 700 px |
| iPhone Pro Max | `promax_landscape` | 横屏（整行横跨） | 1100 px |
| iPhone Duo | `duo_portrait` | 竖屏 | 760 px |
| iPhone Duo | `duo_landscape` | 横屏（整行横跨） | 1000 px |
| iPhone Duo（展开） | `duo_open_portrait` | 展开 · 竖屏 | 800 px |
| iPhone Duo（展开） | `duo_open_landscape` | 展开 · 横屏（整行横跨） | 1100 px |

- **源图**（PNG，8 语言 × 6 张，共 53 MB）在 `/Volumes/ORICO/pigpigplan/<语言>/`。
- 重新生成（已转好的 48 张随仓库提供，约 8 MB）：

```bash
bash scripts/build_marketing_device_shots.sh /Volumes/ORICO/pigpigplan
node scripts/check_marketing_i18n.mjs   # 会逐个断言这 48 个文件存在
```

- 为什么转 JPEG：原始 PNG 单张 0.6–1.9 MB，48 张近 53 MB；转 4:4:4 → q80 后单张 ~100–250 KB，页面按当前语言只懒加载 6 张。
- ⚠️ `de/` 目录源文件名有个笔误：`iphone_duo_opne_landscape.png`（opne）。脚本已内置兜底，**不要**手改源目录。
- 截图里不能出现真实姓名、地址、状态栏通知等隐私信息。

## 每个语言需要放的 14 个文件

### `screenshots/en/`
```text
finance-home.jpg    finance-home-2.jpg    finance-entry.jpg    finance-entry-2.jpg    finance-query.jpg    finance-query-2.jpg
health-home.jpg     health-entry.jpg     health-entry-2.jpg     health-query.jpg     health-query-2.jpg
album-home.jpg      album-entry.jpg      album-query.jpg
```

### `screenshots/zh-Hans/`
```text
finance-home.jpg    finance-home-2.jpg    finance-entry.jpg    finance-entry-2.jpg    finance-query.jpg    finance-query-2.jpg
health-home.jpg     health-entry.jpg     health-entry-2.jpg     health-query.jpg     health-query-2.jpg
album-home.jpg      album-entry.jpg      album-query.jpg
```

### `screenshots/zh-Hant/`
```text
finance-home.jpg    finance-home-2.jpg    finance-entry.jpg    finance-entry-2.jpg    finance-query.jpg    finance-query-2.jpg
health-home.jpg     health-entry.jpg     health-entry-2.jpg     health-query.jpg     health-query-2.jpg
album-home.jpg      album-entry.jpg      album-query.jpg
```

### `screenshots/ja/`
```text
finance-home.jpg    finance-home-2.jpg    finance-entry.jpg    finance-entry-2.jpg    finance-query.jpg    finance-query-2.jpg
health-home.jpg     health-entry.jpg     health-entry-2.jpg     health-query.jpg     health-query-2.jpg
album-home.jpg      album-entry.jpg      album-query.jpg
```

### `screenshots/ko/`
```text
finance-home.jpg    finance-home-2.jpg    finance-entry.jpg    finance-entry-2.jpg    finance-query.jpg    finance-query-2.jpg
health-home.jpg     health-entry.jpg     health-entry-2.jpg     health-query.jpg     health-query-2.jpg
album-home.jpg      album-entry.jpg      album-query.jpg
```

### `screenshots/de/`
```text
finance-home.jpg    finance-home-2.jpg    finance-entry.jpg    finance-entry-2.jpg    finance-query.jpg    finance-query-2.jpg
health-home.jpg     health-entry.jpg     health-entry-2.jpg     health-query.jpg     health-query-2.jpg
album-home.jpg      album-entry.jpg      album-query.jpg
```

### `screenshots/fr/`
```text
finance-home.jpg    finance-home-2.jpg    finance-entry.jpg    finance-entry-2.jpg    finance-query.jpg    finance-query-2.jpg
health-home.jpg     health-entry.jpg     health-entry-2.jpg     health-query.jpg     health-query-2.jpg
album-home.jpg      album-entry.jpg      album-query.jpg
```

### `screenshots/es/`
```text
finance-home.jpg    finance-home-2.jpg    finance-entry.jpg    finance-entry-2.jpg    finance-query.jpg    finance-query-2.jpg
health-home.jpg     health-entry.jpg     health-entry-2.jpg     health-query.jpg     health-query-2.jpg
album-home.jpg      album-entry.jpg      album-query.jpg
```

合计：**8 语言 × 14 张 = 112 张**（财务 6 + 健康 5 + 相册 3）；封面按需再放 `cover.jpg`（1–8 张），最多 120 张。

## 截图建议

- 手机竖屏，建议 1290×2796（iPhone 6.7"）或 1179×2556（6.1"）；同一语言使用同一台设备/主题。
- 切成对应 App 语言后再截图；目录名必须和 App 语言一致。
- 用演示数据，遮掉真实姓名、地址、Apple ID、通知与状态栏隐私信息。
- 财务主页不要开启隐私模式（要能看出金额与图表）；`finance-entry.jpg` 建议包含语音待确认卡或分期「总额 / 期数 / 每期」，`finance-entry-2.jpg` 再补一张不同的录入效果（如手动编辑表单、预算设置或另一类语音录入）；`finance-query.jpg` 建议包含问题与结果，`finance-query-2.jpg` 再补一张不同的查询效果（如计划问答卡、图表报表或另一类自然语言提问）。
- 健康 `health-entry.jpg` 建议用「血压 / 体重」等待确认卡，`health-entry-2.jpg` 再补一张不同的录入效果（如运动、情绪或症状语音录入）；`health-query.jpg` 建议用压力、睡眠或趋势图结果，`health-query-2.jpg` 再补一张不同的查询结果（如“哪几天压力最大”或另一项指标趋势）。
- 相册录入建议用「添加照片 / 筛选」；查询建议用筛选后的网格或两张对比。
- 单张建议控制在 300–600 KB；体积大可用 `sips -Z 1800 原图.jpg --out 目标.jpg` 压到长边 1800 px。

## 补图方式

把 JPG 按上表命名放入对应目录即可，无需改代码。页面会自动从占位虚线框切换为图片；缺图时会显示该文件的预留路径，方便核对。
