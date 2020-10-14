## #1.2 Check Permutation: Given two strings, write a method to decide if one is a permutation of the other. 


## Solution 1: Sort the strings
```Java
/*
If two strings are permutations:  they have the same characters, but in different orders. Therefore: 
	▪ Sorting the strings will put the characters from two permutations in the same order. 
	▪ Then compare the sorted versions of the strings
*/

class Solution { 
    Public boolean isPermutation(String s, String t){
        if(s.length() != t.length())
            return false;
        
        return sort(s).euqls(sort(t));
    }

    String sort(String s){
        char[] chars = s.toCharArray();
        java.util.Arrays.sort(chars);
        return new String(chars);
    }
}

```

## Solution 2:  Check if the two strings have identical character counts
```Java
/*
Permutation: two words with the same character counts. 
	▪ Counting how many times each character appears of one array. 
	▪ Then, compare the counts of two arrays. 

*/

class Solution { 
    Public boolean isPermutation(String s, String t){
        if(s.length() != t.length())
            return false;
        
        int[]letters = new int[128];

        //store each letter counts of s into array
        char[]s_array = s.toCharArray();
        for(char c :s_array){
            letters[c]++;
        }

        //check string t
        for(int i =0; i< t.length(); i++){
            int c = (int)t.charAt(i);
            letter[c]--;
            if(letter[c] < 0){
                return false;
            }
        }//for

        return true;
    }
}

```