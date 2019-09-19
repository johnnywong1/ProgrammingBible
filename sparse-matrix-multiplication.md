# Sparse Matrix Multiplication
Draft Java solution:
```
    public int[][] multiply(int[][] A, int[][] B) {
        //approach: do not perform multiplication if 0 encountered
        int[][] result = new int[A.length][B[0].length];
        for(int i = 0;)
    }
```
FAILED.
Passing solution:
```
    public int[][] multiply(int[][] A, int[][] B){
        //approach: do not peroform multiplication if encountered 0
        int[][] result = new int[A.length][B[0].length];
        for(int i = 0; i < A.length; ++ i){
            for(int j = 0; j < B[0].length; ++ j){
                for(int k = 0; k < B.length; ++ k){
                    if(A[i][k] == 0 || B[k][j] == 0){
                        continue;   //skip multiplication
                    }
                    result[i][j] += A[i][k] * B[k][j];
                }
            }
        }
        return result;
    }
```
More efficient solution:
```
//limitation: requires custom Point class in Java
class Solution {
public:
    vector<vector<int>> multiply(vector<vector<int>>& A, vector<vector<int>>& B) {
        vector<vector<int>> res(A.size(), vector<int>(B[0].size()));
        vector<vector<pair<int, int>>> v(A.size(), vector<pair<int,int>>());
        for (int i = 0; i < A.size(); ++i) {
            for (int k = 0; k < A[i].size(); ++k) {
                if (A[i][k] != 0) v[i].push_back({k, A[i][k]});
            }
        }
        for (int i = 0; i < A.size(); ++i) {
            for (int k = 0; k < v[i].size(); ++k) {
                int col = v[i][k].first;
                int val = v[i][k].second;
                for (int j = 0; j < B[0].size(); ++j) {
                    res[i][j] += val * B[col][j];
                }
            }
        }
        return res;
    }
};
```

