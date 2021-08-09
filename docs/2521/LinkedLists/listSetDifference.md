# `listSetDifference`

Your task is to write a function, listSetDifference, that takes two lists, l1 and l2, that represent sets and returns a new list representing the set difference (l1 - l2). The values in the returned list may be in any order - the testing program will sort the list before displaying it. Since the lists l1 and l2 represent sets, you may assume that no value appears more than once in a list. You should not modify the given lists.

## Download

[Click here to download a zip of the files](2521/LinkedLists/listSetDifference.zip ':ignore')

### The Files

- list.c	Contains the implementation of basic list functions
- list.h	Contains the definition of the list data structure and function prototypes
- testListSetDifference.c	Contains the main function, which reads in two lists from standard input, calls listSetDifference, and prints out the result.
- listSetDifference.c	Contains listSetDifference, the function you must implement
- Makefile	A makefile to compile your code
- tests/	A directory containing the inputs and expected outputs for some basic tests
- autotest	A script that uses the tests in the tests directory to autotest your solution. You should only run this after you have tested your solution manually.

## Examples

```
$ ./testListSetDifference 
Enter list 1: 4 3 1 7 6
Enter list 2: 6 2 1 5 3

Set 1: {4, 3, 1, 7, 6}
Set 2: {6, 2, 1, 5, 3}
Difference: {4, 7}
```	

```
$ ./testListSetDifference
Enter list 1: 1 3 5 7 9
Enter list 2: 8 6 4 2 0

Set 1: {1, 3, 5, 7, 9}
Set 2: {8, 6, 4, 2, 0}
Difference: {1, 3, 5, 7, 9}
```	

```
$ ./testListSetDifference
Enter list 1: 9 1 8 2 5
Enter list 2: 1 5 2 9 8

Set 1: {9, 1, 8, 2, 5}
Set 2: {1, 5, 2, 9, 8}
Difference: {}
```

## Testing

You can test your program manually by compiling your code using make, and then running ./testListSetDifference, as shown above. After you are satisfied with your solution, you can autotest it by running ./autotest. This will run some basic tests on your program.

## Solutions

!> Please do NOT look until you have atleast given it a solid go.

<details>
<summary>Solution</summary>

```c
static bool listContains(List l, int value);

List listSetDifference(List l1, List l2) {
	List l3 = newList();
	
	Node curr = l1->head;
	while (curr != NULL) {
		if (!listContains(l2, curr->value)) {
            // add node
            Node n = newNode(value);
            n->next = l->head;
            l->head = n;
		}
		curr = curr->next;
	}
	
	return l3;
}

static bool listContains(List l, int value) {
	for (Node curr = l->head; curr != NULL; curr = curr->next) {
		if (curr->value == value) {
			return true;
		}
	}
	return false;
}
```

</details>
