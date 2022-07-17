
**LINK** : [Minimum element in a sorted and rotated array](https://practice.geeksforgeeks.org/problems/minimum-element-in-a-sorted-and-rotated-array3611/1?utm_source=youtube&utm_medium=collab_codefromscratch_description&utm_campaign=maxelementinarray)

**Important**
- the minimum element will be the only element having previous element greater than it!
- our answer will lie in the not sorted part
- edge case : when array comes to original state after rotations, then both arrays will be sorted

```
class Solution
{
    int findMin(int arr[], int n)
    {
        int start = 0, end = n-1;
        while(start <= end){
            int mid = start + (end-start)/2;
            
            if(mid==0 || arr[mid-1] > arr[mid])
                return arr[mid];
            
            if(arr[start] > arr[mid]){
                //left sorted array, check in right array
                end = mid-1;
            }else if(arr[mid] > arr[end]){
                //right sorted array, check in left array
                start = mid+1;
            }else
                return arr[start];  // this is added for edge case : when both sub array sorted
        }
        return 0;
    }
}
```
