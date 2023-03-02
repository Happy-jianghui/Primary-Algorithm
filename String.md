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
