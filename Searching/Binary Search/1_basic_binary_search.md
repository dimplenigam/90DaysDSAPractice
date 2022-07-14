
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




**Time Complexity : O(logn)**
at any interation in Binary Search, we are dividing array into half, so length becomes n/2 at each step :
    ![image](https://user-images.githubusercontent.com/66199489/179041165-5d09fb37-c9c1-4bcc-81db-9b4c23da3e5f.png)



After k iterations, if length is 1, hence :
(this is worts case, as we keep searching array till its length is one)

![image](https://user-images.githubusercontent.com/66199489/179041241-b0ececd6-7951-467a-9182-15eebf122993.png)

Thus t.c. is O(log n)
