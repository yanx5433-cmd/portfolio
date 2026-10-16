# 求职作品集 · 薛彦欣

面向 **AI 应用 / 大模型应用工程师** 岗位的个人作品集。三种形态，内容同源：

| 形态 | 位置 | 用途 |
| --- | --- | --- |
| 在线网站 | [`index.html`](index.html) → GitHub Pages | 直接发链接给面试官，手机可看 |
| 可投递 PDF | [`portfolio.pdf`](portfolio.pdf) | 随简历附件投递、打印 |
| 源码 | [`index.html`](index.html) + [`portfolio.tex`](portfolio.tex) | 自证没有用模板站 |

> 页面与 PDF 里的所有数字均来自对应仓库实测（pytest 收集条目数、路由装饰器计数、`wc -l`），
> 未沿用简历概数。演示数据为脚本合成，与任何真实生产环境无关。

## 主打作品

**OpsPilot —— 巡检与故障诊断智能体** · [yanx5433-cmd/opspilot-agent](https://github.com/yanx5433-cmd/opspilot-agent)

一句话：一个不配任何 API Key 也能完整运行的工具调用型 Agent 运行时，
带 5 道护栏闸门、可回放 JSONL 轨迹、证据引用闸门（幻觉可计量）与离线评测集。

作品集里没有把它写成"我做了个聊天机器人"，而是写清了三件更能说明问题的事：
规则/LLM 双引擎的降级路径、为什么裁掉无证据句子而不是标黄、以及**已知局限**。

## 本地查看

网站是单个 HTML 文件，无构建步骤、无外部字体与 CDN 依赖：

```bash
# 直接双击打开，或
python -m http.server 8000     # → http://127.0.0.1:8000
```

## 重新生成 PDF

需要 XeLaTeX（MiKTeX / TeX Live）与中文字体（SimSun / SimHei / Microsoft YaHei）：

```bash
xelatex portfolio.tex
xelatex portfolio.tex     # 两遍，交叉引用与页码才稳定
```

`portfolio.tex` 顶部有一组 `\newcommand` 指标宏（`\Ntests`、`\Neval`、`\Ncases`），
仓库数字变化时只改这几行即可与网站保持一致。

## 设计说明

- **控制室 / 遥测质感**：首屏右侧不是装饰动图，而是 OpsPilot 本机真实跑出来的一条
  `opspilot.trace.v1` 轨迹（`task_6cb5a3f50c`），逐行进场回放。
- **不用 web 字体**：国内网络下第三方字体经常拖慢首屏甚至加载失败，
  所以字体性格靠"宋体标题 + 黑体正文 + 等宽数字"的对比与字号阶梯做，零外部请求。
- **渐进增强**：进场动画只在 JS 真正执行时才隐藏元素（`html.js` 前缀），
  JS 被禁或报错时内容完整可读；同时尊重 `prefers-reduced-motion`。
- **有打印样式**：`@media print` 下自动转白底黑字，浏览器直接打印也能得到一份能看的册子。

## 许可

内容（文字与版式）与代码同样以 MIT 许可发布。
