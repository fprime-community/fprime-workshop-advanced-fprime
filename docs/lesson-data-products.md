# Lesson: Data Products

## Introduction

This lesson introduces **data products** as a mechanism for generating, storing, and downlinking structured mission data in F Prime. Unlike telemetry and events, data products are designed for mission data that is accumulated over time and delivered asynchronously for post-processing.

In this module, you will extend an existing component to generate data products, manage container lifecycle, and verify correct behavior through unit tests. You can then explore decoding these products on the ground.

---

## Learning Goals

By completing this lesson, you will learn how to:

- Model data product records and containers in FPP
- Allocate and manage data product containers safely
- Serialize records into containers correctly
- Handle allocation failure deterministically
- Verify data product behavior using unit tests
- Reason about how data products are processed by the system and interpreted on the ground

---

## Exercise

Given this [BMP 280](https://github.com/fprime-community/fprime-sensors/tree/devel/fprime-sensors/Bmp280/Components/BmpManager) component, you should construct an "Application Layer" component that queries data from the BMP component and packages that data as data product(s).

1. Include the [F Prime Sensors](https://github.com/fprime-community/fprime-sensors) library!
2. Build a component to read BMP 280 data:
    1. Allocate a container
    2. Package data as a record
    3. Serialize record
    4. Send out container
    5. Repeat
3. Instantiate the component and the relevant subtopologies.  Wire together
4. Downlink the data products
5. Decode and process on ground!


## Hints

- Data product containers have explicit ownership and lifecycle; once sent, they must not be reused.
- Record IDs are serialized into the container and must match the ground dictionary.
- Container size must account for both record data and record ID overhead.
- Allocation failure is expected behavior and should not destabilize the component.
- Unit tests are the primary way to verify correct producer behavior.

---

## Optional Goals

If you have additional time, consider extending your solution to:

- Add a second record type to the same container
- Adjust container priority dynamically
- Add a second producer component using shared data product services
- Explore how different container sizes affect memory usage and data loss on reset

---

## References

- [How-To: Generate Data Products](https://fprime.jpl.nasa.gov/devel/docs/how-to/data-products)
- [User Guide: Data Products](https://fprime.jpl.nasa.gov/latest/docs/user-manual/framework/data-products/)
- [DataProducts Producer Example](https://github.com/nasa/fprime-examples/tree/devel/FlightExamples/DataProduct/Producer)
- [FPP User’s Guide](https://nasa.github.io/fpp/fpp-users-guide.html)
