# 百象动效图鉴

同一个 15 秒故事，拍成 100 支世界观完全不同的短片；可按分类筛选、同步时间轴对比，并为任意 AI 编程助手生成中文提示词。

## 直接使用
双击 `index.html` 用浏览器打开即可（需要联网加载 Google Fonts，断网时自动回退到系统中文字体）。

## 目录
- `index.html`：构建好的单文件网页
- `src/kit.js`：绘制引擎（材质、文字特效、分镜、转场、后期采样、`renderAt`）
- `src/styles-1.js` ~ `styles-3.js`：100 种风格的参数与背景（方形、竖屏版使用）
- `src/film-0.js` ~ `film-89995.js`（以及排序用的 `film-9.js`）：100 支专属影片（横屏），每支有自己的主角、镜头和转场
- `src/mg.js`：改编自 mg-styles-15（MIT）的中文提示词数据
- `src/mg.js`：改编自 mg-styles-15（MIT）的中文提示词数据
- `src/mg.js`：改编自 mg-styles-15（MIT）的中文提示词数据
- `src/mg.js`：改编自 mg-styles-15（MIT）的中文提示词数据
- `src/mg.js`：改编自 mg-styles-15（MIT）的中文提示词数据
- `src/mg.js`：改编自 mg-styles-15（MIT）的中文提示词数据
- `src/mg.js`：改编自 mg-styles-15（MIT）的中文提示词数据
- `src/mg.js`：改编自 mg-styles-15（MIT）的中文提示词数据
- `src/mg.js`：改编自 mg-styles-15（MIT）的中文提示词数据
- `src/mg.js`：改编自 mg-styles-15（MIT）的中文提示词数据
- `src/mg.js`：改编自 mg-styles-15（MIT）的中文提示词数据
- `src/gl.js`：逐像素材质层（WebGL 着色器），油彩、金箔、绒毛、粉笔、辉光都在这里
- `src/guard.json`：逐帧测量后生成的文字对比度修复表
- `videos/`：预渲染的 VP9 视频，卡片播放用，保证流畅
- `src/page.html`：页面结构与样式
- `src/app.js`：筛选、预览调度、详情弹层、提示词生成
- `src/build.mjs`：把以上文件拼成 `index.html` 和 `dist/baixiang.html`

## 修改后重新构建
```bash
node --experimental-websocket src/audit.mjs
```
```bash
node src/build.mjs
```
```bash
node --experimental-websocket src/bake.mjs 风格id
```
依次是：重新测量对比度、拼页面、重渲染改动过的风格视频（不写 id 时只补缺失的）。`index.html` 要和 `videos/` 放在一起；视频缺失时卡片会自动改用实时绘制。

## 自检
```bash
node src/qa.mjs 1.8,4.5,8.6,12.4,14.2 sheet
node --experimental-websocket src/e2e.mjs
```
前者把所有风格渲染成接触印相到 `.qa/`，后者用无头 Chrome 跑一遍交互测试。

## 新增一种风格
在任一 `styles-*.js` 末尾加一段 `S({...})`，定义配色、字体和材质；再在 `film-*.js` 里加一段 `Film('id','这支片怎么讲',c=>{...})`，根据 `c.t` 画出每一帧。页面与提示词会自动收录。

## 精选与融合新作

- 展示顺序在 `src/film-9.js`：最好的 10 支在最前，接着是 10 支“融合新作”（`src/styles-4.js` 和 `film-89993.js` ~ `film-89995.js`）。
- 融合新作的动效灵感来自灵感索引里的网站（Three.js Journey、The Book of Shaders、Shadertoy、Magic UI、Aceternity、Uiverse 等），代码全部重新写，其中软糯光线步进用 GPU 着色器逐像素计算。
- 前几轮没有重做的 41 支已从图鉴中剔除，原始源码保存在 `archive/src-100/`，对应视频在 `archive/videos-removed/`。
