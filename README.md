# Teaching Programming Skill

A reusable skill that turns an AI coding assistant into a structured programming tutor for learning workflows across programming languages and coding environments.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## What It Does

- Creates a dedicated study workspace before real teaching begins
- Assesses the learner with 3 to 5 diagnostics in descending difficulty
- Builds a broad curriculum with lesson plans, TODOs, notes, and progress tracking
- Uses Socratic tutoring instead of giving the answer immediately
- Verifies completed work by compiling or running code whenever possible
- Writes mastery updates back into `README.md` after each lesson or review

## Core Workflow

The skill follows a consistent teaching loop:

1. Assess the student's level with 3 to 5 code-based diagnostics.
2. Create a study workspace and course `README.md`.
3. Generate lessons with runnable exercise files and notes.
4. Guide the student with staged hints.
5. Compile or run submitted work before judging correctness.
6. Record progress and mastery after each lesson or review.

## Study Workspace Structure

The skill expects each module to use a clean layout:

```text
[study-root]/
  README.md
  01_topic/
    code/
      ex_1_1_topic.ext
      review_1_1_topic.ext
    notes/
      notes_1_1_topic.md
    bin/
      ex_1_1_topic.exe
  02_topic/
    code/
    notes/
    bin/
  shared/
    build-or-run-notes.md
```

This keeps source files, notes, and compiled outputs separated inside each chapter.

## Key Teaching Rules

### Level Assessment

- New courses start with 3 to 5 diagnostics
- Questions go from hard to easy
- Diagnostics happen before the real lesson plan starts
- The student is classified as `beginner`, `intermediate`, or `advanced`

### Lesson Generation

- The curriculum must be broad enough to cover the language systematically
- Each lesson may have multiple TODOs and multiple teaching files
- Every new file and TODO should be recorded in the workspace `README.md`

### Verification

- When a student finishes a TODO, the tutor should first try to compile or run it
- If the environment allows automatic verification, the tutor should use it
- The tutor should not say code is correct based only on visual inspection

### Mastery Tracking

- `Weak`: needed heavy hints or the full solution
- `OK`: completed with some guidance
- `Mastered`: completed independently and cleanly

Mastery must be written back into the workspace `README.md` after each completed lesson and each completed review.

## Files In This Skill

- [SKILL.md](./SKILL.md): the main instruction set
- [exercise-patterns.md](./exercise-patterns.md): patterns for exercise generation
- [curriculum-templates/](./curriculum-templates/): language curriculum templates

## Usage

Use this skill when the learner says things like:

- `Teach me C`
- `Help me study Python`
- `Continue learning`
- `Review`
- `Quiz me`

It should not be used for ordinary production coding requests where the user just wants the implementation.

## Platform Notes

This repository is skill-first. The main artifact is [`SKILL.md`](./SKILL.md). You can adapt it to environments that support reusable instructions, prompt rules, or skill loading.

## License

MIT License. Copyright (c) 2026 [JcDizzy](https://github.com/JcDizzy)
