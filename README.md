# Weekly Coding #5: Skyrail Station Navigator

## Summary
This program implements a binary tree and binary search tree (BST) using
a recursive approach. It supports three classic tree traversals: preorder,
inorder, and postorder. For the BST, it implements search and insertion,
both of which leverage the BST ordering property to efficiently navigate
left or right. Duplicate values are silently ignored during insertion.

## Approach
- **Preorder traversal:** Visits the current node first, then recurses left,
  then right. Base case returns an empty list for a None node.
- **Inorder traversal:** Recurses left first, then visits the current node,
  then recurses right. Produces sorted output for a valid BST.
- **Postorder traversal:** Recurses left and right first, then visits the
  current node last. Useful for deletion or evaluation scenarios.
- **BST search:** Compares the target to the current node's value and recurses
  left if smaller, right if larger, returning True on a match.
- **BST insert:** Navigates left or right based on value comparison until a
  None slot is found, then places a new TreeNode there. Duplicates are ignored
  by doing nothing when values are equal.

## Complexity

**`preorder_values`**
- Time: O(N)
- Space: O(N)
- Why: Every node is visited exactly once. The result list holds all N values.

**`inorder_values`**
- Time: O(N)
- Space: O(N)
- Why: Every node is visited exactly once. The result list holds all N values.

**`postorder_values`**
- Time: O(N)
- Space: O(N)
- Why: Every node is visited exactly once. The result list holds all N values.

**`bst_contains`**
- Time: O(H) where H is the height of the tree
- Space: O(H)
- Why: Each recursive call moves one level deeper. In a balanced BST,
  H = O(log N); in the worst case (skewed tree), H = O(N).

**`bst_insert`**
- Time: O(H)
- Space: O(H)
- Why: Same as search — we follow one path from root to insertion point,
  so depth of recursion equals the height of the tree.

## Edge-Case Checklist
- [x] **Empty tree traversal returns `[]`** — all three traversal functions
  return `[]` immediately when root is None.
- [x] **Single-node traversal works correctly** — with no children, each
  traversal returns just `[root.value]`.
- [x] **`bst_contains` returns `False` for an empty tree** — the base case
  checks `if root is None: return False`.
- [x] **`bst_contains` returns `False` when the target is missing** — the
  recursion exhausts all paths and hits a None node.
- [x] **`bst_insert` creates a root when the tree is empty** — `if root is
  None: return TreeNode(value)` handles this directly.
- [x] **`bst_insert` ignores duplicate values** — the `elif value > root.value`
  condition means equal values fall through without action.
- [x] **Deeper insert case tested** — inserting multiple values builds a
  correct multi-level BST verified by inorder traversal output.

## Assistance & Sources
- **AI used?** Y
- **What AI helped with:** Structuring the recursive base cases for traversal
  and BST operations.
- **Other sources used:** Python Official Documentation for type hints and
  the `__future__` annotations import.

## Test Results
```
Paste your pytest -q output here after running: pytest -q
```