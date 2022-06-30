
**LINK** : [Searching an element in a sorted array](https://practice.geeksforgeeks.org/problems/who-will-win-1587115621/1)

```
class Solution{
    static int searchInSorted(int arr[], int N, int K)
    {
        int start=0, end=N-1;
        while(start<=end){
            int mid = start+(end-start)/2;  //to avoid overflow condition
            if(arr[mid] == K)
                return 1;
            else if(arr[mid] > K){  //search in first half
                end = mid-1; 
            }else if(arr[mid] < K){ //search in second half
                start = mid+1;
            }
        }
        return -1;
    }
}
```