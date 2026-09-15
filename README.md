# Deep Interview

> 一问一答，把模糊的困扰或没想全的需求，变成可以继续推进的成果。
> An adaptive, one-question-at-a-time interview that turns a vague dilemma or an under-specified task into something you can actually act on. ([English summary](#english))

**v0.3.0** 将 `SKILL.md` 改为中英双语，并把安装与使用说明改为 Agent 中立；访谈方法与交付格式沿用 v0.2（见 [v0.3 方案](docs/design-v0.3.md)）。

**v0.2.0** 新增“需求访谈模式”，保留 v0.1 的自我澄清能力。它根据你的回答动态选择下一问，不会一次抛出固定长问卷。

| 你想做什么 | 使用方式 | 最后得到什么 |
| --- | --- | --- |
| 看清个人困扰、重要选择、反复模式或价值取舍 | 自我澄清 | 有依据、可修正的认知地图 |
| 把任务、自动化、内容或工作流程的需求补全 | 需求访谈 | 可审阅、可交接的任务需求卡 |

不必先指定模式，描述你的目标即可。两种模式都支持随时纠偏、暂停和带卡片续访。中文和英文提问都能触发，访谈会跟随你使用的语言。

## v0.2 能帮你补什么

例如：“每天早上 8:30 给我推送新闻，来源已经选了一些，但类别没想全。”

Skill 会沿用已有条件，先弄清这份新闻帮助你做什么，再检查与用途相关的遗漏类别。需要完整任务规格时，再逐步补齐来源边界、筛选去重、输出与时间语义、异常处理和验收条件。只想补类别，也可以仅完成这一部分。

- 一次只问一个主要问题，已说清的内容不重复问；
- AI 可以主动提出有理由的补项，但建议不自动成为你的需求；
- 区分“已确认、暂定、未知、已否定”，保留拒绝项和修改记录；
- 你明确让 AI 代定的部分，标为“授权默认”，不扩展到未授权事项；
- 输出任务需求卡和必要的续访卡，而不是停在聊天总结；
- 区分“需求已确认”和“任务已创建”，不虚构调度或推送能力。

查看 [v0.2 方案](docs/design-v0.2.md)和[每日新闻示例](examples/daily-news.md)。

## 安装

本 Skill 是一组纯 Markdown 文件，不依赖特定模型、客户端或调度接口。安装方式只有一条通用原则：**把整个仓库目录放到你的 Agent 读取 Skill 的位置，目录名保持 `deep-interview`。**

| Agent | 放置位置 |
| --- | --- |
| Claude Code / Claude 桌面端 | 个人级 `~/.claude/skills/deep-interview`；项目级 `<项目>/.claude/skills/deep-interview` |
| Codex | `$HOME/.agents/skills/deep-interview`，或调用 `$skill-installer` 安装 |
| 其他支持 Skill 目录的 Agent | 按其文档放入对应的 skills 目录 |
| 不支持 Skill 机制的 Agent | 把 `SKILL.md` 作为上下文或系统提示提供，需要时再补对应的 `references/` 文件 |

```bash
# Claude Code / Claude 桌面端
git clone https://github.com/jia140431-png/deep-interview.git "$HOME/.claude/skills/deep-interview"

# Codex
git clone https://github.com/jia140431-png/deep-interview.git "$HOME/.agents/skills/deep-interview"
```

使用 Skill 安装器的客户端（例如 Codex 的 `$skill-installer`）可以直接告诉它：

```text
从 https://github.com/jia140431-png/deep-interview 安装 deep-interview。
```

已有副本请先检查并保留自己的修改，再更新到新版本。若客户端尚未显示新版能力，重新加载 Skill 或重启客户端。

### 分享给其他 Agent 用户

分享本仓库链接即可。核心是 `SKILL.md` 和它引用的 `references/` 文件，不绑定特定模型、客户端或调度接口；`agents/openai.yaml` 只是 Codex 的可选界面元数据，其他 Agent 会忽略它。接收方应按其 Agent 支持的方式加载整个 Skill 目录。不能安装 Skill 时，也可提供入口及所需参考文件作为上下文，但效果取决于 Agent 的指令遵循与上下文能力。

这不代表每个 Agent 的安装、联网、定时执行和推送能力都已验证；本次验证范围见 [测试记录](evals/results-v0.2.md)。

## 使用

不需要固定命令，描述目标即可。带上 Skill 名称能让 Agent 更稳定地进入访谈。

自我澄清：

```text
用 deep-interview 对我做一次深度访谈。
```

需求访谈：

```text
用 deep-interview 的需求访谈模式，帮我补齐每日新闻任务。
每天早上 8:30 给我推送，来源是……，现有类别是……。
先一问一答查漏补缺，再生成需求卡，暂时不要创建任务。
```

只补一部分：

```text
只帮我补齐 AI 新闻类别，主要用于开发选型。
现在有模型发布和开发工具，其他维度先不讨论。
```

也可以直接说“这件事我想不明白，先别给建议，采访我”或“这个任务没想全，先问清楚再做”。英文同理，例如 `interview me about this before giving advice` 或 `ask me questions first — my requirements aren't complete`。已有完整规格且只想直接执行时，不会强制重新访谈。

## 访谈中的控制语句

不需要记忆严格命令，直接表达下面这些意思即可（中英文均可）：

- 开始访谈 / start
- 继续往下 / keep going
- 这个方向不对 / that's the wrong direction
- 换个问题 / ask something else
- 生成当前地图 / give me the map
- 生成任务需求卡 / generate the requirements card
- 先到这里 / let's stop here
- 结束访谈 / we're done
- 继续上次访谈 / resume our last interview

结束时生成的 Interview Resume Card 可以复制到新的会话或其他能读取这些指令的 Agent 中继续使用。v0.1 的认知续访卡仍可使用；卡片不是自动同步，也不自动给接收方执行外部操作的权限。

## 文件结构

```text
deep-interview/
├── SKILL.md                 # 中英双语入口
├── agents/
│   └── openai.yaml          # 可选：Codex 界面元数据
├── references/
│   ├── reflection.md        # 自我澄清策略
│   ├── artifacts.md         # 认知地图与续访卡
│   ├── requirements.md      # 需求覆盖与收敛规则
│   ├── task-card.md         # 任务需求卡与交接
│   └── news-brief.md        # 每日新闻领域补项
├── docs/
│   ├── design-v0.2.md       # v0.2 扩展方案
│   └── design-v0.3.md       # v0.3 双语与 Agent 中立
├── examples/daily-news.md   # 虚构示例与初始草稿
└── evals/                   # 场景与验证记录
```

- `SKILL.md`：共用访谈方法、模式路由和边界，中英双语；
- `references/`：仅在对应模式、领域或成果需要时加载（中文）；
- `agents/openai.yaml`：Codex 的名称、说明和默认启动提示，删除不影响其他 Agent 使用。

## 边界

Deep Interview 是澄清与反思工具，不是心理诊断、治疗或人格测评。它不会替用户做决定，也不应替代医疗、法律、财务等专业意见。

Skill 本身不提供抓取、调度或发送服务，也不绑定任何一种 Agent 或调度平台。如果你明确要求“问清楚后创建任务”，Agent 可以在需求明确后使用当前环境实际可用的工具继续；否则只交付需求。访谈内容不会因安装此 Skill 被自动上传或分享。

## English

**Deep Interview** is a model-agnostic, plain-Markdown skill that interviews you one question at a time instead of dumping a fixed questionnaire on you.

Two modes, picked from what you want out of it — you never name the mode yourself:

| You want to | Mode | You get |
| --- | --- | --- |
| See a personal dilemma, recurring pattern, or value trade-off more clearly | self-clarification | An evidence-backed, correctable understanding map |
| Close the gaps in a task, automation, piece of content, or workflow | requirements | A reviewable, handoff-ready Task Requirement Card |

What it does differently:

- One main question per turn, chosen from your last answer — not a fixed script;
- It proposes reasoned additions you may not have thought of, but a suggestion never silently becomes your requirement;
- Every item is tracked as confirmed / tentative / unknown / rejected, with its evidence;
- Anything you delegate is marked as an authorized default and does not expand beyond what you authorized;
- It separates "requirements confirmed" from "task created", and never fabricates scheduling or delivery capability;
- You can correct, skip, switch modes, ask for the artifact, or stop at any point, and resume later from a Resume Card.

**Install** — drop the repo directory wherever your agent loads skills from, keeping the folder name `deep-interview`:

```bash
# Claude Code / Claude desktop
git clone https://github.com/jia140431-png/deep-interview.git "$HOME/.claude/skills/deep-interview"

# Codex
git clone https://github.com/jia140431-png/deep-interview.git "$HOME/.agents/skills/deep-interview"
```

Any other agent with a skills directory works the same way. If yours has no skill mechanism, paste `SKILL.md` in as context and add the matching `references/` file when a mode needs it. `agents/openai.yaml` is optional Codex-only interface metadata; other agents ignore it.

**Use it** by describing your goal, in English or Chinese:

```text
Interview me about this before giving any advice.
```

```text
Use deep-interview's requirements mode: I want a daily news brief at 8:30am,
I've picked some sources but haven't listed all the categories.
Ask me one question at a time, then generate the requirements card —
don't create the task yet.
```

`SKILL.md` is bilingual (Chinese/English) and the interview follows whichever language you write in; the `references/` files are currently Chinese only, and translations are welcome.

**Boundaries** — this is a clarification and reflection tool, not diagnosis, therapy, or personality assessment, and not a substitute for medical, legal, or financial advice. The skill itself provides no fetching, scheduling, or sending capability and is tied to no particular agent or platform. If you explicitly ask it to create the task after clarifying, the agent may proceed with whatever tools your environment actually has; otherwise it delivers the spec only.

## License

[MIT](LICENSE)
