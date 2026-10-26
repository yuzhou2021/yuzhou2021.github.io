# yuzhou2021.github.io

个人 GitHub Pages 站点：深色主题卡片式静态主页，汇集自制的实用工具、小游戏与健康知识笔记。

**在线访问**：<https://yuzhou2021.github.io/>

纯静态 HTML/CSS/JS，无框架、无构建流程，改完推送即发布。

## 目录结构

```
yuzhou2021.github.io/
├── index.html                        # 主页（卡片导航入口）
├── guangzhou-loan-calc/              # 模块：广州购房贷款计算
│   ├── guangzhou-loan-calc.html
│   └── assets/app.js
├── games/
│   └── looptap.html                  # 模块：LoopTap 小游戏
├── lipid-guide/
│   └── lipid-guide.html              # 模块：血脂管理指南笔记
└── README.md
```

> `index.html.txt` 为早期测试遗留文件，`.trae-html-share-packages/` 为 Trae 生成的分享包，均不参与站点功能，可忽略。

## 现有模块

| 模块 | 路径 | 说明 |
|------|------|------|
| 广州购房贷款计算 | `guangzhou-loan-calc/guangzhou-loan-calc.html` | 不同总价、首付比例、公积金额度下的还款方案，支持等额本息/等额本金对比 |
| LoopTap | `games/looptap.html` | HTML5 小游戏，点击数字使它们相加到 100 |
| 血脂管理指南 | `lipid-guide/lipid-guide.html` | 《中国血脂管理指南》实用笔记：化验单解读、用药与饮食运动建议 |

## 本地预览

任选其一：

- 直接双击打开 `index.html`（无跨域需求的模块均可直接打开）；
- 起本地服务器（推荐，路径行为与线上一致）：

```bash
# Python
python -m http.server 8000
# 或 Node
npx serve .
```

浏览器访问 <http://localhost:8000>。

## 发布

推送 `main` 分支后，GitHub Pages 自动构建并发布，一般 1–2 分钟内生效：

```bash
git add .
git commit -m "feat: xxx"
git push
```

## 新增模块

每个模块是一个独立子文件夹 + 一个 HTML 页面，并在主页 `index.html` 加一张卡片入口。详细步骤见 [ADD_MODULE_GUIDE.md](ADD_MODULE_GUIDE.md)。
