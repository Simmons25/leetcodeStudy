# 问题
在歌曲列表中，第 i 首歌曲的持续时间为 time[i] 秒。

返回其总持续时间（以秒为单位）可被 60 整除的歌曲对的数量。形式上，我们希望索引的数字 i 和 j 满足  i < j 且有 (time[i] + time[j]) % 60 == 0。

 

示例 1：

输入：[30,20,150,100,40]
输出：3
解释：这三对的总持续时间可被 60 整数：
(time[0] = 30, time[2] = 150): 总持续时间 180
(time[1] = 20, time[3] = 100): 总持续时间 120
(time[1] = 20, time[4] = 40): 总持续时间 60
示例 2：

输入：[60,60,60]
输出：3
解释：所有三对的总持续时间都是 120，可以被 60 整数。
 

提示：

1 <= time.length <= 60000
1 <= time[i] <= 500

# 解法1
```
#首先我们先对time[i]取模，得到一个每个元素都小于60的time数组，再对每一个出现的元素计算出现次数
然后我们从小到大计算对数，比如对于元素20，我们只需要看看40出现的次数就可以知道元素20对应的匹配对数
对于0和30我们要单独计算，用一下等差数列求和即可
class Solution {
public:
     int count[61],res = 0;
     int numPairsDivisibleBy60(vector<int>& time) {
        if(time.empty()) return 0;
        memset(count,0,sizeof count);
        for(int i = 0; i < time.size(); i++){
            time[i] %= 60;
            count[time[i]]++;
        }
        sort(time.begin(),time.end());
        for(int i = 0; i < time.size(); i++){
            if(time[i] >= 30) break;
            if(time[i] == 0) continue;
            res += count[60 - time[i]];
        }
        res += (count[0]*(count[0]-1))/2;
        res += (count[30]*(count[30]-1))/2;
        return res;
     }
};

```
# 笔记1
1. 方法真的是巧妙，我用了两次for循环，但是超时间了，这个方法通过每个数对60取余就可以找到与之匹配的，再用一个数组保存每个余数的个数即可。
2.但是要注意，大于三十的时候不要考虑会重复，0和30要单独考虑，要减去一才是配对的数目。
