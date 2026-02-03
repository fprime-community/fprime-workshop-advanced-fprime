# Lesson: Running on small platforms

In this exercise, you'll cross-compile your F´ deployment to run on a **Raspberry Pi Pico 2** with **Zephyr RTOS**. This involves learning how to configure F´ for embedded platforms, diagnose and debug issues on target hardware, and work with Zephyr RTOS.

The goal is to create an F´ deployment and get it running on constrained hardware, which includes understanding the integration and configuration steps required for embedded targets, and optimizing the deployment and configuration to fit the constraints of the target hardware.

> [!CAUTION]
> Zephyr, Zephyr Modules, F Prime, and F Prime libraries consist of a large number of files. This can overwhelm the Raspberry PI 5 provided for the class when running in an indexing IDE. Excluding file watching and C++ intellisense on Zephyr files can offer a speed improvement.
> 
> **Excluding Zephyr Workspace From Build (VsCode)**
>
> Add the following to the VsCode `setting.json` file:
> 
> ```json
> {
>     "files.watcherExclude": {
>         "**/zephyr-workspace/**": true,
>     },
>     "C_Cpp.files.exclude": {
>         "**/zephyr-workspace/**": true,
>     }
> }
> ```

---

## Learning Points

By completing this lesson, you will gain experience in:

1. Using existing F´ platform packages (e.g. `fprime-zephyr`)
2. Cross-compiling F´ for embedded targets
3. Tuning F´ configuration for embedded targets
4. Debugging on embedded hardware
5. Understanding platform-specific constraints (memory and flash size)

---

## Exercise

You should do the following:

1. **Create Project and Add Zephyr**
   * Set up a new F´ project; or use your existing deployment
   * Add the F´ Zephyr support package as a library: https://github.com/fprime-community/fprime-zephyr
   * Explore the F´ Zephyr support package and understand what it provides
   * Install the Zephyr SDK and set up a Zephyr workspace under `lib/zephyr-workspace`

2. **Attempt Cross-Compile**
   * Attempt to build the deployment for Zephyr
   * Identify and resolve any compilation errors (see [Hints](#hints))

3. **Run Onboard and Debug**
   * Flash the compiled binary to your Raspberry Pi Pico 2
   * Boot the system and observe behavior (logs, debugging, etc.)
   * Troubleshoot issues (see [Hints](#hints))


---

## Hints

* **Compilation troubleshooting**: Some components are platform-specific. `fprime-bootstrap` uses the Linux implementations by default. Attempting to compile Linux-specific code for Zephyr will result in errors, so those components will need to be switched to their Zephyr equivalents.
* **Consider Your Components**: `fprime-bootstrap` and `fprime-util new --deployment` ship with a fairly broad number of standard F Prime components. Which do you actually need to prove F Prime on the Pico 2?
* **Tailoring the Project configuration**: The entire system can be further configured to optimize for your constraints, by updating the project configuration. Areas to look at include: subtopology configurations (`fprime/Svc/Subtopologies/`), project configuration (`fprime/default/config/`)
> [!TIP]
> This is done by creating a project configuration module (typically `<project>/project/config`) where configuration overrides are kept.
* **Tailoring the Deployment**: The "stock" F´ deployment likely has too large of a memory footprint to run on a Raspberry Pi Pico 2. `TlmChan` and `CmdDispatcher` are two components known to have a large memory footprint. Identify whether they can be swapped OR configured to fit in your constraints. Some subtopologies may also not be required for a minimal working deployment.
* **Cross Compile With Zephyr**: use the optional positional argument to `fprime-util` to cross compile with Zephyr
```
fprime-util generate zephyr
fprime-util build zephyr
```


---

## Relevant Resources and Documentation

- **[F´ Zephyr Support Package](https://github.com/fprime-community/fprime-zephyr)**
- **[F´ Docs: Configuring F Prime](https://fprime.jpl.nasa.gov/latest/docs/user-manual/framework/configuring-fprime/)**
- **[F´ Docs: Working with (and configuring) Subtopologies](https://fprime.jpl.nasa.gov/devel/docs/user-manual/design-patterns/subtopologies/)**
- **[Zephyr RTOS Documentation](https://docs.zephyrproject.org/)**

## Optional Goals

* **Device Drivers**: Implement Zephyr-specific device drivers and/or device managers for Raspberry Pi Pico 2 peripherals. For example, try to blink an LED.
* **Add More Subsystems:** Add some larger subsystems that you may have removed from the initial baseline.

## Reference Implementation

Students are highly encouraged to go through the lesson on their own without using the reference implementation, to maximize the learning experience. Should you get stuck, the reference implementation for this lesson is available here: https://github.com/fprime-community/fprime-zephyr-reference  


