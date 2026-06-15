---

name: readability-refactor
description: Use when the user asks to improve code readability, rename unclear local variables, simplify tricky code, reduce local complexity, or make code more maintainable while strictly preserving behavior, public interfaces, resource lifetimes, concurrency semantics, and project conventions across programming languages.
---
# Readability Refactor

## Purpose

This skill performs a conservative readability-focused refactor on specified code.

The goal is to make the code easier to read, explain, review, and maintain, while strictly preserving:

* existing behavior
* public interface semantics
* return value semantics
* error handling
* side effects
* resource lifetime
* concurrency behavior
* I/O behavior
* serialization behavior
* logging and transaction order
* project style and language conventions

This is a readability pass, not a feature rewrite, architecture redesign, algorithm replacement, or broad modernization project.

## When to use

Use this skill when the user asks to:

* improve code readability
* make code clearer
* perform a conservative refactor
* modernize local variable names
* simplify tricky code
* reduce local complexity
* clean up confusing expressions
* make a function easier to understand
* improve maintainability without changing behavior
* refactor a file, function, method, class, module, or code snippet safely

This skill applies across languages, including but not limited to:

* C / C++
* Rust
* Go
* Python
* JavaScript / TypeScript
* Java / Kotlin
* C#
* Swift
* Shell scripts
* SQL
* build scripts
* configuration files with embedded logic

## When not to use

Do not perform readability refactoring when:

* the user only needs a quick bug fix
* the user only asks for an explanation
* the user only asks for formatting
* the requested code is generated code
* the code is critical and cannot be verified
* the readability benefit is small but behavior risk is high
* the change requires broad architectural restructuring
* the code intentionally uses a terse or unusual style for compatibility, performance, low-level, teaching, or framework reasons
* the change would require modifying public APIs, data formats, database schema, serialized fields, CLI flags, or configuration keys

In those cases, explain the risk and either leave the code unchanged or suggest a safer, smaller change.

## Core principle

Preserve behavior first. Improve readability second.

If a change may alter behavior, timing, resource cleanup, API compatibility, evaluation order, concurrency behavior, or error handling, do not make the change silently.

When uncertain, keep the original code and explain why.

## Hard constraints

1. Do not change logic.

2. Do not change observable behavior.

3. Do not change public or externally visible interfaces unless the user explicitly allows it.

4. Do not change algorithms or data structures unless the user explicitly allows it.

5. Do not introduce new dependencies, frameworks, design patterns, or architectural layers.

6. Do not mix readability refactoring with feature changes or bug fixes unless the user explicitly asks.

7. Do not change configuration values, environment variable names, route names, database fields, serialized names, CLI flags, protocol fields, or file formats.

8. Do not change error handling semantics, exception behavior, return codes, panic behavior, retry behavior, fallback behavior, logging order, or transaction boundaries.

9. Do not change async scheduling, callback timing, goroutine/thread behavior, lock ordering, atomic behavior, or resource lifetime.

10. Prefer small, local, reviewable changes.

## Change discipline

For small changes, edit directly.

For non-trivial or multi-file changes:

1. Inspect the surrounding code before editing.
2. Identify the affected functions, files, and interfaces.
3. Make one category of change at a time.
4. Keep diffs small and easy to review.
5. Avoid broad movement of code.
6. Run available tests, builds, type checks, or equivalent verification commands.
7. If tests cannot be run, say so clearly and provide manual verification steps.
8. Never claim that tests passed unless the actual output was inspected.

## Readability targets

Look for conservative improvements such as:

* unclear local variable names
* variables reused for different meanings
* overly compact expressions
* complex boolean conditions
* deeply nested conditionals
* repeated small expressions inside one function
* mixed validation, transformation, and side effects
* confusing temporary variables
* misleading or stale comments
* non-obvious resource ownership
* non-obvious lock or transaction constraints
* magic values that can be locally named without changing public API

Avoid broad structural refactors unless explicitly allowed, such as:

* splitting large classes or modules
* redesigning APIs
* introducing parameter objects
* introducing new domain types
* applying design patterns
* moving responsibilities across modules
* replacing algorithms
* changing storage or serialization format
* changing dependency structure

## Naming rules

Improve unclear local names when it helps readability and is safe.

Follow the naming convention of the target language and surrounding project:

* Python: usually `snake_case`
* Rust: usually `snake_case` for variables/functions, `CamelCase` for types
* Go: usually `mixedCaps` or `MixedCaps`
* JavaScript / TypeScript: usually `camelCase` for variables/functions, `PascalCase` for types/components
* Java / Kotlin / C#: usually `camelCase` for variables/methods, `PascalCase` for classes/types
* C: follow the project style, often `snake_case`
* C++: follow the surrounding codebase style
* SQL: follow existing identifier style
* Shell: preserve conventional uppercase names for environment variables

Prefer names that are:

* clear
* natural
* concise
* consistent with nearby code
* specific enough to show the value’s role

Avoid names that are:

* too vague
* misleading
* overloaded with multiple meanings
* unnecessarily long
* inconsistent with the project style

Possible local rename examples:

* `res` → `result` / `response`
* `req` → `request`
* `resp` → `response`
* `cfg` → `config`
* `ctx` → `context`
* `idx` → `index`
* `cnt` → `count`
* `tmp` → `temp_value` or a domain-specific name
* `arr` → `items`
* `obj` → `item` / `record` / `payload`
* `fn` → `callback` / `handler` / `function_name`
* `val` → `value` or a domain-specific name
* `buf` → `buffer`
* `msg` → `message`
* `err` → `error`

Do not rename short conventional names when they are already clear, such as:

* loop variables like `i`, `j`, `k`
* coordinates like `x`, `y`
* common identifiers like `id`, `url`, `err`, `ctx`, `req`
* domain-specific abbreviations that are standard in the project
* public or framework-bound names

## Complexity scan

Before editing, check whether the code is hard to read because of:

* nested conditionals
* long `if` / `else` chains
* long `switch` / `match` blocks
* repeated code blocks
* loops with multiple conditions
* complex boolean expressions
* mixed parsing, validation, transformation, and side effects
* variables whose meaning changes over time
* resource cleanup paths that are easy to miss
* implicit assumptions not visible in the code

Prefer local simplification first.

Extract helper functions only when:

* the extracted logic has a clear name
* the extraction reduces local complexity
* the new helper does not change visibility or public API unexpectedly
* resource lifetime and error handling remain identical
* the surrounding project style supports this kind of helper

Do not create many tiny helper functions merely to appear modern.

## Safe transformations

Allowed transformations include:

* renaming local/private variables
* splitting complex expressions into named intermediate variables
* splitting long boolean conditions into meaningful local booleans
* reducing confusing variable reuse
* clarifying nested control flow when cleanup and side effects remain identical
* replacing repeated local expressions with a local variable
* adding small comments for non-obvious constraints
* lightly polishing stale or unclear comments
* grouping logically related steps when order is preserved
* extracting a small helper only when clearly safe and useful

Risky transformations that require extra caution:

* changing `if` / `else` structure around side effects
* introducing early returns
* changing short-circuit evaluation
* changing lazy evaluation into eager evaluation
* changing iteration order
* changing exception or panic behavior
* changing integer overflow behavior
* changing floating-point evaluation
* changing async timing
* changing lock or resource release timing
* changing transaction boundaries
* changing serialization output
* changing logging order
* changing retry or fallback behavior

## Comments

Comments may be added or lightly revised when they clarify non-obvious logic.

Good comment targets:

* tricky conditions
* resource ownership
* lifetime constraints
* lock ordering
* transaction boundaries
* async behavior
* data conversion
* boundary cases
* compatibility requirements
* framework constraints
* why a simpler-looking rewrite is not safe

Comments should be concise and accurate.

Do not add long tutorials.

Do not explain obvious syntax.

Do not add speculative comments that the code does not support.

Prefer comments that explain why something must be done, not comments that merely restate each line.

## Language-specific caution

### C / C++

Preserve:

* pointer semantics
* ownership expectations
* allocation and free behavior
* `const` correctness
* macro semantics
* include behavior
* struct layout when externally visible
* volatile or atomic semantics
* undefined-behavior-sensitive code
* lock acquire/release order
* cleanup paths
* error codes and `errno` behavior

Do not introduce dynamic allocation unless the original logic already uses it and the change is clearly safe.

Do not convert C code into C++ style.

Do not introduce libraries or language features that the project does not already use.

### Rust

Preserve:

* ownership and borrowing semantics
* lifetime constraints
* public API
* trait implementations
* error type semantics
* `Result` / `Option` behavior
* `unsafe` boundaries
* feature gates
* async behavior
* iterator laziness when observable

Do not replace straightforward code with clever iterator chains if it reduces readability.

Do not change panic behavior unless explicitly requested.

### Go

Preserve:

* exported names
* error handling
* goroutine behavior
* channel close/send/receive semantics
* `defer` order
* context cancellation behavior
* interface satisfaction
* JSON/YAML tags
* package-level API

Do not hide important errors or change wrapping semantics.

### Python

Preserve:

* public function/class names
* decorators
* default argument behavior
* exception behavior
* context manager behavior
* generator laziness
* async behavior
* mutation of input objects
* import side effects
* dynamic attribute behavior

Do not replace simple code with overly clever comprehensions if it harms readability.

### JavaScript / TypeScript

Preserve:

* exported API
* promise and async behavior
* callback timing
* `this` binding
* object shape when observable
* optional vs required properties
* type declarations that affect consumers
* React hook order
* state update semantics
* serialization behavior

Do not change `function` to arrow functions if `this`, `arguments`, hoisting, or constructor behavior may matter.

Do not change `==` to `===` blindly if coercion is intentional or observable.

### Java / Kotlin / C#

Preserve:

* public API
* method overloads
* annotations
* visibility
* exception behavior
* generics
* nullability semantics
* synchronization behavior
* serialization names
* reflection-sensitive names

Do not rename members that may be used by reflection, frameworks, dependency injection, or serialization unless explicitly allowed.

### SQL

Preserve:

* query result shape
* filtering semantics
* join semantics
* transaction behavior
* lock behavior
* ordering when observable
* null handling
* aggregation behavior
* index and schema references

Do not rewrite queries into a different logical form unless equivalence is clear.

### Shell scripts

Preserve:

* quoting behavior
* environment variables
* exit codes
* current working directory effects
* globbing behavior
* signal handling
* pipeline failure behavior
* `set -e`, `set -u`, and `pipefail` semantics

Do not simplify quoting if it may introduce word splitting or glob expansion.

## Verification

After editing, verify behavior preservation using the strongest available check:

* run existing tests
* run targeted unit tests
* run build commands
* run type checks
* run linters when they are relevant and already part of the project
* run sample input/output commands
* manually inspect critical control flow, cleanup, and error paths

Do not claim that tests passed unless the output was actually inspected.

If verification cannot be performed, say so clearly and provide concrete manual verification steps.

## Final validation checklist

Before finishing, check for:

* changed behavior
* changed public APIs
* changed return values
* changed error handling
* changed side effects
* changed I/O behavior
* changed logging order
* changed transaction boundaries
* changed async timing
* changed lock acquire/release order
* changed resource lifetime
* changed serialization or configuration keys
* changed evaluation order
* variable shadowing
* name collisions
* type errors
* ownership or lifetime issues
* missing cleanup on early return
* lost error handling
* lost important comments
* overly large diffs
* unnecessary abstraction
* inconsistent style

If the code involves locks, files, sockets, memory buffers, database handles, transactions, reference counts, async tasks, threads, or external state, verify cleanup and ordering especially carefully.

## Output requirements

If the user asks for code in chat:

1. Briefly list the main changes if the change is non-trivial.
2. Provide the modified code directly.
3. Mention risky changes that were intentionally avoided.

If editing files directly:

1. Modify only the requested files or clearly relevant local files.
2. Summarize changed files.
3. Summarize the main readability improvements.
4. State whether behavior and public interfaces were preserved.
5. Mention anything intentionally left unchanged because it might affect behavior.
6. Mention what verification was run, or say that verification was not run.

Keep the final response concise and concrete.

## Response examples

For a small edit:

```text
已完成 readability refactor：主要调整了局部变量命名，并拆分了一个较长的条件表达式。未修改对外接口和行为语义。
```

For a larger edit:

```text
已完成 readability refactor：

- 将含义不清的局部变量改为更具体的名称。
- 拆分了几处复杂条件和中间计算。
- 补充了少量资源生命周期相关注释。
- 保留了原有错误处理、资源释放顺序和对外接口。

验证：已运行 `...`，测试通过。

以下位置没有改动：`...`，因为改写可能影响 `...` 的行为。
```

If verification cannot be run:

```text
已完成 readability refactor，但当前没有运行测试。建议至少执行：

- `...`
- `...`

我没有修改对外接口、错误处理路径或资源释放顺序。
```
