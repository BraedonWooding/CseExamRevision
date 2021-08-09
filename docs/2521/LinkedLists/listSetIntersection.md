# `listSetIntersection`

Your task is to write a function, listSetIntersection, that takes two lists representing two sets and returns a new list that represents the intersection of those sets. For example, if the two lists are [4, 3, 1, 7, 6] and [3, 2, 5, 1, 6], you should return a list containing the elements 1, 3, and 6. The result list does not have to be ordered in any particular way. Since the input lists represent sets, you can assume they do not contain any duplicate elements. Your function must not modify the input lists.

## Download

[Click here to download a zip of the files](https://github.com/BraedonWooding/CseExamRevision/raw/main/docs/2521/LinkedLists/listSetIntersection.zip ':ignore')

### The Files

- list.c	Contains the implementation of basic list functions
- list.h	Contains the definition of the list data structure and function prototypes
- testListSetIntersection.c	Contains the main function, which reads in two lists from standard input, calls listSetIntersection, sorts the returned list, and prints out the result.
- listSetIntersection.c	Contains listSetIntersection, the function you must implement
- Makefile	A makefile to compile your code
- tests/	A directory containing the inputs and expected outputs for some basic tests
- autotest	A script that uses the tests in the tests directory to autotest your solution. You should only run this after you have tested your solution manually.

## Examples

```
$ ./testListSetIntersection
Enter list 1: 4 3 1 7 6
Enter list 2: 3 2 1 5 6

Set 1: {4, 3, 1, 7, 6}
Set 2: {3, 2, 1, 5, 6}
Intersection: {1, 3, 6}
```

?> Explanation: the returned list is sorted so that your program's output
             can be compared against the expected output.
		
```
$ ./testListSetIntersection
Enter list 1: 1 3 5 7 9
Enter list 2: 8 6 4 2 0

Set 1: {1, 3, 5, 7, 9}
Set 2: {8, 6, 4, 2, 0}
Intersection: {}
```	

```
$ ./testListSetIntersection
Enter list 1: 
Enter list 2: 1 8 3 9

Set 1: {}
Set 2: {1, 8, 3, 9}
Intersection: {}
```	

```
$ ./testListSetIntersection
Enter list 1: 5 8 3 9 6 7 1 4 2
Enter list 2: 3 2 8 4 0 9

Set 1: {5, 8, 3, 9, 6, 7, 1, 4, 2}
Set 2: {3, 2, 8, 4, 0, 9}
Intersection: {2, 3, 4, 8, 9}
```

## Testing

You can test your program manually by compiling your code using make, and then running ./testListSetIntersection, as shown above. After you are satisfied with your solution, you can autotest it by running ./autotest. This will run some basic tests on your program.

## Solutions

!> Please do NOT look until you have atleast given it a solid go.

<details>
<summary>Solution</summary>

```c
bool listContains(List list, int value) {
  Node cur = list->head;
  while (cur != NULL) {
    if (cur->value == value) {
      return true;
    }
    cur = cur->next;
  }
  return false;
}

List listSetIntersection(List s1, List s2) {
  List result = newList();

  Node cur = s1->head;
  while (cur != NULL) {
    if (listContains(s2, cur->value)) {
      // Order doesn't matter but if it did
      // It isn't too much more work
      // Just another loop

      // NOTE: I recommend you remember this
      //       It is effectively a stack very
      //       Easy way to add to a list
      // No branches required to add!
      Node n = newNode(cur->value);
      n->next = result->head;
      result->head = n;
    }
    cur = cur->next;
  }

  return result;
}
```

</details>
