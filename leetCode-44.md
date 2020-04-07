给定一个字符串 (s) 和一个字符模式 (p) ，实现一个支持 '?' 和 '*' 的通配符匹配。

'?' 可以匹配任何单个字符。
'*' 可以匹配任意字符串（包括空字符串）。
两个字符串完全匹配才算匹配成功。

说明:

s 可能为空，且只包含从 a-z 的小写字母。
p 可能为空，且只包含从 a-z 的小写字母，以及字符 ? 和 *。
示例 1:
```
class Solution {
    public boolean isMatch(String s, String p) {
        int len1 = s.length(), len2 = p.length();
        //辅助数组dp，dp[i][j]表示s(0~i-1)与p(0~j-1)子串是否完全匹配
        boolean[][] dp = new boolean[len1+1][len2+1];
        dp[0][0] = true;//s为空字符串 && p为空字符串
        for(int i = 1; i <= len1; i++)
            dp[i][0] = false;//s不为空，p为空字符串
        for(int j = 1; j <= len2; j++)
            dp[0][j] = (p.charAt(j-1) == '*' && dp[0][j-1]);//s为空字符串，p不为空
    
        //需s和p完全匹配，外层循环对p进行遍历
        for(int j = 1; j <= len2; j++)
            for(int i = 1; i <= len1; i++){
                if(p.charAt(j-1) != '*')
                    //若p[j-1]不为*，需判断s(0~i-2)与p(0~j-2)是否匹配（即dp[i-1][j-1]），并且s[i-1]与p[j-1]匹配
                    dp[i][j] = dp[i-1][j-1] && (s.charAt(i-1) == p.charAt(j-1) || '?' == p.charAt(j-1));
                else
                    //若p[j-1]为*,需判断s(0~i-2)与p(0~j-1)是否匹配（当前*匹配s[i-1]及之前部分字符）
                    //或者判断s(0~i-1)与p(0~j-2)是否匹配(当前*匹配空字符串)
                    dp[i][j] = dp[i-1][j] || dp[i][j-1];
            }
    
        return dp[len1][len2];
    }
}
```
解题思路：动态规划
