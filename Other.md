# 其他
## 191.位1的个数
**解题思路**：将该数与1进行与运算，得到的结果是1，说明该数的二进制表示的最低位为1；得到的结果是0，说明该数的二进制表示的最低位为0。然后我们将该数右移一位，再重复上述操作，直到该数变为0为止。
```Python
def hammingWeight(self, n: int) -> int:
        count = 0  # 初始化计数器count
        while n:  # 只要n不为0就一直循环
            if n & 1 == 1:  # 判断n的二进制表示的最低位是否为1
                count += 1  # 如果是1，计数器count加1
            n >>= 1  # 将n右移一位
        return count  # 返回计数器count的值
```

## 461.汉明距离
**解题思路**：和191思路差不多，先两个数异或运算，再用191思路来解题
```Python
def hammingDistance(self, x: int, y: int) -> int:
        count = 0
        res = x ^ y
        while res:
            if res & 1:
                count += 1
            res >>= 1
        return count
```

## 190.颠倒二进制位
**解题思路**：每次把res左移，把n的二进制末尾数字，拼接到结果res的末尾。然后把n右移
```Python
def reverseBits(self, n: int) -> int:
        res = 0
        for i in range(32):
            res = (res << 1) | (n & 1)
            n >>= 1
        return res
```

## 118.杨辉三角
**解题思路**：每次把res左移，把n的二进制末尾数字，拼接到结果res的末尾。然后把n右移
```Python
def generate(self, numRows: int) -> List[List[int]]:
        triangle = [[1]]
        for i in range(1,numRows):
            row = [1]
            for j in range(1, i):
                row.append(triangle[i-1][j-1] + triangle[i-1][j])
            row.append(1)
            triangle.append(row)
        return triangle
```
