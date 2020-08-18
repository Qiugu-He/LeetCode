## #70. Climbing Stairs
You are climbing a stair case. It takes n steps to reach to the top. 
Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

1 <= n <= 45
```
    Input: 2
    Output: 2
    Explanation: There are two ways to climb to the top.
    1. 1 step + 1 step
    2. 2 steps

    Input: 3
    Output: 3
    Explanation: There are three ways to climb to the top.
    1. 1 step + 1 step + 1 step
    2. 1 step + 2 steps
    3. 2 steps + 1 step
```

## Solution 1: Brute Force
```Java
/* 
- Count all possible step (1 or 2) at each step until resach the goal.
- At each step, recursivly calling function for step 1 and 2, sum the return result for both function is the final result.

- Base case:
        if (i > n)  return 0;
        if (i == n) return 1;

-For example: N= 5, the recursion tree looks like: 

                                      (0, 5)
                        (1,5)                        (2, 5)
                     
                  (2, 5)         (3,5)          (3,5)       (4,5)
                    
           (3,5)      (4,5)   (4,5)   (5,5)  (4,5) (5,5)  (5,5)(6,5)

        (4,5)(5,5) (5,5)(6,5)(5,5)(6,5)               
                

- Time complexcity: O(n^2)
    
*/
public class Solution {
    public int climbStairs(int n) {
        climb(0, n);
    }

    public int climb(int i, int n){
        if(i > n){
            return 0;
        }
        if(i == n){
            return 1;
        }

        return climb(i + 1, n) + climb(i + 2, n);
    }
}
```

## Solution 2: Dynamic Programming
```Java
/* 
There are two ways to reach step i:
    1. Taking 1 step from step (i -1)
    2. Taking 2 step from step (i -2)

Therefore, the total number of ways to reach i:
        sum { # ways of reach (i-1), # was of reach (i-2)}

Let dp[i] denotes # ways each step i:
        dp[i] = dp[i-1] + dp[i-2]

Base case:
    dp[1] = 1;
    dp[2] = 2;

Time complexity: O(n)
*/
public class Solution {
    public int climbStairs(int n) {
        if(n == 1){
            return 1;
        }

        int dp[] = new int [n+1];
        dp[1] = 1;
        dp[2] = 2;
        for(int i = 3; i < dp.length; i ++){
            dp[i] = dp[i-1] + dp[i-2];
        }

        return dp[n];
    }
}
```




