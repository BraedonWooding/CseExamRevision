# `listIsPalindromic`

## Download

[Click here to download a zip of the files](https://github.com/BraedonWooding/CseExamRevision/raw/main/docs/2521/LinkedLists/listIsPalindromic.zip ':ignore')

### The Files

- list.c	Contains the implementation of basic list functions
- list.h	Contains the definition of the list data structure and function prototypes
- testListIsPalindromic.c	Contains the main function, which reads in a list from standard input, calls listIsPalindromic, and prints out the result.
- listIsPalindromic.c	Contains listIsPalindromic, the function you must implement
- Makefile	A makefile to compile your code
- tests/	A directory containing the inputs and expected outputs for some basic tests
- autotest	A script that uses the tests in the tests directory to autotest your solution. You should only run this after you have tested your solution manually.

## Examples

```
$ ./testListIsPalindromic
Enter list: 1 2 3 2 1
listIsPalindromic returned TRUE
```

```
$ ./testListIsPalindromic
Enter list: 1 2 3 4
listIsPalindromic returned FALSE
```

```
$ ./testListIsPalindromic
Enter list: 9 4 7 1 1 7 4 9
listIsPalindromic returned TRUE
```

```
$ ./testListIsPalindromic
Enter list: 1 8 2 7 7 2 9 1
listIsPalindromic returned FALSE
```

```
$ ./testListIsPalindromic
Enter list: 
listIsPalindromic returned TRUE
```

## Testing

You can test your program manually by compiling your code using make, and then running ./testListIsPalindromic, as shown above. After you are satisfied with your solution, you can autotest it by running ./autotest. This will run some basic tests on your program.

## Solutions

!> Please do NOT look until you have atleast given it a solid go.

<details>
<summary>Solution</summary>

```c
bool listIsPalindromic(List l) {
  Node front = l->first;
  Node back = l->last;
  while (front != back && back->next != front) {
    if (front->value != back->value)
      return false;
    front = front->next;
    back = back->prev;
  }

  return true;
}
```

</details>
