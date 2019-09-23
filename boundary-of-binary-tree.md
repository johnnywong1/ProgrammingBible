# Boundary of Binary Tree
Draft Java solution:
```
    public List<Integer> boundaryOfBinaryTree(TreeNode root) {
        //bottom-up approach: inorder travesal
        List<Integer> result = new ArrayList();
        util(result, root);
        return result;
    }

    private void util(List<Integer> result, TreeNode root){
        if(root == null){
            return;
        }else{
            util(result, root.left);
            if(root.left == null || root.right == null){
                result.add(root.val);
            }
            util(result, root.right);
        }
    }
```
FAILED

PASSING solution:
```
    public List<Integer> boundaryOfBinaryTree(TreeNode root){
        List<Integer> result = new ArrayList();
        if(root == null){
            return result;
        }
        if(root.left == null && root.right == null){
            result.add(root.val);
            return result;
        }
        if(root.left == null){
            result.add(root.val);
        }else{
            getLeftBoundary(root, result);
            result.remove(result.size() - 1);
        }
        getLeafBoundary(root, result);
        if(root.right != null){
            result.remove(result.size() - 1);   //remove duplicate
            getRightBoundary(root, result);
            result.remove(result.size() - 1);   //remove duplicate
        }
        return result;
    }

    private void getLeftBoundary(TreeNode root, List<Integer> result){
        if(root != null){
            result.add(root.val);
            if(root.left != null){
                getLeftBoundary(root.left, result);
            }else{
                getLeftBoundary(root.right, result);
            }
        }
    }

    private void getRightBoundary(TreeNode root, List<Integer> result){
        if(root != null){
            if(root.right != null){
                getRightBoundary(root.right, result);
            }else{
                getRightBoundary(root.left, result);
            }
            result.add(root.val);
        }
    }

    private void getLeafBoundary(TreeNode root, List<Integer> result){
        if(root != null){
            if(root.left == null && root.right == null){
                result.add(root.val);
            }else{
                getLeafBoundary(root.left, result);
                getLeafBoundary(root.right, result);
            }
        }
    }
```
Note: need to reverse adding sequence in `getRightBoundary()` + handle edge cases such as `[]` and `[1]` 