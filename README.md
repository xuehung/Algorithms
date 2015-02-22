# Algorithms


### Binary Tree Inorder Traversal Iteratively
```Java
Stack<TreeNode> stack = new Stack()
TreeNode curr = root
while (curr != null || !stack.isEmpty) {
    if (curr != null) {
        stack.push(curr)
        curr = curr.left
    } else {
        curr = stack.pop()
        print curr.val
        curr = curr.right
    }
}
```

---

### DFS
```Java
void DFS(Node node) {
    if (node visited) return;
    for (Node n : node.neighbors) {
        DFS(n)
    }
}
```
