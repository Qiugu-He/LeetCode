## 202. Happy Number

Write an algorithm to determine if a number n is "happy".

A happy number is a number defined by the following process:
-  Starting with any positive integer, replace the numbe: 
    - by the sum of the squares of its digits, and repeat the process until the number equals 1

-  or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

Return True if n is a happy number, and False if not.


```Java
    class Solution {
    public boolean isHappy(int n) {
        
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        
        while(true){
            String str1 = Integer.toString(n);
            char [] nc = str1.toCharArray();
            
            int sum = 0;
            for(int i =0; i < nc.length; i++){
                sum += Math.pow(nc[i], 2);
            }
            
            if(sum == 1)
                return true;
            
            else if (map.get(sum) == 1)
                return false;
            
            else
                map.put(sum, map.get(sum)++);
                n = sum;
        }
       return false;
    
    }
}
     
```