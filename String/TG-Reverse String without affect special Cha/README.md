## Reverse a string without affecting special characters

Given a string, that contains special character together with alphabets (‘a’ to ‘z’ and ‘A’ to ‘Z’), reverse the string in a way that special characters are not affected.

```
Input:   str = "a,b$c"
Output:  str = "c,b$a"
Note that $ and , are not moved anywhere.  

Input:   str = "Ab,c,de!$"
Output:  str = "ed,c,bA!$"
```

```Java
/*
    1) init string be 'str[]' and length of string be 'n'
    2) l = 0, r = n-1
    3) While l is smaller than r, do following
        a) If str[l] is not an alphabetic character, do l++
        b) Else If str[r] is not an alphabetic character, do r--
        c) Else swap str[l] and str[r]
*/

void reverse(char str[]) 
{ 
    // Initialize left and right pointers 
    int r = str.length - 1, l = 0; 

    // Traverse string from both ends until 
    // 'l' and 'r' 
    while (l < r) 
    { 
        // Ignore special characters 
        if (!Character.isAlphabetic(str[l])) 
            l++; 
        else if(!Character.isAlphabetic(str[r])) 
            r--; 

        // Both str[l] and str[r] are not spacial 
        else 
        { 
            char tmp = str[l]; 
            str[l] = str[r]; 
            str[r] = tmp; 
            l++; 
            r--; 
        } 
    }
} 
```