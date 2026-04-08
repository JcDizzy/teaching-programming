# C Language Curriculum Template (Comprehensive And Expanded)

Use this template when the target language is C. It is meant to be broad enough to support:

- general C learning
- systems programming
- embedded development
- command-line tools
- protocol and binary data handling
- performance-conscious native programming

This template deliberately aims for large coverage. It should feel closer to a real learning track than to a lightweight intro.

---

## How To Use This Template

1. Run Phase 1 assessment first.
2. Ask 3 to 5 diagnostics from hard to easy.
3. Use the answers to choose the starting module and decide which modules need extra depth.
4. Do not shrink the curriculum into only syntax basics. Preserve broad coverage.
5. If the student has a strong direction such as embedded, systems, tooling, or algorithms, bias projects and examples toward that direction.

---

## Coverage Standard For C

The generated C curriculum should attempt to cover all major practical C knowledge areas:

- language syntax and expression rules
- scalar types and integer / floating-point behavior
- arrays, strings, and memory layout
- pointers, pointer arithmetic, aliasing, and const correctness
- structs, unions, enums, bit-fields, and packed layouts
- preprocessing and compilation model
- storage duration, scope, linkage, and translation units
- dynamic memory management
- standard library usage
- file I/O and binary data handling
- error handling and defensive programming
- testing, debugging, sanitizers, and profiling
- multi-file project structure and build systems
- data structures and generic C design patterns
- concurrency basics, atomics, and POSIX interfaces where relevant
- undefined behavior, portability, and platform differences
- performance thinking and low-level reasoning

---

## Curriculum Overview

Recommended full curriculum size: 12 to 16 modules.

The following template defines 14 modules so the tutor can stay broad while still being modular.

---

## Module 01: Foundations And Expression Semantics (01_foundations)
Prerequisites: none
Estimated time: 6 to 8 hours

### Must Cover

- source file structure
- comments and style basics
- variables and initialization
- integer types and floating-point types
- signed vs unsigned
- fixed-width types vs platform-dependent types
- literals and suffixes
- operators and precedence
- implicit conversions and promotions
- basic control flow
- basic standard I/O

### Subtopics And Traps

- integer promotion surprises
- signed overflow as undefined behavior
- unsigned wraparound
- `sizeof` on types vs expressions
- precedence bugs like `a & 0xFF == 0`
- `switch` fallthrough

### Exercise Ideas

- expression bug hunt
- safe average calculator
- numeric overflow detector
- state-driven text classifier
- mini command parser using `switch`

### Micro-Project

Build a small sensor-readout summarizer that ingests a fixed list of readings, prints categorized status, and produces min / max / average safely.

---

## Module 02: Arrays, Strings, And Memory Representation (02_arrays_strings)
Prerequisites: Module 01
Estimated time: 6 to 8 hours

### Must Cover

- array declaration and indexing
- array decay
- stack arrays
- string literals and mutable char arrays
- null terminators
- `strlen` vs `sizeof`
- copying and concatenation basics
- memory-oriented functions

### Subtopics And Traps

- off-by-one writes
- uninitialized arrays
- buffer overflow patterns
- missing `\0`
- using `strncpy` incorrectly
- string literal mutability mistakes

### Exercise Ideas

- implement safe string length
- bounded copy and append helpers
- array statistics
- token scanning without buffer overruns
- string normalization helper

### Micro-Project

Build a CSV line parser that safely splits, validates, and formats fields without overflowing buffers.

---

## Module 03: Functions, Scope, Storage Duration, And Linkage (03_functions_and_scope)
Prerequisites: Module 02
Estimated time: 5 to 7 hours

### Must Cover

- function declarations and definitions
- parameter passing
- return values
- local vs file-scope identifiers
- storage duration
- scope rules
- `static` local variables
- internal vs external linkage
- declaration vs definition

### Subtopics And Traps

- assuming C is pass-by-reference
- duplicate definitions
- declaring in headers incorrectly
- hidden shared state in `static` locals
- header / source responsibility

### Exercise Ideas

- counter with `static` local state
- API split into `.h` and `.c`
- return-through-output-parameter function
- scope bug identification

### Micro-Project

Build a reusable statistics module with a header, implementation file, and a demo application.

---

## Module 04: Pointers And Pointer Reasoning (04_pointers)
Prerequisites: Module 03
Estimated time: 8 to 10 hours

### Must Cover

- addresses and dereferencing
- pointer types
- null pointers
- pointer arithmetic
- arrays vs pointers
- pointer parameters
- pointer-to-pointer
- `void *`
- const correctness

### Subtopics And Traps

- dereferencing invalid pointers
- using freed or uninitialized pointers
- confusing `int *p[10]` with `int (*p)[10]`
- pointer arithmetic scaling
- `const int *` vs `int * const`

### Exercise Ideas

- swap via pointers
- min/max via output parameters
- reverse array via pointer arithmetic
- dynamic string table traversal
- generic byte buffer inspector using `void *`

### Micro-Project

Build a reusable buffer utilities module that slices, copies, scans, and validates byte ranges safely.

---

## Module 05: Dynamic Memory And Resource Ownership (05_dynamic_memory)
Prerequisites: Module 04
Estimated time: 7 to 9 hours

### Must Cover

- stack vs heap
- `malloc`, `calloc`, `realloc`, `free`
- ownership and lifetime
- dangling pointers
- double free
- leaks
- allocation failure handling
- `realloc` safety pattern

### Subtopics And Traps

- losing the original pointer on `realloc` failure
- freeing memory twice
- leaking on early returns
- using memory after free
- mismatched ownership contracts

### Exercise Ideas

- growable dynamic array
- heap-based string duplication helper
- safe reallocation wrapper
- ownership annotation review exercise

### Micro-Project

Build a dynamically growing line reader or token buffer that safely expands and never leaks on failure paths.

---

## Module 06: Structs, Enums, Unions, And Layout (06_structs_and_layout)
Prerequisites: Module 05
Estimated time: 7 to 9 hours

### Must Cover

- struct declaration and initialization
- designated initializers
- member access
- pointer-to-struct
- enums for states and categories
- unions for shared representation
- tagged union pattern
- padding and alignment
- `offsetof`
- packed layouts and caveats

### Subtopics And Traps

- accidental padding assumptions
- unsafe packed struct access
- abusing unions for type punning without care
- enum-to-string maintenance problems
- invalid tagged union states

### Exercise Ideas

- optimize struct field order
- tagged union value type
- packet header parser
- enum-driven state machine

### Micro-Project

Build a binary record reader that parses file headers, validates metadata, and prints a structured summary.

---

## Module 07: Bit Operations And Binary Data (07_bits_and_binary)
Prerequisites: Module 06
Estimated time: 5 to 7 hours

### Must Cover

- bitwise operators
- masks
- set / clear / toggle / test
- shifts
- packed flags
- field extraction
- endianness
- checksums and compact data representation

### Subtopics And Traps

- shifting signed values
- precedence mistakes in masks
- endian assumptions
- bit-field portability confusion

### Exercise Ideas

- generic bitset
- permission flags
- RGB packed color parser
- simple checksum validator

### Micro-Project

Build a compact permission or device-status system that encodes many flags into a fixed-size integer and prints a readable report.

---

## Module 08: Preprocessor, Compilation, And Build Model (08_preprocessor_and_build)
Prerequisites: Module 07
Estimated time: 6 to 8 hours

### Must Cover

- macros
- header guards
- conditional compilation
- predefined macros
- translation units
- preprocessing, compiling, assembling, linking
- object files and executables
- static vs dynamic linkage at a high level
- Make or CMake basics
- warning flags and optimization levels

### Subtopics And Traps

- macro side effects
- function-like macros without parentheses
- definitions inside headers
- missing include guards
- assuming one `.c` file can see another's private names

### Exercise Ideas

- logging macro with file/line info
- convert monolithic file into module split
- build with warning flags and fix warnings
- include-guard bug hunt

### Micro-Project

Refactor an earlier project into a clean multi-file build with headers, source files, and a reproducible build script.

---

## Module 09: Standard Library Deep Dive (09_standard_library)
Prerequisites: Module 08
Estimated time: 7 to 9 hours

### Must Cover

- `<string.h>`
- `<stdio.h>`
- `<stdlib.h>`
- `<stdint.h>`
- `<stdbool.h>`
- `<ctype.h>`
- `<assert.h>`
- `<time.h>`
- `<stdarg.h>`
- `<errno.h>`

### Subtopics And Traps

- `sprintf` vs `snprintf`
- `atoi` vs `strtol`
- binary vs text mode
- misuse of variadic functions
- format string vulnerabilities

### Exercise Ideas

- robust integer parser
- variadic mini logger
- binary file dumper
- text normalization helper
- log formatter

### Micro-Project

Build a log analyzer that parses files, filters entries, summarizes data, and sorts or groups results.

---

## Module 10: Error Handling, Defensive Programming, And Debugging (10_robustness_and_debugging)
Prerequisites: Module 09
Estimated time: 7 to 9 hours

### Must Cover

- return-code based APIs
- `errno`
- cleanup paths
- `goto` cleanup pattern
- assertions
- defensive parameter validation
- logging
- debugger basics
- sanitizers
- common crash investigation steps

### Subtopics And Traps

- swallowing errors
- partial cleanup bugs
- assertions in the wrong places
- failing to preserve useful context
- undefined behavior hidden until optimization

### Exercise Ideas

- refactor multiple cleanup exits into one safe cleanup flow
- detect memory bugs with sanitizers
- debug a crashing parser
- add robust validation and error reporting

### Micro-Project

Build a robust configuration parser that reports detailed errors, cleans up safely, and survives malformed input.

---

## Module 11: Data Structures And Generic Patterns In C (11_data_structures)
Prerequisites: Module 10
Estimated time: 8 to 10 hours

### Must Cover

- linked lists
- stacks and queues
- hash tables
- trees
- dynamic arrays
- ownership strategy in data structures
- generic patterns with `void *`
- callback-based APIs

### Subtopics And Traps

- who owns nodes and payloads
- shallow copy vs deep copy confusion
- invalid iterator assumptions
- resizing mistakes
- generic API ergonomics in plain C

### Exercise Ideas

- generic linked list
- stack / queue module
- hashmap with string keys
- sorted records with `qsort`

### Micro-Project

Build an in-memory key-value store or symbol table with persistence and tests.

---

## Module 12: File Formats, Serialization, And Systems I/O (12_io_and_system_interfaces)
Prerequisites: Module 11
Estimated time: 7 to 9 hours

### Must Cover

- file streams
- binary file layouts
- parsing structured data
- command-line arguments
- environment variables
- low-level file descriptors where relevant
- process basics or OS APIs where direction requires
- serialization and deserialization patterns

### Subtopics And Traps

- partial reads / writes
- text vs binary confusion
- trusting external file structure
- endian and packing mismatches

### Exercise Ideas

- binary header parser
- custom record serializer
- CLI file transformer
- safe temp-file workflow

### Micro-Project

Build a file indexer, packer, or binary inspection tool depending on student direction.

---

## Module 13: Concurrency, Atomics, And Parallel Work (13_concurrency)
Prerequisites: Module 12
Estimated time: 7 to 10 hours

### Must Cover When Relevant

- POSIX threads basics
- mutexes
- condition variables
- race conditions
- `<stdatomic.h>`
- thread-safe queue patterns
- producer / consumer design
- lock ordering and deadlocks

### Subtopics And Traps

- unsynchronized shared state
- data races on counters
- deadlocks from inconsistent locking
- false assumptions about atomicity

### Exercise Ideas

- thread-safe counter
- producer-consumer queue
- parallel work scheduler
- race condition diagnosis exercise

### Micro-Project

Build a thread-safe message queue or file-processing pipeline with measurable correctness guarantees.

---

## Module 14: Performance, Portability, And Advanced Engineering (14_performance_and_portability)
Prerequisites: Module 13
Estimated time: 8 to 10 hours

### Must Cover

- profiling before optimizing
- memory locality
- algorithmic complexity
- branch prediction awareness
- `restrict`
- `inline` vs macros
- portability across compilers and platforms
- undefined / implementation-defined / unspecified behavior
- ABI / alignment / platform size assumptions

### Subtopics And Traps

- premature optimization
- benchmark noise
- assuming `int` size
- depending on UB accidentally
- code that only works on one compiler or architecture

### Exercise Ideas

- optimize a data-processing loop
- benchmark two data layouts
- port a non-portable snippet
- UB identification challenge

### Final Capstone

Build a multi-file, tested, performance-aware mini system such as:

- concurrent file indexer
- binary protocol analyzer
- reusable embedded-style driver simulation layer
- configurable CLI data processor

The capstone should include build scripts, tests, debugging hooks, and clear module boundaries.

---

## Diagnostic Question Rules For C

The C assessment must follow the current skill rule:

- ask 3 to 5 questions
- ask them from hard to easy
- default to 3 questions
- use question 4 or 5 only if the level remains ambiguous

Recommended order:

1. advanced diagnostic
2. intermediate diagnostic
3. beginner diagnostic
4. optional tie-breaker
5. optional direction-specific tie-breaker

### Axis Coverage

Across the full diagnostic set, try to cover:

- memory / lifetime reasoning
- type / expression semantics
- debugging / bug finding
- architecture / API design or performance awareness

---

## Diagnostic Question Bank For C

### Advanced Diagnostic

Use a question like:

```c
// Why can this design corrupt data under concurrent load?
void hashtable_insert(hashtable_t *ht, const char *key, void *value) {
    uint32_t idx = hash(key) % ht->capacity;
    node_t *node = ht->buckets[idx];
    while (node) {
        if (strcmp(node->key, key) == 0) {
            node->value = value;
            return;
        }
        node = node->next;
    }
    node_t *new_node = malloc(sizeof(node_t));
    new_node->key = strdup(key);
    new_node->value = value;
    new_node->next = ht->buckets[idx];
    ht->buckets[idx] = new_node;
    ht->size++;
}
```

What this tests:

- race conditions
- unsynchronized shared data
- concurrent data structure thinking
- architecture-level debugging

### Intermediate Diagnostic

Use a question like:

```c
// This code "usually works" but sometimes prints garbage. Why?
void print_user(const char *name) {
    char display[8];
    strncpy(display, name, sizeof(display));
    printf("User: %s\n", display);
}
```

What this tests:

- string termination
- library function semantics
- C buffer safety reasoning

### Beginner Diagnostic

Use a question like:

```c
// What is wrong with this function?
char *greet(const char *name) {
    char buf[64];
    snprintf(buf, sizeof(buf), "Hello, %s!", name);
    return buf;
}
```

What this tests:

- stack lifetime
- pointer validity
- returning addresses of local objects

### Optional Tie-Breaker 4

Use when level is ambiguous after the first 3:

```c
// What can go wrong here if realloc fails?
int *data = malloc(n * sizeof(int));
data = realloc(data, 2 * n * sizeof(int));
```

What this tests:

- allocation failure reasoning
- ownership and leak awareness

### Optional Tie-Breaker 5

Make this direction-specific.

Examples:

- embedded: register mask bug, volatile misuse, ISR/shared-state issue
- systems: file descriptor leak, partial read/write bug
- tools/CLI: unsafe parsing, malformed input handling, multi-file API design

---

## Starting Point Guidance

- If the student handles the advanced question well, start around Module 10+ or compress early modules into review.
- If the student misses advanced but handles intermediate well, start around Modules 04 to 06.
- If the student misses intermediate and beginner concepts, start from Module 01.
- If the student shows patchy knowledge, keep early modules but shrink already-solid exercises and preserve their micro-projects.

---

## Final Standard

If the generated C curriculum only teaches variables, loops, arrays, and pointers, it is incomplete.

If it ignores build systems, debugging, testing, UB, portability, or engineering practices, it is incomplete.

If it does not feel large enough to support a serious C learner for multiple weeks or months, it is too small.
