# make-knowledge-cards

`make-knowledge-cards` 是一个 Codex Skill，可将文章整理成简洁、忠于原文的知识卡片，帮助读者抓住值得记忆的要点。它优先提取重要且彼此独立的知识，不重复同一内容，也不补入原文没有的信息。

## 主要功能

- 接受用户直接粘贴的文章，或本地 `.md`、`.markdown`、`.txt` 文件。
- 内容足够时生成 5～8 张卡片；原文支持的独立知识点较少时，生成更少的卡片，不为凑数扩写。
- 每张卡片包含标题、核心知识、简明解释，以及原文中的例子或可由原文回答的自测问题。
- 保留原文中的限定和不确定性，并默认使用原文语言。

当前不支持网页抓取、PDF、Anki 导出或图形界面。

## 安装方法

本项目是 Skill 文件，不需要额外的运行时依赖或包管理器。将 Skill 目录复制到 Codex 的技能目录即可。在项目根目录运行：

```sh
skill_root="${CODEX_HOME:-$HOME/.codex}/skills"
mkdir -p "$skill_root"
cp -R skills/make-knowledge-cards "$skill_root/"
```

如果目标目录中已经存在同名 Skill，请先处理旧目录，避免覆盖时产生混合文件。

## 使用方法

在 Codex 中调用 `$make-knowledge-cards`，并粘贴文章内容；也可以在请求中提供本地 Markdown 或 TXT 文件，例如：

```text
$make-knowledge-cards
请把这篇文章整理成知识卡片：
[在这里粘贴文章]
```

如果输入是 URL、PDF 或空内容，Skill 会请用户改为粘贴文章，或提供支持的本地文本文件；它不会自行抓取网页或补充外部资料。

## 输入与输出示例

**输入：**

> 番茄工作法将工作分成若干专注时段。常见做法是专注 25 分钟后休息 5 分钟；完成四个专注时段后，休息时间可以更长。休息期间应暂时离开当前任务。记录每个时段有助于回顾时间花在哪里，并发现常见干扰。

**输出示例（节选）：**

### 1. 专注时段与短休息
- **核心知识：** 常见安排是专注 25 分钟，随后休息 5 分钟。
- **简明解释：** 工作与短暂休息交替进行，形成清晰的专注节奏。
- **例子或自测：** 一个常见专注时段后休息多久？

### 2. 记录时段用于回顾
- **核心知识：** 记录每个时段有助于回顾时间分配并发现常见干扰。
- **简明解释：** 记录让工作过程可回看，便于识别时间去向和干扰来源。
- **例子或自测：** 记录时段可以帮助发现什么？

完整输出的卡片数量取决于文章中可提取的独立重要知识点。

## 推荐阅读

以下博客涵盖科技资讯、开源实践和编程思考，供阅读与学习参考。

| 博客 | 内容简介 | GitHub 仓库 |
| --- | --- | --- |
| [阮一峰的网络日志](https://www.ruanyifeng.com/blog/) | 中文科技资讯、编程知识与实用工具推荐；科技爱好者周刊适合拓展阅读视野。 | [ruanyf/weekly](https://github.com/ruanyf/weekly)（周刊仓库） |
| [DIYgod](https://diygod.cc/) | 开源项目、个人建站、NAS 实践与生活记录。 | [DIYgod/diygod.me](https://github.com/DIYgod/diygod.me) |
| [Anthony Fu](https://antfu.me/) | 前端工具、开源实践与开发思考，适合关注 Vue、Vite 等生态的读者。 | [antfu/antfu.me](https://github.com/antfu/antfu.me) |
| [Overreacted](https://overreacted.io/) | Dan Abramov 的英文博客，分享 React、JavaScript 与编程思路。 | [gaearon/overreacted.io](https://github.com/gaearon/overreacted.io) |

以上为原站链接与简要介绍，文章版权归原作者所有。使用本 Skill 整理阅读笔记时，请自行提供有权使用的文章文本，并在分享笔记时注明作者和原文链接；本 Skill 不会自动抓取这些网站。
