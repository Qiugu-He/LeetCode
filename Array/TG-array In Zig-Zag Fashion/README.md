## Convert array into Zig-Zag fashion

Given an array of DISTINCT elements, rearrange the elements of array in zig-zag fashion in O(n) time. The converted array should be in form:
                         a < b > c < d > e < f. 

```
Input: arr[] = {4, 3, 7, 8, 6, 2, 1} 
Output: arr[] = {3, 7, 4, 8, 2, 6, 1}

Input: arr[] = {1, 4, 3, 2} 
Output: arr[] = {1, 4, 2, 3}
```

```Java
/*
        Sort: O( n log n )

        1) First sort the array
        2) After sorting, exclude the first element, swap the remaining elements in pairs. 
           (i.e. keep arr[0] as it is, swap arr[1] and arr[2], swap arr[3] and arr[4], and so on). 
*/

void ZigZag(int [] arr){

    // Flag true indicates relation "<" is expected,  
    // else ">" is expected. 
    boolean flag = true;
    int temp = 0;
    for (int i=0; i<=arr.length-2; i++)  
    {  
        if (flag) /* "<" relation expected */
        {  
            /* If we have a situation like A > B > C,  
            we get A > B < C by swapping B and C */
            if (arr[i] > arr[i+1])  
            {  
                // swap  
                temp = arr[i];  
                arr[i] = arr[i+1];  
                arr[i+1] = temp;  
            }  
                
        }  
        else /* ">" relation expected */
        {  
            /* If we have a situation like A < B < C,  
            we get A < C > B by swapping B and C */
            if (arr[i] < arr[i+1])  
            {  
                // swap  
                temp = arr[i];  
                arr[i] = arr[i+1];  
                arr[i+1] = temp;  
            }  
        }  
        flag = !flag; /* flip flag */
    }//for  
}
```