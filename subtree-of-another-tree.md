# Subtree of another tree
This was in my Online Assessment for Amazon.

## Solution
two recursive calls, one for searching for the similar root and then one for verifying that it is true.


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
    public boolean isSubtree(TreeNode s, TreeNode t) {
        if(s==null)return false;//dumbo base case
        if(verifySubtree(s,t)) return true;//checking a lot of things
        return isSubtree(s.left,t) || isSubtree(s.right,t);//recursivly searching for root match
    }
    
    public boolean verifySubtree(TreeNode s, TreeNode t){
        if(s==null && t==null) return true;//as children, nodes are both empty
        if(s==null || t==null) return false;//IMBALANCE NOT OK
        if(s.val!=t.val)return false;//after checking they are balanced, make sure
        return verifySubtree(s.left,t.left) && verifySubtree(s.right,t.right);//recursive, strict
    }
}
```
