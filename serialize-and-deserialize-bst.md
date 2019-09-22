# Serialize and Deserialize Binary Search Tree
Draft Java solution:
```
    // Encodes a tree to a single string.
    private static StringBuilder postorder(TreeNode root, StringBuilder sb){
        if(root == null){
            return sb;
        }
        postorder(root.left, sb);
        postorder(root.right, sb);
        sb.append(root.val);
        sb.append(' ');
        return sb;
    }

    public static String serialize(TreeNode root){
        if(root == null){
            return " ";
        }
        StringBuilder sb = postorder(root, new StringBuilder());
        return sb.toString().substring(0, sb.length() - 1);
    }

    public static TreeNode deserialize(String data){
        if(data.isEmpty()){
            return null;
        }
        LinkedList<Integer> nums = new LinkedList();
        for(String s : data.split("\\s+")){
            nums.add(Integer.valueOf(s));
        }
        return helper(Integer.MIN_VALUE, Integer.MAX_VALUE, nums);
    }

    private static TreeNode helper(Integer lower, Integer upper, LinkedList<Integer> nums){
        if(nums.isEmpty()){
            return null;
        }
        int val = nums.peekLast();
        if(val < lower || val > upper){
            return null;
        }
        nums.removeLast();
        TreeNode root = new TreeNode(val);
        root.right = helper(val, upper, nums);
        root.left = helper(lower, val, nums);
        return root;
    }
```