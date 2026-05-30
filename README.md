<div align="center">

<img src="assets/banner.svg" alt="FindItem · 寻物 — Open-source Smart Parts Locator" width="820">

# FindItem · 寻物

**30-second part location: scan · beep · find**
**扫码、响铃、定位 —— 30 秒找到任意零件**

[![Live demo](https://img.shields.io/badge/live-demo-61C4E3?style=flat-square&labelColor=0B0E11&logo=github&logoColor=white)](https://harryxin0919.github.io/findit-website/)
[![Pages deploy](https://img.shields.io/github/deployments/HarryXin0919/findit-website/github-pages?style=flat-square&label=pages&labelColor=0B0E11&color=2ea44f)](https://github.com/HarryXin0919/findit-website/deployments)
[![Custom domain](https://img.shields.io/badge/finditem-is--a.dev-61C4E3?style=flat-square&labelColor=0B0E11)](https://finditem.is-a.dev)
![Find in 30s](https://img.shields.io/badge/find_in-30s-61C4E3?style=flat-square&labelColor=0B0E11)
![Open source](https://img.shields.io/badge/open-source-61C4E3?style=flat-square&labelColor=0B0E11)

🌐 **Live / 线上**: <https://harryxin0919.github.io/findit-website/> · 🔗 **Domain (pending)**: <https://finditem.is-a.dev>

</div>

---

## 🎯 About / 关于项目

**EN** — FindItem is an **open-source** smart parts locator. Each parts bin is equipped with an ESP32, LED, and buzzer — search for a part by phone or web, and the target bin instantly lights up and beeps. From search to pickup: under 30 seconds.

This repository is the **public-facing landing page** of the project — a vanilla static website that explains how the system works, showcases the five core features, and includes an interactive end-to-end demo.

**中文** — 一个**开源**的智能零件定位系统。每个零件箱装上 ESP32 + LED + 蜂鸣器——通过手机或网页搜索零件,目标箱子自动响铃闪灯,从搜索到取件不到 30 秒。

本仓库是该项目的**官网/落地页**——一个纯静态网站,展示系统原理、5 大功能,并内置可交互的全流程演示。

---

## ✨ Features / 核心功能

| Feature / 功能 | EN | 中文 |
|---|---|---|
| 🔍 **Smart Search / 模糊搜索** | Fuzzy match by name, model, or category — no exact codes needed | 按名称、型号或类别实时匹配,无需精确编号 |
| 👥 **Multi-user / 多人并发** | Up to 7 simultaneous users, unique LED color + beep rhythm per user | 最多 7 人同时查找,每人独立 LED 颜色 + 蜂鸣节奏 |
| 🔐 **Feishu Login / 飞书登录** | OAuth 2.0 sign-in | OAuth 2.0 身份验证 |
| 🔋 **Battery Monitor / 电量监控** | Real-time voltage check, auto Feishu alerts on low battery | 实时电压检测,低电量自动飞书通知管理员 |
| 📦 **Parts Management / 零件管理** | Admin CRUD dashboard, max 3 part types per bin | 管理员后台 CRUD,每个箱子最多 3 种零件 |

---

## 🛠 Tech Stack / 技术栈

### Frontend (this repo) / 前端(本仓库)

**EN**
- Pure **HTML5 + inline CSS + vanilla JavaScript** — zero dependencies, zero build step
- Fonts: **Inter** (Latin) + **Noto Sans SC** (CJK), loaded via Google Fonts
- Dual themes: dark / light, **auto-switched by visitor's local time** (light from 7:00 to 19:00, dark otherwise)
- Bilingual (EN / 中文) with seamless in-page toggle
- Fully responsive, mobile-friendly
- Accent colors: `#61C4E3` (cyan) on dark surfaces, `#0A7099` (deep cyan) on light surfaces

**中文**
- 纯 **HTML5 + 内联 CSS + Vanilla JavaScript**,零依赖、零构建步骤
- 字体:**Inter**(英文)+ **思源黑体 Noto Sans SC**(中文),通过 Google Fonts 加载
- 深 / 浅双主题,**按访客本地时间自动切换**(7:00–19:00 浅色,其余深色)
- 中英双语,页面内无刷新切换
- 完整响应式,适配手机
- 主色:`#61C4E3` 青蓝(深色面)/ `#0A7099` 深青(白昼面)

### Hardware + Backend / 硬件 + 后端
- ESP32-C3 per bin · WiFi + WebSocket · Feishu OAuth + bot webhook
- Backend service + database (in development / 开发中)

---

## 📁 File Structure / 文件结构

```text
findit-website/
├── index.html        # Main page / 主页(~1400 lines, inline <style> + <script>)
├── features.js       # Feature & step modal data + logic / 功能/步骤弹窗数据与逻辑
├── img/
│   ├── cropped/      # Section background photos / 区块背景图
│   └── logo/         # Logo variations / 各版本 logo
├── .gitignore
└── README.md         # This file / 本文件
```

---

## 🚀 Local Development / 本地开发

**EN** — No build step required. Just open `index.html` in any modern browser:

**中文** — 无需任何构建工具,**双击 `index.html` 用浏览器打开**即可:

```powershell
# Windows
cd path\to\findit-website
start index.html

# macOS / Linux
open index.html      # macOS
xdg-open index.html  # Linux
```

After editing `index.html`, refresh your browser to see changes.
修改 `index.html` 后,刷新浏览器即可看到效果。

### Where to edit what / 想改什么 → 改哪

| Want to change / 想改 | File / 文件 | Search for / 搜索 |
|---|---|---|
| Hero headline / Hero 大标题 | `index.html` | `hero_h1:` (in both zh + en dicts) |
| Stat numbers / 数据(40箱、7人...) | `index.html` | `<div class="stat-num">` |
| 3-step explanation / 三步说明 | `index.html` | `step1_title:` etc. |
| Feature cards / 功能卡 | `index.html` | `feat1_title:` etc. |
| **01/02/03 step modals** / **步骤详情弹窗** | `features.js` | `stepDetails` |
| **Feature modals / 功能详情弹窗** | `features.js` | `featureDetails` |
| Roadmap phases / 路线图 | `index.html` | `tl-item` |
| Brand color / fonts / 主色 / 字体 | `index.html` | `:root {` |
| Background images / 背景图 | `img/cropped/` | Overwrite same-name `.jpg` / 覆盖同名 jpg |

### About bilingual content / 关于双语文案

**EN** — All user-facing copy lives in two dictionaries at the bottom of `index.html`:

**中文** — 所有用户可见的文案都在 `index.html` 底部的两个字典里:

```javascript
const zh = { hero_h1: '...', ... };
const en = { hero_h1: '...', ... };
```

⚠️ **Both must be updated** when changing copy — otherwise switching language will reveal the old text.
⚠️ 改文案时**两个都要改**,否则切语言时会露出旧文本。

---

## 📤 Deployment / 部署

**EN** — **GitHub Pages auto-deploys** from the `main` branch root. Whatever you push goes live:

**中文** — **GitHub Pages 自动部署**——`main` 分支根目录直接被构建,推什么发什么:

```powershell
git add .
git commit -m "Update hero copy"
git push
# Live in ~30 seconds / 30 秒后线上更新
```

No build step, pure static hosting. Custom domain (`finditem.is-a.dev`) is provided free by [is-a.dev](https://www.is-a.dev/).
零构建步骤,纯静态托管。自定义域名 (`finditem.is-a.dev`) 由 [is-a.dev](https://www.is-a.dev/) 提供免费子域名。

---

## 🎨 Design Principles / 设计原则

| Principle / 原则 | EN | 中文 |
|---|---|---|
| **Apple-minimal** | Restrained weights (mostly 600 instead of 800), generous whitespace, consistent rhythm | 克制的字重(以 600 为主而非 800),宽松留白,统一节奏 |
| **Visual punch retained** | Full-bleed photos on every section + slow Ken Burns motion | 每区块全屏背景大图 + 缓慢的 Ken Burns 微动 |
| **Smooth motion** | 0.5s theme cross-fade, easing-out panel entry, scroll-triggered reveals | 0.5 秒主题过渡、面板入场缓动、滚动 reveal |
| **Dual-shade accent** | Bright cyan on dark surfaces, deep cyan on light — both readable | 亮青用于深色面,深青用于浅色面,两边都清晰 |
| **Accessible** | Honors `prefers-reduced-motion`, keeps focus rings, HTTPS-everywhere | 尊重 `prefers-reduced-motion`,保留键盘焦点环,全程 HTTPS |

---

## 🗺 Roadmap / 路线图

| Phase / 阶段 | Weeks / 时间 | Goal / 目标 | Status / 状态 |
|---|---|---|---|
| **Phase 1** | Week 1-2 / 第 1-2 周 | MVP prototype · 1 bin, breadboard, basic search + beep / MVP 原型 | ✅ Done / 完成 |
| **Phase 2** | Week 3-4 / 第 3-4 周 | Auth + multi-user · Feishu login, DB, concurrency / 登录 + 多人 | ✅ Done / 完成 |
| **Phase 3** | Week 5-6 / 第 5-6 周 | Production · PCB, 3D case, firmware / 量产:PCB、外壳、固件 | 🚧 In progress / 进行中 |
| **Phase 4** | Week 7-8 / 第 7-8 周 | Deploy · 40 units, parts catalog, go-live / 部署 40 套、录入零件、上线 | 📋 Planned / 计划中 |

---

## 🤝 Credits / 致谢

**An open-source project by [@HarryXin0919](https://github.com/HarryXin0919).**
**开源项目,由 [@HarryXin0919](https://github.com/HarryXin0919) 开发维护。**

---

<sub>© 2026 Harry Xin · Built with HTML, CSS, JavaScript, and a lot of M3 screws / 建于代码与无数 M3 螺丝。</sub>
