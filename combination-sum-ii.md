# Combination Sum II
Java DFS approach:
```
    public static List<List<Integer>> combinationSum2(int[] candidates, int target) {
        //number re-use not allowed
        List<List<Integer>> result = new ArrayList<>();
        List<Integer> temp = new ArrayList<>();
        Arrays.sort(candidates);
        DFS(result, temp, 0, target, candidates);
        return result;
    }

    private static void DFS(List<List<Integer>> result, List<Integer> temp, int i, int target, int[] candidates){
        if(target == 0){
            result.add(new ArrayList<>(temp));
            return; //end searching
        }
        for(int j = i; j < candidates.length; ++ j){
            //check duplicate
            if(j > i && candidates[j] == candidates[j - 1]){
                continue;
            }

            if(candidates[i] <= target){
                temp.add(candidates[j]);
                DFS(result, temp, j + 1, target - candidates[j], candidates);
                temp.remove(temp.size() - 1);
            }

        }
    }
```