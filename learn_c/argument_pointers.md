What if we needed to have a function that editied the paramters that it imported? Let's try it out with this code...

code:
```
#include <stdio.h>
#include <stdlib.h>

int main()
{

        int tuxs;
        tuxs = 0;

        void change(int tuxs) {
            tuxs++;
        }

        printf("We had %d tuxedos\n", tuxs);
        change(tuxs);
        printf("Now we have %d tuxedos\n", tuxs);

        return 0;
}
```

Looking at this code, it appears that it might change the value of the tuxs int. Let's see if it does...

Output:
```
guyinatuxedo@tux:/Athena/pointers/Pointers/bin/Debug$ ./Pointers 
We had 0 tuxedos
Now we have 0 tuxedos
```

As you can see, it did not. This is because the function itself created it's int and changed that. However we can instead import a pointer, and that way when we edit the pointer we are editing the actual value since the program has the memory address. We can signify to give the address of a variable over to the function by putting a "&" infront of the name. Then when we import the variable, we will need to treat it as a pointer since it is.

code:
```
#include <stdio.h>
#include <stdlib.h>

int main()
{

        int tuxs;
        tuxs = 0;

        void change(int * tuxs) {
            (*tuxs)++;
        }

        printf("We had %d tuxedos\n", tuxs);
        change(&tuxs);
        printf("Now we have %d tuxedos\n", tuxs);

        return 0;
}
```

Output:
```
guyinatuxedo@tux:/Athena/pointers/Pointers/bin/Debug$ ./Pointers 
We had 0 tuxedos
Now we have 1 tuxedos
```

As you can see, by giving the function a memory address and by treating that address as a pointer, we were able to successfully modify the argument value. Now what happens when we are dealing with structures? Well it works the same way.
The syntax is different though. You have to declare a structure in the function arguments, and instead of using a "." to seperate the structure from a variable you use "->".

code:
```
#include <stdio.h>
#include <stdlib.h>

struct tux {
         int tuxs;
    };

int main()
{

        struct tux mytux;
        mytux.tuxs = 0;

        void change(struct tux *mytux) {
           mytux->tuxs++;
        }

        printf("We had %d tuxedos\n", mytux.tuxs);
        change(&mytux);
        printf("Now we have %d tuxedos\n", mytux.tuxs);

        return 0;
}
```

Output:
```
guyinatuxedo@tux:/Athena/pointers/Pointers/bin/Debug$ ./Pointers 
We had 0 tuxedos
Now we have 1 tuxedos
```





