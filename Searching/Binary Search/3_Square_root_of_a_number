
**LINK** : [Square root of a number](https://practice.geeksforgeeks.org/problems/square-root/1?utm_source=youtube&utm_medium=collab_keertipurswani_description&utm_campaign=squareroot)


- If we compare graphs of square root and log n, logn performs much better for larger values.
- As number x increases, x^2 will also increase
- The max value till where square root of number x will go is x/2


```
class Solution
{
     long floorSqrt(long x)
	 {
	    if(x == 1) return 1;
		long start=1, end = (x/2);
		long ans = 0;
		
		while(start <= end){
		    long mid = start + ((end-start)/2);
		    long sqr = mid*mid;
		    if(sqr > x){
		        end = mid-1;
		    }
		    else if(sqr < x){
		        ans = mid;
		        start = mid+1;
		    }
		    else{
		        return mid;
		    }
		}
		return ans;
	 }
}
```
