# 数
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
