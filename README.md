
# Primality Testing Engineering Lab

[![build](../../actions/workflows/build.yml/badge.svg)](../../actions/)
![Platforms: Linux, MacOS, Windows](https://img.shields.io/badge/Platform-Linux%20%7C%20MacOS%20%7C%20Windows-blue.svg)
[![Language: Python](https://img.shields.io/badge/Language-Python-blue.svg)](https://www.python.org/)
[![Code Style: Black](https://img.shields.io/badge/Code%20Style-Black-blue.svg)](https://github.com/psf/black)
[![Commits: Conventional](https://img.shields.io/badge/Commits-Conventional-blue.svg)](https://www.conventionalcommits.org/en/v1.0.0/)
[![Discord](https://img.shields.io/discord/872320492936257537?logo=discord)](https://discord.gg/kjah8MFYbR)

## Introduction

In this lab, you will implement a CLI that uses one of two algorithms
to determine if a number is prime. A profiler will be used to
empirically test the time efficiency of the algorithms.

This lab is an Engineering Lab. As described in the syllabus:

**Engineering Labs** are graded, i.e. assigned a number or percentage
indicative of the proportion of points earned relative to the total possible.

- Fifty percent of the grade of each Engineering Lab is determined by
  the percentage of gatorgrade checks passed.
- One quarter of the grade is determined by code correctness following a rubric.
- One quarter of the grade is determined by professional skills and presentation
  following a rubric. Professional presentation is impacted by linting,
  formatting, testing, profiling, duplication avoidance, commenting, markdown
  styling and communication in reflections.

## Learning Objectives

This assignment is about remembering and understanding
programming language constructs by running programs,
observing output, and describing steps.
The learning objectives of this assignment are to:

1. Use Git and GitHub to manage source code file changes
2. Study type annotation in function declarations, floating point
arithmetic, and modulus operations
3. Use profiler for empirical assessment of algorithms.
4. Write clearly about the programming concepts in this assignment.

## Quick Links

- Due date: Check Discord or the
  [Course Materials Schedule](https://github.com/allegheny-college-cmpsc-101-fall-2024/course-materials/blob/main/Schedule.md)
- Policy on
  [Tokens](https://github.com/allegheny-college-cmpsc-101-fall-2024/course-materials#tokens)
- [Token Form for Automatic Extension](https://forms.gle/y9Mz55hQKr84wzvXA)
- Policy for
  [Assignment Evaluation](https://github.com/allegheny-college-cmpsc-101-fall-2024/course-materials#assignment-evaluation)
- Policy for [Assignment Submission](https://github.com/allegheny-college-cmpsc-101-fall-2024/course-materials#assignment-submission).
- [#data-structures Discord channel](https://discord.com/channels/877320365825749002/1274744318124359732)
- [Starter repo](https://github.com/allegheny-college-cmpsc-101-fall-2024/prime-testing-starter)

## Policy Reminders

Students are reminded to uphold the Honor Code. Cloning this assignment
repository is a commitment to the latter.

For this assignment, you may use class materials, the textbook, notes,
and the internet, including AI, for reference and learning. AI may **not** be
used to generate answers that you submit. All code and writing that are turned
in **must be your own work and your own words**. Copying or otherwise
representing ChatGTP or other AI outputs as your own work or your own words is
not permitted.

Please ask questions freely in Lab, on the #data-structures Discord channel,
TL office hours, instructor office hours, or by opening a GitHub Issue with
@emgraber tagged at least 24 hours before the deadline.

Modifications to the gatorgrade.yml file are not permitted without explicit
instruction.

## Project Details ([Project Overview](#project-overview) Below)

### Project Goals

This assignment invites you to implement a program that features multiple
algorithms for performing primality testing. You will implement two algorithms
that conduct a search to determine whether or not the number input to the
program is prime. The exhaustive search algorithm will examine all possible
elements of a search space while, in contrast, the efficient one will use extra
conditional logic to restrict the search space. In addition to adding source
code the provided Python files, you will conduct an experiment to determine
which algorithm is the fastest and estimate by how much it is faster. As you
enhance your [technical
skills](/proactive-skills/introduction-proactive-skills/) and explore the
experimental evaluation of algorithms, you will continue to program with tools
such as VS Code and a terminal window and the Python programming language and
the Poetry package manager.

### Project Access

If you are a student enrolled in a Computer Science class at Allegheny College,
you can access this assignment by clicking the link provided to you in Discord.
Once you click this link it will create a GitHub repository that you can clone
to your computer by following the general-purpose instructions in the
description of the [technical
skills](/proactive-skills/introduction-proactive-skills/). Specifically, you
will need to use the `git clone` command to download the project from GitHub to
your computer. Now you are ready to add source code and documentation to the
project!

### Expected Output

This project invites you to implement a number squaring program called
`primality`. The program accepts as input a number, like `49979687`, a
description of an approach (that can either be `efficient` or `exhaustive`), and
a boolean flag to indicate whether or not the program should profile its
execution. When `primality` is run in `exhaustive` mode it checks all integer
values in `range(2, number)` if `number` is the integer value subject to
primality testing. After you finish the correct implementation of all the
program's features, running it with the command `poetry run primality --number
49979687 --approach efficient --profile` will produce output like the following:

```shell
😄 Attempting to determine if 49979687 is a prime number!

✨ What divisors were found? 1, 49979687
✨ Was this a prime number? Yes

🔬 Here's profiling data from performing primality testing on 49979687!

  _     ._   __/__   _ _  _  _ _/_   Recorded: 22:10:56  Samples:  1
 /_//_/// /_\ / //_// / //_'/ //     Duration: 0.870     CPU time: 0.869
/   _/                      v4.0.3

Program: primality --number 49979687 --approach efficient --profile

0.870 primality  primality/main.py:93
└─ 0.870 primality_test_efficient  primality/main.py:77
```

Did you notice that this program produces profiling data about how long it took
to run the `primality` program in `efficient` mode with the input `49979687`?
This is because of the fact that it uses the
[Pyinstrument](https://github.com/joerick/pyinstrument) program to collect
execution traces and efficiency information about the program. For this run of
the program, it took about `0.870` seconds to determine that `49979687` was a
prime number. Is that fast or not? Well, let's run the `primality` program in
`exhaustive` mode and measure by how much it is slower! Specifically, running
the command `poetry run primality --number 49979687 --approach exhaustive
--profile` produces the following output:

```shell
😄 Attempting to determine if 49979687 is a prime number!

✨ What divisors were found? 1, 49979687
✨ Was this a prime number? Yes

🔬 Here's profiling data from performing primality testing on 49979687!

  _     ._   __/__   _ _  _  _ _/_   Recorded: 22:34:38  Samples:  1
 /_//_/// /_\ / //_// / //_'/ //     Duration: 1.739     CPU time: 1.738
/   _/                      v4.0.3

Program: primality --number 49979687 --approach exhaustive --profile

1.738 primality  primality/main.py:93
└─ 1.738 primality_test_exhaustive  primality/main.py:57
```

If `exhaustive` mode of `primality` takes `1.738` and `efficient` mode only
takes `0.870`, how much faster is `efficient` mode compared to `exhaustive`? If
$T_f$ denotes the execution time of `efficient` mode and $T_x$ denotes the
execution time of `exhausitve` mode, then the following equation defines
$T_{\Delta}$, or the percentage change in the execution time when running
`primality` in `efficient` mode instead of `exhaustive`.

$$
T_{\Delta} = \frac{T_x - T_f}{T_x} \times 100
$$

Using this equation with the timing values of $T_x = 1.738$ and $T_f = 0.87$
from Pyinstrument shows that `efficient` mode is $(1.738
- 0.87) / 1.738 * 100 = 49.9427$ percent faster than `exhaustive` mode. When you
check the source code in the GitHub repository for this project you will see
why! Unlike `exhaustive` mode, the `efficient` mode of `primality` does not
check for even divisors of `number` bigger than two, instead only determining
if `number` is divisible by any odd number in `range(3, x, 2)`. In retrospect,
it makes sense that `efficient` is about $50$ percent faster than
`exhaustive` because, by not checking the even numbers, it does not do half
of `exhaustive`'s work.

It is worth noting that you do not have to run `primality` in the `profile` mode
that uses Pyinstrument. For instance, running the program with `poetry run
primality --number 49979687 --approach exhaustive` would run the program in
`exhaustive` mode and perform the same computation without collecting the
performance data. You can display `primality`'s help menu and learn more about
the features it should support by typing `poetry run primality --help` to
display the following:

```shell
Usage: primality [OPTIONS]

  Use iteration to perform primality testing on a number.

Options:
  --number INTEGER                [default: 5]
  --profile / --no-profile        [default: False]
  --approach [exhaustive|efficient]
                                  [default: efficient]
  --install-completion            Install completion for the current
                                  shell.

  --show-completion               Show completion for the current shell,
                                  to copy it or customize the
                                  installation.

  --help                          Show this message and exit.
```

Please note that the provided source code does not contain all of the
functionality to produce the output displayed in this section. As explain in the
next section, you are invited to add the features needed to ensure that
`primality` produces the expected output!

Don't forget that if you want to run the `primality` program you must use
your terminal window to first go into the GitHub repository containing this
project and then go into the `primality` directory that contains the
project's source code. Finally, remember that before running the program you
must run `poetry install` to add its dependencies, such as Pyinstrument,
Pytest, and Rich.

### Adding Functionality

If you study the file `primality/primality/main.py` you will see that it has
many `TODO` markers that designate the parts of the program that you need to
implement before `primality` will produce correct output. If you run the
provided test suite with the command `poetry run task test` you will see that it
produces a message suggesting that there is a syntax error in the program. Along
with creating instances of the `Typer` and `Profiler` classes, you will need to
resolve all of the syntax errors so that you can run `primality` and its test
suite. You must also implement all of these functions:

- `def human_readable_boolean(answer: bool) -> str`
- `def pretty_print_list(values: Iterable[int]) -> str`
- `def primality_test_exhaustive(x: int) -> Tuple[bool, List[int]]`
- `def primality_test_efficient(x: int) -> Tuple[bool, List[int]]`

The following source code illustrates how to use Pyinstrument to collect the
timing information for the execution of the `efficient` approach for primality
testing, as implemented in the function `primality_test_efficient`. First, line
`1` creates an empty `primality_tuple` and lines `2` and `3` confirm that the
person using the program requested to profile the execution of the `efficient`
approach. Using Pyinstrument, line `4` starts the profiler and line `6` stops
it, with line `5` making the call to the `primality_test_efficient` function.
When the person running `primality` did not use `--profile`, then line `8` calls
`primality_test_efficient` without using Pyinstrument.

```python linenums="1"
primality_tuple: Tuple[bool, List[int]]
if approach.value == PrimalityTestingApproach.efficient:
    if profile:
        profiler.start()
        primality_tuple = primality_test_efficient(number)
        profiler.stop()
    else:
        primality_tuple = primality_test_efficient(number)
```

## Running Checks

### Helper Tasks

Helper tasks are run in the terminal with the poetry environment activated.
The format of the commands are always `poetry run task xyz`...where `xyz`
is the helper task name.

If you study the source code in the `pyproject.toml` file you will see that it
includes the following section that specifies different executable "helper
task" names like `ruff`, `fix`, `ruffdetails`, etc.

```toml
[tool.taskipy.tasks]
```

If you are in the `square` directory that contains the
`pyproject.toml` file, the helper tasks
make it easy to run commands like `poetry run task ruff` to automatically run
the ruff linter designed to check the Python source code in your program
to confirm that your source code adheres to industry standards for formatting.
You can also use the command `poetry run task fix` to automatically reformat the
source code. `poetry run task ruffdetails` will print out detailed linting errors
that point to exactly what ruff views as a linting error. Make sure to examine
the `pyproject.toml` file for other convenient tasks that you can use to both
check and improve your project!

### Gatorgrade

The command `gatorgrade --config config/gatorgrade.yml` will check your work. If
your work meets the baseline requirements and adheres to the best practices that
proactive programmers adopt you will see that all the checks pass when you run
`gatorgrade`. Try to pass as many checks as you can. Missing some checks will only
impact a part of your grade in this Engineering Lab. Note, modifications to the
gatorgrade.yml file are not permitted without explicit instruction.

### Pytest

```shell
collected 7 items

tests/test_primality.py .......
```

## Project Reflection

Once you have finished both of the previous technical tasks, you can use a text
editor to answer all of the questions in the `writing/reflection.md` file. For
instance, you should provide the output of the Python program in a fenced code
block, explain the meaning of the Python source code segments that you
implemented, and answer all of the other questions about your experiences in
completing this project. A specific goal of the reflection for this project is
to evaluate the efficiency of the two different modes (i.e., `exhaustive` and
`efficient`) of the `primality` program.

## Project Assessment

Since this project is an engineering lab, it is aligned with the
**evaluating** and **creating** levels of [Bloom's
taxonomy](/proactive-learning/blooms-taxonomy/). You can learn more about how a
proactive programming expert will assess your work by examining the [assessment
strategy](/proactive-learning/assessment-strategy/). From the start to the end
of this project you may make an unlimited number of reattempts at submitting
source code and technical writing that meet all aspects of the project's
specification.

## Seeking Assistance

Please review the course expectations on the syllabus about
[Seeking Assistance](https://github.com/allegheny-college-cmpsc-101-spring-2024/course-materials#seeking-assistance).
Students are reminded to uphold the Honor Code. Cloning the assignment
repository is a commitment to the latter.

For this assignment, you may use class materials, textbooks, notes, and the
internet. Ensure that your writing is original and based on your own understanding
of the concepts. Examples of plagiarism include:

- verbatim copying without citation
- copying with single word modifications
- paraphrasing sections or notes from a source without citation

To claim that work is your own, it is essential to craft the logic and the
writing together without copying or using the logical structure of another
source. The honor code holds everyone to this standard.

## Project Overview

Accept the GitHub Classroom Assignment. Then clone the repo following these
step:

- In GitHub, copy the SSH link to your repo from the green `code` button
- Open a terminal
- `cd` to a location where you would like to store the project repo
- type `git clone` then paste in the link
- hit enter, type in passphrase if prompted.

After cloning this repository to your computer, please take the following
steps:

- Use the `cd` command to change into the directory for this repository.
- Specifically, you can change into the program directory by typing `cd primality`.
- Install the dependencies for the project by typing `poetry install`.
- Run the program in its two different modes by typing:
  - `poetry run primality --number 49979687 --approach efficient`
  - `poetry run primality --number 49979687 --approach efficient --profile`
  - Please note that the program will not work unless you add the required
    source code at the designated `TODO` markers.
- Confirm that the program is producing the expected output described
  [above](#expected-output)
- Run the automated grading checks by typing
  `gatorgrade --config config/gatorgrade.yml`.
- You may also review the output from running GatorGrader in GitHub Actions.
- Don't forget to provide all of the required responses to the technical writing
  prompts in the `writing/reflection.md` file.
- Please make sure that you completely delete the `TODO` markers and their
  labels from all of the provided source code.
- Please make sure that you also completely delete the `TODO` markers and their
  labels from every line of the `writing/reflection.md` file.

Submit work to GitHub using git:

- Open a terminal
- `cd` to the project directory on your computer
- type `git status` to see a list of files you have updated
- type `git add .` to "stage" your files
- type `git commit -m "WRITE YOUR OWN MESSAGE"` to commit your files
- type `git push origin main` to submit your files
- type your ssh passphrase if requested
