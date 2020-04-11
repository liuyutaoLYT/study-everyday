给定一个可包含重复数字的序列，返回所有不重复的全排列。

示例:

输入: [1,1,2]
输出:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
```
class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        int len = nums.length;
        boolean[]used = new boolean[len];
        List<Integer>path = new ArrayList<Integer>();
        Set<List<Integer>>result = new HashSet<List<Integer>>();
        dfs(nums,len,0,path,used,result);
        return new ArrayList<>(result);
    }
    public void dfs (int []nums,int len,int depth,List<Integer>path,boolean[]used,Set<List<Integer>>result){
        if(len == depth){
            result.add(new ArrayList<Integer>(path));
            return;
        }
        for(int i = 0;i<len;i++){
            if(!used[i]){
                used[i] = true;
                path.add(nums[i]);
                dfs(nums,len,depth+1,path,used,result);
                used[i] = false;
                path.remove(path.size()-1);
            }
        }
        
    }
}
```
