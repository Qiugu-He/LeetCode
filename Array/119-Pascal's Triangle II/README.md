## #118. Pascal's Triangle
Given a non-negative integer numRows, generate the first numRows of Pascal's triangle.
In Pascal's triangle, each number is the sum of the two numbers directly above it.

<img src="https://github.com/Qiugu-He/LeetCode/blob/master/Array/118-Pascal's%20Triangle/pic.png" alt="My cool logo"/>
```
    Input: 5
    Output:
    [
            [1],
           [1,1],
          [1,2,1],
         [1,3,3,1],
        [1,4,6,4,1]
    ]
```

## O(n) Solution
```Java

    /*
        This problem using Dynamic programming approach

        Time complexity : O(n^2)
        Space complexity: O(n^2)

        Pesudo Code:
        Triangel init

        //Base case 1:
        rowNums is 0, then there are 0 rows

        //Base case 2: 
        The first row always 1

        For each remaining row r:
            the first element always 1

            for each remaining element j till j -1, the value of j is:
                sum { [row-1][j-1], [row-1][j] }
        
            The last element of a row alwyas 1
        
        return Triangel

    */
    class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> triangle = new ArrayList<List<Integer>>();
        
        //base case 1: if user requests zero rows, they get zero rows.
        if(numRows == 0){
            return triangle;
        }
        
        //base case 2: first row is always [1].
        triangle.add(new ArrayList<>());
        triangle.get(0).add(1);
        
        //processing the remaining rows, start at twp
        for(int r = 1; r < numRows; r++){
            List<Integer> row = new ArrayList<>();
            List<Integer> prevRow = triangle.get(r-1);
            
            // The row's first element always 1.
            row.add(1);
            
            /*
                For each element in a row(expect the first and last of each row)
                = sum { its above and left, its above }
            */
            for(int j = 1; j< r; j++){
                row.add(prevRow.get(j-1) + prevRow.get(j));
            }
            
            // The Row's last element always 1.
            row.add(1);
            
            triangle.add(row);
        }
        
        return triangle;
    }
}
```




