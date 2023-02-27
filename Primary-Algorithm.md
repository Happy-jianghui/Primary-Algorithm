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

## 217.存在重复元素
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
