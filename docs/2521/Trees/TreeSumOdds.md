# `TreeSumOdds`

Your task is to write a function, TreeSumOdds, that returns the sum of all of the odd values in the given tree.

## Download

[Click here to download a zip of the files](https://github.com/BraedonWooding/CseExamRevision/raw/main/docs/2521/Trees/TreeSumOdds.zip ':ignore')

### The Files

- Tree.c	Contains code for reading and printing a binary tree
- Tree.h	Contains the definition of the binary tree data structure and function prototypes
- testTreeSumOdds.c	Contains the main function, which reads in a binary tree from standard input, calls TreeSumOdds, and prints out the result.
- TreeSumOdds.c	Contains TreeSumOdds, the function you must implement
- Makefile	A makefile to compile your code
- tests/	A directory containing the inputs and expected outputs for some basic tests
- autotest	A script that uses the tests in the tests directory to autotest your solution. You should only run this after you have tested your solution manually.

## Examples

```
$ ./testTreeSumOdds
Enter the preorder traversal of the tree: 3 2 1 4 5
Enter the in-order traversal of the tree: 1 2 3 4 5
Tree:

    3
   / \
  2   4
 /     \
1       5

TreeSumOdds returned 9
```

```
$ ./testTreeSumOdds
Enter the preorder traversal of the tree: 8 4 2 6 12 14
Enter the in-order traversal of the tree: 2 4 6 8 12 14
Tree:

     8
    / \
   /   \
  4    12
 / \     \
2   6    14

TreeSumOdds returned 0
		

$ ./testTreeSumOdds
Enter the preorder traversal of the tree: 3 -9 -5 1 6 4
Enter the in-order traversal of the tree: -9 -5 1 3 4 6
Tree:

    3
   / \
  /   \
 /     \
-9      6
 \     /
 -5   4
   \
    1

TreeSumOdds returned -10
```

## Testing

You can test your program manually by compiling your code using make, and then running ./testTreeSumOdds, as shown above. After you are satisfied with your solution, you can autotest it by running ./autotest. This will run some basic tests on your program.

## Solutions

!> Please do NOT look until you have atleast given it a solid go.

<details>
<summary>Solution</summary>

```c
int TreeSumOdds(Tree t) {
  if (t == NULL) {
    return 0;
  } else {
    int result = TreeSumOdds(t->left) + TreeSumOdds(t->right);
    if (t->value % 2 != 0) {
      result += t->value;
    }
    return result;
  }
}
```

</details>
