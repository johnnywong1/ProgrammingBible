# Is Subsequence
Draft Java solution:
```
    public boolean isSubsequence(String s, String t) {
        //dual pointe approach
        //t >> s, find s in t
        if(s.length() == 0){
            return true;
        }
        int tPtr = 0;
        int sPtr = 0;
        while(tPtr < t.length() && sPtr < s.length()){
            if(s.charAt(sPtr) == t.charAt(tPtr)){
                ++ sPtr;
                ++ tPtr;
            }else{
                ++ tPtr;
            }
        }
        return sPtr == s.length(); //subsequence found   
    }
```
PASSED  