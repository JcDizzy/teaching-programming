# Curriculum Meta-Template

When no pre-built curriculum exists for a target language, use this template to dynamically
generate a comprehensive, structured learning path. This ensures consistent quality and
coverage regardless of the programming language.

---

## Step 1: Language Profile

Before generating modules, analyze the target language along these axes:

| Axis | Question | Example (Java) | Example (Rust) |
|------|----------|----------------|----------------|
| **Paradigm** | OOP? Functional? Procedural? Multi? | OOP + Multi | Multi-paradigm, ownership-based |
| **Type System** | Static/Dynamic? Strong/Weak? | Static, strong | Static, strong, affine types |
| **Memory Model** | GC? Manual? Ownership? | Garbage collected | Ownership + borrowing |
| **Runtime** | Compiled? Interpreted? VM? | JVM bytecode | Compiled (LLVM) |
| **Ecosystem** | Build tool? Package manager? | Maven/Gradle, Maven Central | Cargo, crates.io |
| **Primary Domain** | What is it mainly used for? | Enterprise, Android, backend | Systems, CLI, WebAssembly |
| **Student's Direction** | What does the student want to build? | Android apps / Spring backend | CLI tools / embedded |

This profile determines which modules get more depth and what kind of exercises to generate.

---

## Step 2: Mandatory Module Categories

Every language curriculum MUST cover these 8 categories, regardless of the language. The specific
content within each category adapts to the language's paradigm and features.

### Category A: Foundations
*Always Module 01. No prerequisites.*

Must cover:
- [ ] Data types (primitives, type system, type inference if applicable)
- [ ] Variables (mutability, naming conventions, scope rules)
- [ ] Operators (arithmetic, logical, comparison, language-specific operators)
- [ ] Control flow (conditionals, loops, pattern matching if applicable)
- [ ] Basic I/O (printing, reading input)
- [ ] Comments and documentation conventions

**Adapt for language:**
- Dynamic languages (Python, JS): emphasize type coercion traps
- Static languages (Java, Rust, Go): emphasize type annotations and inference
- Low-level languages (C, Rust): emphasize numeric overflow and bit-level representation

### Category B: Data Structures & Collections
*Prerequisites: A*

Must cover:
- [ ] Arrays / Lists / Vectors (the primary sequential container)
- [ ] Strings (representation, manipulation, encoding)
- [ ] Maps / Dictionaries / HashMaps
- [ ] Sets
- [ ] Iterators and iteration patterns
- [ ] Choosing the right data structure

**Adapt for language:**
- Languages with generics (Java, Rust, C++): cover generic collections
- Dynamic languages (Python, JS): cover duck typing with collections
- Low-level (C): cover manual array management, `struct` arrays

### Category C: Functions & Modularity
*Prerequisites: B*

Must cover:
- [ ] Function definition, parameters, return values
- [ ] Scope and lifetime rules
- [ ] Higher-order functions (if the language supports them)
- [ ] Closures / lambdas (if applicable)
- [ ] Modules / packages / namespaces (code organization)
- [ ] Import/export mechanisms

**Adapt for language:**
- Functional languages (Haskell, Elixir): closures and HOF are central, cover early
- OOP languages (Java, C#): methods belong with classes (Category D)
- C: header files, linkage, `static` vs `extern`

### Category D: Language-Specific Core Paradigm
*Prerequisites: C*

This is the category that varies MOST by language. Cover the language's PRIMARY paradigm deeply.

| Language Type | Core Paradigm Content |
|--------------|----------------------|
| **OOP** (Java, C#, Python) | Classes, inheritance, polymorphism, interfaces, abstract classes, encapsulation |
| **Ownership** (Rust) | Ownership, borrowing, lifetimes, the borrow checker, `Clone` vs `Copy` |
| **Functional** (Haskell, Elixir) | Pure functions, immutability, monads/pattern matching, recursion |
| **Procedural** (C) | Pointers, memory management, structs, function pointers |
| **Prototype** (JavaScript) | Prototypes, `this` binding, closures, async/await |
| **Concurrent** (Go) | Goroutines, channels, select, sync primitives |

**This is typically the LARGEST module (or 2-3 modules) in any curriculum.**

### Category E: Error Handling & Robustness
*Prerequisites: D*

Must cover:
- [ ] Error handling mechanism (exceptions, Result types, error codes)
- [ ] Defensive programming patterns
- [ ] Input validation
- [ ] Logging and debugging techniques
- [ ] Language-specific safety features

**Adapt for language:**
- Java/Python: try-catch-finally, custom exceptions, exception hierarchies
- Rust: `Result<T, E>`, `Option<T>`, `?` operator, `unwrap` dangers
- Go: multiple return values, `error` interface, `defer`
- C: return codes, `errno`, goto-cleanup pattern

### Category F: Project Structure & Build System
*Prerequisites: E*

Must cover:
- [ ] Project directory conventions
- [ ] Build tool usage (compilation, dependencies, tasks)
- [ ] Dependency management
- [ ] Testing frameworks and test organization
- [ ] Debug vs release configurations

**Adapt for language:**
- Java: Maven/Gradle, `src/main/java`, JUnit
- Rust: Cargo, `src/`, `tests/`, `cargo test`
- Python: pip/poetry, `__init__.py`, pytest
- C: CMake/Make, header organization, Unity/CUnit
- JavaScript: npm/pnpm, `package.json`, Jest/Vitest

### Category G: Standard Library & Ecosystem
*Prerequisites: F*

Must cover:
- [ ] File I/O
- [ ] String processing (regex, formatting, parsing)
- [ ] Date/time handling
- [ ] Networking basics (HTTP, sockets — at appropriate level)
- [ ] JSON/XML/data serialization
- [ ] Key third-party libraries for the student's direction

**Adapt for student's direction:**
- If embedded: hardware I/O, serial, register manipulation
- If web: HTTP frameworks, routing, middleware
- If data science: data manipulation libraries, plotting
- If CLI: argument parsing, terminal formatting

### Category H: Advanced Topics & Architecture
*Prerequisites: G*

Must cover:
- [ ] Concurrency / parallelism (language-specific model)
- [ ] Design patterns relevant to the language
- [ ] Performance optimization techniques
- [ ] Testing strategies (unit, integration, mocking)
- [ ] Common anti-patterns and pitfalls

**Plus domain-specific advanced topics based on student's direction.**

---

## Step 3: Module Generation Rules

1. **Number of modules**: 8-12 total (map categories to modules, split large categories)
2. **Naming**: `NN_descriptive_name/` (e.g., `01_foundations/`, `05_error_handling/`)
3. **Each module MUST have**:
   - 3-6 concept exercises (scaffolded, TODO-based)
   - 1 micro-project (integrates 3+ concepts from the module)
   - Clear prerequisites listed
   - Estimated time (hours)
4. **Exercise naming**: `ex_M_N_topic.{ext}` (M=module, N=exercise, ext=language extension)
5. **Progressive scaffolding**:
   - Modules 01-03: 80-90% code provided (beginner)
   - Modules 04-06: 50-70% code provided (intermediate)
   - Modules 07+: 30-40% code provided (advanced)

## Step 4: Exercise Topic Selection

When choosing exercise topics, follow this priority:

1. **Student's actual domain first** — What are they going to build? Use scenarios from that domain.
2. **Universal engineering patterns** — File parsing, data validation, state machines, protocol handling.
3. **Interview-style problems** — ONLY if the student's goal is interview prep. Otherwise, avoid.

**NEVER use** (Iron Law #4):
- Pure math puzzles (FizzBuzz, Fibonacci) unless illustrating recursion
- "Print a pattern" exercises
- Contrived scenarios with no real-world application
- Tutorial clichés ("TodoList app" for web, "Calculator" for desktop)

**ALWAYS prefer**:
- Building blocks the student will reuse (parsers, validators, state machines)
- Exercises that connect to the student's hardware/platform (if embedded)
- Problems that expose language-specific traps (memory leaks, race conditions, type coercion)

---

## Step 5: Diagnostic Question Generation

For Phase 1 Assessment, generate 3 diagnostic questions at increasing difficulty:

### Beginner Diagnostic
- Tests: basic syntax knowledge + one common trap
- Format: "What does this code print?" with a subtle type/scope issue
- If student gets this wrong → start from Module 01

### Intermediate Diagnostic
- Tests: understanding of the core paradigm (Category D)
- Format: "This code has a bug that only manifests after X minutes/iterations. What is it?"
- If student gets this wrong → start from Module 03-04

### Advanced Diagnostic
- Tests: architecture thinking + concurrency/performance awareness
- Format: "This system design will fail under load. Why? How would you fix it?"
- If student gets this right → start from Module 07+

---

## Step 6: Micro-Project Design

Each micro-project MUST:

1. **Integrate 3+ concepts** from the current and previous modules
2. **Produce a usable deliverable** (not throwaway code)
3. **Match the student's direction** (embedded → firmware component, web → API endpoint, etc.)
4. **Have automated acceptance tests** + clear pass/fail criteria
5. **Be significantly harder** than individual exercises (stretch goal)

**Micro-project sizing guide:**
| Module Range | Complexity | Estimated Time |
|-------------|-----------|----------------|
| 01-03 | Single-file, focused utility | 1-2 hours |
| 04-06 | Multi-function, data + logic | 2-4 hours |
| 07-09 | Multi-file, architecture required | 4-6 hours |
| 10+ (capstone) | Complete mini-system | 6-10 hours |

---

## Example: Generating a Java Curriculum

**Student profile:** "I want to learn Java for Android development"

**Generated modules:**
```
01_foundations/        — Types, operators, control flow (Java-specific: autoboxing traps)
02_collections/        — ArrayList, HashMap, iterators, Stream API basics
03_oop_fundamentals/   — Classes, constructors, inheritance, toString/equals/hashCode
04_oop_advanced/       — Interfaces, abstract classes, polymorphism, design patterns
05_error_handling/     — Exceptions hierarchy, try-with-resources, custom exceptions
06_generics_lambdas/   — Generics, wildcards, functional interfaces, lambda expressions
07_project_structure/  — Gradle, JUnit, project layout, dependency management
08_concurrency/        — Threads, ExecutorService, synchronized, volatile, CompletableFuture
09_android_basics/     — Activity lifecycle, Views, Intents, RecyclerView (domain-specific)
10_android_advanced/   — Room database, ViewModel, LiveData, coroutines (domain-specific)
```

**Diagnostic questions:**
- Beginner: "What prints?" — `Integer a = 128; Integer b = 128; System.out.println(a == b);` (tests autoboxing cache)
- Intermediate: "This code leaks memory in an Android app. Why?" — (tests Activity lifecycle + listener registration)
- Advanced: "This network request crashes the app. Why?" — (tests main thread + coroutine understanding)
