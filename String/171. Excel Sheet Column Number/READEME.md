## 171. Excel Sheet Column Number

Given a column title as appear in an Excel sheet, return its corresponding column number.

```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...
    ZY -> 701
```

```Java
/*  
    Go through each letter c
        - result = result * 26 + (c -'A')+1;

    E.g: 
        AA: 1 + 26 = 27
        AB: 2 + 26 = 28
        ..
        ZY: 
            90 - 65 = 25 + 1 = 26
            (89 - 65) + 1 + 26 * 26 = 701
*/
class Solution {
    public int titleToNumber(String s) {
        int result = 0;
        
        for(char c: s.toCharArray()){
            result = result * 26 + (c -'A')+1;
        }
        
        return result;
    }
}
```