# Permutations II
Draft Java solution:
```
    public List<List<Integer>> permuteUnique(int[] nums) {
        //unique permutations only
        //backtrack (with duplicate checking) approach
        List<List<Integer>> result = new ArrayList();
        Arrays.sort(nums);  //prep for duplicate checking
        backtrack(result, nums, 0);
        return result;
    }

    private void backtrack(List<List<Integer>> result, int[] nums, int first){  
        if(first == nums.length - 1){
            List<Integer> temp = new ArrayList();
            for(Integer i : nums){
                temp.add(i);
            }
            result.add(new ArrayList(temp));
            return;
        }
        for(int i = first; i < nums.length; ++ i){
            //duplicate checking
            if(i < nums.length - 1 && nums[i + 1] == nums[i]){
                continue;
            }
            swap(nums, i, first);
            backtrack(result, nums, first + 1);
            swap(nums, first, i);
        }
    }

    private void swap(int[] nums, int i, int j){
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
```
FAILED.

Correct solution (with duplicate checking + visited memory):
```
    public List<List<Integer>> permuteUnique(int[] nums) {
        //unique permutations only
        //backtrack (with duplicate checking) approach
        Set<List<Integer>> result = new HashSet();
        Arrays.sort(nums);  //prep for duplicate checking
        int[] visited = new int[nums.length];
        backtrack(result, nums, 0, visited);
        return new ArrayList(result);
    }

    private void backtrack(Set<List<Integer>> result, int[] nums, int first, int[] visited){  
        if(first == nums.length - 1){
            List<Integer> temp = new ArrayList();
            for(Integer i : nums){
                temp.add(i);
            }
            result.add(new ArrayList(temp));
            return;
        }
        for(int i = first; i < nums.length; ++ i){
            //duplicate checking
            if(visited[i] == 1){
                continue;
            }
            if(i < nums.length - 1 && nums[i + 1] == nums[i]){
                continue;
            }
            swap(nums, i, first);
            backtrack(result, nums, first + 1, visited);
            swap(nums, first, i);
        }
    }

    private void swap(int[] nums, int i, int j){
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
```
Refer to https://www.cnblogs.com/grandyang/p/4359825.html