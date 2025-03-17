560 和为K的子数组

https://leetcode.cn/problems/subarray-sum-equals-k/solutions/2781031/qian-zhui-he-ha-xi-biao-cong-liang-ci-bi-4mwr/



``` java
class Solution {
    public int subarraySum(int[] nums, int k) {
        int ans = 0;
        int s = 0;
        Map<Integer, Integer> count = new HashMap<>(nums.length + 1);
        count.put(0, 1);
        for(int x : nums){
            // 计算前缀和
            s += x;
            // 相当于是获取s[j]-k的个数，也就是s[i]的个数
            ans += count.getOrDefault(s-k, 0);
            // 如果没有 就将1放入
            // 如果有 就是旧值+1
            count.merge(s,1,Integer::sum);
        }
        return ans;
    }
}
```

