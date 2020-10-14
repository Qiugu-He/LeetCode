Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.
```
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```

Example:
```
Input: s = "III"
Output: 3

Input: s = "IV"
Output: 4

Input: s = "IX"
Output: 9

Input: s = "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.

Input: s = "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.

```

Solution 2: 
```Java

/*
        Pesudo: 
            - Create HashMap

            - result = map(s.charAt(len))

            - loop: Strat char i at end from len -2, For each i at string
            -   if(  map(char[i] > = map(char[i+1]  )  
            -       reuslt += map(char[i])
            -   else
            -       result -= map(char[i])
            -
            - return result
        

        e.g.:
            MCMXCIV:
              result = V
              IV: I < V     result -= I
              CI: C > I     result += C
              XC: X < C     result -= X
              MX: M > X     reuslt += M
              CM: C < M     reuslt -= C
              MC: M > C     result += M

            result = V - I + C - X + M - C + M 
                   = 5 - 1 + 100 - 10 + 1000 - 100 + 1000
                   = 4 + 90 + 900 + 1000
                   = 1994

*/
class Solution {
    public int romanToInt(String s) {
       if(s == null || s.length() == 0)
        return -1;

        //store HashMap
        HashMap<Character, Integer> map = new HashMap<Character, Integer>();
        map.put('I', 1);
        map.put('V', 5);
        map.put('X', 10);
        map.put('L', 50);
        map.put('C', 100);
        map.put('D', 500);
        map.put('M', 1000);

        int result = map.get(s.charAt(s.length()-1));

        for(int i = s.length()-2;i >= 0; i--){
            if(map.get(s.charAt(i)) >= map.get(s.charAt(i+1))){
                result += map.get(s.charAt(i));
            }else{
                result -= map.get(s.charAt(i));
            }

        }
        return result;
    }
}

```
Solution 1: 
```Java
class Solution {
    public int romanToInt(String s) {
        int nums[]=new int[s.length()];

        //store each roman value in string into integer
        for(int i =0; i < s.length(); i++){
            switch(s.charAt(i)){
                case 'M':
                    nums[i] = 1000;
                case 'D':
                    nums[i] = 500;
                case 'C':
                    nums[i] = 100;
                case 'L':
                    nums[i] = 50;
                case 'X':
                    nums[i] = 10;
                case 'V':
                    nums[i] = 5;
                case 'I':
                    nums[i] = 1;
            }
        }

        int result = 0;
        //sum the result
        for(int i =0; i< nums.length-1; i++){
            if(nums[i] < nums[i+1]){
                result-=nums[i];
            }else{
                result+=nums[i];
            }
        }

        return result + nums[nums.length-1];
    }
}

```