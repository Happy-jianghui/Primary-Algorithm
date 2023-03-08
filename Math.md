# 数学
## 412.Fizz Buzz
**解题思路**：从1到n依次输出数字，当数字是3的倍数时输出“Fizz”，当数字是5的倍数时输出“Buzz”，当数字既是3的倍数又是5的倍数时输出“FizzBuzz”
```Python
def fizzBuzz(self, n: int) -> List[str]:
        result = []

        for i in range(1, n+1):
            if i % 3 == 0 and i % 5 == 0:
                result.append("FizzBuzz")
            elif i % 3 == 0:
                result.append("Fizz")
            elif i % 5 == 0:
                result.append("Buzz")
            else:
                result.append(str(i))
        return result
```

## 204.计数质数
**解题思路**：埃拉托斯特尼 埃氏筛选法
```Python
def countPrimes(self, n: int) -> int:
        isNumPrimes = [True] * n # 将所有数，展开所有数 标记质数真
        count = 0  # 质数计数器 因为1不是质数 所以 0
        # 遍历2，n 数，判断是否是质数，从2开始对应-质数3 [1,2,3]  1不算质数
        for i in range(2, n):
            if isNumPrimes[i]:
                count += 1
                # 使用埃拉托斯特尼 筛选法进行过滤 将合数去除
                for j in range(i*i, n, i): #遍历 i*i  2倍i值 开始，结束n, 步数i (倍数递增)
                    isNumPrimes[j] = False # 把合数置为 False
        return count
```
