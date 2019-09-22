# String Riddle
Replace question marks in a given string with characters other than its left and right neighbors. Sample: `ab?bc?d` -> `abdbcad`. Can use characters from `a` to `z`

Draft Java solution:
```
    public static String riddle(String s){
        StringBuilder result = new StringBuilder();
        Character left = ' ';
        Character right = ' ';
        for(int i = 0; i < s.length(); ++ i){
            if(s.charAt(i) == '?'){
                if(i < s.length() - 1){
                    right = s.charAt(i + 1);
                }
                if(i > 0){
                    left = s.charAt(i - 1);
                }
                for(int j = 97; j < 122; ++ j){
                    if((char)j != left && (char)j != right){
                        result.append(Character.toString((char)j));
                        break;
                    }
                }
            }else{
                result.append(Character.toString(s.charAt(i)));
            }
        }
        return result.toString();
    
```
PASSED custom test cases.

Note: `'a'` = 97, `'A'` = 65
