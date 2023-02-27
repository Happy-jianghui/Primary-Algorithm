# 数组 
## 26.删除排序数组中的重复项
**解题思路**：一个指针 i 进行数组遍历，另外一个指针j指向有效数组的最后一个位置，如果 i 所指向的值和 j 不一致，才将 i 的值添加到 j 的下一位置。
```Python
def removeDuplicates(nums) -> int:
        n = len(nums)
        j = 0
        for i in range(n):
            if nums[i] != nums[j]:
                j += 1
                nums[j] = nums[i]
        return j + 1

print(removeDuplicates([1,2,2,3,5]))
```

## 122.买卖股票的最佳时机 II
**解题思路**：贪心算法，遍历整个股票交易日价格列表，设 tmp 为第 i-1 日买入与第 i 日卖出赚取的利润，即 tmp = prices[i] - prices[i - 1]，如果tmp > 0，则加入总利润profit，当tmp为0或者负，则直接跳过，遍历完后返回profit.
```Python
def BestTimetoBuyandSellStockII(prices) -> float:
    sum = 0
    n = len(prices)
    for i in range(1,n):
        tmp = prices[i] - prices[i-1]
        if tmp > 0:
            sum += tmp
    return sum

print(BestTimetoBuyandSellStockII([7,1,5,3,6,4]))
```

## 189.轮转数组（旋转数组）
**解题思路**：多次翻转，先旋转整个数组，然后翻转k前的子数组，再翻转k后的子数组，最后返回结果
```Python
def rotate(nums, k) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n = len(nums)
        k %= n
        # 1.翻转整个数组
        reverse(nums, 0, n-1)
        # 2.翻转前k个元素
        reverse(nums, 0, k-1)
        # 3.翻转k后面的元素
        reverse(nums, k, n-1)
        print(nums)

def reverse(nums, start, end) -> None:
    while start < end:
        nums[start], nums[end] = nums[end], nums[start]
        start += 1
        end -= 1
        
print(rotate(nums = [1,2,3,4,5,6,7], k = 3))   
```

## 217.存在重复元素
**解题思路**：新建哈希表（散列表），然后遍历数组的所有元素，如果不在哈希表，则加入哈希表，如果在哈希表，则返回True，遍历完后没找到重复数组，则返回False
```Python
def containsDuplicate(nums) -> bool:
        hash = {}

        for i in nums:
            if i in hash:
                return True
            hash[i] = i
        return False

print(containsDuplicate([1,1,1,3,3,4,3,2,4,2]))  
```

## 217.只出现一次的数字
**解题思路1**：新建哈希表（散列表），然后i遍历数组的所有元素，如果不在哈希表，将元素的值为1加入哈希表，如果在哈希表，则将哈希表的元素加1，遍历完数组元素后j遍历哈希表的key,找最早key==1的值，然后返回j
```Python
def singleNumber(nums) -> int:
        hash = {}

        for i in nums:
            if i not in hash:
                hash[i] = 1
            else:
                hash[i] += 1        
        for j in hash:
            if hash[j] == 1:
                return j

print(singleNumber([4,1,2,1,2])) 
```

**解题思路1**：异或运算
```Python
def singleNumber(nums) -> int:
        res = 0
    for i in nums:
        res ^= i
    return res

print(singleNumber([4,1,2,1,2])) 
```

## 350.两个数组的交集 II
**解题思路1**：利用双指针，先把两个数组排序好后，指针left指向nums1数组首位，指针right指向nums2数组首位，创建临时空列表，用于放结果，开始比较指针left和right的值大小，若两个值不相等，则数字小的指针往右移动一位，若两个指针的值相等，则加入到res，若 nums1 或 nums2 有一方遍历结束，代表另一方的剩余值，都是唯一存在，且不会与之产生交集的。
```Python
def intersect(nums1, nums2):
        nums1.sort()
        nums2.sort()
        n, m = len(nums1), len(nums2)
        left, right = 0, 0
        res = []

        while left < n and right < m:
            if nums1[left] < nums2[right]:
                left += 1
            elif nums1[left] > nums2[right]:
                right += 1
            else:
                res.append(nums1[left])
                left += 1
                right += 1
        return res

print(intersect([1,2,2,1],[2,2]))
```

## 66.加一
**解题思路1**：数组末位数字加1，然后开始倒序遍历数组。判断当前位数字是否需要进位，做出对应处理。遍历数组完毕，若还存在进位，则数组首位添加1即可。
```Python
def plusOne(digits):
    n = len(digits)

    for i in range(n-1, -1, -1):
        if digits[i] != 9:
            digits[i] += 1
            return digits
        else:
            digits[i] = 0
            if digits[0] is 0:
                digits.insert(0, 1)
                return digits

print(plusOne([1,2,9]))
```

## 283.移动零
**解题思路1**：利用双指针，一个指针j指向数组首位，然后指针i遍历整个数组，如果遍历的元素不等于0，j和i的值交换，j往右一位
def moveZeroes(nums) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n = len(nums)
        if n == 1: return nums
        j = 0

        for i in range(n):
            if nums[i] != 0:
                nums[j], nums[i] = nums[i], nums[j]
                j += 1
        return nums
print(moveZeroes([0,1,0,3,12]))
```

## 1.两数之和
**解题思路1**：利用哈希表，先遍历数组的所有元素，然后减target所得的结果是否在哈希表，如果在，则返回数组[哈希表的键对着值, 遍历当前的索引]，否则加入到哈希表
def twoSum(self, nums: List[int], target: int) -> List[int]:
        n = len(nums)
        hash = {}

        for i in range(n):
            tmp = target - nums[i]
            if tmp in hash:
                return [hash[tmp], i]
            hash[nums[i]] = i
```
