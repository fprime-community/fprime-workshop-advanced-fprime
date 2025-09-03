
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

