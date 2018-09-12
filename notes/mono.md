## 记忆化搜索

### 记忆化搜索初步

记忆化搜索常用于树形 DP、状压 DP 等不容易直接写出状态转移方程的动态规划。尤其是树形 DP 这种无法写出一般形式的状态转移方程的 DP。

记忆化搜索容易想到解法（即如果状态设计正确就直接可以转成记忆化而不用像 DP 一样推导什么东西），但是由于多了一些函数调用和递归操作，效率略低，且不太容易优化。但是由于带有搜索的特性，可以通过剪枝来优化。


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkzOTg3OTk2MywtMTU5MTkwODM1NywxOT
I1MDA4NDc2LDEyMzA2NzAwNDAsNzkxMjIzNzgyLDE1ODU3NjM4
OSwtMTg3MTE3MTU3OV19
-->