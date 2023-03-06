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

## 121.买卖股票的最佳时机
**解题思路**：动态规划
```Python
def maxProfit(self, prices: List[int]) -> int:
        minprice = float("inf")
        maxres = 0
        for price in prices:
            minprice = min(minprice, price)
            maxres = max(maxres, price-minprice)
        return maxres
```

## 53.最大子数组和
**解题思路**：动态规划
```Python
def maxSubArray(self, nums: List[int]) -> int:
        for i in range(1, len(nums)):
            if nums[i-1] > 0:
                nums[i] = nums[i-1] + nums[i]
            elif nums[i-1] <= 0:
                nums[i] = nums[i]
        return max(nums)
```

## 198.打家劫舍
**解题思路**：动态规划
```Python
def rob(self, nums: List[int]) -> int:
        cur, pre = 0, 0
        for num in nums:
            cur, pre = max(pre + num, cur), cur
        return cur
```
