---
name: report-section-writer
description: Use when writing or revising Chinese undergraduate experiment report sections based on a real code project, especially “实验原理与总体设计”, “重点代码截图及讲解”, “运行结果截图及分析”, “实验结论及心得体会”, source-code explanations, screenshot guidance, run commands, and result analysis.
---

# Report Section Writer

## Purpose

This skill helps write Chinese undergraduate experiment report sections based on an actual code project.

It is intended for coursework projects where the user needs report content such as:

- 实验目的与要求
- 实验环境
- 实验原理与总体设计
- 实验要求与实现对应关系
- 重点代码截图及讲解
- 运行结果截图及分析
- 实验结论及心得体会

The output should be suitable for direct inclusion in an undergraduate experiment report.

The main tasks are:

- read and understand the provided project source code
- identify important modules, data structures, algorithms, and entry points
- connect implementation details to experiment requirements
- select source code snippets suitable for screenshots
- provide source code in fenced code blocks
- provide exact file/function/line-number locations when possible
- inspect real build scripts, README files, test files, and run commands
- distinguish observed results from inferred or suggested commands
- organize screenshot guidance and result analysis
- write concise Chinese report text

---

## When to use

Use this skill when the user asks to write, revise, complete, or plan report sections such as:

- `实验原理与总体设计`
- `实验要求与实现对应关系`
- `重点代码截图及讲解`
- `运行结果截图及分析`
- `实验结论及心得体会`
- code screenshot explanations
- running result screenshot analysis
- report text based on a project
- report content that references actual project files, functions, commands, or outputs
- a Markdown report section for copying into Word or a school report template

This skill is suitable for projects in different languages, including but not limited to:

- C / C++
- Python
- Java
- Go
- Rust
- JavaScript / TypeScript
- Shell
- SQL
- mixed-language coursework projects

---

## Core rules

1. Read the actual project before writing.

2. Do not judge only by file names. Understand the project structure, main modules, entry points, key functions, and module relationships from real code.

3. Prefer evidence from source code, README, build scripts, tests, command-line entry points, and actual run commands.

4. Do not invent unsupported features, commands, results, file names, or line numbers.

5. If something cannot be confirmed, say so clearly and provide a reasonable suggested command or screenshot plan.

6. The report language should be Chinese by default unless the user explicitly asks for another language.

7. The report style should be suitable for an undergraduate experiment report:

   - concise
   - clear
   - natural
   - not overly colloquial
   - not full of empty phrases
   - focused on the relation between code, experiment principles, and implementation requirements

8. Avoid repetitive sentence patterns such as:

   - “该代码片段定义了……”
   - “该结果表明……”
   - “本节代码完成了……”
   - “通过本次实验，我受益匪浅……”

9. Use natural report wording such as:

   - “这里……”
   - “这一部分……”
   - “函数中先……再……”
   - “从输出可以看到……”
   - “这一结果说明……”
   - “与前一部分相比……”
   - “这一设计使得……”
   - “在实现过程中需要注意……”

10. If the user asks to create a file directly, write the report section to a `.md` file.

11. Do not output images. Provide screenshot positions, screenshot ranges, commands, and analysis text.

12. Do not include irrelevant implementation notes about this skill in the final report.

---

# General workflow

When using this skill, follow this workflow:

1. Inspect the project structure.

2. Identify:

   - source files
   - headers or type definitions
   - entry points
   - build scripts
   - tests
   - README or documentation
   - sample data or example commands

3. Understand the project’s purpose and how it satisfies the assignment requirements.

4. If the assignment document or requirement text is available, build a requirement-to-implementation mapping before writing detailed sections.

5. Select code snippets based on importance, not file coverage.

6. Prefer real commands. Run them if possible. If not possible, mark commands as inferred or suggested.

7. Write report text in Markdown.

8. Preserve the user’s report template style if provided.

---

# Evidence level

When describing commands, outputs, and results, distinguish three evidence levels.

## Observed

Use when the command was actually run and the output was inspected.

Wording examples:

- “实际运行后，输出中可以看到……”
- “从本次运行结果可以看到……”
- “测试汇总显示……”

## Inferred

Use when the command is inferred from Makefile, README, package configuration, source code, or project convention, but was not actually run.

Wording examples:

- “根据 Makefile，可使用以下命令构建项目……”
- “根据 README 中的说明，运行方式为……”
- “从项目入口可以推断，建议使用……”

## Suggested

Use when the command is a recommended verification method but cannot be confirmed from the project.

Wording examples:

- “如果需要补充截图，可以使用以下命令进行验证……”
- “由于当前无法直接运行，该命令作为建议验证方式……”
- “建议在实验环境中运行以下命令并截取输出……”

Do not claim that a command succeeds unless the output was actually observed.

---

# Template adaptation

If the user provides an existing report template or previous report, preserve:

- heading levels
- section numbering
- figure numbering style
- wording density
- whether code snippets are included before or after screenshots
- whether screenshots are referenced as “图 x-x”
- whether the report uses “实验步骤 / 重点代码 / 运行结果 / 结论” style
- whether the report requires “命令 + 截图 + 说明” format

Do not invent a completely different report structure unless the user asks for it.

If the school template is known but the user does not ask for a full report, output only the requested sections.

---

# Requirement mapping

Use this section when the assignment requirements are available.

Before writing detailed code explanations, build a requirement-to-implementation mapping table.

The table should include:

- experiment requirement
- related source file/function/module
- how the implementation satisfies it
- suggested screenshot or run result used as evidence

Suggested format:

```markdown
## 实验要求与实现对应关系

| 实验要求 | 实现位置 | 实现说明 | 验证方式 |
|---|---|---|---|
| 要求 1 | `path/file.c` 中的 `func()` | 简要说明 | 代码截图或运行结果 |
| 要求 2 | `path/file.c` 中的 `func()` | 简要说明 | 代码截图或运行结果 |
```

Rules:

1. Do not write the report only by explaining code.

2. Always connect important code and results back to the experiment requirements.

3. If a requirement is only partially implemented, say so clearly.

4. If a requirement cannot be verified from the project, state that it requires additional runtime evidence.

---

# Section: 实验原理与总体设计

## Goal

Generate report text for the experiment principle and overall design section.

Use this section when the user asks for:

- 实验原理
- 总体设计
- 设计思路
- 项目结构说明
- 模块划分
- 完整实验报告前半部分

## Content requirements

This section should include:

1. experiment background and goal
2. key concepts used by the project
3. project module structure
4. main data flow or control flow
5. how the implementation corresponds to the assignment requirements
6. important simplifications or design choices
7. limitations when relevant

## Style rules

Do not over-explain textbook theory.

The theory should be connected to the actual implementation.

For example, instead of writing a long generic explanation of file systems, write:

```markdown
本实验中的模拟磁盘由 `malloc()` 申请得到，程序将这段连续内存按 1KB 划分为多个盘块。为了管理这些盘块，文件系统在磁盘前部保存超级块、位图和 inode 表，后部作为数据块区保存文件内容。这样可以把文件管理中的“元数据”和“数据区”区分开来。
```

## Text diagrams

For systems, operating system, compiler, database, or network projects, prefer simple text diagrams when useful.

Example:

```text
Input / command
    ↓
main function
    ↓
core module
    ↓
data structure / algorithm
    ↓
output / result
```

For a file system project:

```text
Simulated disk
├── SuperBlock
├── Bitmap
├── Inode Table
└── Data Blocks
```

For a compiler project:

```text
Source text
    ↓
Lexer
    ↓
Parser
    ↓
AST / IR
    ↓
Interpreter / Code Generator
```

## Suggested output format

```markdown
## 1. 实验原理与总体设计

### 1.1 实验目标

...

### 1.2 核心原理

...

### 1.3 项目结构

...

### 1.4 总体流程

...

### 1.5 设计取舍

...
```

Adjust numbering to match the user’s template.

---

# Section: 重点代码截图及讲解

## Goal

Generate complete report text for:

```markdown
## 重点代码截图及讲解
```

This section should explain the most important code snippets in the project and tell the user where to take screenshots.

Unlike a screenshot-only plan, this section must include both:

- the selected source code snippet in a fenced code block
- the corresponding file/function/line-number location
- explanation in report style

## Source reading requirements

Before writing this section:

1. Read the project structure.

2. Identify the main source files.

3. Understand:

   - main modules
   - core data structures
   - important functions
   - entry points
   - algorithm flow
   - interaction between modules
   - how the implementation satisfies the experiment requirements

4. If there are existing report files or previous experiment reports in the project, read them to imitate the user’s writing style.

5. If no prior style sample is available, use a concise undergraduate experiment-report style.

## Code snippet selection rules

Select code snippets that are most suitable for report screenshots.

Prefer:

- core data structures, classes, interfaces, structs, enums, or type definitions
- key algorithm functions
- important module orchestration logic
- code that directly corresponds to experiment requirements
- input/output handling
- command-line entry points
- validation or error handling that reflects important design
- test or demonstration entry points, when relevant

Avoid:

- trivial boilerplate
- repeated similar code
- long unbroken files
- purely mechanical getters/setters
- unrelated UI or configuration code
- code that is hard to explain in a report
- too many screenshots just to cover every file

If there are multiple important snippets in one file, split them into separate figures.

Do not combine multiple unrelated structures or functions into one figure.

## Screenshot density

For a normal undergraduate experiment report, prefer:

- 5 to 8 code figures for medium-size projects
- 8 to 12 code figures for larger projects
- 3 to 5 code figures for small projects

For each code screenshot:

- prefer 15 to 45 lines
- avoid screenshots longer than 70 lines
- split long functions into logically meaningful parts
- do not screenshot entire files unless the file is very short
- avoid selecting many functions that all demonstrate the same idea

If report length is limited, prioritize:

1. core data structures
2. initialization or orchestration logic
3. key algorithm
4. read/write or input/output logic
5. final test or entry point

## Required format for each code figure

Use this structure for each selected code snippet:

```markdown
### 2.x 小节标题

#### 图 2-x 图片标题

**源码片段**

```language
selected source code here
```

**截图位置**

文件名：`path/to/file.ext`

函数名或结构体 / 类 / 枚举名：`name`

建议截图范围：第 x 行至第 y 行

**讲解**

这里写一段简洁但完整的说明，解释该代码片段在实验中的作用、基本实现思路，以及它和实验要求之间的关系。
```

If line numbers cannot be determined precisely, use:

```markdown
建议截图范围：约第 x 行至第 y 行
```

Only use approximate ranges when they are based on actual source inspection.

## Source code block requirements

For every selected screenshot point:

1. Include the actual source code snippet.

2. Wrap the source code in a fenced code block.

3. Use the correct language tag when possible, for example:

   - `c`
   - `cpp`
   - `python`
   - `java`
   - `go`
   - `rust`
   - `ts`
   - `js`
   - `bash`
   - `sql`
   - `json`
   - `yaml`
   - `makefile`

4. The code block should contain only the selected snippet, not the entire file.

5. The snippet should be long enough to show the key logic, but not so long that it becomes unsuitable for a screenshot.

6. Preserve the code exactly unless the user explicitly asks for rewriting.

7. If a function is too long, select the most important continuous region and explain that the screenshot should focus on that range.

8. Do not omit essential lines needed to understand the snippet.

9. Do not replace important code with vague placeholders.

## Explanation style

Each explanation should:

- explain the role of the code in the project
- explain the basic implementation idea
- connect the code to the experiment requirement
- mention important data flow or control flow when relevant
- explain key parameters, return values, or states when useful
- stay concise and concrete
- avoid long tutorials
- avoid unsupported claims
- avoid vague claims such as “提高了效率” unless the code clearly demonstrates that

Good explanation focus:

- what this structure stores
- what this function receives and returns
- how this function coordinates other modules
- how the algorithm proceeds
- how the code handles valid and invalid cases
- how this snippet supports the final experiment result

## Section ending

Do not mechanically add “本节小结” after every subsection.

A short natural closing paragraph may be added when useful, explaining how the selected snippets together support the module or experiment goal.

If the project has too many possible screenshot points, add a final note:

```markdown
若报告篇幅有限，建议优先保留图 2-x、图 2-y 和图 2-z，因为它们分别对应核心数据结构、关键算法流程和最终入口逻辑。
```

---

# Section: 运行结果截图及分析

## Goal

Generate complete report text for:

```markdown
## 运行结果截图及分析
```

This section should explain which commands to run, what output to screenshot, and how each result verifies the experiment.

## Project execution analysis

Before writing this section:

1. Read the project code, README, build scripts, package files, test files, and command-line entry points.

2. Identify real commands supported by the project, such as:

   - `make`
   - `make run`
   - `make test`
   - `python main.py ...`
   - `pytest`
   - `cargo run -- ...`
   - `cargo test`
   - `go run ...`
   - `go test ./...`
   - `npm run ...`
   - `mvn test`
   - `gradle test`
   - custom scripts

3. If sample input files are needed, provide commands to create them.

4. If possible, run the commands and inspect the output.

5. Do not claim a command succeeds unless the output was actually observed.

6. If commands cannot be run, provide recommended commands and clearly state that they are suggested based on the project structure.

## Result organization

Organize results from simple to comprehensive.

A typical order is:

1. build or compilation result
2. basic configuration, input data, or experiment object display
3. core intermediate result
4. key algorithm or module result
5. valid sample result
6. invalid sample or boundary case result
7. comprehensive demonstration
8. automated test result

Do not use a single comprehensive run to replace all module-level evidence.

It is usually better to show several focused results first, then show the full workflow.

## Required format for each result subsection

Use this structure:

```markdown
### 3.x 小节标题

**运行指令**

```bash
command here
```

**建议截图内容**

说明应该截取哪些输出内容，例如开头部分、关键表格、统计信息、最终结果、错误信息、测试汇总等。

如果输出较长，请说明只需要截取哪几部分，避免截图过多。

**结果分析**

用实验报告口吻解释该运行结果说明了什么。分析要结合实验原理和代码功能，说明它如何验证某个模块、算法或实验要求已经实现。
```

## Command requirements

Commands should be based on the project’s real entry points.

Examples:

```bash
make
make run
make test
```

```bash
python main.py examples/input.txt
```

```bash
cargo run -- examples/input.txt
cargo test
```

```bash
npm install
npm run test
npm run dev
```

If sample files are needed, provide creation commands:

```bash
mkdir -p examples
cat > examples/valid.txt <<'EOF'
sample content
EOF
```

Do not invent command-line options that the program does not support.

## Screenshot guidance

For each result, tell the user exactly what to screenshot.

Mention:

- whether to screenshot the command itself
- whether to screenshot the beginning or end of output
- which table, summary line, error message, or final result is most important
- whether long output should be split into multiple screenshots
- which output can be mentioned in text without screenshot

For long output, use wording such as:

```markdown
输出较长时，不需要完整截取，只需保留命令行、核心统计表格和最后的汇总结果。
```

## Result analysis style

The analysis should not merely say:

- “程序运行成功”
- “结果正确”
- “测试通过”
- “说明功能正常”

Instead, explain:

- which part of the output is important
- which experiment requirement it corresponds to
- which module or algorithm it verifies
- how valid input and invalid input differ
- why an error result is reasonable
- what an automatic test result adds beyond manual runs

Use natural expressions:

- “从输出可以看到……”
- “这一结果说明……”
- “与前一组样例相比……”
- “错误信息没有导致程序异常退出，而是……”
- “测试汇总中的 passed 数量说明……”

## Automated tests

If the project contains tests, include a final subsection such as:

```markdown
### 3.x 自动化测试结果
```

Include:

- test command
- suggested screenshot content
- result analysis

Prefer screenshotting the summary line, such as:

- passed / failed count
- test suite summary
- coverage summary, if relevant
- final success message

Do not fabricate test results.

If tests are not run, describe the expected screenshot location after the user runs the command.

## Final screenshot order

At the end of the result section, add:

```markdown
### 建议最终报告保留的截图顺序
```

Then list only the most valuable screenshots.

Each item should briefly explain the role of that screenshot.

Example:

```markdown
1. 项目构建结果：证明代码能够在实验环境中正常编译。
2. 合法输入运行结果：展示核心功能在正常输入下的输出。
3. 边界输入运行结果：说明程序对特殊情况的处理。
4. 自动化测试汇总：补充证明主要模块通过统一测试验证。
```

Keep this list selective.

Do not include every possible screenshot.

---

# Section: 实验结论及心得体会

## Goal

Generate the final conclusion and reflection section.

Use this section when the user asks for:

- 实验结论
- 心得体会
- 总结
- 最后一节
- 报告结尾
- experiment reflection

## Content requirements

The conclusion should include:

1. what the experiment implemented
2. which requirements were verified
3. what was learned from the implementation
4. problems encountered and how they were handled
5. limitations of the current implementation
6. possible future improvements

## Style rules

Avoid empty phrases such as:

- “我受益匪浅”
- “提高了实践能力”
- “加深了理解”
- “为以后的学习打下了坚实基础”

Prefer concrete reflections, such as:

- “在实现 bitmap 分配时，需要同时维护位图状态和空闲计数，否则容易出现元数据不一致。”
- “分块读写使文件偏移、逻辑块号和块内偏移之间的关系更加直观。”
- “在多线程测试中，文件表和块分配信息属于共享元数据，因此需要通过互斥锁保护。”
- “当前实现采用覆盖写语义，没有实现追加写和目录结构，这是后续可以扩展的方向。”

## Suggested format

```markdown
## 实验结论及心得体会

本实验完成了……。从运行结果可以看到……。

在实现过程中，……。

当前实现仍然存在一些简化之处，例如……。如果继续完善，可以考虑……。
```

Keep it concise unless the user asks for a longer conclusion.

---

# Complete report mode

When the user asks for a complete report, generate a structured Markdown report.

Suggested structure:

```markdown
# 实验报告标题

## 1. 实验目的

## 2. 实验环境

## 3. 实验原理与总体设计

## 4. 实验要求与实现对应关系

## 5. 重点代码截图及讲解

## 6. 运行结果截图及分析

## 7. 实验结论及心得体会
```

Adjust numbering to the user’s school template.

If the user already has fixed section numbers, do not renumber them unless asked.

---

# Final output requirements

When the user asks to generate report content:

1. Output a complete Markdown document or section.

2. Include only the requested sections unless the user asks for a full report.

3. For code screenshot sections, every selected code figure must include:

   - figure title
   - source code snippet in a fenced code block
   - file name
   - function/class/struct/enum/module name
   - suggested line range
   - explanation text

4. For result screenshot sections, every result subsection must include:

   - run command
   - suggested screenshot content
   - result analysis

5. Use real project paths, names, commands, and line numbers whenever available.

6. If line numbers cannot be determined precisely, say “建议截图范围：约第 x 行至第 y 行” only when the approximate range is based on actual source inspection.

7. Do not output images.

8. Do not include irrelevant implementation notes about this skill.

9. Keep the report text ready to copy into a `.md` file.

10. If creating a Markdown file directly, choose a clear filename.

## Suggested output file names

If creating a Markdown file directly, use one of these names unless the user specifies another:

```text
report_sections.md
```

```text
report_code_and_results.md
```

```text
report_sections_2_3.md
```

```text
experiment_report_draft.md
```

## Final response style after file creation

If a Markdown file is created directly, reply briefly:

```text
已生成 `experiment_report_draft.md`，内容包含所需实验报告章节，并为代码截图和运行结果截图加入了对应位置、说明和分析。
```

---

# Quality checklist

Before finalizing the report content, check:

- Have the actual project files been inspected?
- Are file names, function names, and line ranges real or clearly marked as approximate?
- Are code snippets short enough for screenshots?
- Are important experiment requirements covered?
- Are commands real, inferred, or suggested?
- Are observed outputs clearly distinguished from suggested outputs?
- Does each result analysis explain what is verified?
- Does the writing avoid empty praise and repetitive formulas?
- Does the structure match the user’s report template?
- Does the final text read like a report section rather than a development note?
