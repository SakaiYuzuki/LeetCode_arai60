```python
from typing import Optional

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = 0
        self.left = left
        self.right = right

class Solution:
    def maxDepth(self, root: Optional[TreeNode])-> int:
        if root is None:
            return 0

        leftDepth = self.maxDepth(root.left)
        rightDepth = self.maxDepth(root.right)

        return max(leftDepth, rightDepth) + 1
```
step1&step2
探索のコードが考えてもわからなかったため、答えを探して、自分なりに綺麗にしてみました。
具体的には、前回学んだ「==」を「is」で表現したり、Noneの場合のために型タイプOptionalを導入したりしています。
