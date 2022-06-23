[42]

# Header Files & Librairies

A header file is a file with extension .h which contains C function declarations and macro definitions to be shared between several source files.
There are two types of header files: the files that the programmer writes and the files that comes with your compiler.

We use system header files (global librairies);

```js
#include <stdio.h>
```

When we want to use user header files (local librairies);

```js
*include "my_librairy"
```

Once-Only Headers:

If a header file happens to be included twice, the compiler will process its contents twice and it will result in an error.
The standard way to prevent this is to enclose the entire real contents of the file in a conditional.

```js
#ifndef HEADER_FILE
#define HEADER_FILE

the entire header file file

#endif
```

This construct is commonly known as a wrapper #ifndef. When the header is included again, the conditional will be false, because HEADER_FILE is defined. The preprocessor will skip over the entire contents of the file, and the compiler will not see it twice.