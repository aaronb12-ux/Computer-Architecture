## Traffic Light Controller Using a Finite State Machine

### Problem Description

Consider the problem of designing a controller for a traffic light at a busy campus intersection.

Engineering students frequently cross **Academic Ave.** while football players cross **Bravado Blvd.** Both groups are often distracted, and several serious injuries have already occurred at the intersection. To prevent further accidents, the Dean of Students asks Ben Bitdiddle to install a traffic light controller.

Ben decides to solve the problem using a **finite state machine (FSM)**.

---

### System Inputs and Outputs

Ben installs:
- Two traffic sensors:
  - **TA** on Academic Ave.
  - **TB** on Bravado Blvd.  
  Each sensor is **TRUE (1)** when traffic is present and **FALSE (0)** otherwise.

- Two traffic lights:
  - **LA** controlling Academic Ave.
  - **LB** controlling Bravado Blvd.  
  Each light can be **Green (G)**, **Yellow (Y)**, or **Red (R)**.

The FSM therefore has:
- **Inputs:** TA, TB
- **Outputs:** LA, LB
- A **clock** with a 5-second period
- A **reset** input to place the system into a known initial state

On each rising edge of the clock, the traffic lights may change based on the sensor inputs.

---

### Intersection Layout

![Intersection Drawing](https://github.com/user-attachments/assets/ee868b4e-9fa5-42fe-bf69-47f33b12259f)

This is a four-way intersection:
- **Academic Ave.** runs West–East
- **Bravado Blvd.** runs North–South

Each street has two lights and one traffic sensor.

---

## State Diagram

![State Diagram](https://github.com/user-attachments/assets/97d603fe-6297-47bd-a35c-5bf883016c6c)

The FSM begins in **state S0**, which is also the **reset state**.

### State Descriptions

- **S0:**  
  - LA = Green  
  - LB = Red  
  This state is used when there is traffic on Academic Ave (**TA = 1**).

Only one street is allowed to have a green light at any time. One of **LA** or **LB** must always be red to prevent collisions.

---

### Transitions

From **S0**:
- If **TA = 0** (no traffic on Academic Ave), transition to **S1**
- If **TA = 1**, remain in or transition to the state where Academic Ave stays green

**S1** is an intermediate state:
- LA turns **Yellow**
- LB remains **Red**

This state exists to ensure a proper yellow-light transition before changing directions.

On the next clock edge from **S1**, the FSM transitions **unconditionally** to **S2**:
- LA = Red
- LB = Green

The same pattern applies symmetrically:
- **S2 → S3 → S0**
- **S3** serves as the yellow-light transition before returning control to Academic Ave

Whenever **RESET** is asserted, the FSM transitions immediately to **S0**.

---

## State Transition Table

The state transition table has three columns:
1. **Current State**
2. **Inputs (TA, TB)**
3. **Next State**

It is interpreted as follows:

- In **state S0**, if **TA = 0**, transition to **S1**  
  (TB is irrelevant in this state)
- In **state S0**, if **TA = 1**, remain in or transition to the Academic-Ave-green state
- Similar logic applies to all other states

The complete transition table is shown in the figure above.

---

## State Encoding

Since we have 4 states, we need encodings of 2 bits because 2^n = 4 where n = 2 (number of bits).  
The general equation is 2^n ≥ number of states, and we choose the smallest value of n that satisfies this condition.

### Encoding Tables

**States:**
- S0: 00
- S1: 01
- S2: 10
- S3: 11

**Outputs:**
- Green: 00
- Yellow: 01
- Red: 10

Using these encodings, we rewrite the state transition table:

![Encoded Transition Table](https://github.com/user-attachments/assets/96bb9edc-0e52-4fbf-b312-838ff174fd49)

---

## Next-State Logic

From the encoded transition table, we derive the next-state equations using the sum-of-products method:

S'1 = ~S1S0 + S1~S0TB + S1~S0~TB  
→ ~S1S0 + S1~S0(TB + ~TB)  
→ ~S1S0 + S1~S0  
→ S1 XOR S0

S'0 = ~S1~S0~TA + S1~S0~TB

---

## Output Logic

![Output Table](https://github.com/user-attachments/assets/965d3824-2377-4b6c-9817-abe67d00e99b)

From the output table, we derive the following equations:

LA1 = S1~S0 + S1S0 → S1(~S0 + S0) → S1  
LA0 = ~S1S0  

LB1 = ~S1~S0 + ~S1S0 → ~S1  
LB0 = S1S0

---

## Circuit Implementation

Using the derived next-state and output equations, we construct the final circuit implementation.

<img width="967" height="484" alt="trafficlightcontroller" src="https://github.com/user-attachments/assets/836819d0-4927-4a53-8017-8b1a94ba36d2" />

---

## Questions

> **Why do we put S'0 and S'1 into the input ports of the D flip-flops?**

**Answer:**

- The outputs of the flip-flops represent the **current state**: `S0` and `S1`
- These outputs are fed into the AND gates, where combined with inputs `TA` and `TB`, they calculate the **next state**: `S'0` and `S'1`
- On each rising clock edge, those next state values get sampled and become the new `Q` outputs — which are now the new current state
- That new current state then feeds back into the logic to calculate the *next* next state, and so on

It's essentially a constant feedback loop:
```
Current State (S0, S1) → combinational logic (AND gates + TA, TB) → Next State (S'0, S'1) → D inputs → [clock edge] → back to Current State
```

---

## Summary

This FSM:
- Responds to traffic demand using sensors
- Ensures safe transitions using yellow-light states
- Synchronizes all behavior to a 5-second clock
- Prevents conflicting green lights at all times
- Can be reset to a known safe state

This design demonstrates how **finite state machines provide a structured and safe way to implement real-world control systems**.
