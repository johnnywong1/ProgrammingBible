# Excel Sheet Column Number
Draft Java solution:
```
public int titleToNumber(String s) {
    //capital letter input only
    //ZY -> 701: 701 % 26 = 25, 701 / 26 = 26
    int result = 0;
    int k = 0;
    for(int i = s.toCharArray().length - 1; i >= 0; -- i){
        result += (s.toCharArray()[i] - '0' - 16) * Math.pow(26, k);
        ++ k;
    }
    return result;
}
```
ACCEPTED
