## 记忆化搜索

### 记忆化搜索初步

记忆化搜索常用于树形 DP、状压 DP 等不容易直接写出状态转移方程的动态规划。尤其是树形 DP 这种无法写出一般形式的状态转移方程的 DP。

记忆化搜索容易想到解法（即如果状态设计正确就直接可以转成记忆化而不用像 DP 一样推导什么东西），但是由于多了一些函数调用和递归操作，效率略低，且不太容易优化。但是由于带有搜索的特性，可以通过剪枝来优化。

其本质与记忆化搜索一致，同样是通过对状态的合理规划来达到避免重复解决重复子问题的思想。

以下通过几道例题来加深对记忆化搜索的理解。主要是一些基础的树形 DP 和一些基础的记忆化。

在此之前先水一发简单的搜索练练手：
```cpp
#include <cstdio>
#include <queue>
#include <unordered_map>
using namespace std;
deque<int> q;
int s;
int c[3][3];
unordered_map<int, int> vis;
int dx[] = {0, -1, 0, 1}, dy[] = {1, 0, -1, 0};
int main() {
  scanf("%d", &s);
  q.push_back(s);
  vis[s] = 0;
  while(!q.empty()) {
    int x = q.front();
    int u = x;
    q.pop_front();
    if(x == 123804765) break;
    int cx = 0, cy = 0;
    for(int i = 2; i >= 0; --i) for(int j = 2; j >= 0; --j) {
        c[i][j] = x % 10, x /= 10;
        if(!c[i][j]) cx = i, cy = j;
      }
    for(int k = 0; k < 4; ++k) {
      int xx = cx + dx[k], yy = cy + dy[k];
      if(xx < 0 || xx > 2 || yy < 0 || yy > 2) continue;
      swap(c[cx][cy], c[xx][yy]);
      int code2 = 0;
      for(int i = 0; i < 3; ++i) for(int j = 0; j < 3; ++j)
          code2 = code2 * 10 + c[i][j];
      if(!vis.count(code2)) q.push_back(code2), vis[code2] = vis[u] + 1;
      swap(c[cx][cy], c[xx][yy]);
    }
  }
  printf("%d\n", vis[123804765]);
  return 0;
}
```
八数码问题，简单的 BFS 加上对状态的简单记录。

### [最大子树和](https://www.luogu.org/record/show?rid=10655795)

题意：给一棵树，可以剪掉任意多棵子树，权值为剩下的子树的权值之和。求最大权值。

题解：贪心 + DP。明显的如果一棵子树的权值为负数我们当然不能选择这棵子树。那么直接 DP 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAzMDcxMjEzNiwtODA2ODMzMTY2LDY4NT
MxOTkxOSwtNjg5OTA2NzgsMjc4MDg1ODg0LC0yOTEwMjg4OTMs
LTE1OTE5MDgzNTcsMTkyNTAwODQ3NiwxMjMwNjcwMDQwLDc5MT
IyMzc4MiwxNTg1NzYzODksLTE4NzExNzE1NzldfQ==
-->