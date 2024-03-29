# 二维数组中的查找

本文是[《剑指Offer》](https://www.nowcoder.com/ta/coding-interviews?page=1)刷题笔记，记录刷题过程中的体会与收获。

## 题目描述

在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

## 解题思路

最简单的方法是暴力搜索，对输入的二维数组逐元素比较，但显然不是我们想要的解法。因为每行元素都是有序排列，因此另一种可行的方法是逐行对目标元素进行二分查找，但这样要注意排除无效行，即首先判断目标元素是否落在某一行元素范围内，若不可能在某一行元素范围内则转至下一行。

因为二维数组行数为`row`，列数为`col`，每一行从左到右递增排列，每一列从上到下递增排列，因此二维数组某一元素`M(i,j)`小于目标元素`target`时，查找范围应该处于`M(i,j)`的右下方；相反则在左上方。因此可将查询起点设置为二维数组的右上方`M(0,col-1)`，若小于目标元素则查找范围缩小至下方；若大于目标元素则查询范围缩小至左方，直至最终找到目标元素。

## 代码示例

```C++
class Solution {
public:
    bool Find(int target, vector<vector<int> > array) {
        int row = 0;
        int col = array[0].size() - 1;
        while(row <= array.size() - 1 && col >= 0) {
            if(target == array[row][col])
                return true;
            else if(target < array[row][col])
                col--;
            else if(target > array[row][col])
                row++;
        }
        return false;
    }
};
```

