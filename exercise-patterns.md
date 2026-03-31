# Exercise Design Patterns

Reference guide for creating effective programming exercises across any language.
Each pattern includes a structural template and design rationale.

> **Note:** Code templates below use C as the example language. When teaching other languages,
> adapt the structure to the target language's idioms (e.g., use `assert` in Python, `#[test]` in Rust,
> JUnit in Java). The **design principles** are universal — only the syntax changes.

---

## Exercise Categories

### Category 1: Bug Hunt (修 Bug 类)
**Student receives:** Working-looking code with a subtle bug
**Student does:** Find and fix the bug
**Tests:** Verify the fixed behavior

**Best for:** Teaching defensive programming, common pitfalls, platform-specific traps

**Template (C):**
```c
/*
 * 【Bug Hunt: Topic Description】
 * This code LOOKS correct but has a subtle issue.
 * On [specific platform], it will [specific failure mode].
 * Find and fix the bug.
 */

// The buggy implementation is provided complete
type_t buggy_function(params) {
    // Subtle bug hidden here
    // (e.g., missing volatile, integer overflow, buffer overrun)
    return result;
}

void run_tests() {
    // Tests that EXPOSE the bug under specific conditions
    // Normal cases pass — edge cases fail
}
```

**Design rules:**
- Bug must be realistic (extracted from real firmware issues)
- Normal test cases should PASS — the bug only manifests under specific conditions
- Provide enough context for the student to reason about the failure mode

---

### Category 2: Implement from Spec (按规格实现类)
**Student receives:** Function signatures + test cases + specification comments
**Student does:** Write the implementation from scratch
**Tests:** Comprehensive, covering happy path + edge cases

**Best for:** Core skills, algorithm implementation, API design understanding

**Template (C):**
```c
/*
 * 【Implement: Topic Description】
 * [Concept explanation with physical analogy]
 */

// 【TODO 1: Implement this function】
// Specification:
//   Input:  [describe inputs]
//   Output: [describe expected output]
//   Edge cases: [list edge cases to handle]
//   Constraints: [memory limits, time limits, etc.]
type_t function_name(params) {
    // Your implementation here
}

void run_tests() {
    int passed = 0;
    int total = N;

    // Happy path tests
    // Edge case tests
    // Boundary condition tests

    if (passed == total) {
        printf("\n🎉 Message\n");
    }
}
```

---

### Category 3: Fill-in-the-Scaffold (填空脚手架类)
**Student receives:** 70-90% complete code with strategic gaps
**Student does:** Fill in the TODO-marked gaps (typically 1-5 key lines each)
**Tests:** Verify the complete system works

**Best for:** Teaching specific patterns, syntax, or API usage within a larger context

**Template (C):**
```c
/*
 * 【Scaffold: Topic Description】
 * [Context: What this code does as a whole]
 * [Your task: Fill in the marked TODOs]
 */

// Context code (provided, DO NOT MODIFY)
void setup_context() { /* ... */ }

// 【TODO 1: Brief description】
// Hint: [one conceptual hint]
void student_fills_this(params) {
    /* provided setup code */
    // --- YOUR CODE HERE ---

    // --- END YOUR CODE ---
    /* provided cleanup code */
}

void run_tests() { /* ... */ }
```

**Scaffolding progression rule:**
| Student Level | Code Provided | Student Writes |
|--------------|--------------|----------------|
| Beginner | 85-90% | 1-2 lines per TODO, heavy hints |
| Intermediate | 60-70% | Function bodies, medium hints |
| Advanced | 30-40% | Architecture decisions, minimal hints |

---

### Category 4: Refactor & Optimize (重构优化类)
**Student receives:** Working but poorly-written code
**Student does:** Refactor for better performance, readability, or memory usage
**Tests:** Same behavior as before, but verify the optimization metric

**Best for:** Teaching best practices, code quality, performance thinking

**Template (C):**
```c
/*
 * 【Refactor: Topic Description】
 * The code below WORKS but has [specific problem]:
 * - [problem 1: e.g., wastes 40% RAM due to padding]
 * - [problem 2: e.g., O(n²) when O(n) is possible]
 * Refactor it. Tests verify both correctness AND the improvement.
 */

// Original (working but bad) implementation
struct BadVersion { /* ... */ };

// 【TODO: Create an optimized version】
struct GoodVersion {
    // Your optimized layout here
};

void run_tests() {
    // Correctness tests (same behavior)
    // Optimization verification tests
    // e.g., sizeof(GoodVersion) < sizeof(BadVersion)
    // e.g., measure execution cycles
}
```

---

### Category 5: Architecture Design (架构设计类)
**Student receives:** Requirements and acceptance criteria only
**Student does:** Design and implement the entire solution
**Tests:** Comprehensive acceptance tests provided

**Best for:** Micro-projects, capstone exercises, integration challenges

**Template (C):**
```c
/*
 * 【Architecture Challenge: Topic Description】
 *
 * Requirements:
 * 1. [Functional requirement]
 * 2. [Functional requirement]
 * 3. [Non-functional: memory limit, no dynamic allocation, etc.]
 *
 * Acceptance Criteria:
 * - All tests in run_tests() pass
 * - Code compiles without warnings under -Wall -Wextra
 * - [Additional criteria: code review by tutor]
 */

// You design the data structures, functions, and implementation.
// Only the test interface is fixed:

// Required API (you must implement these exact signatures):
// void system_init(void);
// int system_process(const uint8_t *input, size_t len);
// const char *system_get_status(void);

void run_tests() {
    // Comprehensive acceptance tests
    // These define the "contract" — everything else is your design
}
```

---

## Hint Design Reference

### L1 Hints (Conceptual)
- Frame as a question, not a statement
- Point to the relevant concept without naming the solution
- ✅ "What happens to a local variable's memory after this function returns?"
- ❌ "You need to make it static" (too direct)

### L2 Hints (Structural)
- Provide the algorithm steps in natural language or pseudocode
- Name the operations without showing syntax
- ✅ "Three steps: 1) create a mask for bits 4-5, 2) clear those bits, 3) set new value"
- ❌ "Use `reg &= ~(0x30); reg |= (val << 4);`" (too much code)

### L3 Hints (Code Fragment)
- Show ONE key line or pattern, not the complete solution
- Always leave something for the student to figure out
- ✅ "`result &= ~mask;` clears the bits. Now, how do you shift the new value into position?"
- ❌ Full function body (defeats the purpose)

---

## Test Design Rules

1. **Minimum 3 tests per exercise**: happy path, edge case, boundary condition
2. **Self-documenting**: test names explain what they verify
3. **Order matters**: put simplest tests first (easier debugging)
4. **Output on failure**: show expected vs actual values
5. **Celebration on complete**: `🎉` emoji + permission to proceed

**Test output format:**
```
[✅] Test 1 Passed: Description
[❌] Test 2 Failed: Expected X, Got Y. Hint message.
[✅] Test 3 Passed: Description

🎉 All N tests passed! You've mastered [topic]. Ready for the next challenge!
⚠️ M/N passed. Review [concept] and try again!
```

---

## Anti-Patterns to Avoid

| Anti-Pattern | Why It's Bad | Better Alternative |
|-------------|-------------|-------------------|
| "Print hello world" | Zero learning value past day 1 | Parse a config string from EEPROM |
| "Implement a calculator" | Disconnected from domain | Implement a unit converter for ADC readings |
| FizzBuzz | Interview cliché, not educational | Implement a packet checksum validator |
| Sorting algorithms in isolation | No real-world context | Sort a sensor reading array for median filtering |
| "Write a class/struct for Person" | Generic, no engineering value | Write a struct for an I2C device descriptor |
