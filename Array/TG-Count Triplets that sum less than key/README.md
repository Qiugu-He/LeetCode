## Count triplets with sum smaller than a given value

Given an array of distinct integers and a sum value. Find count of triplets with sum smaller than given sum value. Expected Time Complexity is O(n^2).

```
Input : arr[] = {-2, 0, 1, 3}
        sum = 2.
Output : 2
Explanation :  Below are triplets with sum less than 2
               (-2, 0, 1) and (-2, 0, 3) 

Input : arr[] = {5, 1, 3, 4, 7}
        sum = 12.
Output : 4
Explanation :  Below are triplets with sum less than 12
               (1, 3, 4), (1, 3, 5), (1, 3, 7) and 
               (1, 4, 5)
```

```Java
/*
    Brute Force: 3 loops ---> O(n^3)

*/

int count(int arr, int sum){
    int result = 0;

    for(int i =0; i< arr.length -2 ; i++){
        for(int j=i+1; j< arr.length -1; j++){
            for(int k = j+ 1; k< arr.length; j++){
                if(arr[i] + arr[j] + arr[k] < sum){
                    result ++;
                }
            }
        }
    }//for

    return result;
}




int countTriplets(int n, int sum) 
    { 
        // Sort input array 
        Arrays.sort(arr); 
       
        int ans = 0; 
       
        // Every iteration of loop counts triplet with first element as arr[i]. 
        for (int i = 0; i < n - 2; i++) 
        { 
            // Initialize other two elements as corner elements of subarray arr[j+1..k] 
            int j = i + 1, k = n - 1; 
       
            // Use Meet in the Middle concept 
            while (j < k) 
            { 
                // If sum of current triplet is more or equal, 
                // move right corner to look for smaller values 
                if (arr[i] + arr[j] + arr[k] >= sum) 
                    k--; 
       
                else
                { 
                    // This is important. For current i and j, there 
                    // can be total k-j third elements. 
                    ans += (k - j); 
                    j++; 
                } 
            } 
        } 
        return ans; 
    } 
```