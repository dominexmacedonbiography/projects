# CMLL Language Guide

CMLL means **Command Language Made Legible**. It is a small command-oriented programming language implemented in C. CMLL is designed for readable scripts that combine variables, conditions, loops, functions, file operations, environment-variable inspection, URL extraction, and operating-system commands.

This guide is based on the current CMLL lexer, parser, and runtime implementation.

## 1. Running CMLL

CMLL executes a `.cmll` source file.

```bash
cmll hello.cmll
```

Show the version:

```bash
cmll --version
```

Show help:

```bash
cmll --help
```

The current executable accepts one command-line argument:

```text
cmll <file.cmll>
cmll --version
cmll --help
```

CMLL is currently a file-based interpreter, not an interactive REPL.

---

## 2. Basic program structure

A CMLL program is made from statements. Statements may be separated by semicolons or by the parser's supported statement separators.

A simple program:

```cmll
say "Hello from CMLL";
say "Command Language Made Legible";
```

`show` is also available:

```cmll
show "Hello from show";
```

Both `say` and `show` evaluate an expression and print its string representation followed by a newline.

---

## 3. Comments and formatting

The current lexer does not define a dedicated comment token. Do not assume that `//` or `#` comments are supported by this version.

Use clear formatting and separate statements:

```cmll
set name = "Dominex Macedon";
set version = "1.0.0";

say name;
say version;
```

Blocks use braces:

```cmll
if true {
    say "The condition is true";
} else {
    say "The condition is false";
}
```

---

## 4. Variables with `set`

Use `set` to create a variable:

```cmll
set name = "CMLL";
set version = 1;
set enabled = true;
```

Variables can be reassigned:

```cmll
set count = 1;
count = count + 1;
count = count + 4;

say count;
```

Assignment can target a variable only in the current runtime implementation.

A variable name must be an identifier:

```cmll
set project_name = "CMLL";
set file_count = 3;
```

---

## 5. Supported value types

The runtime defines these value categories:

- `null`
- numbers
- strings
- booleans
- arrays
- objects
- functions

### 5.1 Numbers

Numbers are represented by the runtime as numeric values.

```cmll
set integer_value = 42;
set decimal_value = 3.14159;
set negative_value = -10;

say integer_value;
say decimal_value;
say negative_value;
```

Arithmetic operators:

```cmll
set a = 20;
set b = 6;

say a + b;
say a - b;
say a * b;
say a / b;
say a % b;
```

Use parentheses when you want to make precedence explicit:

```cmll
set result = (10 + 5) * 2;
say result;
```

### 5.2 Strings

Strings are written with quotes:

```cmll
set language = "CMLL";
set message = "Hello, " + language;

say message;
```

String conversion is handled by the runtime when values are printed or passed to command execution.

### 5.3 Booleans

The boolean literals are `true` and `false`:

```cmll
set installed = true;
set failed = false;

if installed {
    say "The tool is installed";
} else {
    say "The tool is not installed";
}
```

### 5.4 Null

Use `null` when a value is intentionally empty:

```cmll
set result = null;
show result;
```

### 5.5 Arrays

Arrays use square brackets:

```cmll
set tools = [
    "python",
    "node",
    "git",
    "cmake"
];

show tools;
```

Arrays can contain expressions and different value types:

```cmll
set values = [
    10,
    "CMLL",
    true,
    null
];

show values;
```

The current `for` implementation iterates over arrays.

### 5.6 Objects

Objects use braces with key-value pairs:

```cmll
set project = {
    name: "CMLL",
    version: "1.0.0",
    language: "C"
};

show project;
```

Property access is represented by the parser:

```cmll
set user = {
    name: "Dominex",
    role: "developer"
};

say user.name;
say user.role;
```

Object access and object mutation should be tested against the exact runtime version being used. The current runtime is more complete for reading and iterating values than for every possible object-assignment form.

---

## 6. Operators

The lexer defines these operators.

### Arithmetic

```cmll
set sum = 10 + 2;
set difference = 10 - 2;
set product = 10 * 2;
set quotient = 10 / 2;
set remainder = 10 % 3;
```

### Comparisons

```cmll
if 10 == 10 {
    say "Equal";
} else {
    say "Not equal";
}

if 10 != 5 {
    say "Different";
} else {
    say "Same";
}

if 10 < 20 {
    say "Less than";
} else {
    say "Not less than";
}

if 20 <= 20 {
    say "Less than or equal";
} else {
    say "Greater";
}

if 30 > 10 {
    say "Greater than";
} else {
    say "Not greater";
}

if 30 >= 30 {
    say "Greater than or equal";
} else {
    say "Less";
}
```

### Logical operators

The lexer defines:

- `and`
- `or`
- `not`

Example:

```cmll
set has_python = true;
set has_node = false;

if has_python and not has_node {
    say "Python is available but Node.js is not available";
} else {
    say "The condition was not matched";
}
```

Use the logical spelling supported by the lexer instead of assuming C-style `&&` and `||`.

---

## 7. Conditions with `if` and `else`

Basic condition:

```cmll
set age = 20;

if age >= 18 {
    say "Adult";
} else {
    say "Under 18";
}
```

Nested conditions:

```cmll
set operating_system = "linux";
set installed = true;

if operating_system == "linux" {
    if installed {
        say "The tool is installed on Linux";
    } else {
        say "The tool is not installed";
    }
} else {
    say "This example targets Linux";
}
```

An `else if` chain is represented by placing `if` after `else`:

```cmll
set status = 2;

if status == 0 {
    say "Success";
} else if status == 1 {
    say "Warning";
} else {
    say "Failure or unknown status";
}
```

---

## 8. `while` loops

A `while` loop repeats while its condition is truthy:

```cmll
set count = 1;

while count <= 5 {
    say count;
    count = count + 1;
}
```

Another example:

```cmll
set remaining = 3;

while remaining > 0 {
    say "Remaining";
    say remaining;
    remaining = remaining - 1;
}
```

The runtime has a guard that fails a loop after more than one million iterations. Always make sure the loop condition can eventually become false.

---

## 9. `for ... in` loops

The syntax is:

```cmll
for item in collection {
    ...
}
```

The current runtime requires the collection to be an array.

Example:

```cmll
set languages = [
    "CMLL",
    "Puma",
    "greenServe"
];

for language in languages {
    say language;
}
```

Numbers in an array:

```cmll
set numbers = [1, 2, 3, 4, 5];

for number in numbers {
    show number;
}
```

Objects in an array:

```cmll
set tools = [
    {
        name: "Python",
        command: "python"
    },
    {
        name: "Node.js",
        command: "node"
    },
    {
        name: "Git",
        command: "git"
    }
];

for tool in tools {
    say tool.name;
    say tool.command;
}
```

The runtime copies each array item into the loop variable before executing the loop body.

---

## 10. Functions with `func`

Declare a function with `func`, a name, a parameter list, and a block:

```cmll
func greet(name) {
    say "Hello, " + name;
}

greet("Developer");
```

A function can return a value:

```cmll
func add(a, b) {
    return a + b;
}

set result = add(10, 20);
say result;
```

Multiple parameters:

```cmll
func describe(name, version, language) {
    say name;
    say version;
    say language;
}

describe("CMLL", "1.0.0", "C");
```

A function without an explicit return produces a null-like result:

```cmll
func print_message(message) {
    say message;
}

set result = print_message("Hello");
show result;
```

Function declarations are registered before ordinary top-level statements execute. This allows a function to be called before its declaration in the source file:

```cmll
say multiply(4, 5);

func multiply(a, b) {
    return a * b;
}
```

---

## 11. Tasks with `task`

The parser and runtime represent `task` declarations similarly to function declarations:

```cmll
task show_environment() {
    say "Checking environment";
}

show_environment();
```

A task can accept parameters and return values:

```cmll
task announce(name) {
    return "User: " + name;
}

say announce("Dominex");
```

In the current implementation, `task` is not a separate asynchronous scheduler. It is stored and invoked through the same function-value mechanism used by `func`.

---

## 12. Project declarations

Use `project` to print a project description or project value:

```cmll
project "CMLL command utilities";
```

A variable can be used:

```cmll
set project_name = "CMLL Tools";
project project_name;
```

The runtime prints the value in this form:

```text
Project: CMLL Tools
```

---

## 13. Running operating-system commands with `run`

`run` evaluates an expression, converts it to text, and executes it through the operating system command processor.

Check Python:

```cmll
run "python --version";
```

Some systems use `python3`:

```cmll
run "python3 --version";
```

Check Node.js:

```cmll
run "node --version";
```

Check npm:

```cmll
run "npm --version";
```

Check Git:

```cmll
run "git --version";
```

Check CMake:

```cmll
run "cmake --version";
```

Check the C compiler:

```cmll
run "cc --version";
```

Check the current directory:

```cmll
run "pwd";
```

List files on Linux:

```cmll
run "ls -la";
```

List files on Windows Command Prompt:

```cmll
run "dir";
```

Print the current user:

```cmll
run "whoami";
```

The command's exit status is checked by the runtime. A nonzero status causes a CMLL runtime error.

### Security warning

`run` executes operating-system commands. Do not execute untrusted CMLL files, and do not concatenate untrusted user input into shell commands without validation.

---

## 14. Installing and checking Python

The following examples use the system package manager. The correct command depends on the operating system.

### Check whether Python is already installed

Linux/macOS:

```cmll
run "python3 --version";
```

Windows:

```cmll
run "python --version";
```

### Install Python on Debian or Ubuntu

```cmll
run "sudo apt update";
run "sudo apt install -y python3 python3-pip";
```

### Install Python on Fedora

```cmll
run "sudo dnf install -y python3 python3-pip";
```

### Install Python on Arch Linux

```cmll
run "sudo pacman -Sy --needed python python-pip";
```

### Verify Python and pip

```cmll
run "python3 --version";
run "python3 -m pip --version";
```

### Run a Python script

```cmll
run "python3 script.py";
```

### Create and run a Python virtual environment

```cmll
run "python3 -m venv .venv";
run ".venv/bin/python --version";
```

On Windows:

```cmll
run "python -m venv .venv";
run ".venv\\Scripts\\python.exe --version";
```

The command syntax is passed to the operating system. Use the path format appropriate for the operating system where CMLL is running.

---

## 15. Installing and checking Node.js

### Check Node.js and npm

```cmll
run "node --version";
run "npm --version";
```

### Check whether Node.js is available

```cmll
run "command -v node";
```

On Windows:

```cmll
run "where node";
```

### Run a Node.js file

```cmll
run "node app.js";
```

### Create a Node.js project

```cmll
run "mkdir cmll-node-example";
run "cd cmll-node-example && npm init -y";
```

### Install a package

```cmll
run "npm install readline-sync";
```

### Install development dependencies

```cmll
run "npm install --save-dev eslint";
```

### Run an npm script

```cmll
run "npm run start";
```

The `run` statement executes the command in the host shell. Shell features such as `&&`, pipes, redirection, and platform-specific commands depend on the operating system and shell configuration.

---

## 16. Git and repository workflows

Check Git:

```cmll
run "git --version";
```

Initialize a repository:

```cmll
run "git init";
```

Check repository status:

```cmll
run "git status";
```

Show branches:

```cmll
run "git branch";
```

Show recent commits:

```cmll
run "git log --oneline -5";
```

Clone a repository:

```cmll
run "git clone https://github.com/example/project.git";
```

Pull updates:

```cmll
run "git pull";
```

The command runs with the permissions of the current user.

---

## 17. Reading files

The syntax is:

```cmll
read file FILE_EXPRESSION as VARIABLE;
```

Example:

```cmll
read file "README.md" as content;
show content;
```

Read a configuration file:

```cmll
read file "config.json" as config_text;
say config_text;
```

Read a source file and display it:

```cmll
set filename = "example.cmll";
read file filename as source;
show source;
```

If the file cannot be read, the runtime reports an error and marks execution as failed.

---

## 18. Writing files

The syntax is:

```cmll
write file FILE_EXPRESSION from CONTENT_EXPRESSION;
```

Write a text file:

```cmll
write file "hello.txt" from "Hello from CMLL";
```

Write a generated report:

```cmll
set report = "CMLL report\nStatus: complete\n";
write file "report.txt" from report;
```

Write a JSON-like text file:

```cmll
set data = "{\"name\":\"CMLL\",\"version\":\"1.0.0\"}";
write file "data.json" from data;
```

The runtime converts the content expression to text before writing it.

---

## 19. Environment variables with `env`

The `env` keyword reads an environment variable and prints its value when used as a statement.

```cmll
env "HOME";
```

Read common environment variables:

```cmll
env "PATH";
env "USER";
env "SHELL";
```

Check a project-related variable:

```cmll
env "GOOGLE_CLOUD_PROJECT";
```

The current runtime implementation prints the environment value. It does not currently expose `env(...)` as a normal value-returning expression for use in every assignment context.

Prefer this:

```cmll
env "PATH";
```

Do not assume this works in the current runtime:

```cmll
set path = env("PATH");
```

---

## 20. Extracting URLs with `list urls from`

The syntax is:

```cmll
list urls from SOURCE_EXPRESSION;
```

Extract URLs from a string:

```cmll
set text = "Visit https://example.com and http://localhost:8080 for more information.";
list urls from text;
```

Extract URLs from a file's contents:

```cmll
read file "links.txt" as content;
list urls from content;
```

The runtime searches for `http://` and `https://` URLs and prints each detected URL on its own line.

This is a text scanner, not a complete URL validator.

---

## 21. Nested loops and conditions

```cmll
set groups = [
    {
        name: "backend",
        tools: ["C", "Node.js"]
    },
    {
        name: "automation",
        tools: ["Python", "CMLL"]
    }
];

for group in groups {
    say group.name;

    for tool in group.tools {
        say tool;
    }
}
```

Nested conditions:

```cmll
set tool = {
    name: "Python",
    installed: true,
    version: "3.12"
};

if tool.installed {
    if tool.name == "Python" {
        say "Python is installed";
        say tool.version;
    } else {
        say "Another tool is installed";
    }
} else {
    say "Tool is not installed";
}
```

---

## 22. Practical tool-checking script

This example checks several tools. A command that is not installed may cause the runtime to stop because `run` treats a nonzero exit status as an error.

```cmll
project "Development environment check";

say "Checking Python";
run "python3 --version";

say "Checking Node.js";
run "node --version";

say "Checking npm";
run "npm --version";

say "Checking Git";
run "git --version";

say "Checking C compiler";
run "cc --version";

say "Environment check complete";
```

If the target machine may use `python` instead of `python3`, use the command appropriate for that machine.

---

## 23. Generate a project report

```cmll
project "Project report";

set report = "Project: CMLL\n";
set report = report + "Language: C\n";
set report = report + "Purpose: command-oriented scripting\n";

write file "project-report.txt" from report;
say report;
```

---

## 24. File-processing workflow

```cmll
project "File processing";

set input_file = "input.txt";
set output_file = "output.txt";

read file input_file as content;

set result = "Processed content:\n";
set result = result + content;

write file output_file from result;

say "The output file was written";
```

---

## 25. A function-based calculation example

```cmll
func calculate_total(first, second, third) {
    return first + second + third;
}

set total = calculate_total(100, 250, 50);

if total >= 300 {
    say "The total is at least 300";
} else {
    say "The total is below 300";
}

show total;
```

---

## 26. A task-based automation example

```cmll
task check_python() {
    say "Checking Python";
    run "python3 --version";
}

task check_node() {
    say "Checking Node.js";
    run "node --version";
}

task check_git() {
    say "Checking Git";
    run "git --version";
}

check_python();
check_node();
check_git();
```

---

## 27. A complete example

Save this as `development-check.cmll`:

```cmll
project "CMLL Development Check";

set tools = [
    "Python",
    "Node.js",
    "npm",
    "Git"
];

say "Tools to check:";

for tool in tools {
    say tool;
}

say "Checking Python";
run "python3 --version";

say "Checking Node.js";
run "node --version";

say "Checking npm";
run "npm --version";

say "Checking Git";
run "git --version";

set report = "Development check completed\n";
write file "development-check.txt" from report;

say report;
```

Run it:

```bash
cmll development-check.cmll
```

---

## 28. Keyword reference

| Keyword | Purpose |
|---|---|
| `project` | Prints a project value with a `Project:` prefix |
| `set` | Declares a variable and assigns an expression |
| `if` | Executes a block when a condition is truthy |
| `else` | Provides an alternative block |
| `while` | Repeats a block while a condition is truthy |
| `for` | Iterates over an array |
| `in` | Separates a loop variable from its collection |
| `func` | Declares a callable function |
| `task` | Declares a callable task using the same runtime function mechanism |
| `return` | Returns a value from a function or task |
| `say` | Evaluates and prints an expression |
| `show` | Evaluates and prints an expression |
| `run` | Executes a system command |
| `read file` | Reads a file into a variable |
| `write file` | Writes text to a file |
| `list urls from` | Extracts HTTP and HTTPS URLs from text |
| `env` | Prints an environment variable value |
| `true` | Boolean true literal |
| `false` | Boolean false literal |
| `null` | Null literal |

The lexer also contains tokens for `exists`, `get`, and pipeline syntax. Their parser/runtime behavior should be considered experimental or incomplete in this version.

---

## 29. Current implementation limitations

The following points are important when writing programs for this version:

1. `cmll` executes source files and supports `--version` and `--help`; it is not currently an interactive REPL.
2. `run` executes commands through the operating system and should only be used with trusted input.
3. The current `for` runtime requires an array.
4. `while` has a one-million-iteration safety guard.
5. `env` currently prints an environment variable rather than behaving as a fully general value-returning expression.
6. `exists` is tokenized and parsed, but the runtime's file-existence node is currently a no-op.
7. `get` is tokenized and parsed as an HTTP-get node, but the current runtime does not provide a complete HTTP request implementation for it.
8. URL extraction detects text beginning with `http://` or `https://`; it is not a full URL parser.
9. Shell syntax and commands are platform-dependent.
10. The current lexer does not provide a dedicated comment syntax, so comments should not be assumed to work.

---

## 30. Recommended authoring rules

When generating CMLL code:

1. Use `.cmll` as the source-file extension.
2. Use `set name = expression;` for variable declarations.
3. Use `name = expression;` for variable reassignment.
4. Use braces for `if`, `else`, `while`, `for`, `func`, and `task` blocks.
5. Use `for item in array { ... }` for collection iteration.
6. Use `read file path as variable;` for file reading.
7. Use `write file path from content;` for file writing.
8. Use `run "command";` only with trusted command strings.
9. Use `return expression;` inside functions and tasks.
10. Do not assume unsupported features such as imports, asynchronous task scheduling, a complete HTTP client, or a working file-existence expression.
11. Test commands on the target operating system because Linux, macOS, and Windows use different tools and shell syntax.
12. Prefer small scripts with clear variable names and explicit control flow.

---

## 31. Minimal syntax cheat sheet

```cmll
project "Example";

set name = "CMLL";
set count = 0;
set items = ["one", "two", "three"];

if count == 0 {
    say name;
} else {
    show count;
}

while count < 3 {
    count = count + 1;
}

for item in items {
    say item;
}

func add(a, b) {
    return a + b;
}

task announce(message) {
    say message;
}

read file "input.txt" as content;
write file "output.txt" from content;

env "PATH";
list urls from "https://example.com";
run "python3 --version";
```

---

## License and project information

CMLL is a C-based command-oriented programming-language project developed by **Dominex Macedon**.
