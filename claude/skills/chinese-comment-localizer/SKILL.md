---

name: chinese-comment-localizer
description: Use when the user asks to translate, localize, polish, or improve existing English comments in source code or configuration files into concise Chinese comments for learning and code reading, while preserving all code behavior and structure.
---
# Chinese Comment Localizer

## Purpose

This skill helps translate and polish existing English comments in code or configuration files into concise, natural Chinese comments.

The goal is to make the source easier to read and understand for Chinese-speaking learners, while preserving the original code behavior, file structure, and author intent.

## When to use

Use this skill when the user asks to process comments in one or more files, including but not limited to:

* C / C++: `.c`, `.h`, `.cpp`, `.hpp`
* Python: `.py`
* JavaScript / TypeScript: `.js`, `.jsx`, `.ts`, `.tsx`
* Java / Kotlin: `.java`, `.kt`
* Go: `.go`
* Rust: `.rs`
* Shell scripts: `.sh`, `.bash`, `.zsh`
* SQL: `.sql`
* HTML / CSS: `.html`, `.css`, `.scss`
* configuration files: `.yaml`, `.yml`, `.toml`, `.jsonc`, `.ini`, `.conf`
* build or project files that contain comments

Typical user requests include:

* translate existing English comments into Chinese
* polish comments for easier reading
* make comments suitable for beginners
* localize source comments without changing code
* improve comment wording while preserving the original meaning

Do not use this skill for ordinary code refactoring, bug fixing, API redesign, formatting-only cleanup, or writing a separate tutorial unless the user explicitly asks for that.

## Core rules

1. Only translate and optimize comments.

2. Do not modify code logic, function signatures, class names, method names, macro definitions, type definitions, field names, variable names, import statements, configuration values, or behavior-related content.

3. Preserve the original code structure as much as possible.

4. Keep the original comment position and scope:

   * line comments should remain line comments
   * block comments should remain block comments
   * documentation comments should remain documentation comments
   * comments should not be moved far away from the code they describe
   * avoid merging, splitting, or relocating comments unless necessary for readability

5. Comments should be concise, clear, and suitable for learners.

6. Avoid long explanations. Do not turn short inline comments into paragraphs.

7. Avoid machine-translation style. Chinese comments should sound natural in source code.

8. Keep code identifiers, API names, class names, function names, field names, protocol names, command names, and established technical terms in English when appropriate.

9. Do not add speculative explanations that are not supported by the code.

10. For important mechanisms, a small amount of background explanation is allowed, but it must stay close to the original comment and surrounding code.

## Terminology style

When translating comments, preserve important identifiers and technical terms naturally inside Chinese explanations.

Examples:

* `UserService` → 用户服务 `UserService`
* `fetchUser()` → 获取用户数据的 `fetchUser()`
* `props` → 组件属性 `props`
* `middleware` → 中间件 `middleware`
* `Promise` → 异步结果 `Promise`
* `DataFrame` → 表格数据结构 `DataFrame`
* `HashMap` → 哈希映射 `HashMap`
* `mutex` → 互斥锁 `mutex`
* `JWT` → 身份令牌 `JWT`
* `endpoint` → 接口端点 `endpoint`
* `cache` → 缓存 `cache`
* `schema` → 数据结构定义 `schema`

Prefer this style:

```ts
// 从 API 获取用户资料，并返回解析后的 `UserProfile`。
```

Instead of:

```ts
// Fetch user profile from API and return parsed UserProfile.
```

Or:

```ts
// 从应用程序编程接口取得使用者轮廓。
```

## Comment translation guidelines

### Short comments

If the original comment is short, translate it into an equally short Chinese comment.

Example:

```py
# validate input
```

Becomes:

```py
# 校验输入
```

### Incomplete comments

If the original comment is too terse or incomplete, add minimal context based on nearby code.

Example:

```js
// retry
```

Can become:

```js
// 请求失败时重试
```

Only do this when the surrounding code clearly supports the added context.

### Mechanism comments

For key mechanisms, briefly clarify the purpose.

Example:

```rs
// Acquire lock before updating shared state.
```

Can become:

```rs
// 更新共享状态前先获取锁，避免并发修改。
```

Do not over-expand it into a full concurrency tutorial unless the user explicitly asks for that.

### Inline comments

Keep inline comments compact.

Example:

```go
timeout := 5 * time.Second // request timeout
```

Becomes:

```go
timeout := 5 * time.Second // 请求超时时间
```

Avoid making inline comments too long.

### Documentation comments

For documentation comments, preserve their documentation role and format.

Example:

```java
/**
 * Returns the cached value if present.
 */
```

Becomes:

```java
/**
 * 如果缓存中存在对应值，则直接返回。
 */
```

Do not remove documentation markers such as `/** ... */`, `///`, `//!`, `"""..."""`, or docstring conventions.

### Configuration comments

For configuration files, preserve keys and values exactly.

Example:

```yaml
# Enable debug logs in development
debug: true
```

Becomes:

```yaml
# 在开发环境中启用调试日志
debug: true
```

Only the comment should change.

## Workflow

When processing files:

1. Identify the target files requested by the user.

2. Read the target files and, when necessary, nearby related files to understand context.

3. Locate existing English comments.

4. Translate and polish only those comments.

5. Preserve code behavior, configuration values, and file structure.

6. Check that no non-comment content was changed accidentally.

7. Return either:

   * the complete modified file content, or
   * a summary of files modified if editing directly in the workspace

Follow the user's requested output mode. If the user asks to edit files directly, modify the files. If the user asks for the result in chat, output the complete modified file content.

## Validation checklist

Before finishing, verify:

* No code logic was changed.
* No configuration value was changed.
* No function, method, class, type, field, or variable name was changed.
* No import, export, include, package declaration, or build directive was changed.
* Existing English comments were translated or polished.
* Comment positions and scopes were preserved.
* Chinese comments are natural and concise.
* Technical identifiers remain in English where appropriate.
* Added context is supported by the surrounding code.

## Response style

When reporting completion, be brief.

For direct file edits, summarize only:

* which files were processed
* what kind of comment changes were made
* whether non-comment content was left unchanged

Example:

```text
已处理 `api.ts`、`config.yaml` 和 `worker.py` 中的英文注释，将接口调用、配置项和任务流程相关说明翻译并润色为中文。未修改代码逻辑、配置值或文件结构。
```

For chat output, provide the full modified file content when the user requests it.
