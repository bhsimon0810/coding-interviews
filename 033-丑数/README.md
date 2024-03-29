# 丑数

本文是[《剑指Offer》](https://www.nowcoder.com/ta/coding-interviews?page=1)刷题笔记，记录刷题过程中的体会与收获。

## 题目描述

把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。例如 6、8 都是丑数，但 14 不是，因为它包含质因子 7。 习惯上我们把 1 当做是第一个丑数。求按从小到大的顺序的第 N 个丑数。

## 解题思路

最直接粗暴的方法是从小到大遍历，然后逐个判断是否为丑数，如果是则丑数个数加一，当达到个数 N 时返回当前数字即可。但显然这种方法的计算开销较大，对每一个数字（可能是非丑数）都要进行判断能否整除 2/3/5，因此需要考虑更好的解法。

因为丑数是能够整除 2/3/5 的数字，因此若某一丑数 n 乘 2/3/5 的结果仍然是丑数。那么从 1 开始，乘 2/3/5 的结果仍为丑数。但注意题目要求按从小到大的顺序，所以还要注意顺序问题。考虑以空间换时间，定义大小为 N 的数组，按从小到大的顺序依次将 N 个丑数添加
