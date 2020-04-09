# 问题
给定一个非空且只包含非负数的整数数组 nums, 数组的度的定义是指数组里任一元素出现频数的最大值。

你的任务是找到与 nums 拥有相同大小的度的最短连续子数组，返回其长度。

示例 1:

输入: [1, 2, 2, 3, 1]
输出: 2
解释: 
输入数组的度是2，因为元素1和2的出现频数最大，均为2.
连续子数组里面拥有相同度的有如下所示:
[1, 2, 2, 3, 1], [1, 2, 2, 3], [2, 2, 3, 1], [1, 2, 2], [2, 2, 3], [2, 2]
最短连续子数组[2, 2]的长度为2，所以返回2.
示例 2:

输入: [1,2,2,3,1,4,2]
输出: 6
注意:

nums.length 在1到50,000区间范围内。
nums[i] 是一个在0到49,999范围内的整数。

# 代码(未通过，算法太繁琐，定义数组大，超时)
```
class Solution {
public:
     
    int findShortestSubArray(vector<int>& nums) {
        int a[50000]={0};
        vector<int>b(nums);
        int len=b.size();
        sort(b.begin(),b.end());
        int now=1;
        int max=1;
        for(int i=0;i<nums.size()-1;i++)
        {
            if(b[i]==b[i+1])
            {
                now=now+1;
                if(now>max)
                {
                    max=now;  
                }
        }
        else
        {
            now=1;
        }
        }
        int min=nums.size();
        int n=0;
        for(int i=0;i<nums.size();i++)
        {
            a[50000]={0};
            for(int j=i;j<nums.size();j++)
            {
                a[nums[j]]+=1;
                if(a[nums[j]]==max&&j-i+1<min)
                {
                    min=j-i+1;
                    break;
                }
            }
        }
        return min;
    }
};
# 代码（参考题解）
