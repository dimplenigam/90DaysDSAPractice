
**LINK** : [Searching an element in a sorted array](https://practice.geeksforgeeks.org/problems/who-will-win-1587115621/1?page=1&difficulty%5B%5D=-1&category%5B%5D=Binary%20Search&sortBy=submissions&utm_source=youtube&utm_medium=collab_codefromscratch_description&utm_campaign=sortedarray)

### Due to Recusion, O(n) extra space is used. 

```
class Solution{
    static int searchInSorted(int arr[], int N, int K)
    {
        // int start=0, end=N-1;
        // while(start <= end){
        //     int mid = start + (end-start)/2;
        //     if(K < arr[mid])
        //         end = mid-1;
        //     else if(arr[mid] < K)
        //         start = mid+1;
        //     else
        //         return 1;
        // }
        // return -1;
        
        return helper(arr, K, 0, N-1);
    }
    
    static int helper(int arr[], int K, int start, int end){
        if(start > end)
            return -1;
        int mid = start + (end-start)/2;
        if(K < arr[mid])
            return helper(arr, K, start, mid-1);
        else if(arr[mid] < K)
            return helper(arr, K, mid+1, end);
        else
            return 1;
    }
}
```
