# Height and Width

#### [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

```python
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        l,r = self.maxDepth(root.left),self.maxDepth(root.right)
        return max(l,r)+1
```

#### [Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

```python
class Solution:
    def minDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        children = [root.left,root.right]
        if (not root.left and not root.right) :
            return 1
        ans = float("inf")
        for c in children:
            if c:
                ans = min(ans,self.minDepth(c))
        return ans +1
```

#### [Binary Tree Longest Consecutive Sequence](https://leetcode.com/problems/binary-tree-longest-consecutive-sequence/)

Given a binary tree, find the length of the longest consecutive sequence path.

```python
class Solution:
    def longestConsecutive(self, root: TreeNode) -> int:
        
        def dfs(root):
            l = dfs(root.left)+1 if root.left else 1
            if root.left and root.val!=root.left.val-1:
                l=1
            r = dfs(root.right)+1 if root.right else 1
            if root.right and root.val!=root.right.val-1:
                r=1
            self.depth = max(l,r,self.depth)
            return max(l,r)
        self.depth=0
        
        if root:
            dfs(root)
        return self.depth
```

#### Binary Tree Longest Consecutive Sequence II

```python
class Solution:
    def longestConsecutive(self, root: TreeNode) -> int:
        self.longest = 0
        def dfs(root,parent):
            if not root:
                return 0,0
            li,ld = dfs(root.left,root.val)
            ri,rd = dfs(root.right,root.val)
            self.longest = max(self.longest, li+1+rd,ld+1+ri)
            return ( 1+max(li,ri) if root.val+1==parent else 0, 1+max(ld,rd) if root.val-1==parent else 0)
        dfs(root,0)
        return self.longest
```

