## Edit Distance
Given two strings str1 and str2 and below operations that can performed on str1. Find minimum number of edits (operations) required to convert ‘str1’ into ‘str2’.
1. Insert
2. Remove
3. Replace
All of the above operations are of equal cost.

```
E.g.:
Input:   str1 = "geek", str2 = "gesek"
Output:  1
We can convert str1 into str2 by inserting a 's'.

Input:   str1 = "cat", str2 = "cut"
Output:  1
We can convert str1 into str2 by replacing 'a' with 'u'.

Input:   str1 = "sunday", str2 = "saturday"
Output:  3
Replace 'n' with 'r', insert t, insert a
```


```Java
/*
    Building a Dynamic table, fill each cell at minimum cast
        - i = 0 -> insert: dp[i][j] = j
        - j = 0 -> insert: dp[i][j] = i
        - str1.charAt(i - 1) == str2.charAt(j - 1): dp[i][j] = dp[i - 1][j - 1]; 
        - else: 
            dp[i][j] = 1 + min(dp[i][j - 1], // Insert 
                               dp[i - 1][j], // Remove 
                               dp[i - 1][j - 1]); // Replace 
*/
int editDistDP(String str1, String str2, int m, int n) 
{ 
    // Create a table to store results of subproblems 
    int dp[][] = new int[m + 1][n + 1]; 

    // Fill d[][]
    for (int i = 0; i <= m; i++) { 
        for (int j = 0; j <= n; j++) { 
            // If first string is empty, only option is to 
            // insert all characters of second string 
            if (i == 0) 
                dp[i][j] = j; // Min. operations = j 

            // If second string is empty, only option is to 
            // remove all characters of second string 
            else if (j == 0) 
                dp[i][j] = i; // Min. operations = i 

            // If last characters are same, ignore last char 
            // and recur for remaining string 
            else if (str1.charAt(i - 1) == str2.charAt(j - 1)) 
                dp[i][j] = dp[i - 1][j - 1]; 

            // If the last character is different, consider all 
            // possibilities and find the minimum 
            else
                dp[i][j] = 1 + min(dp[i][j - 1], // Insert 
                                    dp[i - 1][j], // Remove 
                                    dp[i - 1][j - 1]); // Replace 
        } 
    } 

    return dp[m][n]; 
} 
```