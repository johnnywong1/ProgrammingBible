# Generate Parentheses
Backtracking (more efficient) approach:
```
    public static List<String> generateParenthesis(int n) {
        //backtrack approach
        List<String> result = new ArrayList<>();
        backtrack(0, 0, n, "", result);
        return result;
    }

    private static void backtrack(int open, int close, int n, String curr, List<String> result){
        if(curr.length() == 2 * n){
            result.add(curr);
            return; //end recursion. Solution set full
        }
        if(open < n){
            backtrack(open + 1, close, n, curr + "(", result);
        }
        if(close < open){
            backtrack(open, close + 1, n, curr + ")", result);
        }
    }
```