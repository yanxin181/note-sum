# intern-log-kit

`intern-log-kit` 是一个面向前端实习和前端校招复盘的 Codex skill，用来把代码对话、本地工程笔记和实习工作整理成适合复盘的学习日志。它会重点记录你在前端项目里做了什么、为什么这么做、涉及哪些组件/页面/状态/数据流、代码里哪些地方值得回看，并支持生成日报、周报，以及给任务做前端简历含金量评分。

它适合前端实习生、初级前端、前端校招准备者，以及正在用 AI 编程助手做前端项目复盘的人。输出内容既可以放进 Obsidian，也可以直接保存成普通 `.md` 文件。

## 推荐搭配
- `intern-log-kit`：生成学习笔记、日报、周报和任务评分
- `obsidian-markdown`：处理 Obsidian 风格 Markdown
- `obsidian-cli`：读取、创建、追加和管理 Obsidian 笔记

## 它解决什么问题

很多 AI 总结只会回答“今天做了什么”。但前端实习复盘更需要回答这些问题：

- 这次解决的原问题是什么？
- 数据从哪里来，状态怎么影响页面？
- 哪个组件、函数或文件最关键？
- 页面展示、用户点击、校验、回显、提交这些流程是怎么串起来的？
- 为什么这段代码能解决问题？
- 这项工作汇报时应该怎么说？
- 这项任务值不值得写进前端简历？

`intern-log-kit` 的目标不是写长文档，而是把每天零散的前端代码工作沉淀成能复盘、能汇报、能辅助简历取舍的学习日志。

## 兼容范围

- 有 Obsidian：可以继续用大纲、wikilink、callout 等能力。
- 没有 Obsidian：也可以直接把输出当普通 Markdown 笔记使用。
- 这个 skill 只负责生成内容结构，不强制依赖 Obsidian。

## 目录结构

```text
intern-log-kit/
├─ SKILL.md
├─ README.md
├─ agents/
│  └─ openai.yaml
├─ templates/
│  ├─ learning-note-template.md
│  ├─ report-template.md
│  └─ task-rating-rules.md
└─ examples/
   ├─ learning-note-example.md
   ├─ daily-report-example.md
   └─ task-rating-example.md
```

## 路径配置

你只需要配置一个路径：

| 占位符 | 含义 |
| --- | --- |
| `{NOTES_DIR}` | 生成笔记、日报、周报和任务评分的存放目录 |
| `{DATE}` | 当前日期，格式为 `YYYY-MM-DD` |

示例：

```text
{NOTES_DIR}=D:\notes\frontend-internship\notes
```

## 常用提示词

```text
使用 $intern-log-kit，把这次代码对话整理成一篇 Obsidian 学习笔记。
```

```text
使用 $intern-log-kit，根据刚才的工作内容写今天的日报。
```

```text
使用 $intern-log-kit，给我 2026-07-01 到 2026-07-15 的实习任务做简历含金量评分。
```

## 推荐工作流

1. 先和 Codex 完成一次真实代码任务。
2. 任务结束后，让 `$intern-log-kit` 追加一篇学习笔记。
3. 需要向导师或组长汇报时，生成日报。
4. 一周积累多篇笔记后，生成周报。
5. 准备简历或面试时，对任务做五星评分和简历取舍。

## 开源前注意隐私

如果要公开生成出来的笔记，请先删除：

- 公司名、内部项目名、仓库路径、接口名、截图。
- 用户数据、订单数据、token、cookie、账号 ID、私有 URL。
- 雇主或客户不允许公开的代码、业务流程和实现细节。

## 开源定位

比较适合的定位是：

> AI 前端实习学习日志系统：把前端代码对话整理成可复盘的 Markdown/Obsidian 学习日志、日报、周报和简历含金量评分。

它的目标用户不是所有开发者，而是前端实习生、初级前端、前端校招准备者、Obsidian 用户，以及希望用 AI 编程助手准备前端简历和面试的人。
