# Delayed Motor Start – RSLogix 500 (TON Timer)

This PLC project uses a TON (On-Delay Timer) instruction to delay the motor start by 5 seconds after the Start button is pressed. The logic prevents motor activation unless the timer completes, offering simple delay functionality used in real-world systems.

## 🧠 How it works:
- `I:1/0`: Start Button (NO)
- `I:1/1`: Stop Button (NC)
- `T4:0`: TON timer with 5-second preset
- `O:2/0`: Motor output

## 🔧 Ladder Logic States:

### 📸 Resting State
> This is the initial state of the logic. The Start button is unpressed, the timer is disabled, and the motor is OFF.

### 📸 Start Button Pressed – Timer Counting
> The Start button (`I:1/0`) is pressed and the Stop button is not, enabling the TON instruction. The timer begins counting to 5 seconds, with the `TT` (Timer Timing) bit active.

### 📸 Start Button Still Pressed – Timer Done
> Once the timer reaches its preset value, the `DN` (Done) bit turns ON, energizing the motor (`O:2/0`).

### 📸 Stop Button Pressed – Reset
> Pressing the Stop button (`I:1/1`) resets the timer by breaking the enabling condition. The `DN` bit turns OFF, and the motor is de-energized.
