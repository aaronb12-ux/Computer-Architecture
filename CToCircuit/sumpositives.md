# Finite State Machines (FSM) and Datapaths

## C Code
```c
int sum_positives(int nums[]) {
    int total = 0, i = 0;
    while (nums[i] > 0) {
        total += nums[i];
        ++i;
    }
    return total;
}
```

## Circuit Diagram

<img width="714" height="711" alt="Screenshot 2026-02-23 at 10 59 51 PM" src="https://github.com/user-attachments/assets/dfd08d31-bf71-4ff5-876d-27591d675fd8" />

## Datapath Definition

**Input Pins:**
- **Start:** Indicates when we are ready to begin executing the logic in the function.
- **Num:** The current number being passed in.
- **CLK:** The clock signal.

**Output Pins:**
- **Ready:** Represents that the function is ready to be called.
- **Total:** The accumulated sum tracked throughout the program.

## Register

Since this program uses the variable `total`, we need a register to store its value.

For the register's **D (Data)** port, the value is either **0** or **num + total**:

- It is **0** when we are beginning computation — only on the initial call before entering the while loop.
- Otherwise, we continuously update `total` by connecting `total` and `num` to an adder.

We only write to D when:
- `beginComputation == 1` (we are starting the program), **or**
- We are inside the while loop and the current number is greater than 0.

The number updates each clock cycle, and each clock cycle we check whether we should enable a write to D.

