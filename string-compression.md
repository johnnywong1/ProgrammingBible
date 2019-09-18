# String Compression
Draft Java solution:
```
    public int compress(char[] chars) {
        int anchor = 0;
        int ptr = 0;
        int cnt = 0;
    }
```
FAILED
Correct solution: three pointers, anchor + write + read
```
public int compress(char[] chars){
    int anchor = 0;
    int write = 0;
    for(int read = 0; read < chars.length; ++ read){
        if(read + 1 == chars.length || chars[read + 1] != chars[read]){
            chars[write ++] = chars[anchor];
            if(read > anchor){
                for(char c: ("" + (read - anchor + 1)).toCharArray()){
                    chars[write ++] = c;
                }
            }
            anchor = read + 1;
        }
    }
    return write;
}
```