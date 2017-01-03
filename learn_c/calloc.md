#What is calloc?  

Calloc is a function like malloc. It will allocate a designated amount of memory. However it does a few things that malloc doesn't. it will initialize the memroy it allocated with zero (which means that it will assign it's first value to be zero). This leads to calloc taking longer than malloc. In addition to that calloc takes two arguments the amount of items to be allocated, and the size of each item. To free the memory used by calloc() you can use the free() function just like if it was malloc().
Here is some sample code that uses calloc...

Code:
```


```
