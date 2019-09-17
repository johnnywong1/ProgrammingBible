# Reverse Words in a String
Draft Java solution:
```
public String reverseWords(String s) {
    //remove redundant spaces + reverse words with punctuations
    //stack approach
    //preprocess input
    StringBuilder result = new StringBuilder();
    if(s.length() == 0 || s.equals(" ") || s.trim().equals("")){
        return result.toString();
    }
    
    Stack<String> stack = new Stack();
    String[] tokens = s.split("");

    for(String token : tokens){
        if(!token.equals(" ")){
                    //deep clean
            while(token.charAt(0) == ' ' || token.charAt(token.length() - 1) == ' '){
                token.trim();   //preprocess token
            }
            stack.push(token);
        }
    }        

    while(!stack.isEmpty()){
        result.append(stack.pop());
        result.append(" ");
    }

    return result.toString().substring(0, result.length() - 1);   //remove last trailing space
}
```
PASSED ALL TEST CASES. NUMBER OF ATTEMPTS: 9