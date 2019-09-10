# Combination Sum III
Java backtracking approach:
```
    public static List<List<Integer>> combinationSum3(int k, int n) {
        //1 - 9 only, no duplicates
        //less efficient approach (based on combination sum II)
        List<List<Integer>> result = new ArrayList<>();
        List<Integer> temp = new ArrayList<>();
        int[] candidates = {1, 2, 3, 4, 5, 6, 7, 8, 9};
        backtrack(result, temp, 0, n, candidates, k);
        return result;
    }

    private static void backtrack(List<List<Integer>> result, List<Integer> temp, int start, int target, int[] candidates, int k){
        if(target == 0){
            if(temp.size() == k){
                result.add(new ArrayList<>(temp));
            }
            return; //end searching
        }
        for(int i = start; i < candidates.length; ++ i){
            //check duplicates
            if(i > start && candidates[i] == candidates[i - 1]){
                continue;
            }
            if(candidates[i] <= target){
                temp.add(candidates[i]);
                backtrack(result, temp, i + 1, target - candidates[i], candidates, k);
                temp.remove(temp.size() - 1);
            }
        }
    }
```