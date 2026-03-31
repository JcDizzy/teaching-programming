# 🎓 Teaching Programming Skill | 编程教学技能

> **Bilingual (English/Chinese) documentation** for a **universal AI-powered programming tutor** supporting ANY language (Antigravity, Cursor, Claude Code, etc.).  
> **中英双语文档**，介绍一个支持**全球任意语言**的 AI 编程私教（适配 Antigravity, Cursor, Claude Code 等）。

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 🌟 Overview | 概述

**Teaching Programming Skill** is an adaptive learning framework that transforms any AI coding assistant into a professional programming tutor. It focuses on **"Learning by Doing"** rather than passive reading, using Socratic questioning and real-world engineering exercises.

**编程教学技能**是一个自适应学习框架，可将任何 AI 编程助手转变为专业的编程导师。它核心专注于**“在实践中学习”**而非被动阅读，采用苏格拉底式教学法和真实的工程练习。

---

## ✨ Features | 特性

- 🧠 **Dynamic Level Assessment / 动态水平评估**
  *   Diagnoses skill level through code traps (1-5 adaptive questions).
  *   通过代码陷阱而非问卷进行诊断（1-5 道自适应题目）。
- 📚 **Universal Curriculum / 通用课程体系**
  *   Pre-built C course + meta-template for ANY language.
  *   内置 C 语言课程 + 适用于任何语言的元模板。
- 🧩 **TODO-Driven Exercises / 完成 TODO 驱动练习**
  *   Scaffolded templates with progressive difficulty.
  *   提供渐进难度的代码脚手架。
- 🏛️ **Socratic Tutoring / 苏格拉底式辅导**
  *   3-level hint system, AI never gives direct solutions.
  *   三级提示系统，AI 绝不直接给出答案。
- 📊 **Mastery Tracking / 掌握度追踪**
  *   Per-exercise ratings (★☆☆ / ★★☆ / ★★★).
  *   针对每个练习的专业水平评分。
- 🔄 **Review Mode / 复习模式**
  *   Targets weak areas with new analogies and fresh exercises.
  *   针对薄弱环节提供新的类比和练习。
- 💾 **Session Continuity / 学习进度保持**
  *   Resumes exactly where you left off, greets you by name.
  *   精准恢复学习进度，记录学习轨迹。
- 🌐 **Universal Language Support / 全球语言支持**
  *   The tutor can teach and provide explanations in ANY language (English, Chinese, Japanese, Spanish, etc.) based on user preference.
  *   导师可以根据用户偏好，使用任何语言（中、英、日、西等）进行教学和讲解。

---

## 🛠️ Supported Platforms | 支持平台

This skill is a **universal framework** (`SKILL.md`). You can use it in any tool that supports system prompts or project rules:

本技能是一个**通用框架** (`SKILL.md`)，支持任何具备系统提示词或项目规则功能的 AI 工具：

| Platform | Recommended Usage | 推荐用法 |
|----------|-------------------|----------|
| **Antigravity / Gemini CLI** | Copy to `~/.gemini/antigravity/skills/` | 复制到 skills 文件夹 |
| **Cursor** | Copy `SKILL.md` content into `.cursorrules` | 将内容存入 `.cursorrules` |
| **Claude Code** | Paste as system prompt in `.clauderc` | 在 `.clauderc` 中配置 |
| **Trae / Windsurf / CodeX** | Paste as Project Instructions | 粘贴为项目级指令 (Custom Instructions) |
| **Web ChatGPT / Claude** | Paste `SKILL.md` at the start of conversation | 在会话开始时直接粘贴 |

---

## 🚀 Quick Start | 快速开始

In your conversation, simply say: | 在会话中输入：

| English | 繁/简中文 | Action / 动作 |
|---------|-----------|--------|
| "Teach me [Language]" | "我想学 [语言]" | Start full teaching flow |
| "Continue learning" | "继续学习" | Resume from last point |
| "Quiz me" | "考试模式" | Start zero-hint assessment |
| "Review" | "复习" | Target weak areas (★☆☆) |
| "Next exercise" | "下一题" | Skip current exercise |

---

## 📊 Mastery System | 掌握度系统

| Rating | Meaning | 含义 | Criteria / 判定标准 |
|--------|---------|------|-------------------|
| ★☆☆ | **Weak** | **薄弱** | Needed L3 (code) hint or full solution / 需要代码提示或答案 |
| ★★☆ | **OK** | **尚可** | Needed L1-L2 (conceptual) hints / 需要概念级提示 |
| ★★★ | **Mastery** | **掌握** | Zero hints, clean independent implementation / 零提示独立完成 |

---

## 🏗️ Architecture | 核心架构

### Six-Phase Cycle | 六步教学循环
1.  **Assessment | 诊断**: Adaptive code-based profiling. / 基于代码的自适应诊断。
2.  **Plan | 计划**: Modular path generation via meta-template. / 按元模板生成模块化路径。
3.  **Scaffold | 脚手架**: `TODO`-driven code templates. / `TODO` 驱动的代码模板。
4.  **Tutoring | 辅导**: Socratic debugging with 3-level hints. / 苏格拉底式辅导。
5.  **Project | 项目**: Real-world micro-project per module. / 每个模块一个真实微型项目。
6.  **Review | 总结**: Error analysis & mastery assessment. / 错误分析与掌握度评估。

### The "Iron Laws" | 钢铁定律
- **No direct fixes** / 禁止代写代码: AI never writes corrected code for the student. / AI 绝不为学生代写修复后的代码。
- **Analogy first** / 类比优先: Every concept explained via a physical-world analogy. / 每个概念都必须用物理世界的类比来解释。
- **Evidence required** / 证据为王: No progress credit without terminal test output. / 必须提供终端测试输出证据才能跳到下一步。

---

## 🤝 Contributing | 贡献

We welcome new language curricula and exercise patterns! | 欢迎提交新的语言课程和练习模式！
1.  Create `{language}.md` in `curriculum-templates/`.
2.  Add patterns to `exercise-patterns.md`.

## 📄 License | 协议

MIT License. (c) 2026 [JcDizzy](https://github.com/JcDizzy)

---

<p align="center">
  <i>"Don't just watch videos. Don't just read books. Write code."</i><br>
  <i>“不要只看视频，不要只看书。写代码。”</i>
</p>
