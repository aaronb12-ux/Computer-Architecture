## Synchronous Sequential Circuits

To avoid circuits with **cyclic (feedback) paths**, we can break these paths by inserting **registers** somewhere in the feedback loop. This transforms the design into a combination of:

- **Combinational logic**
- **Registers**

The registers store the **state of the system**, and this state changes **only on clock edges**. Because state changes occur only at clock edges, we say the state is **synchronized to the clock**.

Using registers in every feedback path leads to the formal definition of a **synchronous sequential circuit**.

---

## Definition

A **sequential circuit** has a finite set of discrete states:

\[
\{ S_0, S_1, S_2, \dots, S_{k-1} \}
\]

A **synchronous sequential circuit** has a clock input whose **rising edges** define the moments when **state transitions occur**.

At any time, the circuit has:
- a **current state**
- a **next state**, which becomes the current state on the next rising edge of the clock

---

## Rules of Synchronous Sequential Circuits

1. Every circuit element is either a **register** or **combinational logic**.
2. At least **one element must be a register**.
3. All registers receive the **same clock signal**.
4. **Every cyclic path contains at least one register**.

Sequential circuits that do **not** satisfy these rules are called **asynchronous sequential circuits**.

---

## Flip-Flop as a Synchronous Sequential Circuit

A **flip-flop** is the simplest synchronous sequential circuit.

It has:
- one data input **D**
- one clock input **CLK**
- one output **Q**
- two states: `{0, 1}`

The functional specification of a D flip-flop is:
- **Next state** = `D`
- **Output Q** = current state

![Flip-Flop State Diagram](https://github.com/user-attachments/assets/dd450972-0802-4b89-ba99-078e2eb4300a)

- **Q** represents the **current state**.
- **D** is the input that determines the **next state**.
- **Q(n + 1)** is fed back to **D** and becomes the new state on the next rising clock edge.
