# `listIsOrdered`

Your task is to write a function, listIsOrdered, that determines whether a linked list is sorted in either ascending or descending order. It should return true if the list is sorted in ascending or descending order, and false otherwise. Your function should not modify the list. An empty list is considered to be sorted.

## Download

[Click here to download a zip of the files](https://github.com/BraedonWooding/CseExamRevision/raw/main/docs/2521/LinkedLists/listIsOrdered.zip ':ignore')

The Files
- list.c	Contains the implementation of basic list functions
- list.h	Contains the definition of the list data structure and function prototypes
- testListIsOrdered.c	Contains the main function, which reads in a list from standard input, calls listIsOrdered, and prints out the result.
- listIsOrdered.c	Contains listIsOrdered, the function you must implement
- Makefile	A makefile to compile your code
- tests/	A directory containing the inputs and expected outputs for some basic tests
- autotest	A script that uses the tests in the tests directory to autotest your solution. You should only run this after you have tested your solution manually.

## Examples

```
$ ./testListIsOrdered
Enter list: 2 4 5 5 8 9
listIsOrdered returned TRUE
```	

```
$ ./testListIsOrdered
Enter list: 2 4 7 5 4
listIsOrdered returned FALSE
```	

```
$ ./testListIsOrdered
Enter list: 9 8 7 2
listIsOrdered returned TRUE
```	

```
$ ./testListIsOrdered
Enter list: 
listIsOrdered returned TRUE
```

## Testing

You can test your program manually by compiling your code using make, and then running ./testListIsOrdered, as shown above. After you are satisfied with your solution, you can autotest it by running ./autotest. This will run some basic tests on your program, as well as check for memory leaks/errors.

## Solutions

!> Please do NOT look until you have atleast given it a solid go.

<details>
<summary>Solution</summary>

```c
bool listIsOrdered(List l) {
  if (l->head == NULL || l->head->next == NULL)
    return true;

  Node cur = l->head;
  bool descending = cur->value > cur->next->value;

  while (cur->next != NULL) {
    // You could spend time making this more concise
    // But sometimes just a dirty quick way of doing something
    // Is best in exams.
    if ((descending && cur->value < cur->next->value) ||
        (!descending && cur->value > cur->next->value)) {
      return false;
    }
    cur = cur->next;
  }
  return true;
}
```

</details>
