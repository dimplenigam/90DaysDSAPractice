**LINK** : [First and last occurrences of X](https://practice.geeksforgeeks.org/problems/first-and-last-occurrences-of-x2041/1/)

```
class Solution{
    public ArrayList<Integer> firstAndLast(int arr[], int N, int x){
        ArrayList<Integer> list = new ArrayList<>();
        int start=0, end=N-1;
        while(start<=end){
            int mid = start + (end-start)/2;
            if(arr[mid] > x)
                end = mid-1;
            else if(arr[mid] < x)
                start = mid+1;
            else if(arr[mid] == x){
             // WE NEED TO SEE PREVIOUS VALUES WHEREVER MATCH HAPPENS
                int i = mid-1, j=mid+1;
                while(i>=0 && arr[i] == x)  i--;
                list.add(i+1);
                while(j<N && arr[j] == x)  j++;
                list.add(j-1);
                return list;
            }
        }
        list.add(-1);
        return list;
    }
}
```



**Actual Solution**
```
class Solution{
    public ArrayList<Integer> firstAndLast(int arr[], int N, int x){
        ArrayList<Integer> list = new ArrayList<>();
        int first = helper(arr, N, x, true);
        int last = helper(arr, N, x, false);
        list.add(first); 
        if(last != -1) list.add(last);
        return list;
    }
    
    private static int helper(int arr[], int N, int x, boolean isFirst){
        int start=0, end=N-1, ans = -1;
        
        while(start<=end){
            int mid = start + (end-start)/2;
            if(arr[mid] > x)
                end = mid-1;
            else if(arr[mid] < x)
                start = mid+1;
            else if(arr[mid] == x){
                if(isFirst)
                    end = mid-1;
                else
                    start = mid+1;
                ans = mid;
            }
        }
        return ans;
    }
}
```
