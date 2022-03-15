[[C code]]

Continue
![[Pasted image 20220130123029.png]]
Inside the `for` loop, we see an `if` statement checking if the current counter, `i`, is an even number by using the `%` operator. If `i` is even, `continue` to the next iteration and _skip_ the print statement below. If `i` is odd, print `i` and continue as normal.

**Note:** These keywords can still affect a loop even if they’re contained inside an `if` statement. This means a `continue` will always advance to the next iteration even if it’s nested in multiple `if / else` statements! This goes for other loop keywords as well, like `break`. If there are nested loops, a keyword will only interact with the most interior loop it is contained in.

Break
![[Pasted image 20220130123258.png]]
The keyword `break` allows us to, quite literally, “break” out of a loop and stop it from running any more times.

It can often simply be avoided with careful planning of the conditional controlling a loop. It’s generally advised to be careful with breaking out of loops because it can result in unexpected processing when a programmer has a mental plan centered around a loop finishing all its iterations.

However, when used effectively, a `break` can increase the efficiency of a program and help minimize its memory uses through unnecessary variables.

**Note:** `break` is most often used when a program wants to run a loop infinitely in a controlled manner. For example, a program that runs until the user types “quit.” In that instance, the program may run forever, but will only break out of its running loop when the user tells it.