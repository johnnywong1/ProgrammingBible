# Combination Sum 
Java backtracking approach:
```
    public static List<List<Integer>> combinationSum(int[] candidates, int target) {
        //unique combinations that lead to sum
        //DFS approach
        List<List<Integer>> result = new ArrayList<>();
        List<Integer> temp = new ArrayList<>();
        Arrays.sort(candidates);
        backtrack(result, temp, candidates, 0, target);
        return result;
    }

    public static void backtrack(List<List<Integer>> result, List<Integer> temp, int[] candidates, int i, int target){
        if(target == 0){
            //save an argument!
            result.add(new ArrayList<>(temp));
            return; //end searching
        }
        for(int j = i; j < candidates.length; ++ j){
            if(j > i && candidates[j] == candidates[j - 1]){
                continue;   //skip duplicates
            }
            if(candidates[j] <= target){
                temp.add(candidates[j]);
                DFS(result, temp, candidates, j, target - candidates[j]);
                //System.out.println(temp.get(temp.size() - 1));
                temp.remove(temp.size() - 1);
            }
        }
    }
```