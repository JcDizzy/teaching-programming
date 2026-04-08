# Curriculum Meta-Template

Use this file when no language-specific curriculum already exists. Its purpose is to force the generated course to be broad, explicit, modular, and large enough to cover the target language seriously rather than producing a shallow crash course.

---

## Core Goal

When generating a curriculum for any target language, the tutor should aim to cover the language's full practical learning surface as far as it is relevant to the student's direction.

That means:

- cover fundamentals thoroughly
- cover the language's core paradigm deeply
- cover tooling, debugging, testing, and project structure explicitly
- cover the standard library and ecosystem, not just syntax
- cover common traps, anti-patterns, and failure modes
- cover advanced engineering usage when the language supports it

The curriculum should default toward being expansive and detailed. Trim only when the student's direction clearly makes a topic out of scope.

---

## Step 1: Build A Language Profile

Before generating modules, analyze the target language along these axes:

| Axis | Questions to Answer |
|------|---------------------|
| Paradigm | Is it procedural, object-oriented, functional, concurrent, logic-based, multi-paradigm, data-oriented, or ownership-based? |
| Type System | Static or dynamic? Strong or weak? Generic? Inferred? Gradually typed? |
| Memory Model | Garbage collection, ownership, reference counting, manual allocation, arena-based, stack-heavy? |
| Runtime Model | Native compiled, VM-based, interpreted, JIT, transpiled, REPL-first? |
| Concurrency Model | Threads, async/await, actors, goroutines, message passing, green threads, event loop? |
| Standard Tooling | Build tool, package manager, formatter, linter, test runner, debugger, profiler |
| Ecosystem Norms | How are projects usually organized? What libraries are foundational? |
| Interop Story | How does it interact with C, OS APIs, databases, browsers, JVM, JS, native libraries, etc.? |
| Safety Model | Error handling, nullability, overflow behavior, panic/exception model, borrow model, UB model |
| Student Direction | Backend, frontend, embedded, CLI, tooling, data, automation, systems, mobile, graphics, game dev, interview prep |

This profile controls which modules get extra depth, which examples to prefer, and which advanced topics are mandatory.

---

## Step 2: Coverage Contract

Every generated curriculum MUST attempt to cover the following topic families unless a family is genuinely not applicable to the language.

### Family A: Syntax And Surface Fundamentals

Must consider:

- lexical structure, tokens, identifiers
- literals and primitive values
- variables and mutability
- operators and precedence
- expressions and statements
- comments and documentation style
- formatting conventions

### Family B: Type System And Value Semantics

Must consider:

- primitive and composite types
- type inference and annotations
- coercion / conversion rules
- references, pointers, objects, values, or bindings
- equality, identity, comparison semantics
- nullability / optionality model
- generic / polymorphic type features where applicable

### Family C: Control Flow And Execution

Must consider:

- branching
- loops / iteration
- pattern matching if applicable
- recursion
- short-circuit behavior
- evaluation order traps
- scoping and lifetime basics

### Family D: Data Structures And Collections

Must consider:

- sequential collections
- associative collections
- sets
- strings and text encoding
- iterators / generators / traversals
- choosing data structures intentionally

### Family E: Functions, Abstractions, And Modularization

Must consider:

- function definition and calls
- parameters and return values
- higher-order functions / callbacks if applicable
- closures / lambdas if applicable
- modules, packages, namespaces, files
- import / export rules
- API boundary design

### Family F: Core Language Paradigm

This family must be one of the largest parts of the curriculum. It should deeply cover the language's defining ideas, for example:

- classes, objects, inheritance, interfaces
- ownership, borrowing, lifetimes
- closures, purity, immutability, algebraic data types
- pointers, structs, unions, function pointers
- prototypes, event loop, async model
- goroutines, channels, actor systems

### Family G: Error Handling, Safety, And Robustness

Must consider:

- error signaling model
- defensive programming
- input validation
- logging and observability basics
- language-specific safety guarantees and failure modes
- common traps and anti-patterns

### Family H: Build, Tooling, And Project Structure

Must consider:

- project layout
- build / package tools
- dependency management
- formatter / linter
- testing toolchain
- debug vs release workflow
- environment and configuration handling

### Family I: Standard Library And Everyday I/O

Must consider:

- file I/O
- parsing and formatting
- string processing
- date / time
- serialization formats
- networking basics when relevant
- process or system interaction when relevant

### Family J: Debugging, Testing, And Quality Practices

Must consider:

- unit tests
- integration tests
- debugging workflow
- assertions
- mocking / test doubles where relevant
- diagnosing runtime failures
- regression thinking

### Family K: Performance, Concurrency, And Systems Concerns

Must consider when applicable:

- concurrency model
- synchronization / coordination
- async execution
- memory behavior
- performance profiling
- algorithmic complexity
- optimization trade-offs

### Family L: Architecture, Ecosystem, And Domain Practice

Must consider:

- idiomatic project architecture
- reusable patterns
- common library choices
- domain-specific frameworks
- deployment/runtime concerns where relevant
- common mistakes seen in real projects

If a topic family is not applicable, the generated curriculum should explicitly say why instead of silently omitting it.

---

## Step 3: Module Planning Rules

The curriculum should usually contain 10 to 18 modules. Large, feature-rich, multi-paradigm languages may need more. Very small languages may need fewer, but should still preserve broad category coverage.

### Module Count Guidance

- Minimal serious curriculum: 10 modules
- Normal comprehensive curriculum: 12 to 16 modules
- Rich ecosystem / multi-domain curriculum: 16 to 20 modules

### Module Naming

Use `NN_descriptive_name/`, for example:

- `01_foundations/`
- `02_types_and_values/`
- `03_collections/`
- `04_functions_and_modules/`

### Every Module Must Include

- purpose / learning outcome
- prerequisite modules
- estimated time
- core knowledge points
- likely bug patterns / traps
- 4 to 8 exercises
- 1 micro-project or strong integrative challenge

### Exercise Volume Guidance

Prefer more exercises over fewer:

- early modules: 5 to 8 smaller exercises
- middle modules: 4 to 7 exercises
- advanced modules: 3 to 6 harder exercises
- each module: 1 micro-project or capstone-like integrative task

### Scaffolding Guidance

- beginner-heavy modules: 70 to 90 percent of structure provided
- intermediate modules: 40 to 70 percent of structure provided
- advanced modules: 20 to 50 percent of structure provided
- micro-projects: requirements first, implementation more student-owned

### Lesson File Volume

The curriculum should not artificially compress content. A module may contain:

- multiple code exercises
- multiple review exercises
- multiple note files
- helper files
- mini-project folders

---

## Step 4: Knowledge Map Expansion Rules

For each generated module, list knowledge points at two levels:

1. **Primary concepts**
2. **Subtopics / traps / practical details**

Bad:

- "Functions"

Good:

- Function declaration vs definition
- Parameter passing model
- Default mutability assumptions
- Variadic support if any
- Named / positional / keyword arguments if any
- Stack behavior / call overhead if relevant
- Common mistakes with argument ownership / aliasing / capture

This prevents vague, under-detailed curricula.

---

## Step 5: Diagnostic Question Rules

Phase 1 diagnostics must match the current teaching workflow.

### Required Rule

Generate **3 to 5 diagnostics**, and ask them **from hard to easy**.

The default sequence is:

1. advanced diagnostic
2. intermediate diagnostic
3. beginner diagnostic

Add a 4th or 5th question only if the level is still ambiguous.

### Diagnostic Coverage Rules

Across the full set of 3 to 5 questions, cover multiple axes such as:

- syntax or semantics
- language core paradigm
- runtime / memory / safety model
- debugging ability
- architecture or performance awareness

### Diagnostic Design Rules

- Questions should be code-based or scenario-based.
- Do not ask only self-report questions.
- Prefer realistic bug or design scenarios.
- The first question should be the hardest reasonable question for the language and direction.
- Only stop before 5 if the student level is unmistakably clear after at least 3 prompts.

### Diagnostic Outcome Mapping

- Fails hard question, handles medium question: likely intermediate
- Fails medium and beginner question: likely beginner
- Handles hard question with good explanation: likely advanced
- Mixed answers: ask 1 to 2 tie-breaker questions

### Diagnostic Question Formats

Prefer:

- "What is the bug and why does it happen?"
- "What happens when this code runs?"
- "Why will this design fail under load / at scale / after repetition?"
- "How would you make this safer / more idiomatic?"

Avoid:

- trivia-only questions
- toy puzzles with no engineering relevance
- definitions copied from textbooks

---

## Step 6: Exercise Topic Selection

Choose exercise themes using this priority:

1. student's real target domain
2. reusable engineering building blocks
3. language-specific traps and idioms
4. interview-style problems only when interview prep is the actual goal

### Strong Exercise Themes

- parsers
- validators
- state machines
- schedulers
- command dispatchers
- file transformers
- configuration handling
- protocol handling
- async orchestration
- memory-safe wrappers
- serialization / deserialization
- concurrency-safe data flow

### Weak Exercise Themes

- pattern printing
- filler arithmetic drills
- puzzles disconnected from the target language's real strengths
- shallow "hello world but renamed"

---

## Step 7: Micro-Project Rules

Each module-level micro-project must:

- integrate at least 3 concepts from current and prior modules
- produce something plausibly reusable
- fit the student's target direction when possible
- have concrete verification criteria
- be meaningfully harder than a normal exercise

### Micro-Project Sizing

| Stage | Typical Scope | Suggested Time |
|-------|---------------|----------------|
| Early | single-file utility or parser | 1 to 2 hours |
| Middle | multi-function component | 2 to 4 hours |
| Late | multi-file subsystem | 4 to 8 hours |
| Final | capstone or mini-system | 6 to 12+ hours |

---

## Step 8: Domain Adaptation Rules

Once the general curriculum is generated, bias examples and projects toward the student's direction:

### Embedded / Systems

- memory layout
- bit manipulation
- register or hardware abstractions
- buffers
- timing
- low-level debugging

### Web / Backend

- request handling
- serialization
- error boundaries
- concurrency / async
- persistence
- modular service structure

### CLI / Tooling

- argument parsing
- file operations
- terminal output
- config files
- logging
- packaging

### Data / Automation

- file parsing
- transformation pipelines
- structured data formats
- scripting ergonomics
- library ecosystems

### Mobile / UI

- state management
- lifecycle / event model
- async data flow
- architecture boundaries

---

## Step 9: Output Requirements For The Generated Curriculum

The generated curriculum should be explicit enough that a future tutoring session can create the workspace without improvising structure.

The curriculum output should include:

- module list
- lesson list per module
- detailed knowledge points per module
- example exercise topics
- micro-project ideas
- prerequisites
- estimated time
- review suggestions for likely weak areas

The first generated `README.md` plan should feel substantial, not skeletal.

---

## Example Module Skeleton

```markdown
## Module 04: Functions And Modules
Prerequisites: Modules 01-03
Estimated time: 8-12 hours

Core knowledge points:
- Function declaration vs definition
- Parameter passing semantics
- Closures / callbacks / lambdas if applicable
- Scope boundaries
- Module organization
- Import/export rules
- API design basics

Common traps:
- Accidental shared state
- Wrong ownership or lifetime assumptions
- Circular imports
- Leaky abstractions

Exercises:
- ex_4_1_callback_pipeline
- ex_4_2_module_boundary_refactor
- ex_4_3_safe_formatter
- ex_4_4_config_loader
- review_4_1_scope_and_lifetime

Micro-project:
- Build a reusable config parsing module with validation and tests
```

---

## Final Standard

If the generated curriculum looks like a short tutorial outline, it is too small.

If it skips tooling, debugging, testing, or common pitfalls, it is incomplete.

If it only teaches syntax and never reaches real engineering tasks, it has failed the purpose of this skill.
