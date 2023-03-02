# 字符串 
## 344.反转字符串
**解题思路**：双指针，一个指针指向首位，另一个指针指向末尾，同时交换，然后一个指针向右往前一位，另一个指针向左往前一位，依此类推，直到相遇为止
```Python
def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        i, j = 0, len(s)-1
        while i <= j:
            s[i], s[j] = s[j], s[i]
            i += 1
            j -= 1
```

## 7.整数反转
**解题思路**：用数学思维，注意考虑取值范围
```Python
def reverse(x) -> int:
        y, res = abs(x), 0
        of = (1 << 31) - 1 if x > 0 else 1 << 31

        while y != 0:
            res = res * 10 + y % 10
            if res > of: return 0
            y //= 10
        return res if x > 0 else -res

print(reverse(123))
```

## 387.字符串中的第一个唯一的字符
**解题思路**：使用哈希表存储索引，第一次遍历字符串时，设当前遍历到的字符为c，如果c不在哈希表中，我们就将 c与它的索引作为一个键值对加入哈希表中，否则我们将c在哈希表中对应的值修改为−1。在第一次遍历结束后，再遍历一次哈希表的所有值，找出其中不为-1的最小值，即为第一个不重复字符的索引。如果哈希映射中的所有值均为−1，就返回−1。

```Python
def firstUniqChar(self, s: str) -> int:
        hash = {}

        for i, c in enumerate(s):
            if c in hash:
                hash[c] = -1
            else:
                hash[c] = i
        for j in hash.values():
            if j != -1:
                return j
        return -1
```
