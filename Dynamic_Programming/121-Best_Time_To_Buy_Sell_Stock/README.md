## #121. Best Time to Buy and Sell Stock    
Given a an array for which the ith element is the price of a given stock on day i.
If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Note that you cannot sell a stock before you buy one.

```
    Input: [7,1,5,3,6,4]
    Output: 5
    Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
    Not 7-1 = 6, as selling price needs to be larger than buying price.
```

## Brute Force
```Java
    /*
        Using Brute Force to find the maxmim difference between two numbers
        I.e. 
        Max(prices[j]−prices[i]), for every i and j such that j > i.

        Time complexity : O(n^2)
        Space complexity : O(1)
    */

    class Solution {
        public int maxProfit(int[] prices) {
            int maxDif = 0;

            for(int i =0; i< prices.length; i++){
                for(int j = i+1; j< prices.length; j++){
                    int dif = prices[j] - prices[i];

                    if(dif > maxDif){
                        maxDif = dif;
                    }
                }
            }           

            return maxDif;
        }
}
```

## Dynamic programming - One Pass, Peak Valley Approach
```Java
    /*
        In the approach, we maintain two variables: 
            - the minmum price
            - the maxProfit corresponding smallest valley and maxProfit

        Time complexity : O(n)
        Space complexity : O(1)
    */

    class Solution {
        public int maxProfit(int[] prices) {
            int mimP = Integer.Max_value;
            int maxDif = 0;

            for(int i =0; i< prices.length; i++){
                if(prices[i] < mimP){
                    mimP = prices[i];
                }
                else if( prices[i] - mimP > maxDif){
                    maxDif = prices[i] - mimP ;
                }
            }

            return maxDif;
        }
}

```




