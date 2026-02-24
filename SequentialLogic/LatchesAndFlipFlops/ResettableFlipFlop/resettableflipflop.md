## Resettable Flip-Flop

A **resettable flip-flop** adds an extra control input called **RESET** that forces the flip-flop into a known state.

- When **RESET is inactive**, the resettable flip-flop behaves like a normal **D flip-flop**.
- When **RESET is active**, the flip-flop **ignores input D** and forces the output **Q to 0**.

Resettable flip-flops are useful for initializing a system to a **known state** when power is first applied.

---

## Synchronous vs Asynchronous Reset

- **Synchronous reset**:  
  The flip-flop resets **only on the active clock edge**.

- **Asynchronous reset**:  
  The flip-flop resets **immediately when RESET becomes active**, independent of the clock.

---

## Resettable Flip-Flop Implementations

![Resettable Flip-Flop Diagram](https://github.com/user-attachments/assets/3604ead1-ff61-4d61-a50f-47aaac2564c0)

**Figure A** shows a **synchronously resettable, active-low reset** flip-flop implemented using a **D flip-flop and an AND gate**.

- When **RESET = 0 (active)**, the AND gate forces a `0` into the D input, so the flip-flop resets to `Q = 0` on the next rising edge of **CLK**.
- When **RESET = 1 (inactive)**, the AND gate passes the input **D**, and the flip-flop behaves normally.

> **Note:** RESET is an **active-low signal**, meaning it performs its function when RESET = 0.  
> Adding an inverter would convert it into an **active-high reset** signal.
