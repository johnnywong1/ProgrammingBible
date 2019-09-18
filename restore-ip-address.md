# Restore IP Address
Draft Java solution:
```
    public static List<String> restoreIpAddresses(String s) {
        //return all possible valid IP combination
        //valid IP combination: A.B.C.D, 0 < x < 255
        //generate all, then check if is valid

        List<String> result = new ArrayList();
        if(s.length() > 12){
            return result;
        }

        for(int i = 1; i < s.length() - 2; ++ i){
            //first dot
            for(int j = i + 1; j < s.length() - 1; ++ j){
                //second dot
                for(int k = j + 1; k < s.length(); ++ k){
                    //third dot
                    StringBuilder IPCandidate = new StringBuilder();
                    IPCandidate.append(s.substring(0, i));
                    IPCandidate.append(".");
                    IPCandidate.append(s.substring(i, j));
                    IPCandidate.append(".");
                    IPCandidate.append(s.substring(j, k));
                    IPCandidate.append(".");
                    IPCandidate.append(s.substring(k));
                    if(isValid(IPCandidate.toString())){
                        result.add(IPCandidate.toString());
                    }
                }
            }
        }
        return result;
    }

    private static boolean isValid(String s){
        if(s.length() > 16){
            return false;
        }
        String[] tokens = s.split("\\.");
        for(String token : tokens){
            if(token.length() > 3 || (token.charAt(0) == '0' && token.length() > 1)){
                return false;
            }
            long i = (long)Integer.parseInt(token);
            if(i > 255 || i < 0){
                return false;
            }
        }
        return true;
    }
```
ACCEPTED AFTER 7 ATTEMPTS. 
Alternative solution (backtracking):
```
    vector<string> restoreIpAddresses(string s) {
        vector<string> res;
        restore(s, 4, "", res);
        return res;
    }
    void restore(string s, int k, string out, vector<string> &res) {
        if (k == 0) {
            if (s.empty()) res.push_back(out);
        }
        else {
            for (int i = 1; i <= 3; ++i) {
                if (s.size() >= i && isValid(s.substr(0, i))) {
                    if (k == 1) restore(s.substr(i), k - 1, out + s.substr(0, i), res);
                    else restore(s.substr(i), k - 1, out + s.substr(0, i) + ".", res);
                }
            }
        }
    }
    bool isValid(string s) {
        if (s.empty() || s.size() > 3 || (s.size() > 1 && s[0] == '0')) return false;
        int res = atoi(s.c_str());
        return res <= 255 && res >= 0;
    }
```