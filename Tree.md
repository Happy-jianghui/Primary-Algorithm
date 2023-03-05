# 树
## 104.二叉树的最大深度
**解题思路**：递归：树的深度等于左子树的深度与右子树的深度中的最大值+1。队列：每遍历一层，则计数器+1 ，直到遍历完成，则可得到树的深度。
```Python
def maxDepth(self, root: Optional[TreeNode]) -> int:
        #递归
        if not root: return 0
        return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1
        
        #队列
        if not root: return 0
        queue = [root]
        res = 0

        while queue:
            tmp = []
            for node in queue:
                if node.left: tmp.append(node.left)
                if node.right: tmp.append(node.right)
            res += 1
            queue = tmp
        return res
```

## 98.验证二叉搜索树
**解题思路**：递归,利用二叉搜索树的定义来递归
```Python
def isValidBST(self, root: Optional[TreeNode]) -> bool:
        def dfs(root, left, right):
            if not root:
                return True
            elif left < root.val < right:
                return dfs(root.left, left, root.val) and dfs(root.right, root.val, right)
            else:
                return False
        return dfs(root, float('-inf'), float('inf'))

```

## 101.对称二叉树
**解题思路**：顶至底递归，判断每对节点是否对称，从而判断树是否为对称二叉树
```Python
def isSymmetric(self, root: TreeNode) -> bool:
        def recur(L,R):
            if not L and not R: return True
            if not L or not R or L.val != R.val: return False

            return recur(L.left, R.right) and recur(L.right, R.left)
        return recur(root.left, root.right) if root else True
```


## 102.二叉树的层序遍历
**解题思路**：广度优先搜索，用队列作为辅助结构，先将根节点放到队列中，然后不断遍历队列。
```Python
def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root: return []
        res = []
        queue = collections.deque()
        queue.append(root)
        while queue:
            temp = []
            for _ in range(len(queue)):
                node = queue.popleft()
                temp.append(node.val)

                if node.left: queue.append(node.left)
                if node.right: queue.append(node.right)
            res.append(temp)
        return res
```

## 108.将有序数组转换为二叉搜索树
**解题思路**：看到BST，优先想到中序遍历，由于题目要求高度平衡，在数组取中间的元素，该元素左边的升序序列构建左子树，该元素的右边的升序序列构建右子树
```Python
def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        if not nums: return None
        mid = len(nums)//2
        node = TreeNode(nums[mid])

        left = nums[:mid]
        right = nums[mid+1:]

        node.left = self.sortedArrayToBST(left)
        node.right = self.sortedArrayToBST(right)
        return node
```
