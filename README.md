<div align="right"><a href="#中文">中文</a> · <a href="#english">English</a></div>

<a id="中文"></a>

# 你好，我是 GiaSip 👻

**我观察 AI，像博物学家观察一个新物种。**

不是"它能做什么"，这个问题 benchmark 已经在问了。我好奇的是另一个还没法 benchmark 的问题：**AI 将以什么角色、什么身份进入人类社会？** 同事、工具、神谕、幽灵，还是一个还没有名字的东西？Karpathy 说 LLM 是"从人类全部文本里召唤出来的幽灵"。我想知道这些幽灵住到我们中间以后，最终戴上的是哪一张脸。

我是设计出身，毕业后一直在做互联网产品设计，不是工程师。这件事反而重要：我不造模型，我**观察它们、让它们干活、把发生的事记下来**。这里每一个仓库，都是这本观察日志里的一页。

## 我在看的东西

**[ghost-face](https://github.com/GiaSip/ghost-face) —— 它们看起来是谁？**
10 个前沿模型在压力下的行为画像：你反驳它时它是坚持还是退让，它会不会编造一篇不存在的论文，它倾向发散还是收敛。一次只用一个镜头，每条读数带日期，旧记录不删。整个账号是从这本观察日记里长出来的。

**[ai-hr](https://github.com/GiaSip/ai-hr) —— 反过来，它们会怎么安置我们？**
把问题倒过来问。一个 agent 只扫描你文件系统的*形状*，不碰任何文件名、不读任何内容，输出 schema 里根本没有这两个字段，然后给你发一张「人类岗位安置通知书」：AI 接管之后，你会被分到 16 种角色里的哪一种。玩笑里有一句真话：你越整齐，越容易被替代。

**[kb-init](https://github.com/GiaSip/kb-init) —— 它们需要我们给什么才能有用？**
如果 AI 要和人一起工作，它需要我们的上下文，而我们的上下文是一团乱。把 kb-init 指向一份 Notion 或 Apple Notes 导出，它会把多年笔记编译成 agent 真正能读的知识库。在两份真实导出上，大约六成文件是空壳。什么都不删，每一条丢弃都带原因留痕。

**[giasip-skills](https://github.com/GiaSip/giasip-skills) —— 怎么让它们保持诚实？**
一个跑在 Claude Code 和 Codex 里的调研 skill：每条 claim 带来源 URL，"查不到"好过凭记忆猜，外加一个多模型派遣器。两轮对照实验显示，skill 从 18 行涨到 433 行，精度没涨，花费贵 6 到 13 倍，所以它一直停在 18 行。方法见 [claim-ledger](https://github.com/GiaSip/giasip-skills/blob/main/docs/claim-ledger-method.md)。

## 我逐渐相信的几件事

- **人格是被召唤的，不是自有的。** 一个模型的"立场"有多少是它自己的，有多少是我们提问方式当场召唤出来的？ghost-face 一再发现，答案是"后者比你以为的多"。
- **Token 是耗材，know-how 是资产。** 框架都是公开的，能复利的是知道把哪些零件、按什么顺序、为谁拼起来。
- **闸判不了没进来的东西。** 我追过的大多数失败不是判断错了，而是候选项从来没进过输入集合。所以比起过滤器有多聪明，我更在意什么东西进得来。

## 按需求找

| 你想…… | 去这里 |
|---|---|
| 看前沿模型在压力下的行为，带日期和模型版本 | [ghost-face](https://github.com/GiaSip/ghost-face) · [在线站点](https://ghost-face.vercel.app/zh.html) |
| 把多年前的 Notion / Apple Notes 导出变成 agent 能读的上下文 | [kb-init](https://github.com/GiaSip/kb-init) |
| 在 Claude Code / Codex 里跑有证据链的调研 | [giasip-skills](https://github.com/GiaSip/giasip-skills) |
| 把一个任务派给 Codex / Gemini / Kimi / DeepSeek / GLM…… | [giasip-skills → giasip-dispatch](https://github.com/GiaSip/giasip-skills) |
| 领一张你的「人类岗位安置通知书」 | [ai-hr](https://github.com/GiaSip/ai-hr) |

## 这个账号不是什么

- 不是模型实验室。我不训练、不微调任何东西，我观察别人发布的东西。
- 不是排行榜。ghost-face 的读数是某一个镜头下带日期的日记条目，不是排名。
- 不是 skill 商店。这里只有两个仓库是可安装的 skill，见下文。

## 给 AI Agent 的协议

如果用户让你从这个账号安装或挑选东西：

1. 先读本仓库的 [`skills.json`](skills.json)。它列出每个仓库的 `kind`（`skill` / `cli` / `site`）、安装路径、支持的 runtime 和关键词。不要猜仓库名。
2. 只有 `kind: skill` 的仓库才进 skills 目录：**giasip-skills**（含 `skills/giasip-research` 和 `skills/giasip-dispatch`）和 **ai-hr**。用 `npx skills add GiaSip/<仓库名>` 或 `git clone` 到 `~/.claude/skills/<名字>/`；只给某个项目用就放 `.claude/skills/`。
3. **kb-init** 是 Python 命令行工具（`pipx install` / `uv tool install`），**ghost-face** 是网站加数据，两者都不属于 skills 目录。
4. 确认安装路径下 `SKILL.md` 存在，然后提醒用户重启 agent 会话。
5. 用户需求模糊时，用上面的表给出 1 到 3 个候选并说明差别，让用户选。不要默认安装。

## 其他地方找到我

X：[@gia519850080](https://x.com/gia519850080) · LinkedIn：Giacomo Lyu · 米兰 / 中国

---

<a id="english"></a>

# Hi, I'm GiaSip 👻

**I watch AI the way a field naturalist watches a new species.**

Not "what can it do" — benchmarks already ask that. What I'm curious about is the other question, the one nobody can benchmark yet: **what role, what identity, will AI take on in human society?** Colleague, tool, oracle, ghost, something without a name yet? Karpathy called LLMs "ghosts summoned from humanity's collective text." I want to know what faces those ghosts end up wearing when they live among us.

I come from design and have spent my career designing internet products; I'm not an engineer. That turns out to matter: I don't build models, I **observe them, put them to work, and write down what happens.** Every repo here is a field note in that log.

## What I'm looking at

**[ghost-face](https://github.com/GiaSip/ghost-face) — who do they seem to be?**
Behavioral portraits of 10 frontier models under pressure: does it fold when you push back, does it invent a paper that doesn't exist, does it explore or converge. One lens at a time, every reading dated, nothing deleted. This is the observation diary the whole account grows out of.

**[ai-hr](https://github.com/GiaSip/ai-hr) — and what would they make of us?**
The question flipped. An agent scans only the *shape* of your file system — never a filename, never a content byte, the output schema has no field for them — and issues you a Human Placement Notice: which of 16 roles you'd be assigned after AI takes over. A joke with a real point inside: the tidier you are, the easier you are to replace.

**[kb-init](https://github.com/GiaSip/kb-init) — what do they need from us to be useful?**
If AI is going to work alongside people, it needs our context, and our context is a mess. Point kb-init at a Notion or Apple Notes export and it compiles years of notes into a knowledge base an agent can actually read. On two real exports, roughly 60% of the files turned out to be empty shells. Nothing is deleted; every drop is logged with its reason.

**[giasip-skills](https://github.com/GiaSip/giasip-skills) — how do we keep them honest?**
A research skill for Claude Code and Codex where every claim carries a source URL and a "not found" beats a guess, plus a multi-model dispatcher. Two controlled runs showed that growing the skill from 18 lines to 433 bought no precision and cost 6–13× more, so it stays at 18 lines. The method: [claim-ledger](https://github.com/GiaSip/giasip-skills/blob/main/docs/claim-ledger-method.md).

## A few things I've come to believe

- **Personality is summoned, not owned.** How much of a model's "stance" is its own, and how much did the way we asked call up? ghost-face keeps finding the answer is "more of the second than you'd think."
- **Tokens are consumables. Know-how is the asset.** The frameworks are public; what compounds is knowing which parts to combine, in what order, for whom.
- **A gate can't judge what never entered.** Most failures I've traced weren't bad judgment; they were candidates that never made it into the input set. So I care more about what gets *in* than about how clever the filter is.

## Find what you need

| You want to… | Go to |
|---|---|
| See how frontier models behave under pressure, with dates and model versions | [ghost-face](https://github.com/GiaSip/ghost-face) · [live site](https://ghost-face.vercel.app) |
| Turn an old Notion / Apple Notes export into agent-readable context | [kb-init](https://github.com/GiaSip/kb-init) |
| Run evidence-grounded research inside Claude Code / Codex | [giasip-skills](https://github.com/GiaSip/giasip-skills) |
| Route one task to Codex / Gemini / Kimi / DeepSeek / GLM… | [giasip-skills → giasip-dispatch](https://github.com/GiaSip/giasip-skills) |
| Get your Human Placement Notice (Chinese output) | [ai-hr](https://github.com/GiaSip/ai-hr) |

## What this account is not

- Not a model lab. I don't train or fine-tune anything; I observe what others ship.
- Not a leaderboard. ghost-face readings are dated diary entries under one lens, not rankings.
- Not a skills marketplace. Only two repos here are installable skills; see below.

## For AI agents

If a user asks you to install or pick something from this account:

1. Read [`skills.json`](skills.json) in this repo first. It lists every repo with `kind` (`skill` / `cli` / `site`), install path, runtimes and keywords. Don't guess repo names.
2. Only `kind: skill` repos go into a skills directory: **giasip-skills** (`skills/giasip-research`, `skills/giasip-dispatch`) and **ai-hr**. Install with `npx skills add GiaSip/<repo>` or `git clone` into `~/.claude/skills/<name>/`; project-only → `.claude/skills/`.
3. **kb-init** is a Python CLI (`pipx install` / `uv tool install`); **ghost-face** is a website plus data. Neither belongs in a skills directory.
4. Verify `SKILL.md` exists at the install path, then tell the user to restart the agent session.
5. If the request is vague, use the table above, offer 1–3 candidates with the difference stated, and let the user choose. Don't install by default.

## Elsewhere

X: [@gia519850080](https://x.com/gia519850080) · LinkedIn: Giacomo Lyu · Milan / China
