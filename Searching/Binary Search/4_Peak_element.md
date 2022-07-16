**LINK** : [Peak element](https://practice.geeksforgeeks.org/problems/peak-element/1?utm_source=youtube&utm_medium=collab_codefromscratch_description&utm_campaign=peakelement))


```
class Solution
{
	public int peakElement(int[] arr,int n)
    {
       int start=0, end=n;
       if(n == 1){      //base case
           return 0;
       }
       while(start <= end){
           int mid = start + ((end-start)/2);
           if((mid == 0 || arr[mid-1] <= arr[mid]) && 
                (mid == n-1 || arr[mid] >= arr[mid+1])){
               return mid;
           }
           if(mid > 0 && arr[mid-1] > arr[mid]){  
               end = mid-1;
           }else 
               start = mid+1;
       }
       return 0;
    }
}
```
