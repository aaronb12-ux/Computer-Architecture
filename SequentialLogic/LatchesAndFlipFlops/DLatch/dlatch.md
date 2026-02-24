# D Latch

The D latch helps with the design of circuits where the questions of **what** and **when** should be separated. It has two inputs:

- **D (Data):** Controls what the next state should be.
- **CLK (Clock):** Controls when the state should change.

<img width="373" height="77" alt="dlatch" src="https://github.com/user-attachments/assets/be5f5fa5-5018-4e9c-8c95-f1ae4931ca2e" />

## How It Works

- If **CLK = 0** → S = R = 0 regardless of D
- If **CLK = 1** → depending on the value of D, one of S or R will be 1

Once S and R are determined, we can use the SR latch truth table to find **Q** and **~Q**.

- When **CLK = 0**, Q remembers its old value **Q_prev**
- When **CLK = 1**, Q = D

The D latch avoids the invalid case of asserting both S and R simultaneously.

## Latch vs. Flip-Flop

A **flip-flop** is edge-triggered — it is a bistable element whose state changes in response to a clock edge (e.g., when the clock rises from 0 to 1). Bistable elements without an edge-triggered clock are called **latches**.

## Summary

The clock determines **when** data flows through:

- When **CLK = 1**, the latch is **transparent** — data flows through to Q as if the latch were just a buffer.
- When **CLK = 0**, the latch is **opaque** — it blocks new data from flowing through, and Q retains its old value.
