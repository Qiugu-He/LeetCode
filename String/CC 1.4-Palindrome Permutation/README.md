## #1.3 URLify:  Given a string, write a function to check if it is a permutation of a palindrome. A palindrome is a word or phrase that is the same forwards and backwards. A permutation is a rearrangement of letters. The palindrome does not need to be limited to just dictionary words. 
```
e.g.: 
    Input: Tact Coa
    Output: True ("Taco cat")

```
## Solution 2: Coutns # 0f odd when go along the string
```Java

class Solution { 
    public isPermutationPalindorme(String s){
        int count = 0;
        int [] table = new int[Character.getNumericValue('z') - Character.getNumericValue('a') + 1];

        for(char c: s.toCharArray()){
            int x = getCharNumber(c);

            if(x!= -1){
                table[x] ++;
                if(table[x]%2 == 1){
                    count ++;
                }else{
                    count --;
                }
            }
        } 

        return count <= 1;
    }
}
```

## Solution 1: Building a HashTable to store the char counts
```Java
/*
    - if the length is "Even", we need to have even counts for each charactor

    - if the length is odd, we must only have 1 chars has odd counts

    - Using Hashtable to count the frequence of each char

*/

class Solution { 
    public boolean replaceSpace(String s){
       int [] table = buildCharFrequenceTable(s);
       return checkMaxOneOdd(table);
    }

    int [] buildCharFrequenceTbale(String s){
        int [] table = new int[Character.getNumericValue('z') - Character.getNumericValue('a') + 1];

        for(char c: s.toCharArray()){
            int x = getCharNumber(c);

            if(x != -1){
                table[x] ++;
            }
        }
    }

    int getCharNumber(Char c){
        int a = Character.getNumericValue('a');
        int z = Character.getNumericValue('z');
        int val = Character.getNumericValue('c');

        if(a <= val && val <= z){
            return val-a;
        }

        return -1;
    }

    boolean checkMaxOneOdd(int [] Table){
        boolean found = false;

        for(int counts: table){
            if(count %2 == 1){
                if(found){
                    return false;
                }
                found = true;
            }
        }

        return true;
    }
}
```
