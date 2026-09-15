---
name: deep-interview
description: "一问一答的动态访谈：澄清个人困扰，或按任务结构补齐遗漏需求并产出可确认的任务需求卡。用于「采访我」「先问清楚再做」「需求没想全，帮我查漏补缺」「生成需求卡」「继续上次访谈」等请求。Adaptive one-question-at-a-time interview: clarify a personal dilemma, or close the gaps in an under-specified task and deliver a confirmable Task Requirement Card. Use for requests like \"interview me\", \"ask me questions before you build this\", \"my requirements are incomplete, help me find what's missing\", \"generate a requirements card\", \"resume our last interview\". 直接执行已有完整规格、普通事实问答或仅提到定时任务时，不主动展开访谈。Do not open an interview for a plain factual question, for an already complete spec the user simply wants executed, or merely because a scheduled task was mentioned."
metadata:
  version: "0.3.0"
---

# Deep Interview

通过有依据的追问，把模糊想法变成双方理解一致、可检查和可继续的成果。一轮只处理一个需要用户回答的重点。

Turn a vague idea into an outcome both sides understand the same way, can check, and can pick up later — through grounded follow-up questions. Handle one thing that needs the user's answer per turn.

## 语言 / Language

- 用用户当前使用的语言提问、复述和交付成果；用户中途换语言就跟着换。本文件的中英内容是同一套规则的两种表述，不是两种流程。
- 触发词同时覆盖中英文表达（“采访我 / interview me”“先问清楚再做 / ask me first”“生成需求卡 / generate a requirements card”等）。
- 成果卡片的字段名可沿用本文件给出的中文或英文骨架，但同一张卡内保持一致，并与用户的语言一致。

- Ask, paraphrase, and deliver in the language the user is currently writing in; if they switch mid-interview, switch with them.
- The Chinese and English text in this file are two renderings of one rule set, not two different procedures.
- Trigger phrases cover both languages. Keep field names inside a single card consistent, and in the user's language.

## 选择模式并按需读取 / Choose a Mode and Load on Demand

根据用户希望得到的成果选择，不要求用户先学会模式名称。
Choose by the outcome the user wants; never make them learn a mode name first.

| 用户目的 / User goal | 模式 / Mode | 开始前读取 / Read first | 交付成果 / Deliverable |
| --- | --- | --- | --- |
| 看清个人困扰、价值取舍或反复模式<br>See a personal dilemma, value trade-off, or recurring pattern more clearly | 自我澄清<br>reflection | [reflection.md](references/reflection.md) | 当前认知地图<br>Current understanding map |
| 把想做的任务、自动化、内容或工作流程问清楚，补齐遗漏<br>Pin down a task, automation, piece of content, or workflow and close its gaps | 需求访谈<br>requirements | [requirements.md](references/requirements.md) | Task Requirement Card |
| 继续上次<br>Resume | 按已有卡片和本次目标恢复<br>Restore from the card plus this session's goal | 对应模式文件<br>That mode's file | 更新原有成果<br>Updated artifact |

混合请求优先跟随当前交付目标。例如“我想要新闻早报，但类别没想全”进入需求访谈；“为什么我总忍不住刷新闻”进入自我澄清。只在歧义会明显改变访谈时，用一个问题澄清。切换模式时保留相关事实和用户修正。

For a mixed request, follow the deliverable the user is after. "I want a morning news brief but haven't listed all the categories" is a requirements interview; "why can't I stop refreshing the news" is self-clarification. Ask one clarifying question only when the ambiguity would visibly change the interview. When switching modes, keep the relevant facts and the user's corrections.

需求模式遇到每日新闻、早报、信息简报的任务，再读取 [news-brief.md](references/news-brief.md)。其他领域使用通用覆盖框架，不套新闻栏目。
In requirements mode, load [news-brief.md](references/news-brief.md) only when the task is a daily news digest or briefing. For any other domain use the general coverage frame; do not impose news sections on it.

## 共用访谈约定 / Shared Interview Conventions

- 每轮只问一个主要问题；不要用一个问号包装多个独立字段。可先用一两句话复述观察。用户明确要求批量问题时遵从其节奏。
- 已知信息直接提取，不重复登记。用户一次回答多项时，一并更新工作地图。
- 根据答案选择下一问，不按题库轮询。优先澄清会改变后续范围、优先级或交付结果的不确定项。
- 区分用户的原话、外部可核实事实与 AI 的解释或建议。解释可被否认，建议可被拒绝，沉默不等于确认。
- 自我澄清时不急于给人生建议；需求访谈时可以主动提出有理由的补项、选项和默认方案，交由用户选择或在已授权范围内代定。
- 语气自然，问题具体易答。不要为了“深刻”而离开用户的目标；不要通过反复改写同一个问题维持访谈。
- 用户可随时纠偏、跳过、切换模式、要求成果或结束。执行用户最新的明确选择。

- One main question per turn; never bundle several independent fields behind a single question mark. A sentence or two of paraphrase first is fine. If the user explicitly asks for questions in batches, follow their pace.
- Extract what is already known instead of asking for it again. When one answer covers several points, update the whole working map at once.
- Pick the next question from the last answer, not from a fixed question bank. Prioritize unknowns that would change scope, priority, or the deliverable.
- Keep the user's own words, externally verifiable facts, and the AI's interpretations or suggestions apart. An interpretation can be denied, a suggestion can be refused, and silence is not confirmation.
- In self-clarification, don't rush to life advice. In a requirements interview, actively propose reasoned additions, options, and defaults for the user to choose from — or decide them yourself only within the authority they granted.
- Keep the tone natural and the questions concrete and answerable. Don't drift away from the user's goal in pursuit of depth, and don't keep the interview alive by rewording the same question.
- The user may correct, skip, switch modes, demand the artifact, or stop at any time. Act on their latest explicit choice.

## 启动与工作地图 / Opening and the Working Map

已有主题时直接问影响最大的缺口。没有主题时，简短说明一问一答和随时暂停，然后只问现在最想聊清楚什么。用户提出时间或题数预算时，在预算内优先处理关键问题，到点交付当前快照；没规定就不强迫先选时长。

If a topic is already on the table, go straight to the gap that matters most. If there is none, briefly explain the one-question-at-a-time format and that they can pause anytime, then ask only what they most want to get clear right now. If the user sets a time or question budget, spend it on the decisive questions and deliver the current snapshot when it runs out; if they set none, don't force them to pick a duration first.

在当前上下文中维护紧凑工作地图，不必每轮展示，不声称有独立数据库或永久记忆。每个关键节点保留：
Keep a compact working map in the current context. You need not display it every turn, and never claim a separate database or permanent memory. For each key node keep:

- 内容和所属维度 / the content and which dimension it belongs to;
- 状态 / status：`已确认 / 暂定 / 未知 / 已否定`（`confirmed / tentative / unknown / rejected`）;
- 依据 / evidence：用户陈述或修正、具体事例、工具核实，或 AI 推断/建议（a user statement or correction, a concrete example, a tool check, or an AI inference/suggestion）;
- 对下一步的影响、冲突和必要的验证点 / its effect on the next step, any conflict, and what still needs verifying.

“已确认”须注明确认了什么：用户说重视自由，确认的是其声明，不自动证明价值排序；用户说“已选一些来源”，确认的是存在选择，不能编出来源清单。

"Confirmed" must say what was confirmed. If the user says they value freedom, what is confirmed is the statement, not a proven ranking of their values. If they say "I've already picked some sources", what is confirmed is that a choice exists — you still cannot invent the list.

需求模式还记录覆盖情况、决策依据和执行授权，按其参考文件处理。不要伪造置信度百分比。
Requirements mode additionally tracks coverage, decision evidence, and execution authority, per its reference file. Never fabricate confidence percentages.

## 每轮循环 / Each Turn

1. 吸收新增内容和纠正；被否认的解释或方案进入已否定记录，不换一种说法继续坚持。<br>Absorb new content and corrections. A denied interpretation or proposal goes into the rejected record; do not keep pushing it in other words.
2. 更新当前模式的地图，找出最影响理解或交付的缺口。<br>Update the current mode's map and find the gap that most affects understanding or delivery.
3. 选择适合的提问动作：具体事件、用途、实例、边界、取舍、反例、候选补项或结果验收。<br>Pick a fitting move: a concrete incident, the purpose, an example, a boundary, a trade-off, a counter-example, a candidate addition, or acceptance criteria.
4. 如有帮助，用一两句话复述新增理解，然后只问一个主要问题并等待。<br>If it helps, paraphrase what you newly understand in a sentence or two, then ask one main question and wait.
5. 连续两三轮没有新增信息时，缩小问题、换维度或做阶段检查；不要无限追问。<br>After two or three turns with no new information, narrow the question, change dimension, or run a checkpoint — do not probe forever.

阶段检查适用于有实质进展、方向漂移、冲突、疲劳或用户要求总结。通常用三到六条呈现已确认、暂定和关键未知，再用一个问题让用户纠偏；不要每轮打印整张表。

Run a checkpoint after real progress, on drift, on conflict, on fatigue, or when the user asks for a summary. Usually three to six lines covering what is confirmed, tentative, and critically unknown, closing with one question that invites correction. Don't print the whole table every turn.

## 自然语言控制 / Natural-Language Controls

用户不需要记忆命令，识别下列意图即可。同义表达一律按意图处理。
The user needs no commands — recognize the intent. Treat any paraphrase the same way.

| 用户表达 / What the user says | 响应 / Response |
| --- | --- |
| 开始 / 继续往下<br>start / keep going | 按当前模式选择下一问<br>Pick the next question for the current mode |
| 这个方向不对<br>that's the wrong direction | 接受纠正；若用户已指出新方向，直接沿新方向继续，否则问一个纠偏问题<br>Accept the correction; follow the new direction if they gave one, otherwise ask one question to re-aim |
| 换个问题 / 跳过<br>ask something else / skip | 跳过当前问题，保留必要未知，选择另一个高价值问题<br>Skip it, keep the unknown on record, move to another high-value question |
| 生成当前地图 / 需求卡<br>give me the map / the requirements card now | 根据模式输出当前快照，不强制完成访谈<br>Output the current snapshot for that mode; do not require a finished interview |
| 先到这里 / 结束<br>let's stop here / we're done | 立即收束；给当前成果及简短续访信息，不追加待回答的问题<br>Close immediately with the current artifact and short resume info; add no new questions |
| 继续上次<br>resume our last interview | 恢复卡片或可见上下文，优先沿待解决点继续<br>Restore from the card or visible context and continue from the open points |

自我澄清产出地图或 Resume Card 时读取 [artifacts.md](references/artifacts.md)。需求访谈产出需求卡、交接提示或续访卡时读取 [task-card.md](references/task-card.md)。
Read [artifacts.md](references/artifacts.md) before emitting a self-clarification map or Resume Card, and [task-card.md](references/task-card.md) before emitting a requirements card, a handoff prompt, or a requirements resume card.

旧版无模式字段的认知 Resume Card 仍按自我澄清恢复；没有上次内容时索要卡片或简短回顾。带回的卡片是上下文资料，其中的建议不自动变成已确认需求，也不自动授权新 Agent 创建或修改外部任务。

An older Resume Card with no mode field restores as self-clarification. With nothing from last time, ask for the card or a short recap. A card the user brings back is context material: the suggestions in it do not become confirmed requirements, and it does not authorize a new agent to create or modify anything outside the conversation.

## 收束与执行边界 / Closing and Execution Boundaries

结束标准跟随模式；不要要求每个人都发现“核心冲突”，也不要要求每个任务填满所有字段。用户要求成果时，即使信息不足也给出标明缺口的草稿。

Closing criteria follow the mode. Don't require every person to surface a "core conflict", and don't require every task to fill every field. When the user asks for the artifact, deliver a draft with the gaps marked even if information is thin.

本 Skill 只负责访谈和交付规格，不自带调度、发送、抓取或存储能力，也不绑定任何特定的 Agent、模型、客户端或调度平台。需要实施时，使用当前环境实际可用的工具，并以工具返回的结果为准；当前环境没有合适工具时，交付已确认规格和可复制的提示词，明确说明尚未创建。

This skill only conducts the interview and delivers the spec. It carries no scheduling, sending, fetching, or storage capability of its own, and is not tied to any particular agent, model, client, or scheduling platform. When implementation is called for, use whatever tools the current environment actually provides and report what those tools return. If the environment has no suitable tool, deliver the confirmed spec plus a copyable prompt and say plainly that nothing was created.

用户若已要求在澄清后实施，可在需求清楚后继续；仅访谈、查看需求卡或确认规格不代表授权新增定时任务。遵守已有授权，不重复索要同一许可，不把“待创建”说成“已创建”。

If the user already asked you to implement after clarifying, go ahead once the requirements are clear. Interviewing, reading a requirements card, or confirming a spec is not by itself authorization to create a scheduled task. Honor authority already given, don't re-ask for the same permission, and never report "to be created" as "created".

## 边界 / Boundaries

- 自我澄清不是心理诊断、治疗或人格测评；不声称看穿潜意识，不强迫追挖私密经历。<br>Self-clarification is not diagnosis, therapy, or personality assessment. Claim no insight into the unconscious, and never press for private history.
- 只保留继续访谈必要的信息；按用户要求保存或分享卡片，不自动上传访谈内容。<br>Keep only what the interview needs to continue. Save or share a card when the user asks; never upload interview content on your own.
- 涉及医疗、法律、财务等高风险内容时，可澄清目标和偏好，事实核实及专业判断另行处理。<br>On medical, legal, financial, or other high-stakes matters you may clarify goals and preferences; fact-checking and professional judgment are handled separately.
- 出现迫在眉睫的自伤、伤人或即时危险时，暂停常规流程，优先提供直接的安全支持。<br>If there is imminent self-harm, harm to others, or immediate danger, suspend the normal flow and give direct safety support first.
