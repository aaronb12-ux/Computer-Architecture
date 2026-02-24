# D Flip-Flop

A D flip-flop can be built from two back-to-back D latches controlled by complementary clocks — a **master** latch and a **slave** latch.

<img width="497" height="747" alt="Screenshot 2026-02-23 at 12 08 23 AM" src="https://github.com/user-attachments/assets/6b14900e-9563-4d15-9083-6193477291ea" />

## How It Works

When **CLK = 0**, the master latch is transparent and the slave is opaque. D flows through the master latch to **N1**, so N1 continuously tracks the value of D.

When **CLK = 1**, the master goes opaque, cutting off D from N1. N1 retains the value D had just before the clock rose. The slave then becomes transparent, allowing N1 to flow through to **Q**. Therefore, Q captures the value of D from just before the rising edge.

## Summary

The D flip-flop copies **D** to **Q** on the **rising edge of the clock**, and retains its state at all other times.

- The **rising clock edge** indicates *when* the state should be updated.
- The **D input** specifies *what* the new state will be.
