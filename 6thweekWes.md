# 问题
给定一个未经排序的整数数组，找到最长且连续的的递增序列。

示例 1:

输入: [1,3,5,4,7]
输出: 3
解释: 最长连续递增序列是 [1,3,5], 长度为3。
尽管 [1,3,5,7] 也是升序的子序列, 但它不是连续的，因为5和7在原数组里被4隔开。 
示例 2:

输入: [2,2,2,2,2]
输出: 1
解释: 最长连续递增序列是 [2], 长度为1。
注意：数组长度不会超过10000。

# 代码
```
class Solution {
public:
    int findLengthOfLCIS(vector<int>& nums) {
        int now=0;
        int max=1;
        int k=1;
        if(nums.size()==0)
        return 0;
        else{
        for(int i=0;i<nums.size()-1;i++)
        {
            if(nums[i]<nums[i+1])
            {
                k=k+1;
                if(k>max)
                max=k;
            }
            else
            {
                k=1;
            }
        }
        return max;
    }}
};
```
# 笔记
1.问题较为简单，就去尝试中等的这类问题，发现遇到很多困难，准备明天专门研究一下那个题及相关算法
2.这个题中最大值要及时更新。
