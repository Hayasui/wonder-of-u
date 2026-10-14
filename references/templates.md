# 两套件骨架与可抄的句子

这份文件给 `wonder-of-u` 用。两类件——**盲判件**（让外部模型独立判一批样本，取回当尺子）
与**追问件**（补上一轮的缺口、顺手审自己的产出）。骨架照抄，把方括号里的东西换掉即可。

## 甲、盲判件

### 骨架顺序

标题 → 指令头 → 背景 → 值域表 → 样本表 → 输出格式与回执 → 使用说明

顺序不能乱。外部模型先读指令头，再读背景，最后才看到样本。样本摆在最后，
它读到时已经知道要按什么形状答。

### 一、标题与首行

`# [用途] — [样本量] items for independent annotation`

首行写版本、日期，加一句「几个活、哪个要联网」。

### 二、指令头六条（可直抄）

```text
You are acting as an independent annotator for a user-research dataset. Your job is to
annotate a sample of [N] raw survey answers, blind. You have no access to the source data
and must not go looking for it. Everything you need is in the task file below.

How to work:

1. Read the task file below in full before you answer anything.
2. Follow section 1 (the steps), section 2 (the value set) and section 3 (the items)
   exactly as written.
3. Judge every item on its own. Do not carry information from one item into another.
4. Where you are unsure, write `UNCERTAIN` or `[对应档]` instead of guessing.
   Both are valid answers. They will be treated as information, not as mistakes.
5. Do not treat the working English rendering as evidence. The original string governs.
6. Do not correct spelling in `entry_text_verbatim`. Keep the original script.

Output exactly two parts, in this order, and nothing else:

- Part 1: one markdown table whose header row is exactly
  `| item_id | entry_no | entry_text_verbatim | [你定的列] | confidence | ambiguity_note |`.
- Part 2: a short section headed "Receipt", answering the five numbered points in section 4.

Constraints:

- No preamble. No restatement of the task. No commentary between the two parts.
- Do not add a [第 N+1] 个码。[保留档] is a flag, not a category.
- If you cannot carry out some part of the task, say so in the receipt. Do not drop it silently.
```

### 三、背景这一节最贵

写三段：被测的场合是什么、题目怎么问的、原始填答长什么样。**必须点名被测环境的关键名词。**
再给值域表（每个码一行，写清含义与边界），并说明「保留档不是第 N+1 个类别，是一个标记」。

### 四、样本表列名

`| # | Item | Q | Respondent's answer (verbatim) | Working English rendering |`

原文逐字，换行用 `<br>` 表示。译文只作阅读辅助，表前写明「原文为准」。

### 五、输出两段

第一段是一张列名定死的表，第二段是回执。回执五问，问法固定：

1. 处理了多少条，产出多少条条目。
2. `UNCERTAIN` 与保留档各多少条，逐条列出是哪几条。
3. 哪里做了合并、删减或改序，各一行理由。
4. 哪些条目卡在两个取值之间，为什么。
5. 哪一部分做不到。

## 乙、追问件

上一轮的缺口攒成一件，分四段，段名就叫 `Job 1` 到 `Job 4`。四种活各占一段。

| 段 | 活 | 要它交什么 |
|---|---|---|
| Job 1 | 解上一轮判不了的残留 | 一行一条：标准名、码、把握度、来源链接、一句说明 |
| Job 2 | 审自己写给它的工作译文 | 一行一条：准确／部分准确／不准确、订正、会不会带偏 |
| Job 3 | 对高频项做批量规范化 | 一行一条：标准名、类型、码、把握度、来源、备注 |
| Job 4 | 查外部规范与通行做法 | 分小节短答，限字数，自己的建议要标 `SUGGESTION` |

**Job 2 的特殊价值**：它审的是自己写出去的译文。译文是唯一的错误通道，
不专门审一次，错了也不知道。

**Job 3 的规模控制**：取高频的前一百项就够，不必铺全。写清「这是高频段，不是全体」，
免得它把比例当总体。

**Job 4 的引用门槛**：明写每条都要来源链接。取回后检查有没有拿问答站、幻灯片分享站，
或与题无关的分类体系凑数。

## 丙、可直抄的句子

| 用途 | 英文句 |
|---|---|
| 不许猜 | `Where you cannot establish something, write UNRESOLVED. Do not guess silently.` |
| 要给来源 | `Give a source URL for every claim that rests on an external fact. A row without a source is worth less than a row that says UNRESOLVED.` |
| 原文为准 | `Judge from the original string. The rendering is a helper, not evidence. Where the rendering and the original disagree, the original wins.` |
| 标建议 | `Mark any recommendation of your own with the word SUGGESTION, so it is not mistaken for a finding.` |
| 不许自造码 | `Do not add a sixteenth code. UNASSIGNED is a flag, not a category.` |
| 不许悄悄漏 | `If you cannot carry out some part of the task, say so in the receipt. Do not drop it silently.` |
| 要字数上限 | `Keep the whole job under [N] words. Do not write an essay.` |

这些句子回到中文，就是本技能第三节第八条与第四节要核的那几项。

## 丁、已验证的实例

这套流程已在真实项目上跑通过一轮，两份件的形状可以直接照搬。

- 盲判件两份并存：一份存档版、含分层说明，一份发送版、分层说明已删。
  样本分五层各十条；取回一百四十余条答案，原文回比零越界。
- 追问件含四个活。取回后用脚本核对，其中一批与已有标准重叠三十余处、零不一致，
  等于顺手把标准复核了一遍。
- 取回后的并入说明可当第四节那份说明件的样板：核对结果、要处置的地方、每个分母的来源，
  三块齐全。
