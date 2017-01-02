#Structure

In C, a structure is essentially a variable that contains other variables inside of it. You can define one, then generate muliple instances of it each with their own unique values.
To establish a structure, you can do it outside of main . The following example will feature named "tux".

code:
```
struct tux {
         char color[10];
         char sexy[20];
         int length;
    };
```

And once you have defined a structure, you can generate an instance like this. This will generate an instance of a tux structure called mytux

code:
```
 struct tux mytux;
```

And finally, if you want to call a variable within a strucutre, you can do so by calling the strucutre instance's name followed by a "." followed by the variable's name. This will copy the string "black" to the variable "color"
located in the "mytux" struct instance.
 
code:
```
strcpy(mytux.color, "black");
```

And here is some sample code that sums it all together...

Sample Code:
```
#include <stdio.h>
#include <stdlib.h>

//This establishes the tux structure
struct tux {
         char color[10];
         char sexy[20];
         int length;
    };

int main()
{
    //This establishes the three instances of the tux structure
    struct tux tux1;
    struct tux mytux;
    struct tux urtux;

    //these just set the values for the individual variables within the structures
    strcpy(tux1.color, "camo");
    strcpy(tux1.sexy, "not sexy");
    tux1.length = 1;

    strcpy(mytux.color, "black");
    strcpy(mytux.sexy, "super sexy");
    mytux.length = 5;

    strcpy(urtux.color, "white");
    strcpy(urtux.sexy, "somewhat sexy");
    urtux.length = 55555;

    //This just prints out the structure variables
    printf("The tux's color is %s\n", tux1.color);
    printf("The tux is %s\n", tux1.sexy);
    printf("The tux's length is %d\n\n", tux1.length);

    printf("The tux's color is %s\n", mytux.color);
    printf("The tux is %s\n", mytux.sexy);
    printf("The tux's length is %d\n\n", mytux.length);

    printf("The tux's color is %s\n", urtux.color);
    printf("The tux is %s\n", urtux.sexy);
    printf("The tux's length is %d\n", urtux.length);


    return 0;
}
```

Output:
```
guyinatuxedo@tux:/Athena/pointers/Pointers/bin/Debug$ ./Pointers 
The tux's color is camo
The tux is not sexy
The tux's length is 1

The tux's color is black
The tux is super sexy
The tux's length is 5

The tux's color is white
The tux is somewhat sexy
The tux's length is 55555
```



