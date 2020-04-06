# 665.非递减数列

给你一个长度为 n 的整数数组，请你判断在 最多 改变 1 个元素的情况下，该数组能否变成一个非递减数列。

我们是这样定义一个非递减数列的： 对于数组中所有的 i (1 <= i < n)，总满足 array[i] <= array[i + 1]。

 

示例 1:

输入: nums = [4,2,3]
输出: true
解释: 你可以通过把第一个4变成1来使得它成为一个非递减数列。
示例 2:

输入: nums = [4,2,1]
输出: false
解释: 你不能在只改变一个元素的情况下将其变为非递减数列。
 

说明：

1 <= n <= 10 ^ 4
- 10 ^ 5 <= nums[i] <= 10 ^ 5
# c++代码
```
class Solution {
public:
    bool checkPossibility(vector<int>& nums) {
        if(nums.size()==2)
        return true;
        else {
            int p=0;
            for(int i=0;i<nums.size();i++)
            {
                int w=0;
                for(int j=0;j<nums.size()-1;j++)
                {
                    int k=0;
                    if(j==i)
                    {
                        continue;
                    }
                    else if(j==i-1&&j!=nums.size()-2)
                    { 
                    if(nums[j]>nums[j+2])
                    {w=1;
                    }}
                    else if(j==i-1&&j==nums.size()-2)
                    {
                        continue;
                    }
                    else{
                        if(nums[j]>nums[j+1])
                        {
                            w=1;
                            break;
                            
                        }
                    }}
                    if(w==0)
                    {p=1;
                    break;}
            }
                if(p==1)
                return true;
                else 
                return false;
            }
        }
    
};
```
# 笔记
1.最初的思路是遍历数组，看是否只有一个相邻数不符题意，但遇到{3，3,2，2}{3,2,4,3}单独讨论很麻烦。

2.看到题解中一组思路，就是逐个将一个数“删去”，看其他是否符合题意，可大大简化思路，并且也不用真的删去，只需跳过即可。

3.调试将近一小时的原因是，数组总是越界，当“删去”的是最后一个数时，会越界，特殊讨论一下即可。
