```
import java.util.List;

/*
 * @lc app=leetcode.cn id=54 lang=java
 *
 * [54] 螺旋矩阵
 */

// @lc code=start
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> result = new ArrayList<Integer>();
        if(matrix.length==0){
            return result;
        }
        int row1 = 0;
        int row2 = matrix.length-1;
        int col1 = 0;
        int col2 = matrix[0].length-1;
        while(row1<=row2 && col1<=col2){
            if(row1 == row2 && col1==col2){
                result.add(matrix[row1][col2]);
                return result;
            }
            if(row1==row2 && col1<=col2){
                for(int o = col1;o<=col2;o++){
                    result.add(matrix[row1][o]);
                }
                return result;
            }
            if(col1==col2 && row1<=row2){
                for(int q = row1;q<=row2;q++){
                    result.add(matrix[q][col1]);
                }
                return result;
            }
            for(int i = col1;i<col2;i++){
                result.add(matrix[row1][i]);

            }
            for(int j = row1;j<row2;j++){
                result.add(matrix[j][col2]);
            }
            for(int k = col2;k>col1;k--){
                result.add(matrix[row2][k]);
            }
            for(int l = row2;l>row1;l--){
                result.add(matrix[l][col1]);
            }
            col1++;
            row1++;
            col2--;
            row2--;
        }
        return result;
    }
}
// @lc code=end
//旋转矩阵 和上次那个顺时针转九十度的矩阵特别相似，也是一层一层循环的；

```
