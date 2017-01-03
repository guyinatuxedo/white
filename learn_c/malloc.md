
To allocate memory dynamically, you can use the malloc() function. The malloc() function will allow code to access a program's heap to store data, and then it will return a pointer for the memory allocated. Keep in mind that if this is not done securely, it can lead to your program being vulnerable to heap exploitation. The benefits of using malloc() include that you don't actually need to know the size of the memory when you write the code, and that the memory allocated to is both read and write. Once you are done with the memory, you can free it by using the free() function. This does not delete the data, but allows it to be reused.

Here are some examples of using malloc. First we have using malloc to allocate a structure.

Code:
```
#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int length;
} tux;

int main()
{
   tux * mytux = malloc(sizeof(tux));

   mytux->length = 5;

   printf("My Tuxedo's length is %d\n", mytux->length);
   printf("The mytux instance is stored at %x\n", mytux);
   free(mytux);
    return 0;
}
```

Output
```
guyinatuxedo@tux:/Athena/misc/bin/Debug$ ./misc
My Tuxedo's length is 5
The mytux instance is stored at 103a010
```

Then we have using malloc to allocate memory to a char.

Code:
```
#include <stdio.h>
#include <stdlib.h>

int main()
{
   char *tux = malloc(sizeof(char));
   tux = "black";
   printf("The tuxedo is %s\n", tux);
      return 0;
}
```

Output
```
guyinatuxedo@tux:/Athena/misc/bin/Debug$ ./misc 
The tuxedo is black
```
