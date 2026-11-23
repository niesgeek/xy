# XK · 星刻 — 复刻版部署说明

原站：https://xk.fs.kg/
仓库：https://github.com/niesgeek/xy

## 这是什么

纯前端静态站，单个 `index.html`（约 576 KB），无后端、无数据库、无表单、无 API 调用。

- 结构：导航 / 首屏（星尘 Canvas + 视差 hero）/ 跑马灯 / 001 释义（XK / FS / KG 三则信条）/ 002 所为（品牌识别 / 数字体验 / 内容叙事）/ 003 工序（观 / 削 / 刻 / 藏）/ 004 概念样张（4 张）/ 引句 / 005 通信（mailto:hello@xk.fs.kg）/ 页脚
- 动效：自定义金色光标、顶部滚动进度条、滚动渐现（IntersectionObserver）、星尘 Canvas、首屏标题逐行升起、跑马灯、颗粒噪点
- 样式：黑底 `#07080A` + 米白 `#EDE8E0` + 金 `#C8A367`，Cormorant Garamond / Noto Serif SC / Inter
- 图片：5 张原站图片已内嵌为 data URI，无需 `assets/` 目录即可完整显示
- 字体：仍走原站同款飞书妙搭 CDN（`miaoda.feishu.cn`）；离线环境下回退到 Georgia / 宋体 / 系统 sans

## 部署（二选一）

### Cloudflare Pages（推荐）

1. Pages → Create → Connect to Git → 选 `niesgeek/xy`，分支 `main`
2. Framework preset 选 `None` / 静态，Build command 留空，Output directory 留空（根目录就是 `index.html`）
3. Deploy，得到 `https://xy.pages.dev`（可在 Pages → Custom domains 绑自己的域名）

### GitHub Pages

仓库 → Settings → Pages → Source 选 `Deploy from a branch` → `main` / `/ (root)` → Save，访问 `https://niesgeek.github.io/xy/`。

## 本地预览

```bash
python3 -m http.server 8000
# 打开 http://localhost:8000/
```

直接双击 `index.html` 也能打开（字体需联网）。

## 如需把图片拆回独立文件

原图在 `https://xk.fs.kg/assets/`：`hero.jpg`、`work-ring.jpg`、`work-silk.jpg`、`work-slit.jpg`、`work-dust.jpg`。
下载到 `assets/` 后，把 `index.html` 里的 5 处 `data:image/jpeg;base64,…` 换回 `assets/xxx.jpg` 即可。
