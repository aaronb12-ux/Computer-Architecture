# SR Latch

An SR latch has two inputs: **S** (set) and **R** (reset), and two outputs **Q** and **~Q**. Its state is controlled through the S and R inputs.

<img width="493" height="395" alt="srlatch" src="https://github.com/user-attachments/assets/14e3eb2e-ec68-43d2-b058-4a691ff4ac1b" />

## Truth Table

<img width="477" height="236" alt="truthtable" src="https://github.com/user-attachments/assets/f274dbe8-0ac1-4aa5-9ef5-7d27049782dd" />

## Special Case: S = R = 0

Case (IV) presents a special scenario where both S = R = 0. For NOR gates, the output is 0 when either input is 0. If both S and R are 0, we cannot determine Q without knowing **~Q** — but we don't know **~Q** either, leaving us stuck.

If we assume Q has some prior value **Q_prev**, we can test both 0 and 1. If Q_prev = 1, then ~Q = 0. Since Q and ~Q are always opposites, ~Q_prev = 0 in this case. This confirms that when S = R = 0:

- **Q = Q_prev**
- **~Q = ~Q_prev**

## Circuit Symbol

<img width="345" height="354" alt="symbol" src="https://github.com/user-attachments/assets/033c9a82-c07b-450a-95ce-d4193468e51d" />

## Summary

The SR latch is a **bistable element** with one bit of state stored in **Q**:

- When **R** is asserted (1), the state is **reset to 0**.
- When **S** is asserted (1), the state is **set to 1**.
- When **neither** is asserted, the state **retains its previous value**.

