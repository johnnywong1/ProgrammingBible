# Valid Parentheses
https://leetcode.com/problems/valid-parentheses/submissions/

## Solution
push open parentheses, if its closing make sure that the top of the stack is the right corresponding parentheses

```
class Solution {
    public boolean isValid(String s) {
        // use stack, push open brackets and pop closed brackets
        // if pop does not return exactly the opposite, return false
        Stack<Character> stk = new Stack<Character>();
        for(int i=0;i<s.length();i++){
            if(s.charAt(i)=='(' || s.charAt(i)=='[' || s.charAt(i)=='{')
                stk.push(s.charAt(i));
            else if(s.charAt(i)==')'){
                if(stk.empty()==false&&stk.peek()=='(')
                    stk.pop();
                else{
                    return false;
                }
            }
            else if(s.charAt(i)=='}'){
                if(stk.empty()==false&&stk.peek()=='{')
                    stk.pop();
                else{
                    return false;
                }
            }
            else if(s.charAt(i)==']'){
                if(stk.empty()==false&&stk.peek()=='[')
                    stk.pop();
                else{
                    return false;
                }
            }
        }
        return stk.empty();
    }
}
```

Better Version
```
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<Character>();
        for (char c : s.toCharArray()) {
            if (c == '(') // just have corresponding values in the stack,
                stack.push(')'); // to match with later
            else if (c == '{')
                stack.push('}');
            else if (c == '[')
                stack.push(']');
            else if (stack.isEmpty() || stack.pop() != c) 
                //when other conditionals are not met, it means closing bracket and it must match the stack
                return false;
        }
        return stack.isEmpty();
    }
}
```
