[[42]] [[Minitalk]]

github simple 1: https://github.com/hanshazairi/42-minitalk

github simple 2: https://github.com/Liudok/Minitalk-42

github Hajar: https://github.com/0xdeadabed/minitalk

signaux UNIX 1: https://www.linuxtricks.fr/wiki/signaux-unix-unix-signals

<<<<<<< HEAD
signaux UNIX 2: https://www.clicours.com/exemples-de-gestion-des-signaux-sous-unix/
=======
signaux UNIX 2: https://fr.wikipedia.org/wiki/Signal_(informatique)

<<<<<<< HEAD
>>>>>>> origin/master
=======
explication du code binaire chez Angelo:

![[minitalk_code_binaire1.png]](../../pictures/minitalk_code_binaire1.png)

![[minitalk_code_binaire2.png]](../../pictures/minitalk_code_binaire2.png)

## "client.c"

![[minitalk_client_c.png]](../../pictures/minitalk_client_c.png)

```js
SIGUSER1 = 1
```

```js
SIGUSER2 = 0
```

```js
int	main(int argc, char **argv)
{
	int	pid;
	int	i;

	i = 0;
	pid = ft_atoi(argv[1]);     //as the "arg" is of type "char **" we need to transform the characters input in the terminal to integer for signal transmition
	if (argc != 3 || pid == 0)  //if less than 3 arguments input in the terminal (it should be "$ ./client xxxx salut) then error
	{
		ft_printf("\033[0;31mInvalid arguments! \033[0m\n");
		exit(EXIT_FAILURE);
	}
	while (argv[2][i])          // arg[2] is the third argument in the terminal which means it the characters string we input (e.g. "salut") and [i] to go through it with incrementation of "i"
		convert_char(argv[2][i++], pid);    //apply ft_atoi() to each character of arg[2] (i.e. "salut")
	exit (EXIT_SUCCESS);
}
```

```js
void	convert_char(char c, int pid)
{
	int	i;

	i = 7;          //because we are dealing with char which are 8 bits long (0 to 7)
	while (i >= 0)
	{
		if (c >> i & 1)     //this will take the binary value of "c" in ASCII and then deplace it to its right "i" times, then it compares the bit in position nb 0 of this new "c" binary value with "1" in binary, if both are "1" then it returns "1" if not it returns "0"
			kill(pid, SIGUSR1);     //kill() sends signal "SIGUSR1" to process "pid"
		else
			kill(pid, SIGUSR2);     //kill() sends signal "SIGUSR2" to process "pid"
		usleep(100);
		i--;
	}
}
```
example with command;
```js
$ ./client 1234 salut
```
first loop with "s" from "salut" :

![[minitalk_client1.png]](../../pictures/minitalk_client1.png)
the client sends "SIGUSR2" which is equal to 0 to the server
then another loop is done after a pause (usleep(100)) for the next bit of character "s"
in the end the client is sending [0 1 1 1 0 0 1 1] to the server after 8th iteration which codes for "s"
same is done for the next character (i.e. "a")

## "serveur.c"

![[minitalk_server_c.png]](../../pictures/minitalk_server_c.png)

```js
int	main(void)
{
	pid_t	pid;                    //declaration of "pid" variable of type "pid_t" (i.e. "int")

	pid = getpid();                 //getpid() returns the process ID of the current process
	ft_printf("PID: %d\n", pid);
	signal(SIGUSR1, convert_msg);   //signal() sets the disposition of hte signum "SIGUSR1" which is a default action terminating the user-defined signal 1, to the handler (here function "convert_msg")
	signal(SIGUSR2, convert_msg);   //signal() sets the disposition of hte signum "SIGUSR2" which is a default action terminating the user-defined signal 2, to the handler (here function "convert_msg")
	while (1)                       // this "while" allows the process to pause
		pause();
}
```

```js
void	convert_msg(int signum)
{
	static int	power;              //static as value of power must not be initialized at the end of the call to function ""convert_msg"
	static int	byte;               //static as value of byte must not be initialized at the end of the call to function ""convert_msg"

	if (signum == SIGUSR1)
		byte += 1 << (7 - power);
	power++;
	if (power == 8)
	{
		ft_printf("%c", byte);
		if (byte == '\0')
			exit (EXIT_SUCCESS);
		power = 0;
		byte = 0;
	}
}
```
>>>>>>> 30200c887ac93ee5c5fc3a025bd12b0a006f458c

