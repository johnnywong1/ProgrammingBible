https://leetcode.com/explore/featured/card/top-interview-questions-easy/127/strings/881/

# First Unique Char
Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.

## Solution
This iterates through the string and for each character checks if it has another occurence. Interesting method is the lastIndexOf.

```
class Solution {
    public int firstUniqChar(String s) {
        for(int i=0;i<s.length();i++){
            char test = s.charAt(i);
            if(s.indexOf(test)==s.lastIndexOf(test)){
                return i;
            }
        }
        return -1;
    }
}
```
