# Symmetric Tree
https://leetcode.com/explore/featured/card/top-interview-questions-easy/94/trees/627/
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

## Solution
Thanks to Dennis
Recursively check if the values are identical
Runtime: 0 ms
Memory Usage: 37.1 MB


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

## Solution 2
Push each half into a list and then later check the lists.
Runtime: 2 ms
Memory Usage: 38.6 MB

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
        List<Integer> left = new LinkedList<Integer>();
        List<Integer> right = new LinkedList<Integer>();
        
        if(root!=null){
            getLeft(left, root.left);
            getRight(right, root.right);
        }
        
        if(left.equals(right)){ // for linked lists, use .equals()
            return true;
        }
        else{
            return false;
        }
    }
    
    private void getLeft(List<Integer> left, TreeNode root){
        if(root!=null){
            left.add(root.val);
            if(root.left==null){
                left.add(-1);
            }else{
                getLeft(left,root.left);
            }
            if(root.right==null){
                left.add(-1);
            }else{
                getLeft(left,root.right);
            }   
        }
        
    }
    
    private void getRight(List<Integer> right, TreeNode root){
        if(root!=null){
            right.add(root.val);
            if(root.right==null){
                right.add(-1);
            }else{
                getRight(right,root.right);
            }
            if(root.left==null){
                right.add(-1);
            }else{
                getRight(right,root.left);
            }   
        }
    }  
}
```
