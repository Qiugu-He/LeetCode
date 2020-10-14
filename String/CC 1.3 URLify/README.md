## #1.3 URLify: Replace all spaces in a string with '%20'. You may assume that the string has sufficient space at the end to hold the additional characters, and that you are given the "true" length of the string.

```
e.g.: 
    Input: "Mr John Smith   ", 13
    Output:"Mr%20John%20Smith"

```


## Solution: Sort the strings
```Java
/*
- Edit the string starting from the end and working backwards

- First pass, count the number of spaces. By tripling this number, we can compute how many extra characters we will have in the final string. 

- Second pass, which is done in reverse order, edit the string. When see a space, replace it with %20. If there is no space, then we copy the original character. 

*/

class Solution { 
    public void replaceSpace(char[] str, int trueLength){
        int spaceCount = 0, index, i =0;

        //count spaces
        for(i = 0; i< trueLength; i++){
            if(str[i] == ' ')
                spaceCount++;
        }

        //replacing, start from Back
        index = trueLength + spaceCount*2;

        if(trueLength < str.length){
            str[trueLength] = '\0';
        }

        for( i = trueLength - 1; i>=0; i--){
            if(str[i] == ' '){
                str[index-1] = '0';
                str[index-2] = '2';
                str[index-3] = '%';

                index = index-3;
            }else{
                str[index -1] = str[i];
                index --;
            }
        }
    }
}
```
