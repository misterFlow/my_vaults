[[C code]]

https://www.youtube.com/watch?v=zuegQmMdy8M&t=520s

Sections 1 & 2

![[pointers1.png]](../pictures/pointers1.png)

![[pointers2.png]](../pictures/pointers2.png)

![[pointers3.png]](../pictures/pointers3.png)

![[pointers4.png]](../pictures/pointers4.png)

![[pointers5.png]](../pictures/pointers5.png)

![[pointers6.png]](../pictures/pointers6.png)

![[pointers7.png]](../pictures/pointers7.png)

![[pointers8.png]](../pictures/pointers8.png)

![[pointers9.png]](../pictures/pointers9.png)

![[pointers10.png]](../pictures/pointers10.png)
![[pointers11.png]](../pictures/pointer11.png)

![[pointers12.png]](../pictures/pointers12.png)
![[pointers13.png]](../pictures/pointers13.png)

![[pointers14.png]](../pictures/pointers14.png)
![[pointers15.png]](../pictures/pointers15.png)


![[pointers16.png]](../pictures/pointers16.png)

Section 3

![[pointers17.png]](../pictures/pointers17.png)

![[pointers18.png]](../pictures/pointers18.png)

when typecasting from int to char, only the last bytes is kept, thouhg value = 1 and not 1025
![[pointers19.png]](../pictures/pointers19.png)

![[pointers20.png]](../pictures/pointers20.png)
![[pointers21.png]](../pictures/pointers21.png)

when typcasting from int to void, no need to use "(void *)" 
![[pointers22.png]](../pictures/pointer22.png)
not possible to dereference a void pointer (e.g. "p0") using "*p0" as a void pointer in not referenced to any particular data type, this would give an error message at compilation
![[pointers23.png]](../pictures/pointers23.png)
![[pointers24.png]](../pictures/pointers24.png)
only the address of the void pointer can be accessed, not the value, and not even the arithmetic on the address trying to point to the next address "p0+1"
![[pointers25.png]](../pictures/pointers25.png)
![[pointers26.png]](../pictures/pointers26.png)
![[pointers27.png]](../pictures/pointers27.png)

Section 4 - Pointer to Pointer

pointers are strongly typed because we do not only use them to get the addresse of a variable but also to deference the value of the variable at this address, hence the need for the same type between the pointer and the variable value at the address it points to
![[pointers28.png]](../pictures/pointers28.png)

pointer to pointer to pointer
![[pointers29.png]](../pictures/pointers29.png)

![[pointers30.png]](../pictures/pointers30.png)
![[pointers31.png]](../pictures/pointers31.png)

![[pointers32.png]](../pictures/pointers32.png)