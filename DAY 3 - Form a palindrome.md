## Form a palindrome [https://www.geeksforgeeks.org/problems/form-a-palindrome1455/1]

**Explanation Video** [https://youtu.be/iQKeblfj6jc?si=wsbxO5SaVLzmb6tw]

Given a string, find the minimum number of characters to be inserted to convert it to a palindrome.

## Examples :

Input: str = "abcd"

Output: 3

Explanation: Inserted character marked with bold characters in dcbabcd, here we need minimum three characters to make it palindrome.

Input: str = "aa"

Output: 0

Explanation: "aa" is already a palindrome.

Expected Time Complexity: O(n2)

Expected Auxiliary Space: O(n2)

Constraints:

1 ≤ |str| ≤ 500

str contains only lowercase alphabets.

## Code 

```
class Solution{
    static int countMin(String str)
    {
        // code here
        int n = str.length();
        String revstr = new StringBuilder(str).reverse().toString();
        int[][] dp = new int[n+1][n+1];
        for(int i = 0; i < n+1; i++){
            for(int j = 0; j < n+1; j++){
                if(i==0 || j == 0){
                    dp[i][j] = 0;
                }
                else if(str.charAt(i-1) == revstr.charAt(j-1)){
                    dp[i][j] = 1 + dp[i - 1][j - 1];
                }
                else{
                    dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
                }
            }
        }
        int lcs = dp[n][n];
        return n - lcs;
    }
    
}
```

## Code Explanation

**Reverse the String:**

Let revstr be the reverse of the string str.

**Create a DP Table:**

Initialize a 2D array dp of size (n+1) x (n+1), where n is the length of str.

- if i = 0 or j = 0 then dp[i][j] = 0 
- else if str.charAt(i-1) == revstr.charAt(j-1), then dp[i][j] = dp[i-1][j-1] + 1. which is left diagonal element + 1;
- else we find the maximum between top element and left element dp[i][j] = max(dp[i-1][j], dp[i][j-1])
- The length of the LCS of str and revstr is stored in dp[n][n]
- The minimum number of insertions required is n - lcs_length, where lcs_length is dp[n][n]
