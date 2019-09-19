# Search in a binary tree
https://leetcode.com/problems/search-in-a-binary-search-tree/

## Solution
Use binary search tree property that everything is sorted
compare values

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
    public TreeNode searchBST(TreeNode root, int val) {
        while(root.val!=val){
            if(root.val>val && root.left!=null){
                root = root.left;
            }else if(root.val<val && root.right!=null){
                root = root.right;
            }
            else{
                return null;
            }
        }
        return root;
    }
}
```
