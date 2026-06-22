# 3-Bit Arithmetic Logic Unit (ALU)
**Course:** Logic Design Portfolio Project

A custom 3-bit Signed-Magnitude ALU built from basic digital logic gates. This processor handles arithmetic, comparison, and bitwise manipulation, outputting to a dynamic magnitude display and real-time status flags.

## How to Run:
1. Download and open **Logisim-Evolution**.
2. Go to `File -> Open` and select your `.circ` file.

## Control Logic Matrix:

| Control Bits | Operation | Active Hardware Output |
| :---: | :--- | :--- |
| `000` | **Addition** | Flagged Sign, Flagged Overflow, Displayed Magnitude |
| `001` | **Subtraction** | Flagged Sign, Flagged Overflow, Displayed Magnitude |
| `010` | **Multiplication** | Flagged Sign, Displayed Magnitude |
| `011` | **Comparison** | Magnitude Output Decoder (`1`, `2`, or `4`) |
| `100` | **1's Complement** | Flagged Sign, Displayed Magnitude |

## Features:
* **Inputs:** 3-bit Signed-Magnitude operands ($A$ and $B$).
* **Output Display:** Seven-segment/Hexadecimal magnitude result.
* **Sign Flag (LED):** Real-time hardware flag where **ON** = Negative and **OFF** = Positive.
* **Overflow Flag (LED):** Real-time arithmetic hardware flag where **ON** = Overflow detected and **OFF** = Safe.

## Operation & Result Breakdown:

### Arithmetic & Logic:
* **Addition / Subtraction:** Full mathematical range tracking with dedicated overflow logic and sign evaluation.
* **Multiplication:** Computes the magnitude product and evaluates the resulting sign bit ($Sign_A \oplus Sign_B$).
* **1's Complement:** Performs a bitwise inversion on the targeted input magnitude.

### Comparison Logic Matrix:
When the control bits are set to `011`, the ALU switches to a comparator mode and outputs a specific numeric code to the magnitude display:
* **$InputA > InputB$** $\rightarrow$ Outputs **`1`**
* **$InputA = InputB$** $\rightarrow$ Outputs **`2`**
* **$InputA < InputB$** $\rightarrow$ Outputs **`4`**
