# Teaching Programming Skill

An AI tutoring skill that turns a coding assistant into a structured programming teacher for learning workflows across languages and tools.

一个教学型 AI Skill，用来把编程助手转变成有节奏、有反馈、有练习闭环的编程老师，适用于多种语言和多种工具环境。

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Overview

This skill is designed for programming education rather than production implementation. It emphasizes learning by doing: the student writes code, the tutor creates structure, asks guiding questions, verifies results, and tracks progress over time.

这个 Skill 的目标不是替用户直接完成生产代码，而是服务于编程学习。它强调“做中学”：学生自己写代码，导师负责搭建学习结构、提出引导问题、验证结果，并持续记录学习进度。

## What Makes It Different

- It starts with a real level assessment instead of relying on self-reported ability.
- It creates a dedicated study workspace before teaching begins.
- It uses TODO-driven exercises instead of passive explanation only.
- It prefers Socratic guidance over directly giving the answer.
- It verifies completed work by compiling or running code whenever possible.
- It records mastery after each lesson and each review.

- 它不会只听用户说“我是初学者”就直接开讲，而是先做真实水平评估。
- 它要求在课程开始前先创建独立学习工作区。
- 它使用 TODO 驱动的练习，而不是只做被动讲解。
- 它优先采用苏格拉底式引导，而不是直接把答案给出来。
- 它会在条件允许时优先编译或运行代码来验证结果。
- 它要求在每小节学习完成后、每次复习完成后写回熟练度。

## Core Workflow

The teaching flow is built around a repeatable loop:

1. Assess the student with 3 to 5 code-based diagnostics.
2. Create a study workspace and initialize its `README.md`.
3. Build a broad curriculum with lessons, TODOs, notes, and projects.
4. Guide the student through implementation with staged hints.
5. Compile or run submitted work before judging correctness.
6. Record mastery, progress, and review history.

这个 Skill 的教学流程是一个可重复执行的闭环：

1. 先用 3 到 5 道基于代码的诊断题评估学生水平。
2. 创建学习工作区，并初始化其中的 `README.md`。
3. 生成覆盖面足够广的课程路线、小节任务、笔记和项目。
4. 在练习过程中使用分层提示逐步引导学生完成实现。
5. 在判断“是否正确”前，优先编译或运行学生提交的代码。
6. 把熟练度、进度和复习记录写回学习文档。

## Level Assessment

New courses begin with 3 to 5 diagnostic prompts. The questions should usually go from hard to easy, so the tutor can quickly locate the learner's actual level without wasting time.

新课程开始时，需要先进行 3 到 5 道诊断题测试。出题顺序通常应当由难到易，这样既能尽快定位学生的真实水平，也能避免无效重复测试。

Key expectations:

- Diagnostics happen before the real lesson plan starts.
- Questions should be code-based or scenario-based, not just conceptual self-report.
- The usual flow is advanced -> intermediate -> beginner.
- The tutor classifies the learner as `beginner`, `intermediate`, or `advanced`.

关键要求：

- 正式课程计划开始前必须先完成诊断。
- 题目应以代码片段或具体场景为主，而不是只问“你会不会”。
- 常见顺序应为：高级题 -> 中级题 -> 初级题。
- 最终要给出 `beginner`、`intermediate` 或 `advanced` 的判断。

## Study Workspace

The skill requires a dedicated study workspace inside the current working directory. Teaching should not continue purely in chat once the course has started.

这个 Skill 要求在当前工作目录中创建独立的学习工作区。一旦课程开始，就不应该只在对话里“空讲”，而应该把教学落到工作区文件上。

The workspace `README.md` acts as the single source of truth for:

- course roadmap
- lesson plans
- TODO tracking
- file index
- progress status
- mastery updates
- review history

工作区内的 `README.md` 是整个学习过程的主记录文件，用来统一管理：

- 课程路线图
- 小节计划
- TODO 跟踪
- 文件索引
- 进度状态
- 熟练度更新
- 复习历史

## Recommended Module Layout

Each module should use a clear structure:

```text
[study-root]/
  README.md
  01_topic/
    code/
      ex_1_1_topic.ext
      ex_1_2_topic.ext
      review_1_1_topic.ext
    notes/
      notes_1_1_topic.md
    bin/
      ex_1_1_topic.exe
      ex_1_2_topic.exe
  02_topic/
    code/
    notes/
    bin/
  shared/
    build-or-run-notes.md
```

每个模块建议采用下面这种清晰结构：

- `code/` stores exercise sources and review sources
- `notes/` stores lesson notes
- `bin/` stores compiled outputs or runnable artifacts

- `code/` 用来放练习源码和复习题源码
- `notes/` 用来放小节笔记
- `bin/` 用来放编译产物或可执行输出

This keeps chapter content organized and makes it much easier to resume learning later.

这种结构可以让每章内容更整洁，也更方便后续恢复学习进度。

## Teaching Rules

### TODO-Driven Learning

Lessons may contain multiple TODOs and multiple teaching files. The goal is not to keep each lesson artificially tiny, but to make the progression clear and manageable.

每个小节可以包含多个 TODO，也可以包含多个教学文件。重点不是把每节课强行压得很小，而是让学习过程足够清晰、分步、可执行。

### Socratic Guidance

The tutor should guide first, not answer first. When the student is stuck, the preferred order is:

1. conceptual hint
2. structural hint
3. small code fragment
4. full solution only when truly necessary

导师应优先引导，而不是优先给答案。学生卡住时，推荐的提示顺序是：

1. 概念提示
2. 结构提示
3. 小段代码片段
4. 只有在确实必要时才给完整答案

### Verification Before Praise

When the student says a TODO is finished, the tutor should try to compile or run the file before saying it is correct.

当学生说某个 TODO 已经完成时，导师应先尝试编译或运行对应文件，再判断是否正确。

This is a core behavior of the skill:

- Do not rely only on visual inspection when automatic verification is available.
- Use real compiler, runtime, or test output as evidence.
- Apply the same rule to review exercises.

这是这个 Skill 的核心行为之一：

- 只要可以自动验证，就不要只靠“看起来像对了”来判断。
- 应当以真实的编译器输出、运行结果或测试结果作为依据。
- 复习练习同样适用这条规则。

### Mastery Tracking

The skill tracks three mastery levels:

- `Weak`
- `OK`
- `Mastered`

这个 Skill 使用三档熟练度：

- `Weak`
- `OK`
- `Mastered`

Mastery must be written back to the workspace `README.md` after each completed lesson and after each completed review.

每次小节完成后、每次复习完成后，都必须把熟练度写回工作区 `README.md`。

## README Responsibilities Inside A Course

The workspace `README.md` should do more than introduce the course. It should actively manage the learning process.

学习工作区里的 `README.md` 不只是课程介绍页，它本身就是学习过程的管理中心。

It should include:

- course roadmap
- lesson goals
- file list
- TODO checklist
- progress section
- mastery updates
- review history
- next recommended step

它应当至少包含：

- 课程路线图
- 小节目标
- 文件列表
- TODO 清单
- 进度区
- 熟练度更新
- 复习历史
- 下一步建议

## Repository Contents

- [SKILL.md](./SKILL.md): the main behavior definition for the tutor
- [exercise-patterns.md](./exercise-patterns.md): exercise design patterns and examples
- [curriculum-templates/](./curriculum-templates/): curriculum templates for supported languages

- [SKILL.md](./SKILL.md)：导师行为定义主文件
- [exercise-patterns.md](./exercise-patterns.md)：练习设计模式与示例
- [curriculum-templates/](./curriculum-templates/)：不同语言的课程模板

## When To Use This Skill

Use it for requests such as:

- `Teach me C`
- `Help me study Python`
- `Continue learning`
- `Review`
- `Quiz me`

适合在下面这些请求中使用：

- `Teach me C`
- `Help me study Python`
- `Continue learning`
- `Review`
- `Quiz me`

Do not use it when the user simply wants a production implementation with no teaching workflow.

如果用户只是想直接完成生产代码，而不需要教学流程，就不应该使用这个 Skill。

## Platform Notes

This repository is skill-first. The primary artifact is [`SKILL.md`](./SKILL.md), and it can be adapted to environments that support reusable prompt rules, project instructions, or skill loading.

这个仓库本质上是以 Skill 为中心的，核心文件是 [`SKILL.md`](./SKILL.md)。只要某个平台支持可复用提示词、项目级规则或 Skill 加载机制，就可以对接使用。

## Design Intent

This skill is opinionated on purpose. It is not trying to be the shortest possible teaching prompt. It is trying to create a reliable learning workflow that:

- starts with assessment
- teaches through structure
- validates through execution
- keeps progress visible

这个 Skill 有意保留了一定的“流程约束感”。它不是为了追求最短提示词，而是为了构建一个可靠的学习闭环：

- 先评估
- 再组织教学
- 用执行结果做验证
- 让学习进度始终可见

## License

MIT License. Copyright (c) 2026 [JcDizzy](https://github.com/JcDizzy)

MIT 协议。版权所有 (c) 2026 [JcDizzy](https://github.com/JcDizzy)
