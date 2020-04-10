# 问题（1）
有两种特殊字符。第一种字符可以用一比特0来表示。第二种字符可以用两比特(10 或 11)来表示。

现给一个由若干比特组成的字符串。问最后一个字符是否必定为一个一比特字符。给定的字符串总是由0结束。

示例 1:

输入: 
bits = [1, 0, 0]
输出: True
解释: 
唯一的编码方式是一个两比特字符和一个一比特字符。所以最后一个字符是一比特字符。
示例 2:

输入: 
bits = [1, 1, 1, 0]
输出: False
解释: 
唯一的编码方式是两比特字符和两比特字符。所以最后一个字符不是一比特字符。
注意:

1 <= len(bits) <= 1000.
bits[i] 总是0 或 1.

# 代码
```
class Solution {
public:
    bool isOneBitCharacter(vector<int>& bits) {
        int k=0;
        while(k<bits.size())
        {
            if(bits[k]==1)
            {
                bits[k]=2;
                bits[k+1]=2;
                k=k+2;
                

            }
            else
            k=k+1;
        }
        if(bits[bits.size()-1]==0)
        {
            return true;
        }
        else
        return false;

    }
};
```

# 问题（2）
给定一个整数类型的数组 nums，请编写一个能够返回数组“中心索引”的方法。

我们是这样定义数组中心索引的：数组中心索引的左侧所有元素相加的和等于右侧所有元素相加的和。

如果数组不存在中心索引，那么我们应该返回 -1。如果数组有多个中心索引，那么我们应该返回最靠近左边的那一个。

示例 1:

输入: 
nums = [1, 7, 3, 6, 5, 6]
输出: 3
解释: 
索引3 (nums[3] = 6) 的左侧数之和(1 + 7 + 3 = 11)，与右侧数之和(5 + 6 = 11)相等。
同时, 3 也是第一个符合要求的中心索引。
示例 2:

输入: 
nums = [1, 2, 3]
输出: -1
解释: 
数组中不存在满足此条件的中心索引。
说明:

nums 的长度范围为 [0, 10000]。
任何一个 nums[i] 将会是一个范围在 [-1000, 1000]的整数。

# 代码（时间复杂度高，超时了，看题解学会简单方法）
```
class Solution {
public:
    int pivotIndex(vector<int>& nums) {
        int w=0;
        int q=0;
        int h=0;
        int a=0;
        if(nums.size()==0)
        {
            return -1;
        }
        else
        {
        for(int j=1;j<nums.size();j++)
        {
            h=h+nums[j];
        }
        if(h==0)
        {
            return 0;
        }
        else
        {
            h=0;
        for(int i=1;i<nums.size();i++)
        {
            for(int j=i-1;j>=0;j--)
            {
                q=q+nums[j];
            }
            for(int j=i+1;j<nums.size();j++)
            {
                h=h+nums[j];
            }
            if(q==h)
            {
                w=1;
                a=i;
                break;
            }
            q=0;
            h=0;
        }
        if(w==1)
        {
            return a;
        }
        else
        return -1;
        }
    }}
};
```
# 代码（通过简单方法）
```
class Solution {
public:
    int pivotIndex(vector<int>& nums) {
        int w=0;
        int q=0;
        int h=0;
        int a=0;
        int sum=0;
        if(nums.size()==0)
        {
            return -1;
        }
        else
        {
        for(int j=1;j<nums.size();j++)
        {
            h=h+nums[j];
        }
        if(h==0)
        {
            return 0;
        }
        else
        {
            sum=h+nums[0];
            h=0;
        for(int i=1;i<nums.size();i++)
        {
           q=q+nums[i-1];
           if(q*2==sum-nums[i])
           {
               return i;
           }
        }
        return -1;
        }
    }}
};
```

# 笔记
1.自己的方法，时间复杂度太高，没有想到前面的和乘两倍等于总和减去索引对应的数作为判断条件，即可在一个循环中完成。

2.注意考虑特殊情况。
