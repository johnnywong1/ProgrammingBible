# Valid Parentheses
https://leetcode.com/problems/valid-parentheses/submissions/

## Solution
push open parentheses, if its closing make sure that the top of the stack is the right corresponding parentheses

```
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stk = new Stack<Character>();
        for(int i=0;i<s.length();i++){
            if(s.charAt(i)=='(' || s.charAt(i)=='{' || s.charAt(i)=='['){
                stk.push(s.charAt(i));
            }
            else if(s.charAt(i)==')'){
                if(stk.empty() || stk.peek()!='('){
                    return false;
                }else{
                    stk.pop();
                }
            }
            else if(s.charAt(i)=='}'){
                if(stk.empty() || stk.peek()!='{'){
                    return false;
                }else{
                    stk.pop();
                }
            }
            else if(s.charAt(i)==']'){
                if(stk.empty() || stk.peek()!='['){
                    return false;
                }else{
                    stk.pop();
                }
            }
        }
        return stk.empty();
    }
}
```
