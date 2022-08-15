[[42]]

# Makefile

![[Makefile.png]](../pictures/Makefile.png)

From https://www.youtube.com/watch?v=-riHEHGP2DU&t=2234s

without Makefile;
gcc <file1.c> <file2.c> <file3.c>
./a.out

Makefile will allow automation of commands and the compiler will only recompile the files that have been modified since last compilation

![[makefile1.png]]every target is dependent on dependencies which need to be validated in order to create the target
the command is the action to do from dependencies to create the target

![[makefile2.png]]
here the target to be created is the object file "main.o" from the dependency file "main.c" through the "gcc" command where we can list the output file "main.o" with "-o" and list the source file "main.c" with ".c" but also any flag needed "-W -Wall"

![[makefile3.png]]
in the same way, the executable file "prog" will be created upon the dependencies "main.o" and "player.o"

![[makefile4.png]]
now in the terminal the command "make" will have the system search for a Makefile and executer the commands listed in it

unlike the "gcc" command in the terminal that does not keep the object file, the "make" command creates and keep the ".o" files
first the system will try to create the executable "prog" file but will not succeed because neither "main.o" not "player.o" dependencies exist, once they are created the executable "prog" can and will be created

![[makefile5.png]]
it is common and recommended to create a target "all" with the dependency "prog" that will avoid errors due to commands' order, whatever the order of the other commands, the "all" target will create the executable in a safer way using "make all" in the terminal

![[makefile6.png]]
the "clean" target without dependencies will delete every ".o" files which are not needed when sharing the code and which can be heavy, this is call in the terminal with the command "make clean"

![[makefile7.png]]
finally the "mrproper" target (or "fclean") will also erase the executables files with "clean" as dependency via the terminal command "make mrproper" or "make fclean"

![[makefile8.png]]
to gain time not listing every object file as dependencies or other command written as static, we can use variables, those have a name which is commonly written in capital and equals a value

![[makefile9.png]]
we commonly use some set of variables names for different actions, to use a variable for the compiler we use "CC"  as the name of the variable which is equal to the name of the compiler, here "gcc"
then to call this variable we use the "$()" with the variable name in the parenthesis

![[makefile10.png]]
to set a variable for the executable files we use the name "EXEC"

![[makefile11.png]]
the sign "$@" is refering to the target where it is used, here "EXEC" which is "prog" in the end

the sign "$<" is refering to the first dependency

the sign "$^" is refering to the list of dependencies

the sign "$?" is refering to the list of dependencies which are more recent than the target

the sign $* is refering to the name of the file (output)

![[makefile13.png]]
instead of writing the target "main.o" and "player.o" we can use the "%" sign to make a rule for every ".o" target from every ".c" dependency
instead of writing this;
![[makefile14.png]]
we can write this;
![[makefile15.png]]
after having first declared the variables "OBJ" and "SRC" as below;
![[makefile16.png]]

we can also make it less long to write using wildcard;
![[makefile17.png]]
the "SRC" here will be any file with ".c" extension
the "OBJ" here will take any source "SRC" but changing its extension from ".c" to ".o"

we can now replace every ".o" file by the "OBJ" variable
![[makefile18.png]]

in this case, the terminal will not compile the Makefile because of orders problem, since the "player.c" file is used in other files such as "main.c" but when creating the "main.o" object the "player.o" is not yet created
to avoid that we need to use the special variables
![[makefile19.png]]
to create the ".o" files, we use "$@" to refer to the target and " $< " to refer to the first dependency ("main.c" for "main.o" and "player.c" for "player.o")

to create the executable file, we use the "$@" to refer to the target but here we use " $^ " to refer to the whole list of dependencies which are the objects list

![[makefile21.png]]
we can also use conditions with specific call, here "ifeq" test if  the variable "WINDOWS" is equal to "yes" and assign "prog.exe" to the "EXEC" variable or only "prog"

we can also use "ifdef" to test if a definition exists