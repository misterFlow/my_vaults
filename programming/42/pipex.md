[42]

explication: https://csnotes.medium.com/pipex-tutorial-42-project-4469f5dd5901

github for inspiration: https://github.com/tolmvad/pipex

youtube CodeVault: https://www.youtube.com/watch?v=6xbLgZpOBi8

function fork():

DESCRIPTION

       fork() creates a new process by duplicating the calling process.
       The new process is referred to as the child process.  The calling
       process is referred to as the parent process.

       The child process and the parent process run in separate memory
       spaces.  At the time of fork() both memory spaces have the same
       content.  Memory writes, file mappings (mmap(2)), and unmappings
       (munmap(2)) performed by one of the processes do not affect the
       other.

RETURN VALUE

       On success, the PID of the child process is returned in the
       parent, and 0 is returned in the child.  On failure, -1 is
       returned in the parent, no child process is created, and errno is
       set to indicate the error.

