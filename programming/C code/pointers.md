[[C code]]

https://www.youtube.com/watch?v=zuegQmMdy8M&t=520s

Sections 1 & 2

![[pointers1.png]](../pictures/pointers1.png)

![[pointers2.png]](../pictures/pointers2.png)

![[pointers3.png]](../pictures/pointers3.png)

![[pointers4.png]](../pictures/pointers4.png)

![[Pasted image 20211210155056.png]]

![[Pasted image 20211210155215.png]]

![[Pasted image 20211210162021.png]]

![[Pasted image 20211210162117.png]]

![[Pasted image 20211210162231.png]]

![[Pasted image 20211210162449.png]]
![[Pasted image 20211210162515.png]]

![[Pasted image 20211210162616.png]]
![[Pasted image 20211210162718.png]]

![[Pasted image 20211210162957.png]]
![[Pasted image 20211210163031.png]]


![[Pasted image 20211210163225.png]]

Section 3

![[Pasted image 20211212132851.png]]

![[Pasted image 20211212133212.png]]

when typecasting from int to char, only the last bytes is kept, thouhg value = 1 and not 1025
![[Pasted image 20211212133729.png]]

![[Pasted image 20211212133953.png]]
![[Pasted image 20211212133905.png]]

when typcasting from int to void, no need to use "(void *)" 
![[Pasted image 20211212134709.png]]
not possible to dereference a void pointer (e.g. "p0") using "*p0" as a void pointer in not referenced to any particular data type, this would give an error message at compilation
![[Pasted image 20211212134905.png]]
![[Pasted image 20211212135029.png]]
only the address of the void pointer can be accessed, not the value, and not even the arithmetic on the address trying to point to the next address "p0+1"
![[Pasted image 20211212135540.png]]
![[Pasted image 20211212135613.png]]
![[Pasted image 20211212135343.png]]

Section 4 - Pointer to Pointer

pointers are strongly typed because we do not only use them to get the addresse of a variable but also to deference the value of the variable at this address, hence the need for the same type between the pointer and the variable value at the address it points to
![[Pasted image 20211212141011.png]]

pointer to pointer to pointer
![[Pasted image 20211212141641.png]]

![[Pasted image 20211212144534.png]]
![[Pasted image 20211212142512.png]]

![[Pasted image 20211212144955.png]]