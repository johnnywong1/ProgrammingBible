# Valid Palindrome
Draft Java solution (iterative approach):
```
    public boolean isPalindrome(String s) {
        //ignore punctuations
        int left = 0;
        int right = s.length() - 1;
        String sLowercase = s.toLowerCase();
        while(left < right){
            Character a = sLowercase.charAt(left);
            Character b = sLowercase.charAt(right);
            if(!Character.isDigit(a) && !Character.isAlphabetic(a)){
                ++ left;
            }else if(!Character.isDigit(b) && !Character.isAlphabetic(b)){
                -- right;
            }else if(a != b){
                return false;
            }else{
                ++ left;
                -- right;
            }
        }
        return true;
    }
```
PASSED after multiple attempts.
More efficient solution: regex on input string `s`, compare using `StringBuilder.reverse()`
Sample code:
```
    public boolean isPalindrome(String s) {
        s = s.replaceAll("[^a-zA-Z0-9]", "");                                    
        return s.equalsIgnoreCase(new StringBuilder(s).reverse().toString());
    }
```
