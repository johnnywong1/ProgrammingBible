# Find Capital Letter with Largest Alphabetical Order
Given `aAbeedxX`, return `X`

Draft Java solution:
```
public char findLetter(String s){
    char result = '';
    for(Character c : s.toCharArray()){
        if(Character.isUpperCase(c)){
            if(c - 'A' > result - 'A'){
                result = c;
            }
        }
    }
    return result;
}
```
PASSED (custom test cases, including edge cases)