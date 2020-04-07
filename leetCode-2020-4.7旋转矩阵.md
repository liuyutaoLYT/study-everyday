题目：将一个矩阵顺时针九十度旋转
```
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length-1;
        for(int i=0;i<=n/2; i++){
            for(int j=i;j<n-i;j++){
                int t = matrix[i][j];
                matrix[i][j] = matrix[n-j][i];
                matrix[n-j][i] = matrix[n-i][n-j];
                matrix[n-i][n-j] = matrix[j][n-i];
                matrix[j][n-i] = t;
            }
        }
    }
}
```
最外面是一圈 第二层是一圈
