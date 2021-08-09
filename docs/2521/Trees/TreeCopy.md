# `TreeCopy`

Your task is to write a function, TreeCopy, that copies a tree up to a given depth. If the given depth is negative, you should return an empty tree. If the given depth is greater than the height of the tree, you should return a copy of the entire tree. Do NOT modify the given tree.

## Download

[Click here to download a zip of the files](2521/Trees/TreeCopy.zip ':ignore')

### The Files

- Tree.c	Contains code for reading and printing a binary tree
- Tree.h	Contains the definition of the binary tree data structure and function prototypes
- testTreeCopy.c	Contains the main function, which reads in a binary tree and a depth from standard input, calls TreeCopy, and prints out the result.
- TreeCopy.c	Contains TreeCopy, the function you must implement
- Makefile	A makefile to compile your code
- tests/	A directory containing the inputs and expected outputs for some basic tests
- autotest	A script that uses the tests in the tests directory to autotest your solution. You should only run this after you have tested your solution manually.

## Examples

```
$ ./testTreeCopy
Enter the preorder traversal of the tree: 4 2 1 3 6 5 7
Enter the in-order traversal of the tree: 1 2 3 4 5 6 7
Enter depth: 1
Original tree:

      4
     / \
    /   \
   /     \
  2       6
 / \     / \
1   3   5   7

Copy of the tree up to depth 1:

  4
 / \
2   6
```

```
$ ./testTreeCopy 
Enter the preorder traversal of the tree: 2 1 4 3 6 5
Enter the in-order traversal of the tree: 1 2 3 4 5 6
Enter depth: 0
Original tree:

  2
 / \
1   4
   / \
  3   6
     /
    5

Copy of the tree up to depth 0:

2
```
	
```
$ ./testTreeCopy
Enter the preorder traversal of the tree: 4 1 7
Enter the in-order traversal of the tree: 1 4 7
Enter depth: -1
Original tree:

  4
 / \
1   7

Copy of the tree up to depth -1:

X
```

## Testing

You can test your program manually by compiling your code using make, and then running ./testTreeCopy, as shown above. After you are satisfied with your solution, you can autotest it by running ./autotest. This will run some basic tests on your program.

## Solutions

!> Please do NOT look until you have atleast given it a solid go.

<details>
<summary>Solution</summary>

```c
static Tree newNode(int value);

Tree TreeCopy(Tree t, int depth) {
	if (t == NULL || depth < 0) {
		return NULL;
	}
	
	Tree copy = newNode(t->value);
	copy->left = TreeCopy(t->left, depth - 1);
	copy->right = TreeCopy(t->right, depth - 1);
	return copy;
}

static Tree newNode(int value) {
	Tree t = malloc(sizeof(*t));
	if (t == NULL) {
		fprintf(stderr, "Insufficient memory!\n");
		exit(EXIT_FAILURE);
	}
	
	t->value = value;
	t->left = NULL;
	t->right = NULL;
	return t;
}
```

</details>
