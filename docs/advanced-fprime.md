## Prerequisites

This is an **advanced workshop**, intended for developers who are already comfortable with the fundamentals of F´. Before attending, you should have:

* A working knowledge of the F´ modeling language (**FPP**) and how it maps to component implementations.
* Experience building and extending **components** and integrating them into **topologies**.
* Completed the [LED Blinker tutorial](https://github.com/fprime-community/fprime-workshop-led-blinker/blob/devel/docs/led-blinker.md) **without needing to copy/paste**, and understood the purpose of each step.
* Familiarity with **C++** as used to implement flight components.

Most importantly, you should be confident working through standard F´ development tasks on your own. If you are still learning the basics, we recommend finishing the introductory workshop before continuing here.

## Workshop Format

This workshop is organized as a series of **hands-on exercises**, each focused on teaching an advanced design pattern or capability in F´.

> [!IMPORTANT]
> This workshop is typically delivered **in person**, where hardware is provided to all attendees.
> If you are following along remotely, please refer to the [hardware list](hardware-list.md) for guidance on what you’ll need to supply yourself. **Remote** users can still complete all exercises on their own hardware.

* You are encouraged to **self-select** which exercises you want to complete.
* All necessary **hardware is provided** during in-person sessions.
* **Instructors are available** throughout to answer questions, provide hints, or help debug issues.
* If you have questions after the workshop or while working on your own, you can post them on the [F´ GitHub Discussions page](https://github.com/nasa/fprime/discussions).
* Each exercise links to the **relevant documentation** so you can dive deeper into the concepts at your own pace.

> [!TIP]
> Teams may choose to tackle multiple lessons in parallel. This can be an efficient way to explore different patterns quickly and share knowledge within your group.

## Tips for Success

This is an **advanced workshop**, and you may find parts of it challenging—that’s by design. Here are some tips to help you get the most out of the experience:

1. **Ask Questions**
   Don’t hesitate to reach out if you get stuck. Instructors and the community are here to support you. No question is too small.

2. **Team Up**
   Software is developed by teams, not individuals. Pair up, share tasks, and learn from each other as you work through the exercises.

3. **Follow the Process**
   Treat each exercise like a real project:

   * Write requirements (even simple ones)
   * Design proper components and document them
   * Implement carefully
   * Test thoroughly

4. **Embrace the Challenge**
   These lessons push beyond the basics. Don’t worry if things don’t work the first time—that’s part of the learning process.

5. **Iterate and Refactor**
   Start with a minimal design, get it working, and then improve it. Iteration mirrors how F´ projects evolve in practice.

6. **Keep Notes**
   Document what you tried, what worked, and what didn’t. These notes will help you later and may be useful to your teammates.

> [!TIP]
> Many of the best insights come from mistakes. Treat every failure as feedback, not a setback.

## Project Setup

In this workshop, we will build on the **LED Blinker** project you created in the [introductory workshop](https://github.com/fprime-community/fprime-workshop-led-blinker/blob/devel/docs/led-blinker.md).
To start, fetch your existing implementation into your chosen workspace using the [`fprime-bootstrap`](https://github.com/fprime-community/fprime-bootstrap) tool:

```bash
fprime-bootstrap clone <path-to-your-LedBlinker>
```

This sets up your environment with the `LedBlinker` component as a starting point.
Throughout this workshop, you’ll extend and enhance this implementation with more advanced F´ concepts.

> [!IMPORTANT]
> Remember to source the virtual environemnt `. fprime-venv/bin/activate` before running commands in this tutorial.

Next, generate and build the cloned project to make sure the base is working correctly:

```bash
cd fprime-workshop-led-blinker
. fprime-venv/bin/activate
fprime-util generate
fprime-util build
```

If the build completes without errors, you are ready to begin.

> [!TIP]
> If you want a clean base to work from—or if you don’t have your own solution handy—you can clone our reference implementation instead:
>
> ```bash
> fprime-bootstrap clone https://github.com/fprime-community/fprime-workshop-led-blinker
> cd fprime-workshop-led-blinker
> . fprime-venv/bin/activate
> fprime-util generate
> fprime-util build
> ```
>
> This gives you a known-good starting point that matches the original tutorial.

## Lessons

This workshop is organized as a set of lessons. Each lesson introduces an advanced F´ pattern or concept, with exercises and optional extensions.

* [Lesson: F Prime Communication Interface (Radios)](./lesson-communications.md)
* [Lesson: Modeling State Machines in FPP (Sensors)](./lesson-fpp-state-machines.md)
