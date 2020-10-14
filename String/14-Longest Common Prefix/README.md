Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".


Example:
```
Input: strs = ["flower","flow","flight"]
Output: "fl"

Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.

```

Solution 1: Horizontal Scanning
```Java
class Solution {
   public String longestCommonPrefix(String[] strs) {
    if (strs.length == 0) return "";
    String prefix = strs[0];
    for (int i = 1; i < strs.length; i++)
        while (strs[i].indexOf(prefix) != 0) {
            prefix = prefix.substring(0, prefix.length() - 1);
            System.out.println();
            if (prefix.isEmpty()) return "";
        }        
    return prefix;
    }
}
```

Solution 2: Sort the array, compare 1st and last sts in array
```Java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        StringBuilder result = new StringBuilder();
        
        if (strs!= null && strs.length > 0){
            Arrays.sort(strs);

            //Compare first str and last str
            char [] a = strs[0].toCharArray();
            char [] b = strs[strs.length-1].toCharArray();
            for (int i = 0; i < a.length; i ++){
                if (b.length > i && b[i] == a[i]){
                    result.append(b[i]);
                }
                else {
                    return result.toString();
                }
            }
        }
        return result.toString();
    }
}
```