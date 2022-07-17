**LINK** : [Search an element in sorted and rotated array](https://practice.geeksforgeeks.org/problems/search-in-a-rotated-array0959/1?category=&utm_source=youtube&utm_medium=collab_codefromscratch_description&utm_campaign=rotatedarray) 

``` 
class Solution 
{ 
    static int Search(int arr[], int key)
	{
	    int start=0, end = arr.length-1;
	    while(start <= end){
	        int mid = start + (end-start)/2;
	        if(arr[mid] == key)
	            return mid;
	        
	        //only <, not = included as its mentioned DISTINCT ELEMENTS
	        if(arr[start] < arr[mid]){  //left is sorted
	            //not = condition in key < arr[mid] bcz if that was true, it will return with first if
	            if(arr[start] <= key && key < arr[mid]){    //check if key exists in this sorted arr
	                  end = mid-1;      //reduce search to left side
	            }else
	                start = mid+1;      //reduce search to right side
	        }
	        else{                //right is sorted
	            if(arr[mid] < key && key <= arr[end]){
	                start=mid+1;
	            }else
	                end = mid-1;
	        }
	    }
	    return -1;
	}
} 
```
