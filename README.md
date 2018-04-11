# extra11
Simple C++ program illustrating AVL tress

## Material used for study
* Princeton notes [Link](http://www.cs.princeton.edu/courses/archive/spr11/cos423/Lectures/BalancedSearchTreesFinal.pdf)
* MIT OpenCourseWare video
* Data Structures Using C++ by Malik
* [Rotations Easily Explained Here](https://www.youtube.com/watch?v=rbg7Qf8GkQ4&t=196s)


## MIT OpenCourseWare
* [YouTube Link](https://youtu.be/FNeL18KsWPc)

### Recall Binary Search Trees (BST's)
* Rooted binary tree
* Each node has
    * key
    * left pointer
    * right pointer
    * parent pointer
* BST property:
    * If you have a node that stores __key x___ then every node in the left subtree stores a key that is less than or equal to x. Every node in the right subtree stores a key that is greater than or equal to __key x__
* Want to know the sorted order?
    * Use __inorder__ traversal
* Functions supported
	* insert
	* delete
	* min
	* max
	* successor
		* Finding next larger node
	* predecessor
		* Finding next smaller node
* Time complexity?
	* Solve in O(h) where h is height of tree		
* What is height?
	* Length of longest path from some root down to a leaf
* What is height of a node?
	* Length of longest path from node to a leaf
	* __max{height(left child), height(right child)} + 1__
* Leaves:
	* Leaves have null pointers
	* Define depth of null pointers to be __-1__. Now __max__ works because find the height of the leaf by taking the max of the 2 children which is __-1__ then add 1 to get __0__
		* This is convenient because do not have to create special cases where the left child does not exist and the right child does not exist by defining the depth of null pointers to be -1

### The Importance of Being Balanced
* If tree is balanced:
	* Time complexity is O(log n)
	* It is balanced if h = O(log n)
* If tree is not balanced
	* Time complexity is O(n)

### AVL Trees
* Definition
	* AVL trees are balanced (h = O(log n))
		* Worst case is when right subtree has height of 1 more than left for every node
	* Require heights of left & right children of every node to differ by at most +- 1
		* By doing this, the tree will stay in O(log n)
* Mathematical formula to prove why we want them balanced. It is to achieve theta(log n)
	* N<sub>h</sub> = min number of nodes in an AVL tree of height h
	* N<sub>h</sub> = 1 + N<sub>h-1</sub> + N<sub>h-2</sub>
		* 1 is the root node
		* N<sub>h-1</sub> is all of the nodes in subtree that is larger of the two
		* N<sub>h-2</sub> is all of the nodes in subtree that is smaller of two
		* Recall:
			* Worst case of an AVL tree is when a subtree has height of 1 more than other subtree
	* N<sub>h</sub> > 1 + 2N<sub>h-2</sub>
		* Want to know when N<sub>h</sub> is greater than something because if I have a larger height then I have more nodes than the subtrees
	* N<sub>h</sub> > 2N<sub>h-2</sub>
		* Got rid of one because it would make the right side of the inequality larger than the left side
	* N<sub>h</sub> = theta(2<sup>h/2</sup>)
	* __h < 2 log n__
		* time complexity is at most some constant times log n
	* Note: Actual worst case time complexity is ~1.440 log n but we theorize 2 log n

* Rotation
	* [Rotations Easily Explained Here (Same as above link)](https://www.youtube.com/watch?v=rbg7Qf8GkQ4&t=196s)
	* __left-rotate(x)__
		* O(1)

				Before:

				| (x) |  |	|
				| --- | --- | --- |
				|  | [A] |
				|  | (y) |	|
				|  |  | [B]	|
				|  |  | [C]	|

				inorder traversal is AxByC

				After:

				| (y) |  |	|
				| --- | --- | --- |
				|  | (x) |
				|  |  | [A]	|
				|  |  | [B]	|
				|  | [C] |	|

				inorder traversal is AxByC
 
* Rotation
* __right-rotate()__
	* For above, go from after to before to complete a right rotation


* insert
	* Algorithm:
		1. simple BST insert
			* this does not preserve the AVL property
		2. fix AVL property from changed node and up
* sort
	* insert n items - theta(n log n)
	* inorder traverlsal is theta(n)
* Abstract Data Type:
	* insert
	* delete
	* min
	* successor
	* predecessor

### Priority Queue implmented by using a heap or AVL tree
* Can use a heap
* Abstract Data Type:
	* insert
	* delete
	* min

### Other Balanced Trees

### Data Structures in General

### Lower Bounds
