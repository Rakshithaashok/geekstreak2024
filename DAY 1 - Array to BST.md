## Array to BST [https://www.geeksforgeeks.org/problems/array-to-bst4443/1]

Given a sorted array. Convert it into a Height Balanced Binary Search Tree (BST). Return the root of the BST.

Height-balanced BST means a binary tree in which the depth of the left subtree and the right subtree of every node never differ by more than 1.

Note: The driver code will check the BST, if it is a Height-balanced BST, the output will be true otherwise the output will be false.

## Examples :

Input: nums = [1, 2, 3, 4]

Output: true

Explanation: The preorder traversal of the following BST formed is [2, 1, 3, 4]:

           2
         /   \
        1     3
               \
                4

Input: nums = [1, 2, 3, 4, 5, 6, 7]

Ouput: true

Explanation: The preorder traversal of the following BST formed is [4, 2, 1, 3, 6, 5, 7]:

        4
       / \
      2   6
     / \   / \
    1 3  5 7

Expected Time Complexity: O(n)

Expected Auxillary Space: O(n)

Constraints:
1 ≤ nums.size() ≤ 105
1 ≤ nums[i] ≤ 105

## Code

```
class Solution {
    public Node sortedArrayToBST(int[] nums) {
        // Code here
        if(nums.length == 0)
            return null;
        return createTree(nums, 0, nums.length -1);
    }
    public Node createTree(int[] nums, int startIndex, int endIndex){
        if(startIndex > endIndex)
            return null;
            
        int mid = (startIndex + endIndex) / 2;
        Node node = new Node(nums[mid]);
        node.left = createTree(nums, startIndex, mid-1);
        node.right = createTree(nums, mid+1, endIndex);
        
        return node;
    }
}
```

## Code Explanation

- The approach uses a recursive method to build the BST from the sorted array. 
- The key idea is to use the middle element of the current array segment as the root of the subtree, ensuring the tree remains balanced.
- **Base Case:** If the segment of the array being considered is empty (i.e., startIndex > endIndex), the function returns null, indicating no node should be created.
- **Finding the Middle Element:** The middle element of the current segment (nums[mid]) is chosen as the root of the subtree. This choice ensures that the left and right subtrees are balanced.
- **Recursive Construction:**
- Left Subtree: The function recursively builds the left subtree from the segment of the array before the middle element (startIndex to mid - 1).
- Right Subtree: Similarly, it builds the right subtree from the segment of the array after the middle element (mid + 1 to endIndex).
- **Node Creation:** A new node is created with the value of the middle element, and its left and right children are assigned from the recursive calls.

This approach ensures that the resulting BST is height-balanced, as each node is chosen to evenly distribute the elements on both sides.
