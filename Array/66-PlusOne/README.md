## #66. PlusOne
Given a non-empty array of digits representing a non-negative integer, increment one to the integer.
The digits are stored such that the most significant digit is at the head of the list, and each element in the array contains a single digit.
```
    Input: [1,2,3]
    Output: [1,2,4]
    Explanation: The array represents the integer 123, then plus 1 is 124
```

## 0(n) Solution
```Java
/* 
Using sum and carry

Pseudo
    increment = 1
    Loop through the arry of digits, backfoward
        if increment + digit[i] == 0, then needs to carry
            digit[i] = 0

        else, no need to worry about carry
            simply increate the last digit and return
    
    Finally, carry add to the very first digit
*/
public class Solution {
    public int[] plusOne(int[] digits) {
        if(digits == null) 
            return digits;
        
        int carry = 1;
        //start at end
        for(int i = digits.length-1; i >= 0; i--){
            
            //if needs to carry
            if(carry + digits[i] == 10){
                digits[i] = 0;
                carry = 1;
            }
            //no need to carry, simply increase last digit
            else{
                digits[i]++;
                return digits;
            }
        }
        
        //Carry for the very first digit
        int[] ans = new int[digits.length+1];
        ans[0] = 1;
        return ans;
    }
}
/*
Time complextiy : O(n)
*/
```




