[[Minitalk]]

## - write

    NAME

       write - write to a file descriptor

    SYNOPSIS
       #include <unistd.h>

       ssize_t write(int fd, const void *buf, size_t count);

    DESCRIPTION
       write() writes up to count bytes from the buffer starting at buf to the file referred to by the file descriptor fd.
    
    RETURN VALUE
        On success, the number of bytes written is returned.  On error, -1 is returned, and errno is set to indicate the error.

## signal handler

    a signal handler is a routine that can be specified or registered and which will be executed once a signal is sent from this process, if no signal handler are registered, the default signal handler is executed.

## - signal
    signal() : https://en.wikipedia.org/wiki/Signal_(IPC)
    C signal handling : https://en.wikipedia.org/wiki/C_signal_handling

    NAME
       signal - ANSI C signal handling
    
    SYNOPSIS
       #include <signal.h>

       typedef void (*sighandler_t)(int);

       sighandler_t signal(int signum, sighandler_t handler);

    DESCRIPTION
        WARNING: the behavior of signal() varies across UNIX versions, and has also varied historically across different versions of Linux.  Avoid its use: use sigaction(2) instead.  See Portability below.

       signal() sets the disposition of the signal signum to handler, which is either SIG_IGN, SIG_DFL, or the address of a programmer- defined function (a "signal handler").
       
       If the signal signum is delivered to the process, then one of the following happens:

       *  If the disposition is set to SIG_IGN, then the signal is ignored.

       *  If the disposition is set to SIG_DFL, then the default action associated with the signal (see signal(7)) occurs.

       *  If the disposition is set to a function, then first either the disposition is reset to SIG_DFL, or the signal is blocked (see Portability below), and then handler is called with argument signum.  If invocation of the handler caused the signal to be blocked, then the signal is unblocked upon return from the handler.
       
       The signals SIGKILL and SIGSTOP cannot be caught or ignored.

    RETURN VALUE
        signal() returns the previous value of the signal handler.
        On failure, it returns SIG_ERR, and errno is set to indicate the error.

## - sigemptyset

    NAME
       sigemptyset — initialize and empty a signal set

    SYNOPSIS
       #include <signal.h>

       int sigemptyset(sigset_t *set);

    DESCRIPTION
       The sigemptyset() function initializes the signal set pointed to by set, such that all signals defined in POSIX.1‐2008 are excluded.

    RETURN VALUE
       Upon successful completion, sigemptyset() shall return 0; otherwise, it shall return -1 and set errno to indicate the error.

## - sigaddset

    Synopsis
        
        #include <signal.h>

        int sigemptyset(sigset_t *set);

        int sigfillset(sigset_t *set);

        int sigaddset(sigset_t *set, int signum);

        int sigdelset(sigset_t *set, int signum);

        int sigismember(const sigset_t *set, int signum);

    Description
        These functions allow the manipulation of POSIX signal sets.

        sigemptyset() initializes the signal set given by set to empty, with all signals excluded from the set.

        sigfillset() initializes set to full, including all signals.

        sigaddset() and sigdelset() add and delete respectively signal signum from set.

        sigismember() tests whether signum is a member of set.

        Objects of type sigset_t must be initialized by a call to either sigemptyset() or sigfillset() before being passed to the functions sigaddset(), sigdelset() and sigismember() or the additional glibc functions described below (sigisemptyset(), sigandset(), and sigorset()). The results are undefined if this is not done.

    Return Value
        sigemptyset(), sigfillset(), sigaddset(), and sigdelset() return 0 on success and -1 on error.

        sigismember() returns 1 if signum is a member of set, 0 if signum is not a member, and -1 on error.

## - sigaction

    NAME
       sigaction, rt_sigaction - examine and change a signal action

    SYNOPSIS
       #include <signal.h>

       int sigaction(int signum, const struct sigaction *restrict act, struct sigaction *restrict oldact);

    DESCRIPTION
       The sigaction() system call is used to change the action taken by a process on receipt of a specific signal.

       signum specifies the signal and can be any valid signal except SIGKILL and SIGSTOP.

       If act is non-NULL, the new action for signal signum is installed from act.  If oldact is non-NULL, the previous action is saved in oldact.

       The sigaction structure is defined as something like:

           struct sigaction {
               void     (*sa_handler)(int);
               void     (*sa_sigaction)(int, siginfo_t *, void *);
               sigset_t   sa_mask;
               int        sa_flags;
               void     (*sa_restorer)(void);
            };

    RETURN VALUE
       sigaction() returns 0 on success; on error, -1 is returned, and errno is set to indicate the error.

## - kill

    Name
        kill - send signal to a process

    Synopsis
        #include <sys/types.h>
        #include <signal.h>

        int kill(pid_t pid, int sig);

    Description
        The kill() system call can be used to send any signal to any process group or process.
        If pid is positive, then signal sig is sent to the process with the ID specified by pid.
        If pid equals 0, then sig is sent to every process in the process group of the calling process.
        If pid equals -1, then sig is sent to every process for which the calling process has permission to send signals, except for process 1 (init), but see below.
        If pid is less than -1, then sig is sent to every process in the process group whose ID is -pid.
        If sig is 0, then no signal is sent, but error checking is still performed; this can be used to check for the existence of a process ID or process group ID.
        
        For a process to have permission to send a signal it must either be privileged (under Linux: have the CAP_KILL capability), or the real or effective user ID of the sending process must equal the real or saved set-user-ID of the target process. In the case of SIGCONT it suffices when the sending and receiving processes belong to the same session.

    Return Value
        On success (at least one signal was sent), zero is returned. On error, -1 is returned, and errno is set appropriately.

## - getpid

    Name
        getpid, getppid - get process identification

    Synopsis
        #include <sys/types.h>
        #include <unistd.h>
        
        pid_t getpid(void);
        pid_t getppid(void);

    Description
        getpid() returns the process ID of the calling process. (This is often used by routines that generate unique temporary filenames.)
        getppid() returns the process ID of the parent of the calling process.

    Errors
        These functions are always successful.

## pid_t getpid()

    The pid_t data type represents process IDs. You can get the process ID of a process by calling getpid. The function getppid returns the process ID of the parent of the current process (this is also known as the parent process ID). Your program should include the header files `unistd.h' and `sys/types.h' to use these functions.

    Data Type: pid_t
    The pid_t data type is a signed integer type which is capable of representing a process ID. In the GNU library, this is an int.

    Function: pid_t getpid (void)
    The getpid function returns the process ID of the current process.

    Function: pid_t getppid (void)
    The getppid function returns the process ID of the parent of the current process.

## -  malloc
    Name
        malloc, free, calloc, realloc - allocate and free dynamic memory

    Synopsis
        #include <stdlib.h>

    void *malloc(size_t size);
    void free(void *ptr);
    void *calloc(size_t nmemb, size_t size);
    void *realloc(void *ptr, size_t size);

    Description
        The malloc() function allocates size bytes and returns a pointer to the allocated memory. The memory is not initialized. If size is 0, then malloc() returns either NULL, or a unique pointer value that can later be successfully passed to free().

        The free() function frees the memory space pointed to by ptr, which must have been returned by a previous call to malloc(), calloc() or realloc(). Otherwise, or if free(ptr) has already been called before, undefined behavior occurs. If ptr is NULL, no operation is performed.

        The calloc() function allocates memory for an array of nmemb elements of size bytes each and returns a pointer to the allocated memory. The memory is set to zero. If nmemb or size is 0, then calloc() returns either NULL, or a unique pointer value that can later be successfully passed to free().

        The realloc() function changes the size of the memory block pointed to by ptr to size bytes. The contents will be unchanged in the range from the start of the region up to the minimum of the old and new sizes. If the new size is larger than the old size, the added memory will not be initialized. If ptr is NULL, then the call is equivalent to malloc(size), for all values of size; if size is equal to zero, and ptr is not NULL, then the call is equivalent to free(ptr). Unless ptr is NULL, it must have been returned by an earlier call to malloc(), calloc() or realloc(). If the area pointed to was moved, a free(ptr) is done.

    Return Value
        The malloc() and calloc() functions return a pointer to the allocated memory that is suitably aligned for any kind of variable. On error, these functions return NULL. NULL may also be returned by a successful call to malloc() with a size of zero, or by a successful call to calloc() with nmemb or size equal to zero.

        The free() function returns no value.

        The realloc() function returns a pointer to the newly allocated memory, which is suitably aligned for any kind of variable and may be different from ptr, or NULL if the request fails. If size was equal to 0, either NULL or a pointer suitable to be passed to free() is returned. If realloc() fails the original block is left untouched; it is not freed or moved.

## - free

    Name
        free - Display amount of free and used memory in the system
    Synopsis
        free [-b | -k | -m] [-o] [-s delay ] [-t] [-l] [-V]

Description
    free displays the total amount of free and used physical and swap memory in the system, as well as the buffers used by the kernel. The shared memory column should be ignored; it is obsolete.

    Options
        The -b switch displays the amount of memory in bytes; the -k switch (set by default) displays it in kilobytes; the -m switch displays it in megabytes.
        The -t switch displays a line containing the totals.

        The -o switch disables the display of a "buffer adjusted" line. If the -o option is not specified, free subtracts buffer memory from the used memory and adds it to the free memory reported.

        The -s switch activates continuous polling delay seconds apart. You may actually specify any floating point number for delay, usleep(3) is used for microsecond resolution delay times.

        The -l switch shows detailed low and high memory statistics.

        The -V switch displays version information.

## - pause

    Name
        pause - wait for signal

    Synopsis
        #include <unistd.h>
        int pause(void);

    Description
        pause() causes the calling process (or thread) to sleep until a signal is delivered that either terminates the process or causes the invocation of a signal-catching function.

    Return Value
        pause() only returns when a signal was caught and the signal-catching function returned. In this case pause() returns -1, and errno is set to EINTR.

## - sleep

    Name
        sleep - sleep for the specified number of seconds

    Synopsis
        #include <unistd.h>
        unsigned int sleep(unsigned int seconds);

    Description
        sleep() makes the calling thread sleep until seconds seconds have elapsed or a signal arrives which is not ignored.

    Return Value
        Zero if the requested time has elapsed, or the number of seconds left to sleep, if the call was interrupted by a signal handler.

## - usleep

    Name
        usleep - suspend execution for microsecond intervals
    
    Synopsis
        #include <unistd.h>

        int usleep(useconds_t usec);

    Description
        The usleep() function suspends execution of the calling thread for (at least) usec microseconds. The sleep may be lengthened slightly by any system activity or by the time spent processing the call or by the granularity of system timers.

    Return Value
        0 on success, -1 on error.

## - exit

    Name
        exit - cause normal process termination

    Synopsis
        #include <stdlib.h>
        void exit(int status);

    Description
        The exit() function causes normal process termination and the value of status & 0377 is returned to the parent (see wait(2)).
        All functions registered with atexit(3) and on_exit(3) are called, in the reverse order of their registration. (It is possible for one of these functions to use atexit(3) or on_exit(3) to register an additional function to be executed during exit processing; the new registration is added to the front of the list of functions that remain to be called.) If one of these functions does not return (e.g., it calls _exit(2), or kills itself with a signal), then none of the remaining functions is called, and further exit processing (in particular, flushing of stdio(3) streams) is abandoned. If a function has been registered multiple times using atexit(3) or on_exit(3), then it is called as many times as it was registered.

        All open stdio(3) streams are flushed and closed. Files created by tmpfile(3) are removed.

        The C standard specifies two constants, EXIT_SUCCESS and EXIT_FAILURE, that may be passed to exit() to indicate successful or unsuccessful termination, respectively.

    Return Value
        The exit() function does not return.

