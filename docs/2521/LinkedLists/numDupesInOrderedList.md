# `numDupesInOrderedList`

Your task is to write a function, numDupesInOrderedList, that returns the number of duplicate elements in the given ordered linked list. The number of duplicate elements is the minimum number of elements that would need to be removed to obtain a list with no duplicates. For example, the list [1, 2, 2, 3, 3, 3] contains three duplicate elements, because three elements would need to be removed to obtain a list with no duplicates: 2, 3, and 3. (However, you should not actually remove any elements - you should simply return the number of duplicate values.) Your function should not modify the list. You can assume that the linked list is sorted in either ascending or descending order.

## Download

[Click here to download a zip of the files](https://github.com/BraedonWooding/CseExamRevision/raw/main/docs/2521/LinkedLists/numDupesInOrderedList.zip ':ignore')

The Files
- list.c	Contains the implementation of basic list functions
- list.h	Contains the definition of the list data structure and function prototypes
- testNumDupesInOrderedList.c	Contains the main function, which reads in a list from standard input, calls numDupesInOrderedList, and prints out the result.
- numDupesInOrderedList.c	Contains numDupesInOrderedList, the function you must implement
- Makefile	A makefile to compile your code
- tests/	A directory containing the inputs and expected outputs for some basic tests
- autotest	A script that uses the tests in the tests directory to autotest your solution. You should only run this after you have tested your solution manually.

## Examples

```
$ ./testNumDupesInOrderedList
Enter list: 1 2 3 4 5 5 5
numDupesInOrderedList returned 2
```

?> Explanation: two elements would need to be removed to obtain a list with
             no duplicates: 5 and 5.
	
```
$ ./testNumDupesInOrderedList
Enter list: 1 1 1 1 1 1 1
numDupesInOrderedList returned 6
```

?> Explanation: six elements (all 1's) would need to be removed to obtain a
             list with no duplicates.
		
```
$ ./testNumDupesInOrderedList
Enter list: 6 6 5 5 4 4 3 3 2 2 1 1 0
numDupesInOrderedList returned 6
```

?> Explanation: six elements would need to be removed to obtain a list with
             no duplicates: 6, 5, 4, 3, 2, 1.
		
```
$ ./testNumDupesInOrderedList
Enter list: 1 1 1 1 1 1 2 2 3 4 5 5 5 5
numDupesInOrderedList returned 9
```
?> Explanation: nine  elements  need to be removed to obtain a list with no
             duplicates: 1, 1, 1, 1, 1, 2, 5, 5, 5.

## Testing

You can test your program manually by compiling your code using make, and then running ./testNumDupesInOrderedList, as shown above. After you are satisfied with your solution, you can autotest it by running ./autotest. This will run some basic tests on your program, as well as check for memory leaks/errors.

## Solutions

!> Please do NOT look until you have atleast given it a solid go.

<details>
<summary>Solution</summary>

```c
int numDupesInOrderedList(List l) {
  int numDupes = 0;
  Node cur = l->head;
  Node dupe = NULL;

  while (cur != NULL) {
    if (dupe && dupe->value == cur->value) {
      numDupes++;
    } else {
      dupe = cur;
    }
    cur = cur->next;
  }

  return numDupes;
}
```

</details>

