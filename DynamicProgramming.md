# 动态规划
## 70.爬楼梯
**解题思路**：如果有n阶，若爬了1台阶，还有n-1台阶要爬，若爬了2台阶，还有n-2台阶要爬，得出结论dp[i] = dp[i-1]+dp[i-2]
```Python
def climbStairs(self, n: int) -> int:
        dp = [0]*(n+1)
        dp[0] = 1
        dp[1] = 1

        for i in range(2,n+1):
            dp[i] = dp[i-1] + dp[i-2]
        return dp[n]
```
