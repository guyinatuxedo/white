#What is calloc?  

Calloc is a function like malloc. It will allocate a designated amount of memory. However it does a few things that malloc doesn't. it will initialize the memroy it allocated with zero (which means that it will assign it's first value to be zero). This leads to calloc taking longer than malloc. In addition to that calloc takes two arguments the amount of items to be allocated, and the size of each item. To free the memory used by calloc() you can use the free() function just like if it was malloc().
Here is some sample code that uses calloc...

Code:
```
#include <stdio.h>
#include <stdlib.h>

int main()
{

   int items, i;
   items = 5;

    int *tuxs;

   tuxs = (int*)calloc(items, sizeof(int));

   for ( i=0 ; i < items ; i++ )
   {
    printf("%d \n", tuxs[i]);
   }

   free(tuxs);

   return(0);
}
```

As you can see, that calloc instance will generate 5 items, each the size of a C x86 integer (4 bytes). It then will print out the value of each item, which should be zero since calloc() intiitalizes it's data at 0, and we don't edit it in the code. Let's see what we get...

Output:
```
guyinatuxedo@tux:/Athena/misc/bin/Debug$ ./misc 
0 
0 
0 
0 
0 
```

Now let's edit the value of the items, so we can get something other than 0.

Code:
```
#include <stdio.h>
#include <stdlib.h>

int main()
{

   int items, i;
   items = 5;

    int *tuxs;

   tuxs = (int*)calloc(items, sizeof(int));

   for ( i = 0;  i < items; i++)
   {
    printf("What is the value of the %d tux?\n", i);
    scanf("%d", &tuxs[i]);
   }

   for ( i = 0; i < items; i++)
   {
    printf("The value of the %d tux is ", i);
    printf("%d \n", tuxs[i]);
   }

   free(tuxs);

   return(0);
}
```

Output:
```
guyinatuxedo@tux:/Athena/misc/bin/Debug$ ./misc 
What is the value of the 0 tux?
87
What is the value of the 1 tux?
25
What is the value of the 2 tux?
34
What is the value of the 3 tux?
79
What is the value of the 4 tux?
4
The value of the 0 tux is 87 
The value of the 1 tux is 25 
The value of the 2 tux is 34 
The value of the 3 tux is 79 
The value of the 4 tux is 4 
```

One thing to note, since calloc generates multiple value the variable we stored the output of is treated as an array.
