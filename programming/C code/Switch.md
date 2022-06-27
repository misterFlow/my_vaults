[[C code]]]

![[switch1.png]](../pictures/switch1.png)

The `switch` keyword initiates the statement and is followed by `()`, which contains the value that each case will compare. In the example, the value or expression of the switch statement is `grade`. One restriction on this expression is that it must evaluate to an integral type (`int`, `char`, `short`, `long`, `long long`, or `enum`).

Inside the block, `{}`, there are multiple cases. The `case` keyword checks if the expression matches the specified value that comes after it. The value following the first case is `9`. If the value of `grade` is equal to `9`, then the code that follows the `:` would run.

The `break` keyword tells the computer to exit the block and not execute any more code or check any other cases inside the code block.

At the end of each switch statement, there is a `default` statement. If none of the cases are `true`, then the code in the default statement will run. It’s essentially the `else` part. In the code above, suppose `grade` is equal to `10`, then the output would be “Sophomore”.

**Note:** Without the `break` keyword at the end of each case, the program would execute the code for the first matching case and _all_ subsequent cases, including the `default` code. This behavior is different from `if` / `else` conditional statements which execute only one block of code.