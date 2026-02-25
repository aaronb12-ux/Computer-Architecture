## Finite State Machines (FSMs)

Synchronous sequential circuits can be represented using the following structure:

![Finite State Machine Diagram](https://github.com/user-attachments/assets/7aa0fb8f-08b8-497b-aae4-f5f2327e3c2b)

These circuits are called **finite state machines (FSMs)**.

A circuit with **k state bits** can be in a finite number of unique states—specifically **2^k** possible states.  
An FSM has:
- **M inputs**
- **N outputs**
- **k bits of state**
- a **clock input**
- an optional **reset** signal

---

## FSM Structure

An FSM consists of:
- **Next-state combinational logic**
- **Output combinational logic**
- A **register** that stores the current state

On each rising edge of the clock, the FSM:
1. Computes the **next state** based on the **current state** and **inputs**
2. Updates the state register with this next state

---

## FSM Models

### Moore Machine
- Outputs depend **only on the current state**

### Mealy Machine
- Outputs depend on the **current state and current inputs**

---

Finite state machines provide a **systematic method** for designing synchronous sequential circuits from a functional specification.
