## Summary: Latches, Flip-Flops, and Registers

**Latches and flip-flops** are the fundamental building blocks of **sequential circuits**.

- A **D latch** is **level-sensitive**: when **CLK = 1**, the latch is *transparent*, allowing the input **D** to propagate directly to the output **Q**.
- A **D flip-flop** is **edge-triggered**: it copies **D** to **Q** only on the **rising edge of the clock**.

At all other times, both latches and flip-flops **retain their previous state**.

A **register** is a collection of **D flip-flops** that share a common **CLK** signal, allowing multiple bits of data to be stored and updated simultaneously.
