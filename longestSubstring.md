# Longest Substring Without Repeating Characters
https://leetcode.com/problems/longest-substring-without-repeating-characters/submissions/

## Solution
Make a hashmap of all the characters
If a character already exists, then restart the next string 

```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashMap<Character, Integer> hmap = new HashMap<Character, Integer>();
        int max = 0;
        for(int i=0, j=0;i<s.length();i++){
            if(hmap.containsKey(s.charAt(i))){
                j = Math.max(j, hmap.get(s.charAt(i))+1);
            }
            hmap.put(s.charAt(i),i);
            max = Math.max(max, i-j+1);
        }
        return max;
    }
}
```
