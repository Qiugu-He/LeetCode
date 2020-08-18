## #119. Pascal's Triangle II
Given an integer rowIndex, return the rowIndexth row of the Pascal's triangle.
Notice that the row index starts from 0.

```
    N: 5
    Pascal's Triangle:
    [
        [1],
        [1,1],
        [1,2,1],
        [1,3,3,1],
        [1,4,6,4,1]
    ]

    Input: rowIndex = 3
    Output: [1,3,3,1]
```

## O(n) Solution
```Java
/*
    Strategy:
    This algorithm init a single ArrayList, expanding and replacing elements in it when we build for each row
        for row != 0 && row = last
            row[j] = sum { row[j] + row[j-1] }

    for example:
        row = 0
        Al = [1]
        row = 1
        Al = [1,1]
        row = 2 
        Al = [1,2,1]
        row = 3
        Al = [1,3,3,1]
*/

class Solution {
     public List<Integer> getRow(int rowIndex) {
         List<Integer> res = new ArrayList<Integer>();

         for(int i =0; i< rowIndex; i++){
             res.add(1);
             for(int j = i; j >= 0; j< --){
                 if(j != 0 && j != i){
                     result.set(j, result.get(j) + result.get(j-1));
                 }
             }
         }

         return res;
    }
}

```




