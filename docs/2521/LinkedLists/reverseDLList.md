# `reverseDLList`

Your task is to write a function, reverseDLList, that reverses a given doubly linked list. You should not change the values in any nodes or create any new nodes - instead, you should rearrange the nodes of the given list.

## Download

[Click here to download a zip of the files](https://github.com/BraedonWooding/CseExamRevision/raw/main/docs/2521/LinkedLists/reverseDLList.zip ':ignore')

## The Files

- list.c	Contains the implementation of basic list functions
- list.h	Contains the definition of the list data structure and function prototypes
- testReverseDLList.c	Contains the main function, which reads in a list from standard input, calls reverseDLList, and prints out the original and resulting list.
- reverseDLList.c	Contains reverseDLList, the function you must implement
- Makefile	A makefile to compile your code
- tests/	A directory containing the inputs and expected outputs for some basic tests
- autotest	A script that uses the tests in the tests directory to autotest your solution. You should only run this after you have tested your solution manually.

## Examples
Your program should behave like these examples:

```
$ ./testReverseDLList
Enter list: 2 3 5 7 11

Original list:
Size: 5
Forwards:  [2] -> [3] -> [5] -> [7] -> [11] -> X
Backwards: [11] -> [7] -> [5] -> [3] -> [2] -> X

Reversed list:
Size: 5
Forwards:  [11] -> [7] -> [5] -> [3] -> [2] -> X
Backwards: [2] -> [3] -> [5] -> [7] -> [11] -> X
```

```
$ ./testReverseDLList
Enter list: 

Original list:
Size: 0
Forwards:  X
Backwards: X

Reversed list:
Size: 0
Forwards:  X
Backwards: X
```	

```
$ ./testReverseDLList
Enter list: 1 2 7 9 2 1

Original list:
Size: 6
Forwards:  [1] -> [2] -> [7] -> [9] -> [2] -> [1] -> X
Backwards: [1] -> [2] -> [9] -> [7] -> [2] -> [1] -> X

Reversed list:
Size: 6
Forwards:  [1] -> [2] -> [9] -> [7] -> [2] -> [1] -> X
Backwards: [1] -> [2] -> [7] -> [9] -> [2] -> [1] -> X
```

## Testing

You can test your program manually by compiling your code using make, and then running ./testReverseDLList, as shown above. After you are satisfied with your solution, you can autotest it by running ./autotest. This will run some basic tests on your program, as well as check for memory leaks/errors.

## Solution

## Solutions

!> Please do NOT look until you have atleast given it a solid go.

<details>
<summary>Solution</summary>

```c
void reverseDLList(List l) {
  Node cur = l->first;
  l->first = l->last;
  l->last = cur;

  while (cur != NULL) {
    // A little weird so you may want to draw a picture
    Node tmp = cur->prev;
    cur->prev = cur->next;
    cur->next = tmp;
    cur = cur->prev;
  }
}
```
</details>
