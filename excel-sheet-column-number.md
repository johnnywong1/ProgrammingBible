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

better solution (handles overflow for test case CFDGSXM):
```
class Solution {
public:
    int titleToNumber(string s) {
        int n = s.size();
        int res = 0;
        int tmp = 1;
        for (int i = n; i >= 1; --i) {
            res += (s[i - 1] - 'A' + 1) * tmp; 
            tmp *= 26;
        }
        return res;
    }
};
```