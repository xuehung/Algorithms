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

---

Given an unsorted array, find the max j - i difference between indices such that j > i and a[j] > a[i] in O(n)
[Solution](http://stackoverflow.com/questions/18281625/find-the-max-difference-between-j-and-i-indices-such-that-j-i-and-aj-ai)

---

### Best Time to Buy and Sell Stock
Design an algorithm to find the maximum profit. You may complete at most two transactions.
[Solution](https://oj.leetcode.com/discuss/18330/is-it-best-solution-with-o-n-o-1)
```Java
public int maxProfit(int[] prices) {
    int hold1 = Integer.MIN_VALUE, hold2 = Integer.MIN_VALUE;
    int release1 = 0, release2 = 0;
    for(int i:prices){                              // Assume we only have 0 money at first
        release2 = Math.max(release2, hold2+i);     // The maximum if we've just sold 2nd stock so far.
        hold2    = Math.max(hold2,    release1-i);  // The maximum if we've just buy  2nd stock so far.
        release1 = Math.max(release1, hold1+i);     // The maximum if we've just sold 1nd stock so far.
        hold1    = Math.max(hold1,    -i);          // The maximum if we've just buy  1st stock so far.
    }
    return release2; ///Since release1 is initiated as 0, so release2 will always higher than release1.
}
```

### Longest Valid Parentheses
For "(()", the longest valid parentheses substring is "()", which has length = 2.
Another example is ")()())", where the longest valid parentheses substring is "()()", which has length = 4.
[Solution](https://oj.leetcode.com/discuss/24045/simple-java-solution)
```Java
public int longestValidParentheses(String s) {
    char[] S = s.toCharArray();
    int[] V = new int[S.length];
    int open = 0;
    int max = 0;
    for (int i=0; i<S.length; i++) {
        if (S[i] == '(') open++;
        if (S[i] == ')' && open > 0) {
            V[i] = 2 + V[i-1] + (i-2-V[i-1] > 0 ? V[i-2-V[i-1]] : 0);
            open--;
        }
        if (V[i] > max) max = V[i];
    }
    return max;
}
```

---

### Longest Increasing Subsequence (LIS)
```Java
int lis(int[] a) {
    if (a.length == 0) return 0;
    stack.push(a[0]);
    for (int i = 1 ; i < a.length ; i++) {
        if (stack.peek() < a[i]) {
            stack.push(a[i]);
        } else {
            // can use binary search here
            int i = k where stack.get(k) is the first number > a[i]
            stack.set(k, a[i]);
        }
    }
    return stack.size();
}
```

---

### Longest Common Subsequence (LCS)
```Java
dp[i][j] = LCS of s1.substring(0, i) and s2.substring(0, j)
if (s1.charAt(i - 1) == s2.charAt(j - 1)) {
    dp[i][j] = dp[i - 1][j - 1]
} else {
    dp[i][j] = Math.max(dp[i][j - 1], dp[i - 1][j])
}
```

---

### Largest Empty Rectangle
```Java
Build dp[][] where dp[i][j] is the histogram height at array[i][j]
for (i in 0..H) {
    for (j in 0..W) {
        int h = dp[i][j];
        if (stack.isEmpty() || h > dp[i][stack.top()]) {
            stack.push(j)
        } else {
            while(!stack.isEmpty() && h < dp[i][stack.top()]) {
                max = Math.max(max, h * (j - stack.top()))
                stack.pop()
            }
            if (stack.isEmpty() || h > dp[i][stack.top()]) {
                stack.push(j)
            }
        }
    }
    // do similar with the remaing elements in the stack
    area = dp[i][stack.top()] * (W - stack.top())
    max = Math.max(area, max)
}
```
[Solution](http://www.csie.ntnu.edu.tw/~u91029/MaximumSubarray.html#2)

---

### Backpack Problem
Given n items with size A[i], an integer m denotes the size of a backpack. How full you can fill this backpack?

```Java
public int backPack(int m, int[] A) {
    int[] dp = new int[m + 1];
    // for all items
    for (int i = 0 ; i < A.length ; i++) {
        for (int w = m ; w - A[i] >= 0 ; w--) {
            dp[w] = Math.max(
                    dp[w], // not put this item
                    dp[w - A[i]] + A[i] // put htis item
                    );
        }
    }
    return dp[m];
}
```
What if each item has unlimited quantity? How to solve this problem?
---

### Lowest Common Ancestor in a Binary Tree
 - Find the pathes to n1 and n2, then compare pathes
 - Resursive
```Java
LCA(root, n1, n2) {
    if (root == null) return null;
    if (root.val == n1 || root.val == n2) return root;
    Node left = LCA(root.left, n1, n2);
    Node right = LCA(root.right, n1, n2);
    if (left != null && right != null) return root;
    return (left != null) ? left : right;
}
```
You can do better in binary search tree. How?

---

### Money Changing Problem


---

### Given an array arr[], find the maximum j – i such that arr[j] > arr[i]

---

### Find Majority

### Trapping Rain Water
