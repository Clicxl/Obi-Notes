#hardware #coding
Digital system design is the process of talking to the hardware using logic and gates to obtain desired output.

##### Boolean Functions 
$$f(A,B,C) = Y$$

- Where A, B, C are inputs given to the logic gates and Y is the output received. 
- Canonical Forms are just simplest standard ways of writing any expression or function.
1. `Minterm Canonical Form` (Sum of Product, m): Its a function where at given integer position is 1
2. `Maxterm Canonical Form` (Product of sum, m): Its a function where at given integer position is 0
### Notes
- If a bit is in between 5V or 0V there a 2 ways to resolve it (they are called buffers):
  1. Transistor Transistor Logic Buffer (TTL): `0 - 2.2 V => 0` ; `2.2 - 3.6V => dont care state` ; `3.7 - 5V => 1`
  2. Schmitt Trigger Buffer (ST) : `0-3.3V => 0` ; `3.4 - 5V => 1`
- 