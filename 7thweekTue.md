# 问题
如果一个矩阵的每一方向由左上到右下的对角线上具有相同元素，那么这个矩阵是托普利茨矩阵。

给定一个 M x N 的矩阵，当且仅当它是托普利茨矩阵时返回 True。

示例 1:

输入: 
matrix = [
  [1,2,3,4],
  [5,1,2,3],
  [9,5,1,2]
]
输出: True
解释:
在上述矩阵中, 其对角线为:
"[9]", "[5, 5]", "[1, 1, 1]", "[2, 2, 2]", "[3, 3]", "[4]"。
各条对角线上的所有元素均相同, 因此答案是True。
示例 2:

输入:
matrix = [
  [1,2],
  [2,2]
]
输出: False
解释: 
对角线"[1, 2]"上的元素不同。
说明:

 matrix 是一个包含整数的二维数组。
matrix 的行数和列数均在 [1, 20]范围内。
matrix[i][j] 包含的整数在 [0, 99]范围内。
进阶:

如果矩阵存储在磁盘上，并且磁盘内存是有限的，因此一次最多只能将一行矩阵加载到内存中，该怎么办？
如果矩阵太大以至于只能一次将部分行加载到内存中，该怎么办？

# 代码（1）
```
class Solution {
public:
    bool isToeplitzMatrix(vector<vector<int>>& matrix) {
       int r=matrix.size();
       int c=matrix[0].size();
       if(r==1&&c==1)
       return true;
       else{

       
       for(int i=1;i<r;i++)
       {
           for(int j=1;j<c;j++)
           {
               if(matrix[i][j]!=matrix[i-1][j-1])
               return false;
           }
       }
return true;}

    }
};
```
# 笔记
1.暴力遍历法，只要保证左上角与当前元素相等即可，要防止数组越界

# 代码（2）(总是输出错误)
```
class Solution {
public:
    bool isToeplitzMatrix(vector<vector<int>>& matrix) {
       int r=matrix.size();
       int c=matrix[0].size();
       if(r==1&&c==1)
       return true;
       else{
           int a[100]={-1};


       
       for(int i=0;i<r;i++)
       {
           for(int j=0;j<c;j++)
           {
              if(a[i-j+20]==-1)
              {
                  a[i-j+20]=matrix[i][j];
              }
              else{
                  if(a[i-j+20]!=matrix[i][j])
                  return false;
              }
           }
       }
return true;}

    }
};
```
# 笔记
1.参考的官方题解的方法，找出对角元素的共同点。
