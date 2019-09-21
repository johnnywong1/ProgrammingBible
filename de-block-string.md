# De-block String

Process a string so there are no blocks of same character of length > 3

Draft Java solution:
```
public String deblockString(String s){
    StringBuilder result = new StringBuilder();
    int cnt = 0;
    StringBuilder temp = new StringBuilder();
    for(int i = 0; i < s.length(); ++ i){
        if(i > 0 && s.charAt(i) != s.charAt(i - 1)){
            //reset count
            cnt = 0;
            result.append(temp.toString());
            temp = new StringBuilder(Character.toString(s.charAt(i)));
        }else{
            if(cnt < 2){
                temp.append(s.charAt(i));
            }
            ++ cnt;
        }
    }
    result.append(temp.toString());
    return result.toString();
}
```
PASSED (custom test cases, including edge case)