---

name: report-write
description: Use when the user asks to write, revise, or complete Chinese undergraduate experiment report sections based on a code project, especially key code screenshots, source-code explanations, running result screenshots, and result analysis. The output should be a Markdown report section.
---
# Report Write

## Purpose

This skill helps write Chinese undergraduate experiment report sections based on an actual code project.

The main tasks are:

* read and understand the provided project source code
* identify important code snippets suitable for screenshots
* provide the corresponding source code in fenced code blocks
* provide exact file/function/line-number locations
* write concise explanations in experiment-report style
* inspect or infer real running commands from the project
* organize running result screenshots and analysis
* output the final content as a Markdown document

The output should be suitable for direct inclusion in an experiment report.

## When to use

Use this skill when the user asks to write or revise report sections such as:

* `2. 重点代码截图及讲解`
* `3. 运行结果截图及分析`
* code screenshot explanations
* running result screenshot analysis
* experiment report content based on a project
* report text that references actual project files, functions, commands, or outputs

This skill is suitable for projects in different languages, including but not limited to:

* C / C++
* Python
* Java
* Go
* Rust
* JavaScript / TypeScript
* Shell
* SQL
* mixed-language coursework projects

## Core rules

1. Read the actual project before writing.

2. Do not judge only by file names. Understand the project structure, main modules, entry points, key functions, and module relationships from real code.

3. Prefer evidence from source code, README, build scripts, tests, command-line entry points, and actual run commands.

4. Do not invent unsupported features, commands, results, file names, or line numbers.

5. If something cannot be confirmed, say so clearly and provide a reasonable suggested command or screenshot plan.

6. The report language should be suitable for an undergraduate experiment report:

   * concise
   * clear
   * natural
   * not overly colloquial
   * not full of empty phrases
   * focused on the relation between code, experiment principles, and implementation requirements

7. Avoid repetitive sentence patterns such as:

   * “该代码片段定义了……”
   * “该结果表明……”
   * “本节代码完成了……”

8. Use natural report wording such as:

   * “这里……”
   * “这一部分……”
   * “函数中先……再……”
   * “从输出可以看到……”
   * “这一结果说明……”
   * “与前一部分相比……”

9. Output the final answer as Markdown content.

10. If the user asks to create a file directly, write the report section to a `.md` file.

---

# Section 2: 重点代码截图及讲解

## Goal

Generate the complete report text for:

```markdown
## 2. 重点代码截图及讲解
```

This section should explain the most important code snippets in the project and tell the user where to take screenshots.

Unlike a screenshot-only plan, this section must include both:

* the selected source code snippet in a fenced code block
* the corresponding file/function/line-number location

## Source reading requirements

Before writing Section 2:

1. Read the project structure.

2. Identify the main source files.

3. Understand:

   * main modules
   * core data structures
   * important functions
   * entry points
   * algorithm flow
   * interaction between modules
   * how the implementation satisfies the experiment requirements

4. If there are existing report files or previous experiment reports in the project, read them to imitate the user’s writing style.

5. If no prior style sample is available, use a concise undergraduate experiment-report style.

## Code snippet selection rules

Select code snippets that are most suitable for report screenshots.

Prefer:

* core data structures, classes, interfaces, structs, enums, or type definitions
* key algorithm functions
* important module orchestration logic
* code that directly corresponds to experiment requirements
* input/output handling
* command-line entry points
* validation or error handling that reflects important design
* test or demonstration entry points, when relevant

Avoid:

* trivial boilerplate
* repeated similar code
* long unbroken files
* purely mechanical getters/setters
* unrelated UI or configuration code
* code that is hard to explain in a report
* too many screenshots just to cover every file

If there are multiple important snippets in one file, split them into separate figures. Do not combine multiple unrelated structures or functions into one figure.

## Required format for each code figure

Each code snippet should be written as one figure.

Use this structure:

````markdown
### 2.x 小节标题

#### 图 2-x 图片标题

**源码片段**

```language
selected source code here
````

**截图位置**

文件名：`path/to/file.ext`
函数名或结构体 / 类 / 枚举名：`name`
建议截图范围：第 x 行至第 y 行

**讲解**

这里写一段简洁但完整的说明，解释该代码片段在实验中的作用、基本实现思路，以及它和实验要求之间的关系。

````

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

## Section 2 ending

Do not mechanically add “本节小结” after every subsection.

A short natural closing paragraph may be added when useful, explaining how the selected snippets together support the module or experiment goal.

If the project has too many possible screenshot points, add a final note:

```markdown
若报告篇幅有限，建议优先保留图 2-x、图 2-y 和图 2-z，因为它们分别对应核心数据结构、关键算法流程和最终入口逻辑。
````

---

# Section 3: 运行结果截图及分析

## Goal

Generate the complete report text for:

```markdown
## 3. 运行结果截图及分析
```

This section should explain which commands to run, what output to screenshot, and how each result verifies the experiment.

## Project execution analysis

Before writing Section 3:

1. Read the project code, README, build scripts, package files, test files, and command-line entry points.

2. Identify real commands supported by the project, such as:

   * `make`
   * `make test`
   * `python main.py ...`
   * `pytest`
   * `cargo run -- ...`
   * `cargo test`
   * `go run ...`
   * `go test ./...`
   * `npm run ...`
   * `mvn test`
   * `gradle test`
   * custom scripts

3. If sample input files are needed, provide commands to create them.

4. If possible, run the commands and inspect the output.

5. Do not claim a command succeeds unless the output was actually observed.

6. If commands cannot be run, provide recommended commands and clearly state that they are suggested based on the project structure.

## Result organization

Organize results from simple to comprehensive.

A typical order is:

1. basic configuration, input data, or experiment object display
2. core intermediate result
3. key algorithm or module result
4. final function result
5. valid sample result
6. invalid sample or boundary case result
7. comprehensive demonstration
8. automated test result

Do not use a single comprehensive run to replace all module-level evidence. It is usually better to show several focused results first, then show the full workflow.

## Required format for each result subsection

Use this structure:

````markdown
### 3.x 小节标题

**运行指令**

```bash
command here
````

**建议截图内容**

说明应该截取哪些输出内容，例如开头部分、关键表格、统计信息、最终结果、错误信息、测试汇总等。
如果输出较长，请说明只需要截取哪几部分，避免截图过多。

**结果分析**

用实验报告口吻解释该运行结果说明了什么。分析要结合实验原理和代码功能，说明它如何验证某个模块、算法或实验要求已经实现。

````

## Command requirements

Commands should be based on the project’s real entry points.

Examples:

```bash
make
make test
````

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

* whether to screenshot the command itself
* whether to screenshot the beginning or end of output
* which table, summary line, error message, or final result is most important
* whether long output should be split into multiple screenshots
* which output can be mentioned in text without screenshot

For long output, use wording such as:

```markdown
输出较长时，不需要完整截取，只需保留命令行、核心统计表格和最后的汇总结果。
```

## Result analysis style

The analysis should not merely say:

* “程序运行成功”
* “结果正确”
* “测试通过”
* “说明功能正常”

Instead, explain:

* which part of the output is important
* which experiment requirement it corresponds to
* which module or algorithm it verifies
* how valid input and invalid input differ
* why an error result is reasonable
* what an automatic test result adds beyond manual runs

Use natural expressions:

* “从输出可以看到……”
* “这一结果说明……”
* “与前一组样例相比……”
* “错误信息没有导致程序异常退出，而是……”
* “测试汇总中的 passed 数量说明……”

## Automated tests

If the project contains tests, include a final subsection such as:

```markdown
### 3.x 自动化测试结果
```

Include:

* test command
* suggested screenshot content
* result analysis

Prefer screenshotting the summary line, such as:

* passed / failed count
* test suite summary
* coverage summary, if relevant
* final success message

Do not fabricate test results. If tests are not run, describe the expected screenshot location after the user runs the command.

## Final screenshot order

At the end of Section 3, add:

```markdown
### 建议最终报告保留的截图顺序
```

Then list only the most valuable screenshots.

Each item should briefly explain the role of that screenshot.

Example:

```markdown
1. 项目构建结果：证明代码能够在实验环境中正常编译或启动。
2. 合法输入运行结果：展示核心功能在正常输入下的输出。
3. 边界输入运行结果：说明程序对特殊情况的处理。
4. 自动化测试汇总：补充证明主要模块通过统一测试验证。
```

Keep this list selective. Do not include every possible screenshot.

---

# Final output requirements

When the user asks to generate the report:

1. Output a complete Markdown document.

2. Include the requested sections only, unless the user asks for more.

3. For Section 2, every selected code figure must include:

   * figure title
   * source code snippet in a fenced code block
   * file name
   * function/class/struct/enum/module name
   * suggested line range
   * explanation text

4. For Section 3, every result subsection must include:

   * run command
   * suggested screenshot content
   * result analysis

5. Use real project paths, names, commands, and line numbers whenever available.

6. If line numbers cannot be determined precisely, say “建议截图范围：约第 x 行至第 y 行” only when the approximate range is based on actual source inspection.

7. Do not output images.

8. Do not include irrelevant implementation notes about this skill.

9. Keep the report text ready to copy into a `.md` file.

## Suggested output file name

If creating a Markdown file directly, use one of these names unless the user specifies another:

```text
report_sections_2_3.md
```

or:

```text
report_code_and_results.md
```

## Final response style after file creation

If a Markdown file is created directly, reply briefly:

```text
已生成 `report_sections_2_3.md`，内容包含“2. 重点代码截图及讲解”和“3. 运行结果截图及分析”。其中第 2 节已为每个截图点加入源码代码块、对应位置和讲解。
```
