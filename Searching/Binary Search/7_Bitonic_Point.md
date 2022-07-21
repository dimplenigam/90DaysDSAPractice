

**LINK** : [Bitonic Point](https://practice.geeksforgeeks.org/problems/maximum-value-in-a-bitonic-array3001/1?utm_source=youtube&utm_medium=collab_codefromscratch_description&utm_campaign=bitonic-array)

```
class Solution {
    int findMaximum(int[] arr, int n) {
        
        int start = 0, end = n-1;
        while(start <= end){
            int mid = start + (end-start)/2;
            if( (mid == 0 || arr[mid-1] < arr[mid])
             && (mid == n-1 || arr[mid+1] < arr[mid]) ){
                return arr[mid];
            }else if(arr[mid-1] < arr[mid]){
                start = mid+1;
            }else {
                end = mid-1;
            }
        }
        return -1;
    }
}
```
