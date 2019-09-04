# Decode String
Java solution (dual stack + iteration):
```
    public static String decodeString(String s) {
        StringBuilder token = new StringBuilder();
        Stack<Integer> num = new Stack<>();
        Stack<String> str = new Stack<>();
        int cnt = 0;
        for(int i = 0; i < s.length(); ++ i){
            if(s.charAt(i) >= '0' && s.charAt(i) <= '9'){
                //calculate number from string
                cnt = 10 * cnt + (s.charAt(i) - '0');
            }else if(s.charAt(i) == '['){
                num.push(cnt);
                cnt = 0;
                str.push(token.toString());
                token.setLength(0); //clear current token cuz finished
            }else if(s.charAt(i) == ']'){
                int j = num.pop();
                StringBuilder temp = new StringBuilder(str.pop());
                for(int k = 0; k < j; ++ k){
                    temp.append(token);
                }
                token = new StringBuilder(temp);    //reset token
            }else{
                token.append(s.charAt(i));
            }
            //System.out.println(token.toString());
        }
        return token.toString();
    }
```