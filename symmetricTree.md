# Symmetric Tree
https://leetcode.com/explore/featured/card/top-interview-questions-easy/94/trees/627/
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

## Solution
Thanks to Dennis
Recursively check if the values are identical



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
    public boolean isSymmetric(TreeNode root) {
        return helper(root,root);
    }
    public boolean helper(TreeNode left, TreeNode right){
        if(left==null && right==null){
            return true;
        }
        if(left==null || right==null || left.val!=right.val){
            return false;
        }
        return helper(left.left,right.right) && helper(left.right,right.left);
    }
}
```
