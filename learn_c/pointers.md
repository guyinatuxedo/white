#Pointer

All a pointer is, is it is an integer variable that holds the memory address of a value, versus the actual value. So instead of holding a value such as "0000", it points to where on the stack "0000" is. This is used for things such as dealing with large allocated amounts of memory.

#String Pointers

Now pointers can also be made as strings. Take for instance the following line of code.

```
char * guy = "inatuxedo";
```

That line of code would do a couple of things.

0.) It would store the string "inatuxedo" somewhere in the program's memory once it is executed.
1.) It would create a local variable named "guy", which is a pointer
2.) It would set the pointer "guy" equal to the memory address of the first letter of the string, which is "i"

Since the pointer only points to the first character in the string, then wouldn't it just be able to represent that one character? Let's see...

Code:
```
#include <stdio.h>
#include <stdlib.h>

int main()
{
    //Establish the pointer
    char * guy = "inatuxedo";
    
    //print the pointer
    printf("%s\n", guy);

    return 0;
}
```

Output:
```
guyinatuxedo@tux:/Athena/pointers/Pointers/bin/Debug$ ./Pointers 
inatuxedo
```

So as we can see here, the program printed out the entire string. This is because the rest of the string is stored in order, with a null terminator (otherwise known as "\0") at the end. The program will print untill it reaches the null termianor. So even though the pointer only points to the first character, we can still use it to interface with the entire string.

#Dereferencing

Now we can use pointers to directly affect other variables. But first we will need to dereference them, which is when we specify that we want to interface with the value that it is pointing to, and not the pointer itself. We do this using the same character we use to specify a pointer, "*".

```
#include <stdio.h>
#include <stdlib.h>

int main()
{
    //establish a local variable
    int tux;

    //create a pointer to that variable
    int * tux_pointer = &tux;

    printf("You have %d tuxedos\n", tux);

    return 0;
}
```

Output:
```
guyinatuxedo@tux:/Athena/pointers/Pointers/bin/Debug$ ./Pointers 
You have 0 tuxedos
```

As you can see, I created a local int printed it out and it returned the default value of 0. Now let's use the "tux_pointer" pointer to change the value.

Code:
```
#include <stdio.h>
#include <stdlib.h>

int main()
{
    //establish a local variable
    int tux;

    //create a pointer to that variable
    int * tux_pointer = &tux;

    //add ten to tux
    *tux_pointer += 10;

    printf("You have %d tuxedos\n", tux);

    return 0;
}
```

Output:
```
guyinatuxedo@tux:/Athena/pointers/Pointers/bin/Debug$ ./Pointers 
You have 10 tuxedos
```

As you can see, we have used the pointer to directly affect the value of the variable.




