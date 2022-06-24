[[42]] [[Pipex]]

explication: https://csnotes.medium.com/pipex-tutorial-42-project-4469f5dd5901

explication github Eddy42: https://github.com/widium/pipex

github (simple1) : https://codeberg.org/UncleReaton/pipex

github (simple2) : https://github.com/m3zh/pipex

github (simple3) : https://github.com/keulee/pipex

github (complex): https://github.com/tolmvad/pipex

youtube CodeVault: https://www.youtube.com/watch?v=6xbLgZpOBi8



## function fork()

NAME

       fork - create a child process

SYNOPSIS

       #include <unistd.h>
       pid_t fork(void);

DESCRIPTION

       fork() creates a new process by duplicating the calling process. The new process is referred to as the child process.  The calling process is referred to as the parent process.

       The child process and the parent process run in separate memory spaces.  At the time of fork() both memory spaces have the same content.  Memory writes, file mappings (mmap(2)), and unmappings (munmap(2)) performed by one of the processes do not affect the other.

RETURN VALUE

       On success, the PID of the child process is returned in the parent, and 0 is returned in the child.  On failure, -1 is returned in the parent, no child process is created, and errno is set to indicate the error.


## function open()

NAME

       open, openat, creat - open and possibly create a file

SYNOPSIS

       #include <fcntl.h>

       int open(const char *pathname, int flags);
       int open(const char *pathname, int flags, mode_t mode);

       int creat(const char *pathname, mode_t mode);

       int openat(int dirfd, const char *pathname, int flags);
       int openat(int dirfd, const char *pathname, int flags, mode_t mode);

DESCRIPTION

       The open() system call opens the file specified by pathname.  If the specified file does not exist, it may optionally (if O_CREAT is specified in flags) be created by open().

       The return value of open() is a file descriptor, a small, nonnegative integer that is an index to an entry in the process's table of open file descriptors.  The file descriptor is used in subsequent system call (read(2), write(2), lseek(2), fcntl(2), etc.) to refer to the open file.  The file descriptor returned by a successful call will be the lowest-numbered file descriptor not currently open for the process.

       By default, the new file descriptor is set to remain open across an execve(2) (i.e., the FD_CLOEXEC file descriptor flag described in fcntl(2) is initially disabled); the O_CLOEXEC flag, described below, can be used to change this default.  The file offset is set to the beginning of the file (see lseek(2)).

       A call to open() creates a new open file description, an entry in the system-wide table of open files.  The open file description
       records the file offset and the file status flags (see below).  A file descriptor is a reference to an open file description; this reference is unaffected if pathname is subsequently removed or modified to refer to a different file.  For further details on open file descriptions, see NOTES.

       The argument flags must include one of the following access modes: O_RDONLY, O_WRONLY, or O_RDWR.  These request opening the file read-only, write-only, or read/write, respectively.

       In addition, zero or more file creation flags and file status flags can be bitwise-or'd in flags.  The file creation flags are O_CLOEXEC, O_CREAT, O_DIRECTORY, O_EXCL, O_NOCTTY, O_NOFOLLOW, O_TMPFILE, and O_TRUNC.  The file status flags are all of the remaining flags listed below.  The distinction between these two groups of flags is that the file creation flags affect the semantics of the open operation itself, while the file status flags affect the semantics of subsequent I/O operations.  The file status flags can be retrieved and (in some cases) modified; see fcntl(2) for details.

       O_CREAT
              The owner (user ID) of the new file is set to the effective user ID of the process.

              The group ownership (group ID) of the new file is set either to the effective group ID of the process (System V semantics) or to the group ID of the parent directory (BSD semantics).  On Linux, the behavior depends on whether the set-group-ID mode bit is set on the parent directory: if that bit is set, then BSD semantics apply; otherwise, System V semantics apply.  For some filesystems, the behavior also depends on the bsdgroups and sysvgroups mount options described in mount(8).

              The mode argument specifies the file mode bits to be applied when a new file is created.  If neither O_CREAT nor O_TMPFILE is specified in flags, then mode is ignored (and can thus be specified as 0, or simply omitted).  The mode argument must be supplied if O_CREAT or O_TMPFILE is specified in flags; if it is not supplied, some arbitrary bytes from the stack will be applied as the file mode.

              The effective mode is modified by the process's umask in the usual way: in the absence of a default ACL, the mode of the created file is (mode & ~umask).

              Note that mode applies only to future accesses of the newly created file; the open() call that creates a read- only file may well return a read/write file descriptor.

              The following symbolic constants are provided for mode:

              S_IRWXU  00700 user (file owner) has read, write, and execute permission

              S_IRUSR  00400 user has read permission

              S_IWUSR  00200 user has write permission

              S_IXUSR  00100 user has execute permission

              S_IRWXG  00070 group has read, write, and execute permission

              S_IRGRP  00040 group has read permission

              S_IWGRP  00020 group has write permission

              S_IXGRP  00010 group has execute permission

              S_IRWXO  00007 others have read, write, and execute permission

              S_IROTH  00004 others have read permission

              S_IWOTH  00002 others have write permission

              S_IXOTH  00001 others have execute permission

              According to POSIX, the effect when other bits are set in mode is unspecified.  On Linux, the following bits are also honored in mode:

              S_ISUID  0004000 set-user-ID bit

              S_ISGID  0002000 set-group-ID bit (see inode(7)).

              S_ISVTX  0001000 sticky bit (see inode(7)).

       O_TRUNC
              If the file already exists and is a regular file and the access mode allows writing (i.e., is O_RDWR or O_WRONLY) it will be truncated to length 0.  If the file is a FIFO or terminal device file, the O_TRUNC flag is ignored. Otherwise, the effect of O_TRUNC is unspecified.

RETURN VALUE

       On success, open(), openat(), and creat() return the new file descriptor (a nonnegative integer).  On error, -1 is returned and errno is set to indicate the error.

function find_path()
    
    A short-hand signature is:
        
        find_path (<VAR> name1 [path1 path2 ...])

    This command is used to find a directory containing the named file. A cache entry, or a normal variable if NO_CACHE is specified, named by <VAR> is created to store the result of this command. If the file in a directory is found the result is stored in the variable and the search will not be repeated unless the variable is cleared. If nothing is found, the result will be <VAR>-NOTFOUND.

## functions wait(), waitpid()

Name

       wait, waitpid - wait for a child process to stop or terminate

Synopsis

      #include <sys/wait.h>

 Description

       The wait() and waitpid() functions shall obtain status information pertaining to one of the caller's child processes. Various options permit status information to be obtained for child processes that have terminated or stopped. If status information is available for two or more child processes, the order in which their status is reported is unspecified.

       The wait() function shall suspend execution of the calling thread until status information for one of the terminated child processes of the calling process is available, or until delivery of a signal whose action is either to execute a signal-catching function or to terminate the process. If more than one thread is suspended in wait() or waitpid() awaiting termination of the same process, exactly one thread shall return the process status at the time of the target process termination. If status information is available prior to the call to wait(), return shall be immediate.

       The waitpid() function shall be equivalent to wait() if the pid argument is (pid_t)-1 and the options argument is 0. Otherwise, its behavior shall be modified by the values of the pid and options arguments.

       The pid argument specifies a set of child processes for which status is requested. The waitpid() function shall only return the status of a child process from this set:

       *
       If pid is equal to (pid_t)-1, status is requested for any child process. In this respect, waitpid() is then equivalent to wait().
       *
       If pid is greater than 0, it specifies the process ID of a single child process for which status is requested.
       *
       If pid is 0, status is requested for any child process whose process group ID is equal to that of the calling process.
       *
       If pid is less than (pid_t)-1, status is requested for any child process whose process group ID is equal to the absolute value of pid.

Return Value

       If wait() or waitpid() returns because the status of a child process is available, these functions shall return a value equal to the process ID of the child process for which status is reported. If wait() or waitpid() returns due to the delivery of a signal to the calling process, -1 shall be returned and errno set to [EINTR]. If waitpid() was invoked with WNOHANG set in options, it has at least one child process specified by pid for which status is not available, and status is not available for any process specified by pid, 0 is returned. Otherwise, (pid_t)-1 shall be returned, and errno set to indicate the error.

## function execev()

Name

       execve - execute program

Synopsis

       #include <unistd.h>

        int execve(const char *pathname, char *const argv[], char *const envp[]);

Description

       execve() executes the program pointed to by filename. filename must be either a binary executable, or a script starting with a line of the form:

       #! interpreter [optional-arg]
       For details of the latter case, see "Interpreter scripts" below.
       argv is an array of argument strings passed to the new program. By convention, the first of these strings should contain the filename associated with the file being executed. envp is an array of strings, conventionally of the form key=value, which are passed as environment to the new program. Both argv and envp must be terminated by a NULL pointer. The argument vector and environment can be accessed by the called program's main function, when it is defined as:

              int main(int argc, char *argv[], char *envp[])
       execve() does not return on success, and the text, data, bss, and stack of the calling process are overwritten by that of the program loaded.

## function dup2()

NAME

       dup, dup2, dup3 - duplicate a file descriptor

SYNOPSIS

       #include <unistd.h>

       int dup(int oldfd);
       int dup2(int oldfd, int newfd);

DESCRIPTION

       The dup() system call allocates a new file descriptor that refers to the same open file description as the descriptor oldfd.
       (For an explanation of open file descriptions, see open(2).)
       The new file descriptor number is guaranteed to be the lowest-numbered file descriptor that was unused in the calling process.

       After a successful return, the old and new file descriptors may be used interchangeably.  Since the two file descriptors refer to the same open file description, they share file offset and file status flags; for example, if the file offset is modified by using lseek(2) on one of the file descriptors, the offset is also changed for the other file descriptor.

       The two file descriptors do not share file descriptor flags (the close-on-exec flag).  The close-on-exec flag (FD_CLOEXEC; see fcntl(2)) for the duplicate descriptor is off.

       dup2()
       The dup2() system call performs the same task as dup(), but instead of using the lowest-numbered unused file descriptor, it uses the file descriptor number specified in newfd.  In other words, the file descriptor newfd is adjusted so that it now refers to the same open file description as oldfd.

       If the file descriptor newfd was previously open, it is closed before being reused; the close is performed silently (i.e., any errors during the close are not reported by dup2()).

       The steps of closing and reusing the file descriptor newfd are performed atomically.  This is important, because trying to implement equivalent functionality using close(2) and dup() would be subject to race conditions, whereby newfd might be reused between the two steps.  Such reuse could happen because the main program is interrupted by a signal handler that allocates a file descriptor, or because a parallel thread allocates a file descriptor.

       Note the following points:

       *  If oldfd is not a valid file descriptor, then the call fails, and newfd is not closed.

       *  If oldfd is a valid file descriptor, and newfd has the same value as oldfd, then dup2() does nothing, and returns newfd.

       dup3()
       dup3() is the same as dup2(), except that:

       *  The caller can force the close-on-exec flag to be set for the new file descriptor by specifying O_CLOEXEC in flags.  See the description of the same flag in open(2) for reasons why this may be useful.

       *  If oldfd equals newfd, then dup3() fails with the error EINVAL.

RETURN VALUE

       On success, these system calls return the new file descriptor.
       On error, -1 is returned, and errno is set to indicate the error.