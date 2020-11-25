# Path Sum

#### Binary Tree Paths

```python
class Solution:
    def binaryTreePaths(self, root: TreeNode) -> List[str]:
        if not root:
            return []
        res = []
        self.dfs(root,res,"")
        return res
    def dfs(self,node,res, cur):
        if not node.left and not node.right:
            res.append(cur+str(node.val))
        if node.left:
            self.dfs(node.left,res,cur+str(node.val)+"->")
        if node.right:
            self.dfs(node.right,res,cur+str(node.val)+"->")
```

#### [Path Sum I](https://leetcode.com/problems/path-sum/)

Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

```python
class Solution:
    def hasPathSum(self, root: TreeNode, sum: int) -> bool:
        if not root:
            return False
        sum -= root.val
        if not root.left and not root.right:
            return sum==0
        return self.hasPathSum(root.left,sum) or self.hasPathSum(root.right,sum)
```

#### [Path Sum II](https://leetcode.com/problems/path-sum-ii/)

Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.

```python
class Solution:
    def pathSum(self, root: TreeNode, sum: int) -> List[List[int]]:
        if not root:
            return
        res = []
        self.dfs(root,sum,res,[])
        return res
    def dfs(self, root, sum, res, cur):
        if not root.left and not root.right and sum == root.val:
            res.append(cur+[root.val])
        ##if sum <0:
        ##    return
        if root.left:
            self.dfs(root.left, sum - root.val, res, cur+[root.val])
        if root.right:
            self.dfs(root.right, sum - root.val, res, cur+[root.val])
```

#### [Path Sum III](https://leetcode.com/problems/path-sum-ii/description/)

You are given a binary tree in which each node contains an integer value.

Find the number of paths that sum to a given value.

The path does not need to start or end at the root or a leaf, but it must go downwards \(traveling only from parent nodes to child nodes\).

```python
class Solution:
    def pathSum(self, root: TreeNode, sum: int) -> int:
        if not root:
            return 0
        def dfs(node,sum):
            if not node:
                return 0
            count = 0
            if node.val==sum:
                count += 1
            count += dfs(node.left,sum-node.val)
            count += dfs(node.right,sum-node.val)
            return count
        return dfs(root,sum) + self.pathSum(root.left,sum) + self.pathSum(root.right,sum)
    


```

#### [Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/)

```python
class Solution:
    def sumNumbers(self, root: TreeNode) -> int:
        if not root:
            return 0
        ans = []
        self.dfs(root,ans,0)
        
        return sum(ans)
    def dfs(self,root,ans,cur):
        if not root.left and not root.right:
            ans.append(cur*10+root.val)
           
        if root.left:
            self.dfs(root.left,ans,cur*10+root.val)
        if root.right:
            self.dfs(root.right,ans,cur*10+root.val)
```









