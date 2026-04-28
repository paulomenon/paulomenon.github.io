---
layout: single
title: "Learn Python from Examples — From Basics to Real-World Use Cases"
date: 2026-04-28 12:00:00 +0000
description: "A hands-on guide to learning Python through practical examples organised by difficulty level — from hello world to REST APIs, multithreading, and backtracking algorithms."
tags: [python, programming, beginner, intermediate, advanced, learning, examples, open source, github]
header:
  og_image: "/assets/images/python-examples.jpg"
---

## Learn Python from Examples — From Basics to Real-World Use Cases

<figure>
<img src="/assets/images/daniil-komov-unsplash.jpg" title="Photo by Daniil Komov">
 <figcaption style="font-size: 0.8em;
            color: #555;">Photo by <a href="https://unsplash.com/@dkomow?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Daniil Komov</a> on <a href="https://unsplash.com/photos/laptop-screen-displaying-code-with-glasses-and-mug-kAM9s_t1igY?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
</figcaption>
</figure>

I put together a collection of Python examples that progress from basic concepts to more real-world, advanced use cases. The repository is open source and available on GitHub — feel free to clone it, experiment with it, and use it however you like.

<i class="fab fa-youtube"></i> If you don't know what a repository is, **[learn here](https://www.youtube.com/watch?v=a9u2yZvsqHA)** and come back!

<i class="fab fa-github"></i> **[python-simple-example](https://github.com/paulomenon/python-simple-example)**

If you're struggling to learn how to program, the most important thing I can tell you is this: **you need to think like a programmer**. Programming isn't about memorising syntax — it's about breaking problems down into smaller pieces, thinking logically, and building solutions step by step. If you haven't already, I'd recommend reading my earlier posts on [Essential Problem-Solving Exercises to Kickstart Your Programming Journey](/problem-solving/) and [Get Started Programming](/get-started-programming/), where I cover the mindset and fundamentals that will make everything in this repository click much faster.

With that foundation in place, this repository is designed to give you the **practical, hands-on practice** you need to turn that thinking into real code.

---

## How the Repository is Organised

The examples are split into three levels, each in its own folder. Every example is self-contained with its own README, so you can jump into any one that interests you without needing to work through them in order — though if you're just starting out, I'd recommend going from beginner to advanced.

---

## Prerequisites — Setting Up Python on Your Machine

Before diving into the examples, you'll need Python installed and a code editor to work with. Here's how to get set up on each platform.

### Installing Python

<p align="center">
  <a href="https://www.python.org/"><img src="/assets/images/python-logo.png" alt="Python Logo" width="300"></a>
</p>

**[Python](https://www.python.org/)** is a free, open-source programming language known for its clean syntax and readability — one of the best languages to start with.

- **Linux** — Most distributions come with Python pre-installed. Open a terminal and run `python3 --version` to check. If it's not there, install it with your package manager (e.g. `sudo apt install python3` on Ubuntu/Debian or `sudo dnf install python3` on Fedora/RHEL).

- **macOS** — macOS may ship with an older version. I'd recommend installing the latest version from [python.org](https://www.python.org/downloads/) or via Homebrew with `brew install python3`.

- **Windows** — Download the installer from [python.org](https://www.python.org/downloads/). During installation, make sure to tick **"Add Python to PATH"** — this saves you a lot of headaches later. You can verify the installation by opening Command Prompt and running `python --version`.

For all platforms, you'll want **Python 3.10 or later** to take advantage of features like structural pattern matching (`match/case`) used in some of the examples.

### Choosing an IDE or Code Editor

You can write Python in any text editor, but a good IDE makes a huge difference — especially for beginners. Here are my recommendations:

- **[Visual Studio Code (VS Code)](https://code.visualstudio.com/)** — This is what I use daily. It's free, lightweight, and incredibly powerful with the right extensions. Install the **Python extension by Microsoft** from the marketplace and you'll get syntax highlighting, IntelliSense, debugging, and integrated terminal support out of the box. It runs on Linux, macOS, and Windows.

- **[PyCharm Community Edition](https://www.jetbrains.com/pycharm/download/)** — A popular choice specifically designed for Python development. The Community Edition is free and comes with built-in debugging, testing, and project management. It's slightly heavier than VS Code but provides a more opinionated, Python-focused experience.

- **[Thonny](https://thonny.org/)** — If you're a complete beginner, Thonny is designed with you in mind. It's a simple, clean Python IDE that comes with Python bundled, so you don't need to install anything separately. Great for learning, though you'll likely outgrow it as your skills develop.

- **[Jupyter Notebooks](https://jupyter.org/)** — Ideal if you prefer running code in small, interactive cells rather than full scripts. Popular in data science and great for experimentation. You can install it with `pip install notebook` and launch it with `jupyter notebook`.

Once you have Python installed and an editor ready, you're all set to start working through the examples.

---

## Beginner Level

The `beginner-level/` folder covers the fundamentals. These are the building blocks that everything else is built on.

| Example | What It Covers |
|---|---|
| **Hello World** | `print()`, basic script structure |
| **Name Input Program** | `input()`, string concatenation |
| **Simple Calculator** | User input, `if/elif/else`, arithmetic, division by zero |
| **Even or Odd Checker** | Modulo operator `%`, conditionals |
| **Age Checker** | Chained conditionals, comparison operators, f-strings |
| **Loop Counters** | `for` loop, `while` loop, `range()`, patterns |
| **Multiplication Table** | `for` loop, string formatting, arithmetic in loops |
| **Temperature Converter** | Math formulas, float formatting, multiple conversions |
| **Unit Converters** | Constants, functions, miles/km, cm/inches |
| **Arrays and Lists** | Lists, iteration, basic data structures |
| **Functions** | Defining and calling functions, return values |
| **Match/Case** | Python 3.10+ structural pattern matching |
| **Mini Games** | Loops, random numbers, user interaction |
| **Spreadsheet to SQLite to PDF** | File I/O, databases, PDF generation |

If you're completely new to Python, start with **Hello World** and work your way down. Each example introduces one or two new concepts, so by the time you reach the spreadsheet example at the bottom, you'll have covered a solid range of fundamentals.

---

## Intermediate Level

The `intermediate-level/` folder builds on the basics and introduces more practical patterns you'll encounter in real projects.

| Example | What It Covers |
|---|---|
| **Function-Based Calculator** | Functions, return values, dict-based dispatch |
| **Word Count Analyzer** | String methods, dictionaries, sorting |
| **Palindrome Checker** | String slicing, reversal, input cleaning |
| **Fibonacci Sequence Generator** | Loops, sequences, list indexing |
| **Number Base Converter** | `bin()`, `hex()`, `int()` with base, validation |
| **Caesar Cipher Encoder/Decoder** | `ord()`/`chr()`, modular arithmetic |
| **Simple File Search Tool** | `os.walk()`, directory traversal, file filtering |
| **To-Do List (with file saving)** | JSON file I/O, persistent data, CRUD operations |
| **Basic Text Adventure Game** | Game state, dictionaries as data, input parsing |
| **Email Slicer** | `split()`, `rsplit()`, input validation |

This is where things start to get interesting. The **Caesar Cipher** is a great exercise in understanding how characters are represented as numbers. The **To-Do List** teaches you how to persist data across sessions using JSON — a pattern you'll use constantly in real applications. And the **Text Adventure Game** is just plain fun while teaching you about managing state with dictionaries.

---

## Advanced Level

The `advanced-level/` folder covers algorithms, data structures, networking, concurrency, and backtracking. These are the kinds of problems that come up in technical interviews and real-world engineering.

| Example | What It Covers |
|---|---|
| **Recursive Merge Sort** | Divide and conquer, recursion, merging sorted halves |
| **Quick Sort Algorithm** | Partitioning, pivot selection, in-place sorting |
| **Depth-First Search (DFS)** | Graph traversal, stacks, recursion |
| **Breadth-First Search (BFS)** | Queues, shortest path, level-order |
| **Bubble Sort Algorithm** | Nested loops, swapping, early exit optimisation |
| **Hash Table Implementation** | Hashing, collision chaining, auto-resize |
| **Binary Tree Traversal** | BST, in/pre/post-order, level-order |
| **REST API Client** | HTTP requests, JSON parsing, error handling |
| **Multithreaded Downloader** | Threading, concurrent I/O, performance comparison |
| **Sudoku Solver (Backtracking)** | Backtracking, constraint satisfaction, recursion |

If you want to understand how things work under the hood, this is the section for you. The **sorting algorithms** (Merge Sort, Quick Sort, Bubble Sort) teach you to think about efficiency and trade-offs. The **graph traversals** (DFS and BFS) are foundational for everything from route planning to dependency resolution. The **REST API Client** shows you how to interact with external services — a skill you'll use in almost every modern application. And the **Sudoku Solver** is a brilliant example of backtracking, where you build a solution incrementally and undo choices that lead to dead ends.

---

## Getting Started

Setting up the project is straightforward:

1. **Clone the repository:**

```bash
git clone https://github.com/paulomenon/python-simple-example.git
cd python-simple-example
```

2. **(Optional) Create a virtual environment:**

```bash
python -m venv venv
source venv/bin/activate  # On Windows use venv\Scripts\activate
```

3. **Navigate into any example folder and run it:**

```bash
cd beginner-level/hello-world-sample
python hello_world.py
```

Each folder has its own README with instructions and expected output, so you always know what to expect before running anything.

---

## Running the Tests

The repository includes a test runner that automatically discovers and runs all the scripts. This is useful for verifying everything works in your environment, and it's also a good example of how automated testing works in practice.

```bash
python run_tests.py basic          # beginner-level
python run_tests.py intermediate   # intermediate-level
python run_tests.py advanced       # advanced-level
python run_tests.py all            # everything
```

Add `-v` for verbose output if you want to see each script's full output:

```bash
python run_tests.py all -v
```

If a script needs user input, it reads from a matching `.input` file automatically — so you don't need to type anything manually when running the tests.

---

## My Advice for Learning

If there's one thing I've learned from teaching and mentoring engineers over the years, it's that **reading code is not the same as writing code**. You can read a hundred tutorials and still feel lost when you open a blank file. The only way to get comfortable is to actually write code, break things, fix them, and repeat.

Here's what I'd suggest:

- **Start small** — Don't jump straight to the advanced section. Build your confidence with the beginner examples first.
- **Type the code yourself** — Don't just copy and paste. Typing it out forces your brain to process every line.
- **Break things on purpose** — Change a variable, remove a line, pass the wrong type. Understanding *why* something breaks teaches you more than getting it right the first time.
- **Build something of your own** — Once you've worked through a few examples, try building something small from scratch. A tip calculator, a password generator, a quiz game — anything that interests you.

And remember — if you're struggling, go back to the fundamentals. Read my posts on [problem solving](/problem-solving/) and [getting started with programming](/get-started-programming/). The mindset matters just as much as the syntax.

---

## Contributing

The repository is open source and contributions are welcome. If you have an idea for a new example or an improvement to an existing one, feel free to open a pull request on GitHub.

<i class="fab fa-github"></i> **[github.com/paulomenon/python-simple-example](https://github.com/paulomenon/python-simple-example)**

Happy coding!
