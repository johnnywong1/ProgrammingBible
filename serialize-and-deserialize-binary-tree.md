# Serialize and Deserialize Binary Tree
Draft Java Solution:
```
    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        StringBuilder result = new StringBuilder();
        return serializeUtil(root, result).toString();
    }

    private StringBuilder serializeUtil(TreeNode root, StringBuilder result){
        //pre-order approach
        if(root == null){
            result.append("null,");
        }else{
            result.append(String.valueOf(root.val) + ",");
            result = serializeUtil(root.left, result);
            result = serializeUtil(root.right, result);
        }
        return result;
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        String[] nodesArr = data.split(",");
        List<String> nodes = new ArrayList(Arrays.asList(nodesArr));
        return deserializeUtil(nodes);
    }

    private TreeNode deserializeUtil(List<String> nodes){
        if(nodes.get(0).equals("null")){
            nodes.remove(0);
            return null;
        }
        TreeNode root = new TreeNode(Integer.valueOf(nodes.get(0)));
        nodes.remove(0);
        root.left = deserializeUtil(nodes);
        root.right = deserializeUtil(nodes);
        return root;
    }
```
Note: can be extended to binary search tree serialization / deserialization