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

### Binary Tree Postorder Traversal Iteratively
```Java
Stack<TreeNode> stack = new Stack()
stack.push(root)
List<Integer> output = new ArrayList<Integer>()
while (!stack.isEmpty) {
    TreeNode curr = stack.pop()
    if (curr == null) continue
    output.add(curr.val)
    stack.push(curr.left)
    stack.push(curr.right)
}
Collections.reverse(output)
```

---

### DFS
```Java
void DFS(Node node) {
    if (node visited) return
    for (Node n : node.neighbors) {
        DFS(n)
    }
}
```
