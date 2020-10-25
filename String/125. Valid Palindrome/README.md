## 125. Valid Palindrome

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

Note: For the purpose of this problem, we define empty string as valid palindrome.

```
Example 1:

Input: "A man, a plan, a canal: Panama"
Output: true
Example 2:

Input: "race a car"
Output: false
```

```Java

/*
    - Choose two pointers to scan from left and right, until the left pointer meets the right pointer.
    - if any pointer pointing to a invalid character, (special character, space) it skip this character.
    - When left pointer and right pointer pointing at different valid character, we exit and return false.

*/
class Solution {
    public boolean isPalindrome(String s) {
        int l =0;
        int r = s.length() -1;
        
        char c1;
        char c2;
        
        while(l <= r){
            c1 = s.charAt(l);
            c2 = s.charAt(r);
            
            //skip the special char
            if(!Character.isLetterOrDigit(c1)){
                l++;
            }
            
            else if(!Character.isLetterOrDigit(c2)){
                r--;
            }
            
            else{
                //check if two letters are same
                
                if(Character.toLowerCase(c1) != Character.toLowerCase(c2)){
                    return false;
                }
                                       
                l++;
                r--;
            }

        }
        
        return true;
        
    }
}
```