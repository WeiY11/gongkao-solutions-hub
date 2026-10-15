# 公考解题导航

行测与申论交互式解题页的目录站。每个解题页是一个自包含的 HTML（图片以 base64 内嵌），不依赖构建工具、不依赖外部资源，可直接用浏览器打开。

在线地址：<https://weiy11.github.io/gongkao-solutions-hub/>

## 目录结构

```
index.html          导航页（目录数据内嵌在 SOLUTIONS 数组中）
solutions/          各个解题页 HTML
```

## 新增一个解题页

1. 把解题 HTML 放进 `solutions/`，文件名用 ASCII 短横线命名，例如 `ziliao-fenxi-20ti-data-highlight.html`。
2. 在文件 `<body>` 后保留返回条，使子页能回到导航：

   ```html
   <div class="hubbar"><a href="../index.html">← 返回解题导航</a><span>/</span><span>页面标题</span></div>
   ```

3. 在 `index.html` 的 `SOLUTIONS` 数组里追加一条：

   ```js
   {
     title:"资料分析 · 20题原文数据高亮",
     module:"资料分析",            // 资料分析 / 数量关系 / 判断推理 / 言语理解与表达 / 常识判断 / 申论
     file:"solutions/ziliao-fenxi-20ti-data-highlight.html",
     desc:"一句话说明这页能做什么。",
     count:"20 题 · 4 篇资料",
     tags:["高亮解题数据","练习模式","计时器"],
     date:"2026-10-15"
   }
   ```

4. 提交并推送到 `main`，GitHub Pages 会自动重新发布。

新模块名不在 `MODULE_ORDER` 里也会自动成组显示，只是排在已知模块之后；需要固定顺序时把它加进 `MODULE_ORDER`。

## 本地查看

直接双击 `index.html` 即可，无需服务器（目录数据是内联的，不走 fetch）。

## 各页面进度存储

每个解题页把自己作答进度、计时与视图状态保存在浏览器 `localStorage`，键名在各页脚本顶部的 `sessionKey` 常量里。换浏览器或清缓存后进度不保留。
