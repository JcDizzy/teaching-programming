# C Language Curriculum Template (Comprehensive)

A complete C language learning path covering all fundamental and advanced C concepts.
Applicable to systems programming, tool development, algorithm implementation, and as a
foundation for any domain (embedded, OS, networking, game engines, etc.).

## How to Use This Template

1. In Phase 1 (Assessment), determine the student's level
2. Skip already-mastered modules, but NEVER skip their micro-projects (use as review)
3. Expand weak-area modules with additional exercises
4. If the student has a specific domain focus (embedded, networking, etc.), adjust exercise scenarios accordingly

---

## Module 01: Foundations (01_foundations)
*Prerequisites: None*
*Estimated time: 4-6 hours*

### 1.1 Data Types & Overflow Traps
- Fixed-width integers: `uint8_t`, `int16_t`, `uint32_t` vs platform-dependent `int`, `long`
- Integer overflow: signed overflow is undefined behavior, unsigned wraps around
- Implicit type promotion rules: when `uint8_t + uint8_t` becomes `int`
- IEEE 754 float representation pitfalls (why `0.1 + 0.2 != 0.3`)
- `sizeof` operator: platform-dependent sizes, `size_t` for portable code
- **Exercise**: Write a function that safely detects integer overflow before it happens

### 1.2 Operators & Expression Evaluation
- Arithmetic, relational, logical operators
- Short-circuit evaluation: `&&` and `||` for guard patterns
- Operator precedence traps: `a & 0xFF == 0` vs `(a & 0xFF) == 0`
- Compound assignment: `+=`, `-=`, `|=`, `&=`, `^=`, `<<=`
- Comma operator (rarely used but important to recognize)
- **Exercise**: Fix 5 expressions with common precedence bugs

### 1.3 Control Flow
- `if-else` chains vs `switch-case` (when to use which)
- `switch` fall-through: intentional use and accidental bugs
- Loops: `for`, `while`, `do-while` — choosing the right one
- `break`, `continue`, `goto` — the controversial but sometimes necessary `goto` for error cleanup in C
- Loop invariants: thinking about what stays true across iterations
- **Exercise**: Implement a simple text tokenizer using state-driven `switch-case`

### 1.4 Arrays & Strings
- Stack arrays vs heap arrays, VLAs (Variable Length Arrays) and why to avoid them
- Buffer overflow: the #1 C security vulnerability
- C strings: `\0` terminator, `strlen` vs `sizeof`, off-by-one errors
- Safe string functions: `strncpy`, `snprintf`, `memcpy`, `memset`
- **Exercise**: Implement safe `my_strlen()` and `my_strcat()` with boundary checks

### 1.5 Functions & Scope
- Storage classes: `auto`, `static` (local vs file-scope), `extern`, `register`
- Linkage: internal (`static`) vs external (`extern`) — multi-file projects
- Function declaration vs definition, header file conventions
- `static` local variables: persistent state across calls (use case: call counter, simple generators)
- Pass-by-value semantics: why you can't modify caller's variables directly
- **Exercise**: Implement a pseudo-random number generator using `static` local state

### 1.6 The Preprocessor
- `#define` macros: simple constants, parameterized macros, dangers of macro side-effects
- `#include` guards and `#pragma once`
- Conditional compilation: `#ifdef`, `#ifndef`, `#if defined()`
- Predefined macros: `__FILE__`, `__LINE__`, `__func__`, `__DATE__`
- Stringification (`#`) and token pasting (`##`)
- **Exercise**: Write a debug logging macro that includes file/line info and can be compiled out with a flag

### 🔧 Micro-Project: CSV Data Processor
Build a command-line program that:
- Reads a CSV file and parses fields (handling quoted strings with commas)
- Supports column selection (e.g., print only columns 1, 3, 5)
- Calculates basic statistics per numeric column (min, max, average)
- Uses `static` variables for running statistics across rows
- Tests: automated with predefined input/expected output

---

## Module 02: Pointers & Memory (02_pointers_memory)
*Prerequisites: Module 01*
*Estimated time: 6-8 hours*

### 2.1 Pointer Fundamentals
- Address-of `&` and dereference `*` — what they actually do at the hardware level
- Pointer types and why they matter: `int *` vs `char *` pointer arithmetic
- `NULL` pointers: checking, dereferencing consequences, defensive programming
- `void *`: the generic pointer, type erasure, required explicit casts
- Pointer-to-pointer (`**`): modifying a caller's pointer from a function
- **Exercise**: Implement a `swap()` function and a `find_min_max()` that returns results via pointer parameters

### 2.2 Pointers & Arrays
- Array name decay: when an array "becomes" a pointer (and when it doesn't: `sizeof`, `&`)
- Pointer arithmetic: `ptr + n` advances by `n * sizeof(*ptr)` bytes
- Array-of-pointers vs pointer-to-array: `char *argv[]` vs `char (*p)[10]`
- Multi-dimensional arrays: row-major layout, passing to functions
- **Exercise**: Implement `my_reverse()` that reverses an array in-place using pointer arithmetic only (no index `[]`)

### 2.3 Dynamic Memory Management
- `malloc()`, `calloc()`, `realloc()`, `free()` — the heap lifecycle
- Memory leaks: detection patterns, tools (Valgrind, AddressSanitizer)
- Dangling pointers: use-after-free, double-free
- `realloc` pitfalls: the temporary pointer pattern to avoid leaks on failure
- When to use stack vs heap allocation
- **Exercise**: Implement a dynamic integer array (`dyn_array`) that grows automatically when full

### 2.4 Const Correctness
- `const int *p` — pointer to const data (read-only data access)
- `int * const p` — const pointer (fixed address)
- `const int * const p` — both const
- Function parameters: `const` for input-only buffers (API contracts)
- **Exercise**: Write a CRC8 calculator that takes `const uint8_t *data, size_t len`

### 🔧 Micro-Project: Ring Buffer (Circular Queue)
Implement a production-quality ring buffer:
- Fixed-size, statically allocated (configurable at compile time)
- `ringbuf_init()`, `ringbuf_push()`, `ringbuf_pop()`, `ringbuf_is_full()`, `ringbuf_is_empty()`
- Generic data support via `void *` and element size parameter
- Tests: push/pop sequences, overflow handling, wrap-around correctness

---

## Module 03: Bit Manipulation (03_bit_manipulation)
*Prerequisites: Module 02*
*Estimated time: 4-5 hours*

### 3.1 Bitwise Operators
- AND `&`, OR `|`, XOR `^`, NOT `~`, shifts `<<` `>>`
- Bit masks: creating, combining, inverting
- The "Big Four" bit operations: SET, CLEAR, TOGGLE, READ a specific bit
- Shift operations: logical vs arithmetic right shift (signed vs unsigned)
- **Exercise**: Implement `set_bit()`, `clear_bit()`, `toggle_bit()`, `read_bit()` functions

### 3.2 Practical Bit Manipulation
- Packing multiple boolean flags into a single integer (permission bits, feature flags)
- Extracting bit fields from packed data (e.g., parsing a pixel: `RGB565`)
- Power-of-two checks: `n & (n-1) == 0`
- Counting set bits (popcount) — multiple algorithms
- Byte-order conversion (endianness): big-endian vs little-endian, `htons`/`ntohs`
- **Exercise**: Parse a packed 32-bit color value into R, G, B, A components

### 3.3 Bit Manipulation in Practice
- Encoding/decoding: Base64, UTF-8 byte patterns
- Checksum algorithms using XOR
- Bitmap data structures: tracking allocation with bit arrays
- **Exercise**: Implement a compact `bitset` (bit array) with set/clear/test/count operations

### 🔧 Micro-Project: Permission System
Build a Unix-style permission system:
- Encode read/write/execute permissions for owner/group/other in a 16-bit integer
- `perm_set()`, `perm_check()`, `perm_to_string()` (e.g., `"rwxr-x---"`)
- Support `chmod`-style octal notation (`0755`)
- Tests: set permissions, verify bit patterns, format strings

---

## Module 04: Structs, Unions & Memory Layout (04_structs_memory)
*Prerequisites: Module 03*
*Estimated time: 6-8 hours*

### 4.1 Structures
- Definition, initialization (designated initializers `{.field = value}`)
- Member access: `.` and `->` (pointer to struct)
- Memory layout and alignment: padding rules, `sizeof` vs sum of member sizes
- `offsetof()` macro: finding member offsets
- Struct-ordering optimization: reorder members to minimize padding
- **Exercise**: Optimize a poorly-ordered struct from 24B to 16B

### 4.2 Packed Structures
- `__attribute__((packed))` / `#pragma pack(1)`: forcing zero-padding layout
- Use case: network protocol headers, file format headers, serialization
- Performance penalty: unaligned access on some architectures
- **Exercise**: Define a packed struct matching a BMP image file header

### 4.3 Unions
- Overlapping memory: all members share the same starting address
- Type punning: interpret the same bytes as different types (float ↔ uint32_t)
- Tagged unions: union + enum for type-safe variant types
- Anonymous unions inside structs
- **Exercise**: Build a JSON-like value type using tagged union (number / string / boolean / null)

### 4.4 Bit-Fields
- Defining bit-width for struct members: `uint32_t flag : 1;`
- Mapping to compact data layouts
- Portability concerns: bit-field layout is implementation-defined
- When to use bit-fields vs manual bit manipulation (trade-offs)

### 4.5 Enumerations
- `enum` basics: named constants with auto-incrementing values
- Typed enums and size control
- Using enums for state machine states, error codes, command types
- **Exercise**: Design a log-level enum with string conversion and filtering support

### 🔧 Micro-Project: Binary File Format Reader
Build a reader for a simple binary file format (e.g., BMP header or custom format):
- Use packed structs for the file header layout
- Use unions for variant data sections
- Read binary files with `fread`, validate magic numbers and checksums
- Pretty-print parsed structure contents
- Tests: parse valid files, detect corrupted headers, handle edge cases

---

## Module 05: Advanced Pointers & Function Pointers (05_advanced_pointers)
*Prerequisites: Module 04*
*Estimated time: 5-7 hours*

### 5.1 Function Pointers
- Syntax: `void (*fp)(int)` — reading the declaration
- `typedef` for function pointer types: `typedef void (*callback_t)(int);`
- Assigning, calling through function pointers
- Use case: callbacks, plugin systems, strategy pattern
- **Exercise**: Build a sorting framework where the comparison function is a parameter (like `qsort`)

### 5.2 Function Pointer Tables
- Arrays of function pointers for dispatch tables
- Replacing long `switch-case` chains with indexed dispatch
- State machine implementation: state = index into function pointer array
- Command dispatchers: parsing command string → calling handler function
- **Exercise**: Implement a CLI command dispatcher that maps command names to handler functions

### 5.3 Opaque Pointers & Information Hiding
- Forward declarations: `struct Impl;` without defining contents
- Opaque pointer pattern: expose only operations, hide data layout
- C "object-oriented" patterns: struct + function pointer table (vtable)
- **Exercise**: Refactor a module to hide its internal struct behind an opaque API (`stack_t` with create/push/pop/destroy`)

### 🔧 Micro-Project: Plugin System
Build a lightweight plugin system:
- Define a plugin interface (struct of function pointers: `init`, `process`, `cleanup`)
- Plugin registry: register plugins by name, look up by name
- Load and execute plugins in order
- Static allocation (no `dlopen`, just compile-time registration)
- Tests: register multiple plugins, verify execution order, test error handling

---

## Module 06: Multi-file Projects & Compilation (06_build_system)
*Prerequisites: Module 05*
*Estimated time: 3-4 hours*

### 6.1 Compilation Model
- Preprocessor → Compiler → Assembler → Linker: what each stage does
- Translation units: each `.c` file compiles independently
- Header files: declarations, include guards, forward declarations
- Common mistakes: defining variables/functions in headers

### 6.2 Linkage & Visibility
- `extern` declarations: sharing across translation units
- `static` file-scope functions/variables: internal linkage (encapsulation in C)
- One Definition Rule (ODR)
- `inline` functions: when and how to use in headers

### 6.3 Build Systems
- Makefiles: targets, dependencies, recipes, automatic variables (`$@`, `$<`, `$^`)
- CMake basics: `CMakeLists.txt`, `add_executable`, `target_link_libraries`
- Compiler flags: `-Wall -Wextra -Werror -std=c11 -O2` and what they do
- Debug vs Release builds: `-g -O0 -fsanitize=address` vs `-O2 -DNDEBUG`
- Using sanitizers: AddressSanitizer, UndefinedBehaviorSanitizer

### 🔧 Micro-Project: Multi-Module Library
Refactor a monolithic program into:
- `ringbuf.h` / `ringbuf.c` — ring buffer module (from Module 02)
- `parser.h` / `parser.c` — CSV/data parser module (from Module 01)
- `main.c` — application that uses both modules
- `CMakeLists.txt` with proper dependency tracking
- Tests: each module testable independently via a test runner

---

## Module 07: The C Standard Library (07_stdlib)
*Prerequisites: Module 06*
*Estimated time: 4-5 hours*

### 7.1 String Operations (`<string.h>`)
- `memcpy`, `memmove`, `memset`, `memcmp` — the "mem" family
- `strcpy`, `strncpy`, `strcat`, `strncat` — string manipulation
- `strcmp`, `strncmp`, `strstr`, `strchr` — searching
- Buffer overflow prevention patterns

### 7.2 Formatted I/O (`<stdio.h>`)
- `printf` format specifiers: `%d`, `%u`, `%x`, `%02X`, `%s`, `%p`, `%zu`
- `sprintf` vs `snprintf` (always prefer `snprintf`)
- `sscanf` for parsing strings
- File I/O: `fopen`, `fread`, `fwrite`, `fclose`, `fseek`, `ftell`
- Binary vs text mode: `"rb"` vs `"r"`

### 7.3 Utility Functions
- `<stdlib.h>`: `atoi`, `strtol`, `strtoul`, `strtod`, `abs`, `qsort`, `bsearch`
- `<ctype.h>`: `isdigit`, `isalpha`, `isspace`, `toupper`, `tolower`
- `<stdarg.h>`: variadic functions (`va_list`, `va_start`, `va_arg`, `va_end`)
- `<assert.h>`: runtime assertions and `NDEBUG`
- `<time.h>`: `time()`, `clock()`, `difftime()`, measuring execution time
- **Exercise**: Implement a `my_printf` that handles `%d`, `%x`, `%s` using `<stdarg.h>`

### 🔧 Micro-Project: Log File Analyzer
Build a log file analyzer that:
- Reads a log file line by line (handle large files without loading all into memory)
- Parses timestamps, log levels, and messages using string operations
- Filters by log level and time range
- Outputs summary statistics (error count, most frequent message pattern)
- Uses `qsort` for sorting results

---

## Module 08: Error Handling & Defensive Programming (08_error_handling)
*Prerequisites: Module 07*
*Estimated time: 4-5 hours*

### 8.1 Error Handling Patterns in C
- Return codes: conventions (`0` = success, negative = error, positive = result)
- `errno` and `perror()`, `strerror()`: system error reporting
- Error propagation: checking and forwarding errors up the call stack
- The goto-cleanup pattern: structured resource cleanup on error
- **Exercise**: Refactor a function with multiple `malloc`/`fopen` calls to use goto-cleanup

### 8.2 Defensive Programming
- Input validation: never trust external data (files, user input, network data)
- Assertions vs error codes: when to crash vs when to recover
- Preconditions, postconditions, invariants
- Defensive `NULL` checks: parameter validation at function entry
- **Exercise**: Add comprehensive input validation to a data parser

### 8.3 Memory Safety
- Common vulnerabilities: buffer overflow, format string attacks, use-after-free
- Safe coding practices: bounds checking, `snprintf`, `strncpy`
- Tools: Valgrind, AddressSanitizer (`-fsanitize=address`), UBSan
- Stack canaries and ASLR (conceptual understanding)
- **Exercise**: Find and fix 5 memory safety bugs in a provided codebase

### 8.4 Resource Management (RAII in C)
- The "acquire-use-release" pattern
- Cleanup functions and destructor-like patterns
- Using `__attribute__((cleanup))` for automatic cleanup (GCC extension)
- File handle, memory, and lock management patterns

### 🔧 Micro-Project: Robust Configuration File Parser
Build a config file parser (INI-style) that:
- Handles malformed input gracefully (never crashes, always reports errors)
- Uses goto-cleanup for resource management
- Validates all values (type checking, range checking)
- Returns detailed error information (line number, error type, context)
- Tests: valid configs, malformed configs, edge cases (empty file, huge values)

---

## Module 09: Data Structures & Algorithms in C (09_data_structures)
*Prerequisites: Module 08*
*Estimated time: 6-8 hours*

### 9.1 Linked Lists
- Singly linked list: insert, delete, search, reverse
- Doubly linked list: bidirectional traversal, sorted insertion
- Intrusive linked lists: embedding the node inside the data struct (Linux kernel style)
- Memory management: who owns the nodes? Caller vs library allocation
- **Exercise**: Implement a generic singly linked list using `void *` data

### 9.2 Hash Tables
- Hash functions: requirements (deterministic, uniform distribution, fast)
- Collision resolution: separate chaining vs open addressing (linear probing)
- Load factor and rehashing: when and how to grow the table
- **Exercise**: Implement a string→string hash map with separate chaining

### 9.3 Trees
- Binary search tree: insert, search, delete, in-order traversal
- Tree balancing concepts (why BST degrades to O(n) without it)
- Practical tree usage: expression parsing, hierarchical data
- **Exercise**: Implement a BST for an in-memory key-value store

### 9.4 Sorting & Searching
- `qsort()` deep dive: writing comparison functions, sorting structs
- `bsearch()` for sorted arrays
- When to use arrays vs linked lists vs hash tables vs trees
- **Exercise**: Sort an array of structs by multiple criteria using `qsort` with compound comparison

### 🔧 Micro-Project: In-Memory Database
Build a simple in-memory key-value store:
- Hash table backend with string keys and typed values (int, string, float)
- Support `SET`, `GET`, `DELETE`, `KEYS` operations
- CLI interface for interactive usage
- Persistence: save/load to binary file
- Tests: CRUD operations, collision handling, persistence round-trip

---

## Module 10: Advanced Topics (10_advanced)
*Prerequisites: Module 09*
*Estimated time: 8-10 hours*

### 10.1 Concurrency & Multithreading
- POSIX threads (`pthread`): create, join, detach
- Mutexes: protecting shared data, lock ordering to prevent deadlocks
- Condition variables: producer-consumer pattern
- Race conditions: identifying and preventing data races
- Atomic operations: `<stdatomic.h>` (C11)
- **Exercise**: Build a thread-safe message queue (producer-consumer)

### 10.2 Process & System Interaction
- `fork()`, `exec()`, `wait()`: process creation and management
- Pipes and inter-process communication (IPC)
- `signal()` and `sigaction()`: signal handling basics
- File descriptors and low-level I/O: `open()`, `read()`, `write()`, `close()`
- **Exercise**: Build a simple pipeline that connects two programs via pipe

### 10.3 Memory Layout & Linker
- Process memory layout: text, data, BSS, heap, stack segments
- Stack frames: how function calls work at the machine level
- Buffer overflow exploitation (conceptual): understanding why it works
- Static vs dynamic linking: `.a` vs `.so` / `.lib` vs `.dll`
- `nm`, `objdump`, `readelf`: inspecting compiled binaries

### 10.4 Performance & Optimization
- Profiling: `gprof`, `perf`, `time` — measuring before optimizing
- Cache-friendly data structures: struct-of-arrays vs array-of-structs
- Branch prediction and branchless programming
- `restrict` keyword: promising no pointer aliasing (helps optimizer)
- `inline` functions vs macros: when to use each
- **Exercise**: Optimize a matrix multiplication from naive O(n³) to cache-friendly version

### 10.5 Testing in C
- Unit testing frameworks: Unity, Check, or minimal custom assert macros
- Test-Driven Development (TDD) in C
- Mocking strategies: function pointer injection, link-time substitution
- Continuous integration for C projects
- Code coverage: `gcov`, `lcov`

### 🔧 Final Capstone Project: Multi-threaded File Indexer
Build a concurrent file indexer from scratch:
- Recursively scan a directory tree (using `opendir`/`readdir`)
- Build an inverted index (word → list of files containing it)
- Multi-threaded: producer threads scan files, consumer threads build index
- Thread-safe hash table for the index
- Query interface: search for words, return matching files with line numbers
- Persistence: save/load index to binary file
- Full automated test suite
- Multi-file project with proper CMake build

---

## Assessment Question Bank (for Phase 1 Diagnostics)

### Beginner Detection Questions
```c
// Q: "What does this print?"
int x = 300;
uint8_t y = x;
printf("%d\n", y);  // Answer: 44 (300 - 256, unsigned wrap-around)
```

```c
// Q: "What's wrong with this function?"
char *greet(const char *name) {
    char buf[64];
    snprintf(buf, sizeof(buf), "Hello, %s!", name);
    return buf;  // Issue: returning pointer to stack-allocated buffer
}
```

### Intermediate Detection Questions
```c
// Q: "This program sometimes prints garbage after the name. Why?"
void print_user(const char *name) {
    char display[8];
    strncpy(display, name, sizeof(display));
    printf("User: %s\n", display);
}
// Issue: strncpy doesn't null-terminate if name >= 8 chars
```

```c
// Q: "This code is supposed to double a dynamic array. What can go wrong?"
int *data = malloc(n * sizeof(int));
// ... fill data ...
data = realloc(data, 2 * n * sizeof(int));
// Issue: if realloc fails, data becomes NULL, leaking original memory
```

### Advanced Detection Questions
```c
// Q: "This hash table implementation has a subtle concurrency bug.
//     It works fine single-threaded but corrupts data under load. Why?"
void hashtable_insert(hashtable_t *ht, const char *key, void *value) {
    uint32_t idx = hash(key) % ht->capacity;
    // Walk chain to find existing key...
    node_t *node = ht->buckets[idx];
    while (node) {
        if (strcmp(node->key, key) == 0) {
            node->value = value;
            return;
        }
        node = node->next;
    }
    // Insert new node at head
    node_t *new_node = malloc(sizeof(node_t));
    new_node->key = strdup(key);
    new_node->value = value;
    new_node->next = ht->buckets[idx];
    ht->buckets[idx] = new_node;
    ht->size++;
}
// Issue: no locking — two threads can race on same bucket, corrupting the chain;
// size++ is also a data race (non-atomic read-modify-write)
```
