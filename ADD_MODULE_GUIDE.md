# 新增模块页面步骤说明

本站点所有功能模块（工具、游戏、笔记）遵循同一套约定：**一个模块 = 一个独立文件夹 + 一个 HTML 页面**，并在主页卡片墙中注册入口。全程无需构建，按以下 6 步操作即可上线一个新模块。

## 第 1 步：创建模块文件夹

在仓库根目录新建文件夹，命名使用小写英文加连字符：

```
my-tool/          # 例如：word-counter/、pomodoro-timer/
```

## 第 2 步：编写模块页面

- 页面命名为 `文件夹名.html`（如 `my-tool/my-tool.html`），或直接用 `index.html`（则链接可简写为 `my-tool/`）；
- 如有 JS/CSS，放入模块内的 `assets/` 子目录，例如 `guangzhou-loan-calc/assets/app.js`；
- 保持单页自包含或仅相对路径引用，**不要引用仓库外的资源**。

最快的做法：复制现有模块（如 `lipid-guide/`）作为模板，再修改内容。页面 `<head>` 建议保留：

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

## 第 3 步：在主页注册卡片入口

编辑 `index.html`，在 `<div class="card-grid">` 内新增一个卡片（可插在 "More Coming Soon" 卡片之前）：

```html
<a class="card" href="./my-tool/my-tool.html">
  <div class="card-icon blue">&#128295;</div>
  <h3>模块标题</h3>
  <p>一两句话说明模块的功能与亮点。</p>
  <div class="card-arrow">进入工具 &#8594;</div>
</a>
```

三个要点：

1. **`href`**：使用相对路径指向第 2 步的页面；
2. **图标颜色**：`card-icon` 支持 `blue` / `purple` / `green` 三种底色，用 `&#xxxxx;` HTML 实体作图标字符（如 &#127922; 游戏、&#128202; 工具、&#128218; 笔记）；
3. **箭头文案**：按模块类型调整，如「进入工具 →」「开始游戏 →」「阅读笔记 →」。

无需处理移动端适配——主页卡片栅格（`auto-fill`）自动换行；模块页自身建议保留 viewport meta。

## 第 4 步：本地预览验证

```bash
python -m http.server 8000
```

访问 <http://localhost:8000>，逐项确认：

- [ ] 主页新卡片显示正常，点击能跳转到模块页；
- [ ] 模块页样式、脚本加载正常（相对路径无误）；
- [ ] 从模块页返回主页的路径（如有）可用；
- [ ] 手机宽度下（浏览器开发者工具模拟）布局不乱。

## 第 5 步：提交发布

```bash
git add .
git commit -m "feat: 新增 xxx 模块"
git push
```

推送 `main` 后 GitHub Pages 自动发布，1–2 分钟后访问 `https://yuzhou2021.github.io/my-tool/my-tool.html` 验证线上效果。

## 第 6 步（可选）：维护入口列表

同步更新 `README.md` 的「现有模块」表格，保持文档与站点一致。

## 常见问题

| 问题 | 原因与处理 |
|------|-----------|
| 线上 404 | 路径大小写不一致或文件未推送。GitHub Pages 大小写敏感，`href` 与实际文件名必须完全一致 |
| 样式/脚本不生效 | 使用了绝对路径（如 `/assets/app.js`）。改成相对路径 `./assets/app.js` |
| 卡片图标显示为方块 | HTML 实体编号有误，确认格式为 `&#128295;` 且以分号结尾 |
| 本地打开正常、线上异常 | 多为本地直接双击打开掩盖了相对路径问题，预览请用本地服务器 |
