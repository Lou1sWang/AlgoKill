# Tree Traversal

### [Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/description/)

```python
# recursion
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        self.dfs(root,res)
        return res
    def dfs(self,root,res):
        if root:
            self.dfs(root.left,res)
            res.append(root.val)
            self.dfs(root.right,res)

# iteration
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        stack = []
        res = []
        node = root
        while stack or node:
            while node:
                stack.append(node)
                node = node.left
                
            node = stack.pop()
            res.append(node.val)
            node = node.right
        return res
```

### [Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/)

```python
class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        res = []
        stack = [root]
        while stack:
            node = stack.pop()
            res.append(node.val)
            if node.right:
                stack.append(node.right)
            if node.left:
                stack.append(node.left)
        return res

class Solution(object):
    def preorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        res = []
        def dfs(node):
            if node:
                res.append(node.val)
                dfs(node.left)
                dfs(node.right)
        dfs(root)
        return res
```

### Postorder Traversal

```python
class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        res = []
        self.dfs(root,res)
        return res
    def dfs(self, root , res):
        if root:
            self.dfs(root.left,res)
            self.dfs(root.right,res)
            res.append(root.val)
class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        res = []
        stack = [root]
        while stack:
            node = stack.pop()
            res.append(node.val)
            if node.left:
                stack.append(node.left)
            if node.right:
                stack.append(node.right)
     
        return res[::-1]
```

### [Level Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)

```python
class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        res = []
        stack = [root]
        while stack:
            n = len(stack)
            cur = []
            for _ in range(n):
                node = stack.pop(0)
                cur.append(node.val)
                if node.left:
                    stack.append(node.left)
                if node.right:
                    stack.append(node.right)
            res.append(cur)
        return res
```

### [ZigZag Level Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

```python
class Solution:
    def zigzagLevelOrder(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        res = []
        stack = deque([root])
        direction = True
        while stack:
            n = len(stack)
            cur = []
            for _ in range(n):
                node = stack.popleft()
                cur.append(node.val)
                if node.left:
                    stack.append(node.left)
                if node.right:
                    stack.append(node.right)
            if direction:
                res.append(cur)
            else:
                res.append(cur[::-1])
            direction = not direction
        return res
```

### [Vertical Order Traversal](https://leetcode.com/problems/binary-tree-vertical-order-traversal/description/)

```python
class Solution:
    def verticalOrder(self, root: TreeNode) -> List[List[int]]:
        from collections import defaultdict
        columnTable = defaultdict(list)
        queue = deque([(root,0)])
        
        while queue:
            node, column = queue.popleft()
            
            if node:
                columnTable[column].append(node.val)
                queue.append((node.left,column-1))
                queue.append((node.right,column+1))
        return [columnTable[x] for x in sorted(columnTable.keys())]
# Time Complexity: O(NlogN)

```



