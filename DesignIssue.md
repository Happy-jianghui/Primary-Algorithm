# 设计问题
## 384.打乱数组
**解题思路**：打牌算法，一个有限序列中，取一个随机元素与序列中最后一个元素交换位置，然后在剩下的元素中继续这个过程，直到整个序列被打乱。
```Python
class Solution:

    def __init__(self, nums: List[int]):
        self.list = nums

    def reset(self) -> List[int]:
        return self.list

    def shuffle(self) -> List[int]:
        n = len(self.list)
        shuffled = self.list[:]
        for i in range(n-1, 0, -1):
            j = random.randint(0,i)
            shuffled[j], shuffled[i] = shuffled[i], shuffled[j]
        return shuffled
```

## 155.最小栈
**解题思路**：借用一个辅助栈min_stack，用于存获取stack中最小值。
```Python
class MinStack:

    def __init__(self):
        self.A = []
        self.B = []


    def push(self, val: int) -> None:
        self.A.append(val)
        if not self.B or self.B[-1] >= val:
            self.B.append(val)

    def pop(self) -> None:
        if self.A.pop() == self.B[-1]:
            self.B.pop()


    def top(self) -> int:
        return self.A[-1]

    def getMin(self) -> int:
        return self.B[-1]



# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```
