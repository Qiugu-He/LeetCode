## 3. Longest Substring Without Repeating Characters

Given a string s, find the length of the longest substring without repeating characters.

```
Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

```Java

/*
    Apprach: HashTable / Sliding Window

    Window (i , j) with unique characters
    1. Use a hashTable to store the last indies of each charactor
    2. Keep track the valid starting point
        a. when there is a match update the starting point to the current one
     
    i = max(i, map.get(s.charAt(j)), i+1)
    ans = max( ans, j - i + 1 )


    E.g.:
    "abcabcbb"
    s[j]    j   i   map             ss
    a       0   0   a:0             a
    b       1   0   a:0 b:1         ab
    c       2   0   a:0 b:1 c:2     abc

    a       3   1   a:3 b:1 c:2     bca
    b       4   2   a:3 b:4 c:2     cab
    c       5   3   a:3 b:4 c:5     abc
    b       6   5   a:4 b:6 c:5     cb
    b       7   7   a:4 b:7 c:5     b

*/
    public int lengthOfLongestSubstring(String s) {
        int n = s.length(), ans = 0;
        Map<Character, Integer> map = new HashMap<>();
        
        for(int j = 0, i =0; j < n; j++){
            if(map.containsKey(s.charAt(j)))
                i = Math.max(map.get(s.charAt(j)), i);

            ans = Math.max(ans, j - i + 1);
            map.put(s.charAt(j), j+ 1);
        }
        
        return ans;
    }
```