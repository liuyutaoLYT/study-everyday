# 给定两个整数 n 和 k，返回 1 ... n 中所有可能的 k 个数的组合。
先和大家讲一下思路吧，转化成一个树形结构，然后进行一个迭代，一次就往下一层，如果层数和k相同了，就可以返回了。
```
import java.util.ArrayList;
import java.util.List;

/*
 * @lc app=leetcode.cn id=77 lang=java
 *
 * [77] 组合
 */

// @lc code=start
class Solution {
    public static List<List<Integer>> combine(int n, int k) {
        List<Integer>nums = new ArrayList<Integer>();
        List<List<Integer>>result = new ArrayList<List<Integer>>();
        List<Integer>path = new ArrayList<Integer>();
        if(n<k){
            return result;
        }
        for(int i =1;i<=n;i++){
            nums.add(i);
        }
        dfs(nums, 0, path, result, k);
        return result;
    }
    public static void dfs(List<Integer>nums,int currRow,List<Integer>path,List<List<Integer>>result,int k){
        if(currRow == k){
            result.add(new ArrayList(path));
            return;
        }    
        for(int i = 0;i<nums.size();i++){
        	if(path.size()==0 ||(path.size()>0 && nums.get(i)>path.get(path.size()-1))){
                path.add(nums.get(i));
                dfs(nums, currRow+1, path, result, k);
                path.remove(path.size()-1);
            }
        }
    }
}
// @lc code=end


```
