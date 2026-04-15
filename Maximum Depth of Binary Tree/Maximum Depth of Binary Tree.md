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

```
step3
他の方のコードやコメントを確認して、今回取り入れたい点

- コードを書いたら計算量と時間の見積もりを考える
  =時間計算量 : O(V + E)、空間計算量 : O(h)
    テストケース1の場合
    一瞬(0秒以下)

- 保守性の観点を持つ
  =maxで最大値を記録する

- 別解を考える
  =stackとpopで解く方法がある
```

```python
#popとstackを使った解法
from typing import Optional

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = 0
        self.left = left
        self.right = right

class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if root is None:
            return 0
        
        stack = [[root, 1]]
        depth = 0

        while stack:
            node, current_depth = stack.pop()

            if node:
                depth = max(depth, current_depth)
                stack.append([node.left, current_depth + 1])
                stack.append([node.right, current_depth + 1])

        return depth

```
