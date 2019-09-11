# Maximum Depth of Binary Tree
https://leetcode.com/explore/featured/card/top-interview-questions-easy/94/trees/555/
## Solution
Recursive, add by one for each left and right and keep track of the max, 


```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public int maxDepth(TreeNode root) { // Depth First Search
        if(root==null){
            return 0;
        }
        
        int left = maxDepth(root.left);
        int right = maxDepth(root.right);
        
        int depth = left + 1;
        if(left<right){
            depth = right + 1;
        }
        return depth;
    }
}

// Depth first uses stack
// Breadth first uses queue

```
