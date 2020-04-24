```
/*
 * @lc app=leetcode.cn id=56 lang=java
 *
 * [56] 合并区间
 */

// @lc code=start
class Solution {
    public int[][] merge(int[][] intervals) {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        if (intervals.length < 2) {
            return intervals;
        }
        Arrays.sort(intervals, Comparator.comparingInt(o -> o[0]));
        for(int i = 0;i<intervals.length;i++){
            int left = intervals[i][0];
            int right = intervals[i][1];
            if(result.size()>0 && right<=result.get(result.size()-1).get(1) && left>=result.get(result.size()-1).get(0)){
                continue;
            }
            int maxright = intervals[i][1];
            int minleft = intervals[i][0];
            for(int j = i;j<intervals.length;j++){
                if((maxright>=intervals[j][0] && intervals[j][1]>=maxright) || (minleft>=intervals[j][0] && minleft<=intervals[j][1])){
                    if(intervals[j][1]>=maxright){
                        maxright = intervals[j][1];
                    }
                    if(minleft>=intervals[j][0]){
                        minleft = intervals[j][0];
                    }
                }
            }
            List<Integer>oneResult = new ArrayList<Integer>();
            oneResult.add(minleft);
            oneResult.add(maxright);
            result.add(oneResult);
        }
        int [][]res = new int[result.size()][2];
        for(int i=0;i<result.size();i++){
            res[i][0] = result.get(i).get(0);
            res[i][1] = result.get(i).get(1); 
        }
        return res;
    }
}
// @lc code=end

//贪心算法啊啊啊啊啊啊啊啊
```
