## Row with max 1s [https://www.geeksforgeeks.org/problems/row-with-max-1s0023/1]

Given a boolean 2D array, consisting of only 1's and 0's, where each row is sorted. Return the 0-based index of the first row that has the most number of 1s. If no such row exists, return -1.

## Examples:

Input: arr[][] = [[0, 1, 1, 1],
               [0, 0, 1, 1],
               [1, 1, 1, 1],
               [0, 0, 0, 0]]

Output: 2

Explanation: Row 2 contains 4 1's (0-based indexing).

Input: arr[][] = [[0, 0], 
               [1, 1]]

Output: 1

Explanation: Row 1 contains 2 1's (0-based indexing).

Expected Time Complexity: O(n+m)

Expected Auxiliary Space: O(1)

Constraints:

1 ≤ number of rows, number of columns ≤ 103

0 ≤ arr[i][j] ≤ 1 

## Code

```
class Solution {
    public int rowWithMax1s(int arr[][]) {
        // code here
        int max = Integer.MIN_VALUE;
        int index = -1;
        int count = 0;
        for(int i = 0; i < arr.length; i++){
            count = 0;
            for(int j = 0; j < arr[i].length; j++){
                if(arr[i][j] == 1){
                    count++;
                }
            }
            if(count > max){
                max = count;
                index = i;
            }
        }
        if(max == 0){
            index = -1;
        }
        return index;
    }
}
```

## Explanation 

- The rowWithMax1s function aims to find the index of the row that contains the maximum number of 1s in a given 2D binary matrix.
- int max = Integer.MIN_VALUE; initializes the maximum count of 1s to the smallest possible integer value
- int index = -1; initializes the row index to -1, indicating no row found yet with 1s.
- int count = 0; is used to count the number of 1s in the current row.

**Outer Loop:**
- for(int i = 0; i < arr.length; i++) iterates over each row of the matrix.

**Inner Loop:**
- for(int j = 0; j < arr[i].length; j++) iterates over each element in the current row.
  
- if(arr[i][j] == 1) count++; increments the count for each 1 found in the row.

- if(count > max){ max = count; index = i; } updates the max and index if the current row has more 1s than previously found rows.

- if(max == 0) index = -1; ensures the function returns -1 if no 1s are found in any row.

- return index; returns the index of the row with the maximum number of 1s.
