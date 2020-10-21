## Reverse an array or string

Given an array (or string), the task is to reverse the array/string.

```
Input  : arr[] = {1, 2, 3}
Output : arr[] = {3, 2, 1}

Input :  arr[] = {4, 5, 1, 2}
Output : arr[] = {2, 1, 5, 4}
```

```Java
/*  
    Iterative: O(log n)

    1) Initialize start and end indexes as start = 0, end = n-1 
    2) In a loop, swap arr[start] with arr[end] and change start and end as follows : 
       start = start +1, end = end – 1
*/

int reverse (int arr[], int start, int end){
    int temp;

    while(start < end){
        temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start ++ ;
        end --;
    }
}

/*
    Recursive: O(log n)

    1) Initialize start and end indexes as start = 0, end = n-1 
    2) Swap arr[start] with arr[end] 
    3) Recursively call reverse for rest of the array.

*/

int reverse (int arr[], int start, int end){
        int temp;
        if (start >= end)
            return;

        temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;

        rvereseArray(arr, start+1, end-1);
}
```