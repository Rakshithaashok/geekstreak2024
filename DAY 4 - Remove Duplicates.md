## Remove Duplicates [https://www.geeksforgeeks.org/problems/remove-duplicates3034/1]

Given a string str without spaces, the task is to remove all duplicate characters from it, keeping only the first occurrence.

Note: The original order of characters must be kept the same. 

## Examples :

Input: str = "zvvo"

Output: "zvo"

Explanation: Only keep the first occurrence

Input: str = "gfg"

Output: "gf"

Explanation: Only keep the first occurrence

Expected Time Complexity: O(n)

Expected Auxiliary Space: O(1)

Constraints:

1 <= |str| <= 105

str contains lowercase English alphabets

## Code 

```
class Solution {
    String removeDups(String str) {
        // code here
        StringBuilder s = new StringBuilder();
        for(char c : str.toCharArray()){
            if(s.indexOf(String.valueOf(c)) < 0){
                s.append(c);
            }
        }
        return s.toString();
    }
}
```

## Explanation

- StringBuilder s = new StringBuilder(); : Initializes a StringBuilder to build the result string efficiently.
- for (char c : str.toCharArray()): Loops over each character in the input string converted to a character array.
- if (s.indexOf(String.valueOf(c)) < 0): Checks if the character c is already in the StringBuilder using indexOf. If the character is not found (indexOf returns -1), it proceeds to the next step.
- s.append(c);: Appends the character c to the StringBuilder if it is not a duplicate.
- return s.toString();: Converts the StringBuilder back to a string and returns it.
