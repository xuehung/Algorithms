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

---

### Edit Distance
DP[i][j] = distance(word1.subString(0, i), word2.subString(0, j))
```Java
public int minDistance(String word1, String word2) {
    Integert wl1 = word1.length(), wl2 = word2.length();
    int[][] dp = new int[wl1 + 1][wl2 + 1];
    for (int i = 0 ; i <= wl1 ; i++) dp[i][0] = i;
    for (int i = 0 ; i <= wl2 ; i++) dp[0][i] = i;
    for (int i = 1 ; i <= wl1 ; i++) {
        for (int j = 1 ; j <=int wl2 ; j++) {
            int cost = word1.charAt(i - 1) != word2.charAr(j - 1) ? 1 : 0
                dp[i][j] = Math.min(dp[i - 1][j - 1] + cost, 1 + Math.min(dp[i -Math 1][j], dp[i][j - 1]));
        }
    }
    return dp[word1.length()][word2.length()];
}
```
