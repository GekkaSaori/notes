## 记忆化搜索

### 记忆化搜索初步

记忆化搜索常用于树形 DP、状压 DP 等不容易直接写出状态转移方程的动态规划。尤其是树形 DP 这种无法写出一般形式的状态转移方程的 DP。

记忆化搜索容易想到解法（即如果状态设计正确就直接可以转成记忆化而不用像 DP 一样推导什么东西），但是由于多了一些函数调用和递归操作，效率略低，且不太容易优化。但是由于带有搜索的特性，可以通过剪枝来优化。

其本质与记忆化搜索一致，同样是通过对状态的合理规划来达到避免重复解决重复子问题的思想。

通过几道
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjQyNzQ2NjgxLDE4OTIxMzY0MzcsLTE1OT
E5MDgzNTcsMTkyNTAwODQ3NiwxMjMwNjcwMDQwLDc5MTIyMzc4
MiwxNTg1NzYzODksLTE4NzExNzE1NzldfQ==
-->