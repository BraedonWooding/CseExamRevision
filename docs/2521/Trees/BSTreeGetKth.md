# `BSTreeGetKth`

Your task is to write a function, BSTreeGetKth, that returns the k'th smallest value in the given BST. You can assume that k is between 0 and N - 1, where N is the size of the tree.

## Download

[Click here to download a zip of the files](https://github.com/BraedonWooding/CseExamRevision/raw/main/docs/2521/Trees/BSTreeGetKth.zip ':ignore')

### The Files

- BSTree.c	Contains code for reading and printing a BST
- BSTree.h	Contains the definition of the BST data structure and function prototypes
- testBSTreeGetKth.c	Contains the main function, which reads in a BST from standard input, calls BSTreeGetKth for each value of k read in, and prints out the results.
- BSTreeGetKth.c	Contains BSTreeGetKth, the function you must implement
- Makefile	A makefile to compile your code
- tests/	A directory containing the inputs and expected outputs for some basic tests
- autotest	A script that uses the tests in the tests directory to autotest your solution. You should only run this after you have tested your solution manually.

## Examples

```
$ ./testBSTreeGetKth
Enter the preorder traversal of the BST: 3 2 1 4 5
Tree:

    3
   / \
  2   4
 /     \
1       5

Enter k: 0
For k = 0, BSTreeGetKth returned 1
Enter k: 1
For k = 1, BSTreeGetKth returned 2
Enter k: 2
For k = 2, BSTreeGetKth returned 3
Enter k: 3
For k = 3, BSTreeGetKth returned 4
Enter k: 4
For k = 4, BSTreeGetKth returned 5
Enter k: (Ctrl + D)
```

```
$ ./testBSTreeGetKth
Enter the preorder traversal of the BST: 8 2 5 4 7 12 13
Tree:

   8
  / \
 /   \
2    12
 \     \
  5    13
 / \
4   7

Enter k: 0
For k = 0, BSTreeGetKth returned 2
Enter k: 1
For k = 1, BSTreeGetKth returned 4
Enter k: 2
For k = 2, BSTreeGetKth returned 5
Enter k: 3
For k = 3, BSTreeGetKth returned 7
Enter k: 4
For k = 4, BSTreeGetKth returned 8
Enter k: 5
For k = 5, BSTreeGetKth returned 12
Enter k: 6
For k = 6, BSTreeGetKth returned 13
Enter k: (Ctrl + D)
```
	
```
$ ./testBSTreeGetKth
Enter the preorder traversal of the BST: 7
Tree:

7

Enter k: 0
For k = 0, BSTreeGetKth returned 7
Enter k: (Ctrl + D)
```

## Testing

You can test your program manually by compiling your code using make, and then running ./testBSTreeGetKth, as shown above. After you are satisfied with your solution, you can autotest it by running ./autotest. This will run some basic tests on your program.

## Solutions

!> Please do NOT look until you have atleast given it a solid go.

<details>
<summary>Solution</summary>

```c
// I've attached a simpler way of doing this question at the bottom

// Helper function to carry some state along with us
// Not pure recursion but useful.
// We set state to -1 when we find the value we want
int BSTreeGetKthRec(BSTree t, int k, int *state) {
  if (t == NULL) {
    return 0;
  }

  int left = BSTreeGetKthRec(t->left, k, state);
  if (*state == -1) {
    // If found in left subtree
    return left;
  }

  // Else we are the next smallest
  // If we are the next smallest that we want
  // Then set state to -1 and return
  // Else find the next smallest after us
  if (k == *state) {
    *state = -1;
    return t->value;
  } else {
    (*state)++;
  }

  // Return right regardless since we only propagate
  // it if state == -1
  int right = BSTreeGetKthRec(t->right, k, state);
  return right;
}

int BSTreeGetKth(BSTree t, int k) {
  // There are many ways to solve this problem.
  // This is just one that uses a stack (recursion)
  int state = 0; // find the 0'th smallest
  return BSTreeGetKthRec(t, k, &state);
}

/*
  Simpler way.
*/

static int BSTreeSize(BSTree t) {
	if (t == NULL) {
		return 0;
	} else {
		return 1 + BSTreeSize(t->left) + BSTreeSize(t->right);
	}
}

int SimplerBSTreeGetKth(BSTree t, int k) {
	int leftSize = BSTreeSize(t->left);
	if (k == leftSize) {
		return t->value;
	} else if (k < leftSize) {
		return SimplerBSTreeGetKth(t->left, k);
	} else {
		return SimplerBSTreeGetKth(t->right, k - leftSize - 1);
	}
}
```

</details>
