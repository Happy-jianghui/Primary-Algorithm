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


## 242.有效的字母异位词
**解题思路**：使用哈希表存储索引，首先判断两个字符串长度是否相等，不相等则直接返回 false，若相等，则初始化 26 个字母哈希表，遍历字符串 s 和 t，s 负责在对应位置增加，t 负责在对应位置减少，如果哈希表的值都为 0，则二者是字母异位词
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

## 125.验证回文串
**解题思路**：双指针，遇到非数字字母的字符直接跳过，再判断这两个指针指向的字符是否相同，直到相遇
```Python
def isPalindrome(self, s: str) -> bool:
        i, j = 0, len(s)-1

        while i < j:
            # not string.isalnum 如果不是字母或者数字，则直接跳过
            while i < j and not s[i].isalnum():
                i += 1
            while i < j and not s[j].isalnum():
                j -= 1

            if i < j:
                if s[i].lower() != s[j].lower():
                    return False
                i += 1
                j -= 1
        return True
```

## 28.找出字符串中第一个匹配项的下表
**解题思路**：KMP没看懂，用暴力法，次列表的长度遍历主列表，直到找到对应的字符串，就返回第一个的下标，否则返回-1
```Python
def strStr(haystack, needle) -> int:
        n = len(needle)
        if n == 0:
            return 0
        for i in range(len(haystack) - n + 1):
            if haystack[i:i + n] == needle:
                return i
        return -1
print(strStr( "sadbutsad", "but"))
```

## 14.最长公共前缀
**解题思路**：当字符串数组长度为 0 时则公共前缀为空，直接返回，令最长公共前缀 ans 的值为第一个字符串，进行初始化，遍历后面的字符串，依次将其与 ans 进行比较，两两找出公共前缀，最终结果即为最长公共前缀，如果查找过程中出现了 ans 为空的情况，则公共前缀不存在直接返回
```Python
def longestCommonPrefix(strs) -> str:
    if len(strs) == 0: return ""
    ans = strs[0]
    for i in range(1, len(strs)):
        idx = 0
        for c1, c2 in zip(ans, strs[i]):
            if c1 != c2:
                break
            idx += 1
        ans = ans[0:idx]
        if ans == "": return ans
    return ans

print(longestCommonPrefix(["flower","flow","flight"]))
```
