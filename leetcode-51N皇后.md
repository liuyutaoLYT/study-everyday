```
import java.util.List;

/*
 * @lc app=leetcode.cn id=51 lang=java
 *
 * [51] N皇后
 */

// @lc code=start
class Solution {
    private List<List<String>> res = new ArrayList<>();
    public List<List<String>> solveNQueens(int n) {
        char[][] board = new char[n][n];
        // 初始化所有位置为 .
        for (char[] rowChars : board){
            Arrays.fill(rowChars, '.');
        } 
        // 回溯法
        backTrack(board, 0);
        // 返回
        return res;
    }
    public void backTrack(char[][]board,int row){
        if(row==board.length){
            res.add(charArrayToList(board));
            return;
        }
        for(int i = 0;i<board.length;i++){
            if(!valid(board,row,i)){
                continue;
            }
            board[row][i] ='Q';
            backTrack(board,row+1);
            board[row][i] = '.';
        }
    }
    private boolean valid(char[][] board, int row, int col) {
        // 判断这一列，是否有其他皇后，因为之后的行还未试探，所以这里只需判断这一行之上的行的这一列
        for (int k = 0; k < row; k++)
            if (board[k][col] == 'Q')
                return false;
        // 判断左上方向上是否存在 Q
        for (int i = row - 1, j = col - 1; i >= 0 && j >= 0; i--, j--) {
            if (board[i][j] == 'Q')
                return false;
        }
        // 判断右上方向上是否存在 Q
        for (int i = row - 1, j = col + 1; i >= 0 && j < board.length; i--, j++) {
            if (board[i][j] == 'Q')
                return false;
        }
        return true;
    }
    private List<String> charArrayToList(char[][] board) {
        ArrayList<String> list = new ArrayList<>();
        for (char[] rowChars : board)
            list.add(String.valueOf(rowChars));
        return list;
    }

}
// @lc code=end


```
