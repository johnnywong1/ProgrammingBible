# String Compression
Given an array of characters, compress it in-place.

The length after compression must always be smaller than or equal to the original array.

Every element of the array should be a character (not int) of length 1.
After you are done modifying the input array in-place, return the new length of the array.

**Follow up:**
Could you solve it using only O(1) extra space?


```Input:
["a","a","b","b","c","c","c"]

Output:
Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]

Explanation:
"aa" is replaced by "a2". "bb" is replaced by "b2". "ccc" is replaced by "c3".
```

```Input:
["a"]

Output:
Return 1, and the first 1 characters of the input array should be: ["a"]

Explanation:
Nothing is replaced.
```

```
Input:
["a","b","b","b","b","b","b","b","b","b","b","b","b"]

Output:
Return 4, and the first 4 characters of the input array should be: ["a","b","1","2"].

Explanation:
Since the character "a" does not repeat, it is not compressed. "bbbbbbbbbbbb" is replaced by "b12".
Notice each digit has it's own entry in the array.
```
The Solution to do this in Linear Time and Constant Time is 2 pointers.

## Python Implementation
```
class Solution(object):
    def compress(self, chars):
        left = i = 0
        while i < len(chars):
            char, length = chars[i], 1
            while (i + 1) < len(chars) and char == chars[i + 1]:
                length, i = length + 1, i + 1
            chars[left] = char
            if length > 1:
                len_str = str(length)
                chars[left + 1:left + 1 + len(len_str)] = len_str
                left += len(len_str)
            left, i = left + 1, i + 1
        return left
```
## Java Implementation
```
class Solution {
    public int compress(char[] chars) {
        int cons = 0;
        int index = 0;
        for (int i = 0; i < chars.length; i++){
            cons++;
            if(i+1 == chars.length||chars[i] != chars[i+1]){
                chars[index++] = chars[i];
                if(cons != 1){
                    String str = String.valueOf(cons);
                    for (int j = 0; j<str.length(); j++){
                        chars[index] = str.charAt(j);
                        index++;
                    }
                }
                cons = 0;
            }
        }
        
        return index;
    }
}
```
