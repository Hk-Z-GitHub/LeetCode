# [572. Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree)

[中文文档](/solution/0500-0599/0572.Subtree%20of%20Another%20Tree/README.md)

## Description

<p>Given two <strong>non-empty</strong> binary trees <b>s</b> and <b>t</b>, check whether tree <b>t</b> has exactly the same structure and node values with a subtree of <b>s</b>. A subtree of <b>s</b> is a tree consists of a node in <b>s</b> and all of this node&#39;s descendants. The tree <b>s</b> could also be considered as a subtree of itself.</p>

<p><b>Example 1:</b><br />
Given tree s:</p>

<pre>
     3
    / \
   4   5
  / \
 1   2
</pre>

Given tree t:

<pre>
   4 
  / \
 1   2
</pre>

Return <b>true</b>, because t has the same structure and node values with a subtree of s.

<p>&nbsp;</p>

<p><b>Example 2:</b><br />
Given tree s:</p>

<pre>
     3
    / \
   4   5
  / \
 1   2
    /
   0
</pre>

Given tree t:

<pre>
   4
  / \
 1   2
</pre>

Return <b>false</b>.

<p>&nbsp;</p>

## Solutions

<!-- tabs:start -->

### **Python3**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSubtree(self, root: TreeNode, subRoot: TreeNode) -> bool:
        def dfs(root1, root2):
            if root1 is None and root2 is None:
                return True
            if root1 is None or root2 is None:
                return False
            return root1.val == root2.val and dfs(root1.left, root2.left) and dfs(root1.right, root2.right)

        if root is None:
            return False
        return dfs(root, subRoot) or self.isSubtree(root.left, subRoot) or self.isSubtree(root.right, subRoot)
```

### **Java**

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if (root == null) {
            return false;
        }
        return dfs(root, subRoot) || isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot);
    }

    private boolean dfs(TreeNode root1, TreeNode root2) {
        if (root1 == null && root2 == null) {
            return true;
        }
        if (root1 == null || root2 == null) {
            return false;
        }
        return root1.val == root2.val && dfs(root1.left, root2.left) && dfs(root1.right, root2.right);
    }
}
```

### **C++**

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool isSubtree(TreeNode* root, TreeNode* subRoot) {
        if (!root) return 0;
        return dfs(root, subRoot) || isSubtree(root->left, subRoot) || isSubtree(root->right, subRoot);
    }

    bool dfs(TreeNode* root1, TreeNode* root2) {
        if (!root1 && !root2) return 1;
        if (!root1 || !root2) return 0;
        return root1->val == root2->val && dfs(root1->left, root2->left) && dfs(root1->right, root2->right);
    }
};
```

### **Go**

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func isSubtree(root *TreeNode, subRoot *TreeNode) bool {
	if root == nil {
		return false
	}
	var dfs func(root1, root2 *TreeNode) bool
	dfs = func(root1, root2 *TreeNode) bool {
		if root1 == nil && root2 == nil {
			return true
		}
		if root1 == nil || root2 == nil {
			return false
		}
		return root1.Val == root2.Val && dfs(root1.Left, root2.Left) && dfs(root1.Right, root2.Right)
	}
	return dfs(root, subRoot) || isSubtree(root.Left, subRoot) || isSubtree(root.Right, subRoot)
}
```

### **JavaScript**

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @param {TreeNode} subRoot
 * @return {boolean}
 */
var isSubtree = function (root, subRoot) {
    if (!root) return false;
    let dfs = function (root1, root2) {
        if (!root1 && !root2) {
            return true;
        }
        if (!root1 || !root2) {
            return false;
        }
        return (
            root1.val == root2.val &&
            dfs(root1.left, root2.left) &&
            dfs(root1.right, root2.right)
        );
    };
    return (
        dfs(root, subRoot) ||
        isSubtree(root.left, subRoot) ||
        isSubtree(root.right, subRoot)
    );
};
```

### **...**

```

```

<!-- tabs:end -->
