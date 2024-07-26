## K-Pangrams [https://www.geeksforgeeks.org/problems/k-pangrams0909/1]

Given a string str and an integer k, return true if the string can be changed into a pangram after at most k operations, else return false.

A single operation consists of swapping an existing alphabetic character with any other alphabetic character.

Note - A pangram is a sentence containing every letter in the english alphabet.

## Examples :

Input: str = "the quick brown fox jumps over the lazy dog", k = 0

Output: true

Explanation: the sentence contains all 26 characters and is already a pangram.

Input: str = "aaaaaaaaaaaaaaaaaaaaaaaaaa", k = 25 

Output: true

Explanation: The word contains 26 instances of 'a'. Since only 25 operations are allowed. We can keep 1 instance and change all others to make str a pangram.

Input: str = "a b c d e f g h i j k l m", k = 20

Output: false

Explaanation: Since there are only 25 charaacters only in this case, so no amount of swapping we can have complete alphabets here.

Expected Time Complexity: O(n)

Expected Auxiliary Space: O(1)  

Constraints:

1<= str.size() <= 105

0<= k <= 50

str may contain duplicate characters.

str contains only lowercase alphabets or spaces.

## Code 

```
class Solution {
    boolean kPangram(String str, int k) {
        // code here
        boolean[] present = new boolean[26];
        int charCount = 0;
        for(char c : str.toCharArray()){
            if(c == ' '){
                continue;
            }
            charCount++;
            present[c - 'a'] = true;
        }
        
        int count = 0;
        for(boolean isPresent : present){
            if(!isPresent)
                count++;
        }
        return k >= count && charCount >= 26;
    }
}
```

## Code Explanation 

**Boolean Array Initialization:**
- boolean[] present = new boolean[26];
- This array tracks the presence of each letter in the alphabet. Each index corresponds to a letter where present[0] is 'a', present[1] is 'b', and so on.

**Character Count Initialization:**
- int charCount = 0;
- This variable counts the number of non-space characters in the string.

**Processing the String:**
- for (char c : str.toCharArray()) { ... }
- Iterates through each character in the string. If the character is not a space, it marks the letter as present in the present array and increments charCount.

**Counting Missing Letters:**
- int count = 0;
- This counter tracks how many letters of the alphabet are missing from the string.
- for (boolean isPresent : present) { ... }
- Iterates through the present array and counts the number of false values, which represent missing letters.

**Feasibility Check:**
- return k >= count && charCount >= 26;
- Checks if the allowed number of operations k is sufficient to cover all missing letters and ensures that the total number of non-space characters is at least 26, which is necessary to accommodate all letters of the alphabet.
