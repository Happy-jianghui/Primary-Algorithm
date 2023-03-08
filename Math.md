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
