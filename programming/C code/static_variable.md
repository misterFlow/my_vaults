[[C code]] [[42]]

https://www.codesdope.com/discussion/what-is-the-difference-between-static-int-and-int/#:~:text=static%20int%20is%20a%20variable,of%20the%20program%20once%20initialized.

int is a datatype for a variable storing integer values. static int is a variable storing integer values which is declared static.

If we declare a variable as static, it exists till the end of the program once initialized. For example, if we declare an int variable in a function, then that variable is a local variable for that function which gets destroyed as the function ends. But if we declare an int variable in a function also as static, then that variable will not get destroyed as the function ends and will not get destroyed until the program ends.

Let’s see two examples to understand it clearly;
```js
#include <stdio.h>
 
 void func(){
 	int i = 0;
 	i++;
 	printf("i = %d\n",i);
 }
int main(){
	func();	
	func();
	func();
	func();
	return 0;
}
```
Here, the int variable i is declared inside the function func() and thus is a local variable for that function. Every time the function gets called, i gets initialized, its value gets incremented to 1 and gets destroyed when the function ends.

Now lets see the same example with static int;
```js
#include <stdio.h>
 
 void func(){
 	static int i = 0;
 	i++;
 	printf("i = %d\n",i);
 }
int main(){
	func();	
	func();
	func();
	func();
	return 0;
}
```

On declaring the int variable as static, the variable did not get destroyed when the function ended. When the function was called the first time, the value of i became 1, second time it got incremented to 2 and so on.