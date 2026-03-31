# 🎓 Teaching Programming Skill

> A programming tutor agent skill.
> Teaches any programming language through TODO-driven scaffolding, Socratic questioning, and real-world engineering exercises.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## ✨ Features

- 🧠 **Dynamic Level Assessment** — Diagnoses skill level through code traps, not questionnaires (1-5 adaptive questions)
- 📚 **Universal Curriculum Engine** — Pre-built C course + meta-template for generating curricula for ANY language
- 🧩 **TODO-Driven Exercises** — Scaffolded code templates with progressive difficulty and auto-verification
- 🏛️ **Socratic Tutoring** — 3-level hint system (Conceptual → Structural → Code Fragment), never gives direct answers
- 🏗️ **Micro-Projects** — Real-world engineering deliverables at the end of each module
- 📊 **Mastery Tracking** — ★☆☆ / ★★☆ / ★★★ per-exercise proficiency ratings
- 📝 **Exam Mode** — Zero-hint testing with post-submission scoring and weakness analysis
- 🔄 **Review Mode** — Mastery-driven review with adaptive intensity (deep review vs quick refresher)
- 💾 **Cross-Session Continuity** — Resumes exactly where you left off, greets you by name

## 📦 Installation

### Option 1: Copy to skills directory

```bash
# Clone the repo
git clone https://github.com/JcDizzy/teaching-programming.git

# Copy to your skills directory
# Windows:
xcopy /E /I teaching-programming "%USERPROFILE%\.gemini\antigravity\skills\teaching-programming"

# macOS/Linux:
cp -r teaching-programming ~/.gemini/antigravity/skills/teaching-programming
```

### Option 2: Symlink (recommended for development)

```bash
# Windows (run as admin):
mklink /D "%USERPROFILE%\.gemini\antigravity\skills\teaching-programming" "path\to\cloned\repo"

# macOS/Linux:
ln -s /path/to/cloned/repo ~/.gemini/antigravity/skills/teaching-programming
```

## 🚀 Quick Start

In any Gemini CLI conversation, say:

| You say | What happens |
|---------|-------------|
| "我想学C语言" / "teach me Python" | Full teaching flow (assessment → curriculum → exercises) |
| "继续学习" / "continue my learning" | Resume from where you left off |
| "考试模式" / "quiz me" | Zero-hint exam, scored after submission |
| "复习" / "review" | Review weak areas based on mastery ratings |
| "下一题" / "next exercise" | Skip to next exercise |

## 📖 How It Works

### Teaching Flow

```
Phase 1: Dynamic Assessment     Code-based skill diagnosis (not questionnaires)
    ↓
Phase 2: Curriculum Design      Generates modular learning path for any language
    ↓
Phase 3: Exercise Generation    TODO-scaffolded templates with auto-verification
    ↓
Phase 4: Socratic Tutoring      Guided by questions + 3-level hint system
    ↓
Phase 5: Micro-Projects         Real-world integration project per module
    ↓
Phase 6: Review & Mastery       Error analysis + ★-ratings + review suggestions
```

### Mastery System

| Rating | Meaning | Criteria |
|--------|---------|----------|
| ★☆☆ | Weak — needs review | Needed L3 hint or full solution |
| ★★☆ | OK — understood with guidance | Needed L1-L2 hints |
| ★★★ | Mastered — independent | Zero hints, clean solution |

### Three-Level Hint System

| Level | Type | Example |
|-------|------|---------|
| L1 | Conceptual question | "What happens to a pointer after `free()`?" |
| L2 | Pseudocode outline | "Three steps: create mask → clear bits → OR new value" |
| L3 | Code fragment | "`result &= ~mask;` — how do you set new bits?" |

## 🗂️ Supported Languages

| Language | Status | Notes |
|----------|--------|-------|
| **C** | ✅ Pre-built curriculum | 10 modules, diagnostic question bank |
| Any other | ✅ Dynamic generation | Auto-generated via TEMPLATE.md |

> The meta-template (`TEMPLATE.md`) defines 8 mandatory categories ensuring comprehensive coverage for any language: Foundations → Collections → Functions → Core Paradigm → Error Handling → Build System → StdLib → Advanced.

## 📁 Project Structure

```
teaching-programming/
├── SKILL.md                          # Core AI instructions (the "brain")
├── README.md                         # This file
├── LICENSE                           # MIT License
├── .gitignore
├── exercise-patterns.md              # 5 exercise design patterns
└── curriculum-templates/
    ├── TEMPLATE.md                   # Universal meta-template for any language
    └── c-language.md                 # C language curriculum (10 modules)
```

## 🎯 Design Principles

### Four Iron Laws

1. **Socratic Debugging** — AI never writes corrected code; only asks guiding questions
2. **Analogy-First** — Every concept explained via physical-world analogy, not documentation
3. **One Concept Per Exercise** — No overloading; each exercise focuses on exactly one thing
4. **Real-World Only** — No FizzBuzz, no toy problems; every exercise simulates a real scenario

### Anti-Rationalization Defenses

The skill includes **14 Red Flags**, **10 Rationalization Guards**, and a **"Violating the letter is violating the spirit"** statement to prevent the AI from taking shortcuts.

## 🔧 Customization

### Adding a new language curriculum

Create `curriculum-templates/{language}.md` following the structure in `c-language.md`:
- List all modules with sub-topics
- Include micro-projects per module
- Add a diagnostic question bank

Or let the AI generate one automatically — just say "teach me [language]" and it will use `TEMPLATE.md`.

### Adjusting teaching style

Edit `SKILL.md`:
- **More lenient**: Lower the L3→full-answer threshold
- **More strict**: Remove L3, keep only L1/L2 hints
- **Domain-specific**: Add domain examples to exercise patterns

## 🤝 Contributing

Contributions are welcome! Here's how:

1. **New language curricula** — Add a pre-built curriculum in `curriculum-templates/`
2. **Exercise patterns** — Add new patterns to `exercise-patterns.md`
3. **Bug reports** — Open an issue if the AI misbehaves during teaching
4. **Translations** — The skill supports any language; help translate exercise templates

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

<p align="center">
  <i>Built with ❤️ for learners who believe the best way to learn programming is by writing code, not reading about it.</i>
</p>
