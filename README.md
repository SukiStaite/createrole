<div align="center">

# 搭角色（AIRA · 捏角色工具）

**以林晴祈（祈宝）的口吻，从零问出一个角色的血肉、骨骼、欲望与灵魂，最后组装成一份可直接投入 RP 的完整档案。**

`V4.2.0` · 离线单文件 · 零依赖 · 纯前端

**V4.2 三批次全量**：16 项必须功能 · 22 项应该添加 · 22 项沉浸感 · 记忆存档系统（B手动/A自动/C面板）· 119 项自动化测试全绿 · 10 个已知 bug 全修

[在线使用](https://sukistaite.github.io/createrole/) · [离线版下载](https://github.com/SukiStaite/createrole/raw/main/搭角色V4.2.0.html)

</div>

---

## ✨ 这是什么

一个**浏览器里跑的角色创建器**。它像一位耐心的搭档，逐题问你关于角色的方方面面——外貌、性格、日常、身体数据、性偏好、发情期档案、好感度、称呼、微信、作息……答完自动组装成一份**零留空、可直接开 RP 的完整档案**，并完成世界观检查与体系登记。

精细度对标林晴祈档案，**生成即登记**：发情期 / 初夜 / 好感度 / 身体数据 / 称呼 / 微信 / 作息自动入册。

## 🚀 快速开始

```bash
# 直接用（无需安装、无需联网、无需服务器）
# 双击 dist/搭角色V4.2.0.html 即可，或直接访问上面的在线地址

# 本地起服务（可选）
python3 -m http.server 8000
# 打开 http://localhost:8000
```

## 🧩 核心特性

- **档案零留空**：档案模板与题库抽取完全对齐，所有字段强制纳入提问计划，默认流程下档案不再出现「—」占位
- **分层随机抽题**：题库 630 题按体量配额分层随机抽取，覆盖均衡，支持「重新抽取题库」
- **14 条世界观检查自动校验**：年龄≥18、AL 系数区间、姓名/昵称查重、初夜状态、第一梯队关系线、登记信息齐备等自动判定，不通过即拦截
- **自动存档**：localStorage 防抖自动保存，误刷新可「继续上次」
- **一键导出**：档案复制 markdown / 下载 `.md`
- **可问性过滤**：SFW 向自动隐藏并跳过 NSFW 与双性配置题；DLC9=否 跳过双性配置；多形态追加形态切换题
- **必答强制**：体系登记 / 补完层及档案核心题必答
- **移动端适配**：触摸目标 ≥44px、safe-area、响应式布局
- **离线单文件**：构建产物自包含，无外部依赖

## 📚 题库结构（630 题）

| 层 | 数量 | 题号 | 说明 |
|---|---|---|---|
| SFW | 250 | 1–250 | 日常向 |
| NSFW | 215 | 251–465 | 成人向（SFW 向自动隐藏） |
| DLC | 100 | 466–565 | 世界观 / 种族 / 能力 |
| 体系登记 | 30 | 566–595 | 必答 |
| 祈宝级补完 | 35 | 596–630 | 必答 |

## 🗂️ 项目结构

```
createrole/
├── index.html            # 入口（单文件离线版即完整应用）
├── config.js             # 常量配置（版本、体量映射、选项）
├── schema.js             # 档案模板 / 核心题 / 检查清单 / 登记清单
├── engine.js             # 核心逻辑（抽题、档案组装、校验、markdown）
├── storage.js            # localStorage 持久化 + 迁移
├── app.js                # UI 层（六步流程）
├── data/questions.js     # 题库（630 题）
├── style.css             # 样式
├── build.js              # 打包脚本（node build.js）
├── test/                 # 自动化测试
└── .github/workflows/    # GitHub Pages 自动部署
```

## 🛠️ 技术栈

- **纯前端**：HTML + CSS + 原生 JavaScript（无框架、无构建依赖）
- **逻辑层**：UMD 风格纯逻辑模块（config/schema/engine/storage），node 可直接 `require` 测试
- **测试**：node 内置 `assert`（单元测试）+ jsdom（UI 冒烟 + 打包版冒烟），共 71 项
- **部署**：GitHub Pages（`.github/workflows/pages.yml` 自动构建）

## 🧪 开发与测试

```bash
# 单元测试（引擎逻辑 35 项）
node test/engine.test.js

# UI 冒烟测试（26 项，需 jsdom）
node test/ui.smoke.js

# 打包单文件
node build.js

# 打包版冒烟（10 项）
node test/bundle.smoke.js
```

## 📦 部署与更新

- 推送到 `main` 分支 → GitHub Actions 自动构建部署到 `https://sukistaite.github.io/createrole/`
- 改代码后重新 `node build.js`，上传新 `index.html` 即可，URL 不变
- 版本号在 `config.js` 的 `VERSION`；存档 key 版本化（`aira_dajuese_v41`），升级不互相污染

## 📄 许可

本项目为虚构沙盒用途，仅用于「只有一个男生的世界」世界观内的角色创建。**个人使用，请勿商用。**
