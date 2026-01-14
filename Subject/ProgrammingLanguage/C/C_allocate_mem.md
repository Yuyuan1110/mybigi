---
tags: 
  - programming
  - allocate
  - malloc
  - calloc
  - realloc
  - alloc
alias: []
created: 2025-07-04
updated:
source:
---
# allocate memory note
`malloc`, `calloc`, `realloc`, there are all memory allocate key word in manual allocate in C programming language, here to introduce what the different between them.

## malloc
`malloc` is most often to use, it will allocated a spacific size memory block, but it just allocated, need initiallizte manully, if you do not initial this memory block, you may get NULL or some garbage data.
```clike
int *my_array = (int*)malloc(sizeof(int) * size);
my_array[0] = 1; // need initial manual, otherwise you will get some garbage data.
```

## calloc
`calloc` is more convenience than `malloc`, it will initail when you declarated.
```clike
int *my_array = (int*)calloc(size, sizeof(int));
print("it will init automaticlly: %d", my_array[0]); // output: 0
```
If using other type, it will initial to NULL (string or struct).

## realloc
`realloc` is like `malloc`, it will not initiallize automaticlly, it use when you need to re-allocate the memory what you have allocated before, whatever is using `calloc` or `malloc`.
```clike
int *arr = (int*)malloc(5 * sizeof(int)); 
int *new_arr = (int*)realloc(arr, 10 * sizeof(int)); 
if (new_arr == NULL) { 
	free(arr);
	return 1;
	} 
arr = new_arr; 
```