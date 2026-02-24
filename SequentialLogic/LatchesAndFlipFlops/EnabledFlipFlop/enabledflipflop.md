## Enabled Flip-Flop

An **enabled flip-flop** adds an extra control input called **EN** (or **ENABLE**) that determines whether new data is loaded on the active clock edge.

- When **EN = 1 (TRUE)**, the enabled flip-flop behaves like a normal **D flip-flop**: the value at **D** is loaded on the clock edge.
- When **EN = 0 (FALSE)**, the flip-flop **ignores the clock edge** and **retains its current state**.

Enabled flip-flops are useful when we want to load a new value **only some of the time**, rather than on every clock edge.

### Enabled Flip-Flop Implementations

![Enabled Flip-Flop Diagram](https://github.com/user-attachments/assets/6f94f3e1-7e4c-4b01-a058-d60f025dbd2e)

**Figure A** shows how to build an enabled flip-flop using a **D flip-flop and a multiplexer**.  
- When **EN = 1**, the multiplexer selects the input **D**, allowing new data to be loaded.
- When **EN = 0**, the multiplexer feeds back the current output **Q**, recycling the old state and preventing any change.

**Figure B** shows an implementation using **clock gating**.  
- When **EN = 1**, the clock signal is allowed to toggle normally, and the flip-flop updates as usual.
- When **EN = 0**, the clock is held inactive, so the flip-flop retains its previous value.

> **Note:** In real designs, clock gating must be implemented carefully to avoid glitches and timing issues.
