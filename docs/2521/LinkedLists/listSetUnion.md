# `listSetUnion`

Your task is to write a function, listSetUnion, that takes two lists representing two sets and returns a new list that represents the union of those sets. For example, if the two lists are [4, 3, 1, 7, 6] and [3, 2, 5, 1, 6], you should return a list containing the elements 1, 2, 3, 4, 5, 6, and 7. The result list does not have to be ordered in any particular way. Since the input lists represent sets, you can assume they do not contain any duplicate elements. Your function must not modify the input lists.

## Download

[Click here to download a zip of the files](https://github.com/BraedonWooding/CseExamRevision/raw/main/docs/2521/LinkedLists/listSetUnion.zip ':ignore')

### The Files

- list.c	Contains the implementation of basic list functions
- list.h	Contains the definition of the list data structure and function prototypes
- testListSetUnion.c	Contains the main function, which reads in two lists from standard input, calls listSetUnion, sorts the returned list, and prints out the result.
- listSetUnion.c	Contains listSetUnion, the function you must implement
- Makefile	A makefile to compile your code
- tests/	A directory containing the inputs and expected outputs for some basic tests
- autotest	A script that uses the tests in the tests directory to autotest your solution. You should only run this after you have tested your solution manually.

## Examples

```
$ ./testListSetUnion
Enter list 1: 4 3 1 7 6
Enter list 2: 3 2 1 5 6

Set 1: {4, 3, 1, 7, 6}
Set 2: {3, 2, 1, 5, 6}
Union set: {1, 2, 3, 4, 5, 6, 7}
```

?> Explanation: the returned list is sorted so that your program's output
             can be compared against the expected output.
		
```
$ ./testListSetUnion
Enter list 1: 1 3 5 7 9
Enter list 2: 8 6 4 2 0

Set 1: {1, 3, 5, 7, 9}
Set 2: {8, 6, 4, 2, 0}
Union set: {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
```	

```
$ ./testListSetUnion
Enter list 1: 
Enter list 2: 1 8 3 9

Set 1: {}
Set 2: {1, 8, 3, 9}
Union set: {1, 3, 8, 9}
```	

```
$ ./testListSetUnion
Enter list 1: 
Enter list 2: 

Set 1: {}
Set 2: {}
Union set: {}
```

## Testing

You can test your program manually by compiling your code using make, and then running ./testListSetUnion, as shown above. After you are satisfied with your solution, you can autotest it by running ./autotest. This will run some basic tests on your program.

## Solutions

!> Please do NOT look until you have atleast given it a solid go.

<details>
<summary>Solution</summary>

```c
// Doesn't have to be fast, just be productive, do the simplest solution

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

void listAdd(List list, List result) {
  Node cur = list->head;
  while (cur != NULL) {
    if (!listContains(result, cur->value)) {
      Node n = newNode(cur->value);
      n->next = result->head;
      result->head = n;
    }
    cur = cur->next;
  }
}

List listSetUnion(List s1, List s2) {
  List result = newList();
  listAdd(s1, result);
  listAdd(s2, result);
  return result;
}
```

</details>
