# Permutations
Draft Java solution:
```
    public List<List<Integer>> permute(int[] nums) {
        //input is distinct
        //backtrack approach
        List<List<Integer>> result = new ArrayList();
        backtrack(result, nums, 0);
        return result;
    }

    private void backtrack(List<List<Integer>> result, int[] nums, int first){
        if(first == nums.length - 1){
            //end backtrack
            List<Integer> temp = new ArrayList();
            for(Integer i : nums){
                temp.add(i);
            }
            result.add(new ArrayList(temp));
            return;
        }
        for(int i = first; i < nums.length; ++ i){
            swap(nums, i, first);
            backtrack(result, nums, first + 1);
            swap(nums, first, i);
        }
    }

    private void swap(int[] nums, int i, int j){
        int temp = nums[j];
        nums[j] = nums[i];
        nums[i] = temp;
    }
```
PASSED with 1 attempt