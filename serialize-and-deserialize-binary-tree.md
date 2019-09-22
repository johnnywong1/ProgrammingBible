# Serialize and Deserialize Binary Tree
Draft Java Solution:
```
    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        //in-order approach
        StringBuilder result = new StringBuilder();
        List<String> temp = new ArrayList();
        serializeUtil(result, root);
        for(String token : temp){
            result.append(token);
            result.append("#");
        }
        return result.toString().substring(0, result.length() - 1);
    }

    private void serializeUtil(List<String> result, TreeNode root){
        if(root == null){
            result.add("null");
            return;
        }else{
            result.add(Integer.toString(root.val));
            serializeUtil(result, root.left);
            serializeUtil(reslut, root.right);
        }
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        
    }
```