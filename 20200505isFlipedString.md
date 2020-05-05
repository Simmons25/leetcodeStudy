# 问题
字符串轮转。给定两个字符串s1和s2，请编写代码检查s2是否为s1旋转而成（比如，waterbottle是erbottlewat旋转后的字符串）。

示例1:

 输入：s1 = "waterbottle", s2 = "erbottlewat"
 输出：True
示例2:

 输入：s1 = "aa", "aba"
 输出：False
提示：

字符串长度在[0, 100000]范围内。
说明:

你能只调用一次检查子串的方法吗？

# 代码
```
class Solution {
public:
    bool isFlipedString(string s1, string s2) {
        if(s1.size()!=s2.size())
        {
            return false;
        }
        else{

        
        s2=s2+s2;
        
        if(s2.find(s1)==-1)
        {return false;}
        else
        return true;
        }
    }
};
```
# 笔记
1.方法巧妙，依照该题意旋转得到的字符串复制一遍后一定会出现原来字符串，即可通过find函数找到即可。
