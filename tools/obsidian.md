# 半年来用 Obsidian

今天简单分享一下我这半年来用 Obsidian 的心得。不是官方文档，一个学生的主观体验，但步骤按能跟着做完来写。

默认你会登录 GitHub，电脑上有自己的 agent（Claude Code、Codex 之类）。

下载：[https://obsidian.md](https://obsidian.md) 或 [GitHub Releases](https://github.com/obsidianmd/obsidian-releases)。电脑、安卓、iOS 都有。主题和基础配置也可以丢给 agent 装：[kepano/obsidian-skills](https://github.com/kepano/obsidian-skills)。

---

## 为什么用它，不继续待在 VSCode 里写 md

VSCode 写 Markdown 能用，但预览要再开一栏：左边 `# 标题`、`**加粗**`，右边才是排好的样子。改一个字，眼睛两边跳。

Obsidian 默认 **实时预览**：打 `## 标题` 回车，屏幕上就是标题。加粗、列表、图片、链接，写的时候就是读的时候。要抠语法再切源码。

另外两件事 VSCode 也能凑合，但没这么顺手：

- 库（vault）就是一个普通文件夹，全是 `.md` 和附件。资源管理器能打开，Git 能同步，VSCode 也能改同一批文件。
- `[[另一篇笔记]]` 双向链接。被提到的那篇右边会列出「谁链到了我」。

写代码我还是回 VSCode。记笔记、读 PDF、看链接网，用 Obsidian。
![[Pasted image 20260911162827.png]]
![[Pasted image 20260911162843.png]]

---

## 从零开始（先别装第三方插件）


### 安装、建库

第一次打开：创建新库，或打开已有文件夹。选一个本地目录，比如桌面上的 `notes`。这个文件夹就是全部笔记、图片、PDF、插件配置。没有「账号里的云端库」（官方 Sync 要钱，我没用）。

界面三块：左文件列表，中编辑，右反向链接/大纲。左下角齿轮是设置。

![[Pasted image 20260911163008.png]]

### 三种模式

| 模式 | 干什么 |
| --- | --- |
| 源码 | 纯 Markdown，改表格、复杂链接时用 |
| 实时预览 | 默认，日常写 |
| 阅读 | 只看不改 |

右上角切换。日常就用实时预览。

![[Pasted image 20260911163226.png]]


- **关系图谱**：挺有意思的：

![[Pasted image 20260911163433.png]]



### 核心插件（官方自带，不用关安全模式）

设置 → 核心插件。保持默认即可

---

## 主题：Minimal

设置 → 外观 → 主题 → 管理，搜 `Minimal`，安装并启用。作者 kepano。干净，长时间读不累。我从一开始就用这个，没换过。暗色亮色都行。

![[Pasted image 20260911163524.png]]

---

## 四个第三方插件

设置 → 第三方插件 → **关闭安全模式** → 浏览 → 搜索 → 安装完还要再点 **启用**。只装不启用等于没装。

![[Pasted image 20260911163559.png]]

Obsidian 生态很大，GitHub 上自己挖。我天天开的就这四个。

### Claudian

最常用。前提是电脑上已经装着 agent。它把对话放在侧边栏，不用切走当前笔记。

两件事好评：默认带上当前文件，甚至某一行；可以同时开好几个会话。AI 用多了以后，等一个任务跑完才能开下一句，受不了。

![[images/Pasted image 20260911144440.png]]

图里链接了当前这篇，还带了选中的一行。模型、工作量、YOLO 开关自己调。平板上基本用不上，它依赖电脑本地的 agent。

### Git

主要是用来同步笔记的。库不大（主要是 md + 少量图片）就用社区插件 **Obsidian Git**，在 Obsidian 里 commit / pull / push。

1. 先在库文件夹里 `git init`，推到 GitHub（命令行、GitHub Desktop 或让 agent 做都行）
2. 安装并启用 Obsidian Git
3. 设置里打开：启动时 pull、定时 commit-and-sync（比如 10 分钟）

左下角能看到同没同步。平板上也是这个插件，配置写在后面。

![[Pasted image 20260911163823.png]]

### Excalidraw

画框图、流程、手写草稿。电脑鼠标也能画，平板配笔才舒服。新建的是 `.excalidraw.md`，能被库搜索到，也能 `![[xxx]]` 嵌进笔记。

素材在电脑上从素材库导入，再 Git 同步到平板。别在平板上下完再加，后面写。



![[Pasted image 20260911164422.png]]

### PDF++

电脑上看 PDF：高亮、下划线，高亮能复制成带位置的链接贴回笔记，点一下跳回那一页。文件就在库里，Git 管得住。

平板上手写不是在 Obsidian 里直接画，装 Handwritten Notes，打开 PDF 点钢笔会跳到 Xodo，存完切回来。后面单独写。

![[Pasted image 20260911164217.png]]

---

## 知识库怎么搭：卡帕西那篇 LLM Wiki

插件解决的是「在 Obsidian 里怎么写、怎么画」。库本身怎么长，我是照着卡帕西那篇 **LLM Wiki** 搭的。原文可以直接复制给自己的 agent：

```text
# LLM Wiki

A pattern for building personal knowledge bases using LLMs.

This is an idea file, it is designed to be copy pasted to your own LLM Agent (e.g. OpenAI Codex, Claude Code, OpenCode / Pi, or etc.). Its goal is to communicate the high level idea, but your agent will build out the specifics in collaboration with you.

## The core idea

Most people's experience with LLMs and documents looks like RAG: you upload a collection of files, the LLM retrieves relevant chunks at query time, and generates an answer. This works, but the LLM is rediscovering knowledge from scratch on every question. There's no accumulation. Ask a subtle question that requires synthesizing five documents, and the LLM has to find and piece together the relevant fragments every time. Nothing is built up. NotebookLM, ChatGPT file uploads, and most RAG systems work this way.

The idea here is different. Instead of just retrieving from raw documents at query time, the LLM **incrementally builds and maintains a persistent wiki** — a structured, interlinked collection of markdown files that sits between you and the raw sources. When you add a new source, the LLM doesn't just index it for later retrieval. It reads it, extracts the key information, and integrates it into the existing wiki — updating entity pages, revising topic summaries, noting where new data contradicts old claims, strengthening or challenging the evolving synthesis. The knowledge is compiled once and then _kept current_, not re-derived on every query.

This is the key difference: **the wiki is a persistent, compounding artifact.** The cross-references are already there. The contradictions have already been flagged. The synthesis already reflects everything you've read. The wiki keeps getting richer with every source you add and every question you ask.

You never (or rarely) write the wiki yourself — the LLM writes and maintains all of it. You're in charge of sourcing, exploration, and asking the right questions. The LLM does all the grunt work — the summarizing, cross-referencing, filing, and bookkeeping that makes a knowledge base actually useful over time. In practice, I have the LLM agent open on one side and Obsidian open on the other. The LLM makes edits based on our conversation, and I browse the results in real time — following links, checking the graph view, reading the updated pages. Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase.

This can apply to a lot of different contexts. A few examples:

- **Personal**: tracking your own goals, health, psychology, self-improvement — filing journal entries, articles, podcast notes, and building up a structured picture of yourself over time.
- **Research**: going deep on a topic over weeks or months — reading papers, articles, reports, and incrementally building a comprehensive wiki with an evolving thesis.
- **Reading a book**: filing each chapter as you go, building out pages for characters, themes, plot threads, and how they connect. By the end you have a rich companion wiki. Think of fan wikis like Tolkien Gateway — thousands of interlinked pages covering characters, places, events, languages, built by a community of volunteers over years. You could build something like that personally as you read, with the LLM doing all the cross-referencing and maintenance.
- **Business/team**: an internal wiki maintained by LLMs, fed by Slack threads, meeting transcripts, project documents, customer calls. Possibly with humans in the loop reviewing updates. The wiki stays current because the LLM does the maintenance that no one on the team wants to do.
- **Competitive analysis, due diligence, trip planning, course notes, hobby deep-dives** — anything where you're accumulating knowledge over time and want it organized rather than scattered.

## Architecture

There are three layers:

**Raw sources** — your curated collection of source documents. Articles, papers, images, data files. These are immutable — the LLM reads from them but never modifies them. This is your source of truth.

**The wiki** — a directory of LLM-generated markdown files. Summaries, entity pages, concept pages, comparisons, an overview, a synthesis. The LLM owns this layer entirely. It creates pages, updates them when new sources arrive, maintains cross-references, and keeps everything consistent. You read it; the LLM writes it.

**The schema** — a document (e.g. CLAUDE.md for Claude Code or AGENTS.md for Codex) that tells the LLM how the wiki is structured, what the conventions are, and what workflows to follow when ingesting sources, answering questions, or maintaining the wiki. This is the key configuration file — it's what makes the LLM a disciplined wiki maintainer rather than a generic chatbot. You and the LLM co-evolve this over time as you figure out what works for your domain.

## Operations

**Ingest.** You drop a new source into the raw collection and tell the LLM to process it. An example flow: the LLM reads the source, discusses key takeaways with you, writes a summary page in the wiki, updates the index, updates relevant entity and concept pages across the wiki, and appends an entry to the log. A single source might touch 10-15 wiki pages. Personally I prefer to ingest sources one at a time and stay involved — I read the summaries, check the updates, and guide the LLM on what to emphasize. But you could also batch-ingest many sources at once with less supervision. It's up to you to develop the workflow that fits your style and document it in the schema for future sessions.

**Query.** You ask questions against the wiki. The LLM searches for relevant pages, reads them, and synthesizes an answer with citations. Answers can take different forms depending on the question — a markdown page, a comparison table, a slide deck (Marp), a chart (matplotlib), a canvas. The important insight: **good answers can be filed back into the wiki as new pages.** A comparison you asked for, an analysis, a connection you discovered — these are valuable and shouldn't disappear into chat history. This way your explorations compound in the knowledge base just like ingested sources do.

**Lint.** Periodically, ask the LLM to health-check the wiki. Look for: contradictions between pages, stale claims that newer sources have superseded, orphan pages with no inbound links, important concepts mentioned but lacking their own page, missing cross-references, data gaps that could be filled with a web search. The LLM is good at suggesting new questions to investigate and new sources to look for. This keeps the wiki healthy as it grows.

## Indexing and logging

Two special files help the LLM (and you) navigate the wiki as it grows. They serve different purposes:

**index.md** is content-oriented. It's a catalog of everything in the wiki — each page listed with a link, a one-line summary, and optionally metadata like date or source count. Organized by category (entities, concepts, sources, etc.). The LLM updates it on every ingest. When answering a query, the LLM reads the index first to find relevant pages, then drills into them. This works surprisingly well at moderate scale (~100 sources, ~hundreds of pages) and avoids the need for embedding-based RAG infrastructure.

**log.md** is chronological. It's an append-only record of what happened and when — ingests, queries, lint passes. A useful tip: if each entry starts with a consistent prefix (e.g. `## [2026-04-02] ingest | Article Title`), the log becomes parseable with simple unix tools — `grep "^## " log.md | tail -5` gives you the last 5 entries. The log gives you a timeline of the wiki's evolution and helps the LLM understand what's been done recently.

## Optional: CLI tools

At some point you may want to build small tools that help the LLM operate on the wiki more efficiently. A search engine over the wiki pages is the most obvious one — at small scale the index file is enough, but as the wiki grows you want proper search. [qmd is a good option: it's a local search engine for markdown files with hybrid BM25/vector search and LLM re-ranking, all on-device. It has both a CLI (so the LLM can shell out to it) and an MCP server (so the LLM can use it as a native tool). You could also build something simpler yourself — the LLM can help you vibe-code a naive search script as the need arises.

## Tips and tricks

- **Obsidian Web Clipper** is a browser extension that converts web articles to markdown. Very useful for quickly getting sources into your raw collection.
- **Download images locally.** In Obsidian Settings → Files and links, set "Attachment folder path" to a fixed directory (e.g. `raw/assets/`). Then in Settings → Hotkeys, search for "Download" to find "Download attachments for current file" and bind it to a hotkey (e.g. Ctrl+Shift+D). After clipping an article, hit the hotkey and all images get downloaded to local disk. This is optional but useful — it lets the LLM view and reference images directly instead of relying on URLs that may break. Note that LLMs can't natively read markdown with inline images in one pass — the workaround is to have the LLM read the text first, then view some or all of the referenced images separately to gain additional context. It's a bit clunky but works well enough.
- **Obsidian's graph view** is the best way to see the shape of your wiki — what's connected to what, which pages are hubs, which are orphans.
- **Marp** is a markdown-based slide deck format. Obsidian has a plugin for it. Useful for generating presentations directly from wiki content.
- **Dataview** is an Obsidian plugin that runs queries over page frontmatter. If your LLM adds YAML frontmatter to wiki pages (tags, dates, source counts), Dataview can generate dynamic tables and lists.
- The wiki is just a git repo of markdown files. You get version history, branching, and collaboration for free.

## Why this works

The tedious part of maintaining a knowledge base is not the reading or the thinking — it's the bookkeeping. Updating cross-references, keeping summaries current, noting when new data contradicts old claims, maintaining consistency across dozens of pages. Humans abandon wikis because the maintenance burden grows faster than the value. LLMs don't get bored, don't forget to update a cross-reference, and can touch 15 files in one pass. The wiki stays maintained because the cost of maintenance is near zero.

The human's job is to curate sources, direct the analysis, ask good questions, and think about what it all means. The LLM's job is everything else.

The idea is related in spirit to Vannevar Bush's Memex (1945) — a personal, curated knowledge store with associative trails between documents. Bush's vision was closer to this than to what the web became: private, actively curated, with the connections between documents as valuable as the documents themselves. The part he couldn't solve was who does the maintenance. The LLM handles that.

## Note

This document is intentionally abstract. It describes the idea, not a specific implementation. The exact directory structure, the schema conventions, the page formats, the tooling — all of that will depend on your domain, your preferences, and your LLM of choice. Everything mentioned above is optional and modular — pick what's useful, ignore what isn't. For example: your sources might be text-only, so you don't need image handling at all. Your wiki might be small enough that the index file is all you need, no search engine required. You might not care about slide decks and just want markdown pages. You might want a completely different set of output formats. The right way to use this is to share it with your LLM agent and work together to instantiate a version that fits your needs. The document's only job is to communicate the pattern. Your LLM can figure out the rest.
```

我自己就是一边开 Obsidian 点链接、看图谱，一边用 Claudian 或终端里的 agent 改 `wiki/`。写代码仍回 VSCode。两边打开的可以是同一个文件夹。

![[Pasted image 20260911164558.png]]

---

## 电脑写、平板用：Git 同步

电脑：写长笔记、ingest、PDF++ 摘录、跑 Claudian。  
平板：读 PDF、手写、Excalidraw。

桥是 Git，不是网盘。网盘双端一起改，容易出冲突副本。

电脑端用上面的 Obsidian Git，或库根目录手动 `git add / commit / push`。

### 平板：还是 Obsidian 里的 Git 插件

我平板上没有另装 Git 客户端，用的就是 Obsidian 自带社区插件那套 **Git**。电脑、平板同一套操作。库别太大，大了会慢、会卡。

第一次：

1. 平板装 Obsidian
2. GitHub 生成 Personal Access Token，勾 `repo`（私有库没 token 拉不下来）
3. 命令面板搜 `Git: Clone an existing remote repo`，把仓库克隆到平板上一个你找得到的目录，再「打开文件夹作为库」
4. 关掉安全模式。如果 `.obsidian/plugins` 已经在仓库里，Git 插件会在，点启用就行；没有就自己装一次
5. Git 插件设置里填 GitHub 用户名和 token（移动端走 HTTPS，一般不用 SSH）

日常：打开先 pull → 读、标、画 → 离开前 commit-and-sync / push → 回电脑再 pull。

建议打开git插件中的启动自动拉取：

![[Pasted image 20260911164729.png]]

注意：

- 同一篇不要两端同时改。PDF、画板更别
- 拉不下来就先别写
- 电脑和平板不要同时开自动同步去抢同一轮提交，容易乱

---

## 平板 PDF：Handwritten Notes + Xodo 5.0.22

Obsidian 里不能直接在 PDF 上用手写笔批注。流程是：插件把 PDF 交给 Xodo 写（也可以用你平板自带的或者wps等等），存完再回到 Obsidian，批注已经在这份文件上。Git 一推，电脑 PDF++ 也能看到。

1. 安装插件 Handwritten Notes
2. 平板安装 **Xodo Docs 5.0.22 旧版**（不要装新版）
3. Obsidian 打开 PDF，点钢笔图标 → 自动跳 Xodo 手写；保存后切回 Obsidian，批注保存完成

Xodo 别装应用商店最新版，会员和广告都多。从 APKMirror 装（国外知名 APK 存档站）：

1. 平板浏览器打开：`apkmirror.com`
2. 搜索包名：`com.xodo.pdf.reader`，找到版本 **5.0.22**
3. 下载 `arm64-v8a` 的 APK（绝大多数安卓平板都是这个 CPU 架构）
4. 下载完成后，在浏览器下载记录点 apk 文件，系统提示：允许此来源的应用，打开权限，安装

APKMirror 网页广告很多，认准蓝色 `Download APK`，不要点绿色 “get it” 广告按钮。

![[Pasted image 20260911164848.png]]

标完回到 Obsidian，用 Git 插件提交。同一份不要电脑和平板同时标，二进制冲突几乎救不回来。

---

## 平板上的 Excalidraw 素材：电脑导入再同步

平板上下载素材再往 Excalidraw 里加，很难。文件选择器经常找不到刚下的东西。电脑上导好，Git 拉过去就行，不用自己建文件夹。

电脑上：

![[Pasted image 20260911165028.png]]

1. 打开任意一张 Excalidraw 画板，右边素材栏点 **浏览素材库**
2. 挑好的下载下来（一般是 `.excalidrawlib`）
3. 素材栏右上角三个点 → **导入**，选刚下的文件
4. Git 插件 commit + push

![[Pasted image 20260911165608.png]]

平板上：Git 插件 pull。打开画板，右边素材栏里已经有了，直接拖出来用。不要再走一遍下载。

素材跟着这个库走。换平板、重装，只要库能拉下来就还在。

---

## 注意事项

### 新开一个 vault，插件不会从另一个库带来

这点最反直觉。VSCode 扩展装在编辑器上，换文件夹还在。Obsidian 的第三方插件、主题、快捷键都在 **当前这个库的 `.obsidian/`** 里。

所以：你新建一个 vault，那边是空的。Claudian、Git、Excalidraw、Minimal 都不会出现。不是软件卸了，是新文件夹里没有那份配置。

怎么办：

- 能一个库用到底就别乱新建。用文件夹分类。
- 真要新库：先关掉 Obsidian，把旧库的 `.obsidian` 整份复制过去。
- 新电脑 / 平板：打开的必须是原来那个文件夹（或 Git 克隆下来的那份），然后 **再关一次安全模式**。插件列表在的话，灰的再点启用。

没有「重装软件，插件跟着账号回来」这回事。只有这个文件夹。


### 其它

- GitHub 单文件 100MB。PDF 只放要反复读的，库太大平板 pull 会痛。
- 先 pull 再写。
- `workspace.json` 以前提交过的，从仓库删掉并忽略，别每次合并窗口布局。
- 同一份 Excalidraw / PDF 不要双端同时改。
- 克隆后插件是灰的：第三方插件页点启用。
