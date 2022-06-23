[[C code]]

We need to use 3 different macros;

How to define the variadic function;

```js
type function_name(type required_argument, ...)
```


e.g.

```js
void print_function(int num, ...)
```


We first define a va_list type variable;
`va_list` e.g. "args", this is basically a list of elements

We need to use 3 different macros;
`va_start` takes two arguments: the `va_list` variable and the name of the last parameter before the argument list in the funcion (e.g. "num"), this indicate to start after the last parameter in the function
`va_arg` takes two arguments:
- the `va_list` variable and to pull off the arguments one by one in the order they are listed
- the type of argument (only self promoting types i.e. "int" "double" "pointer" are ok but not "char" "short" " float")
`va_end` is required to end the process, it takes the `va_list` variable as an argument

![[Pasted image 20220222140949.png]]

![[Pasted image 20220222141636.png]]

![[Pasted image 20220222142304.png]]

![[Pasted image 20220222142146.png]]

If too many arguments entered then the extra ones will be ignored
![[Pasted image 20220222142712.png]]
If too few arguments entered then we got garbage
![[Pasted image 20220222142447.png]] ![[Pasted image 20220222142608.png]]

![[stdarg1.jpg]]

![[stdarg2.jpg]]



