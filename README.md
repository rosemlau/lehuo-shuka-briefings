# 🍃 乐活书咖·每日简报 — 使用手册

> 版本：v1.0 | 更新日期：2026-03-25

---

## 📁 文件结构

```
daily-briefing/
├── generate_briefing.py      # 第一步：生成简报 HTML
├── publish_to_github.py      # 第二步：推送到 GitHub Pages（在线预览）
├── screenshot_edge.js        # 备用：截图为 PNG 长图
├── README.md                 # 本说明文档
└── output/                   # 生成的简报文件存放目录
```

---

## 🚀 每日使用流程

### 方式一：自动化（推荐）
每天早上 9 点，WorkBuddy 自动执行，无需手动操作。  
自动完成：生成 HTML → 推送 → 生成链接。

### 方式二：手动执行

**第一步：生成简报**
```powershell
cd C:\Users\Administrator\WorkBuddy\Claw\daily-briefing
& "C:\Users\Administrator\.workbuddy\binaries\python\versions\3.13.12\python.exe" generate_briefing.py
```
生成文件：`output/briefing_YYYYMMDD.html`

**第二步：发布到 GitHub Pages（在线预览链接）**
```powershell
& "C:\Users\Administrator\.workbuddy\binaries\python\versions\3.13.12\python.exe" publish_to_github.py
```
脚本自动找到今日简报 → 推送 → 输出在线链接。

**第二步（备用）：截图为长图**
```powershell
$env:NODE_PATH="C:\Users\Administrator\AppData\Roaming\npm\node_modules"
node screenshot_edge.js
```
生成文件：`briefing_screenshot.png`

---

## 🔗 在线访问地址

| 链接 | 说明 |
|------|------|
| https://rosemlau.github.io/lehuo-shuka-briefings/ | 简报总目录 |
| https://rosemlau.github.io/lehuo-shuka-briefings/briefings/YYYY/MM/briefing_YYYYMMDD.html | 当日简报直链 |

> 📌 推送后约 **1-2 分钟** 生效

---

## ⚙️ 配置信息

### GitHub
- **账号**：rosemlau（rosemlau@163.com）
- **仓库**：https://github.com/rosemlau/lehuo-shuka-briefings
- **本地仓库**：`C:\Users\Administrator\WorkBuddy\lehuo-briefings-repo`
- **Token**：存储在本机 `daily-briefing/.env` 文件中（不公开）

### 阿里云 OSS（备用存储）
- **Bucket**：lehuo-shuka（华东1·杭州，公共读）
- **Endpoint**：oss-cn-hangzhou.aliyuncs.com
- **AccessKeyId**：LTAI5tSCHMRTd6m2sr9Exwse
- **说明**：OSS 默认域名访问 HTML 会强制下载（系统安全策略），需绑定自定义域名才能在线预览。当前主力方案为 GitHub Pages。

---

## 📋 简报内容模块

| 模块 | 内容 | 数据来源 |
|------|------|----------|
| 🌤️ 深圳天气 | 实时气温、湿度、体感温度、穿衣建议、3天预报 | wttr.in 免费 API |
| 📅 今日安排 | 日程提醒 | 预留（手动填写） |
| 🌍 国际热点 | 今日最新国际新闻 5 条 | DuckDuckGo / Serper |
| 🤖 AI 资讯 | 人工智能最新动态 5 条 | DuckDuckGo / Serper |
| 📱 短视频热点 | 抖音/小红书热点话题 5 条 | DuckDuckGo / Serper |

> 💡 如需提升新闻精准度，可在 `generate_briefing.py` 中配置 `SERPER_API_KEY`  
> 注册地址：https://serper.dev（每月 2500 次免费）

---

## 🎨 视觉风格

- **背景**：深色太空蓝（#0a0e1a）
- **主题色**：青蓝色 #00d4ff（天气/国际）、绿色 #22c55e（日程）、紫色 #b366ff（AI）、粉色 #ff6b9d（短视频）
- **字体**：Noto Sans SC + PingFang SC
- **风格**：科技感暗色主题，适合截图分享

---

## 🔧 常见问题

**Q：推送后链接打不开？**  
A：等待 1-2 分钟，GitHub Pages 有部署延迟。

**Q：新闻内容不准确？**  
A：配置 Serper API Key 可显著提升搜索质量。

**Q：截图脚本报错？**  
A：确保 Edge 浏览器已安装，且已全局安装 puppeteer-core。

**Q：GitHub Token 过期怎么办？**  
A：访问 https://github.com/settings/tokens 重新生成，更新 `publish_to_github.py` 中的 `GITHUB_TOKEN` 变量。

---

*乐活书咖 · 修身齐家乐活 · 每日更新*
