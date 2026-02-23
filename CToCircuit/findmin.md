# Converting C-Code to Hardware

## C Code

```c
int main(int nums[]) {
    int cur_min = nums[0];
    while (!stop) {
        if (nums[i] < cur_min) {
            cur_min = nums[i];
        }
    }
    return cur_min;
}
```

*(Note: original code contains syntax errors, shown here for reference)*

---

## Circuit Diagram

![C to Circuit Diagram](https://github.com/user-attachments/assets/d82f5481-c085-476c-94a8-04c6c6153d56)

---

> [!IMPORTANT]
> Important: In the above diagram, 'Clk' gate should be attached to the R port in the register.

## Datapath Definition

### Input Pins

| Pin     | Description                                  |
|---------|----------------------------------------------|
| `Start` | Determines if the program should begin       |
| `Stop`  | Determines whether the program should stop   |
| `Num`   | The current number being processed           |
| `Clk`   | The clock signal                             |

### Output Pins

| Pin        | Description                          |
|------------|--------------------------------------|
| `ReadyOut` | Signals that the circuit is ready    |
| `Min`      | The minimum value found in the array |

---

## Register

Since the C program uses variables, we need a **register**:

- **Output** → `Min` (the current minimum value)
- **Input** → `Num` (the value being stored, mirroring the C variable)

---

## Register Update Conditions

The register updates under **one of two conditions** (connected via an OR gate):

1. **Initialization** — When `Ready` AND `Start` are both active
   - Maps to the line `int cur_min = nums[0]`
   - `Start` = the function was called
   - `Ready` = the circuit is ready to begin

2. **Loop Update** — When inside the loop and `Num < Min`
   - Maps to the `if (nums[i] < cur_min)` check

## Finite State Machine Diagram

![FSM Diagram](https://github.com/user-attachments/assets/effc9a05-4748-4656-8af3-3833ba42ffd5)

---

## FSM States & Transitions

### State 1: `Ready`
The function has been called and the circuit is ready to begin.

| Condition  | Action                          |
|------------|---------------------------------|
| `Start = 0` | Stay in `Ready` state          |
| `Start = 1` | Transition to `InLoop` state   |

### State 2: `InLoop`
The circuit is actively processing the array.

| Condition  | Action                          |
|------------|---------------------------------|
| `Stop = 0` | Stay in `InLoop` state         |
| `Stop = 1` | Transition back to `Ready` state |
