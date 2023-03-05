# 排序和搜索
## 88.合并两个有序数组
**解题思路**：从后往前确定两组中该用哪个数字
```Python
def merge(nums1, m, nums2, n) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        i, j = m - 1, n - 1
        k = m + n - 1
        while i >= 0 or j >= 0:
            if i == -1:
                nums1[k] = nums2[j]
                j -= 1
            elif j == -1:
                nums1[k] = nums1[i]
                i -= 1
            elif nums1[i] > nums2[j]:
                nums1[k] = nums1[i]
                i -= 1
            else:
                nums1[k] = nums2[j]
                j -= 1
            k -= 1
print(merge( [1,2,3,0,0,0], 3, [2,5,6],3))
```

## 278.第一个错误版本
**解题思路**：根据题目描述 “错误的版本之后的所有版本都是错的” ，说明给定的版本正确性列表是「有序的」，即以某个版本为分界点，左边（右边）都是正确（错误）版本。因此，考虑使用「二分查找」来查找首个错误版本。
```Python
def firstBadVersion(self, n: int) -> int:
        i, j = 1, n
        while i <= j:
            m = (i+j) // 2
            if isBadVersion(m):
                j = m - 1
            else:
                i = m + 1
        return i
```
