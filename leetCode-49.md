题目：给定一个字符串数组，将字母异位词组合在一起。字母异位词指字母相同，但排列不同的字符串。

示例:

输入: ["eat", "tea", "tan", "ate", "nat", "bat"]
输出:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```
/*
 * @lc app=leetcode.cn id=49 lang=java
 *
 * [49] 字母异位词分组
 */

// @lc code=start
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        if(strs.length==0){
            return new ArrayList();
        }
        Map<String,List<String>> result = new HashMap<String,List<String>>();
        for(String s:strs){
            char[] charArray = s.toCharArray();
            Arrays.sort(charArray);
            String a = String.valueOf(charArray);
            if(!result.containsKey(a)){
                result.put(a, new ArrayList());
            }
            result.get(a).add(s);
            
        }
        return new ArrayList(result.values());        
    }
}
// @lc code=end
```
