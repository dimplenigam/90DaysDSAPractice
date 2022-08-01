
**LINK** : [Reverse a String](https://practice.geeksforgeeks.org/problems/reverse-a-string/1)


### Solution 1
```
class Reverse
{
    public static String reverseWord(String str)
    {
        return helper(str, 0);
        
    }
    
    private static void helper(String str, int n){
        if(n == str.length())
            return ;
        helper(str, n+1);
        System.out.print(str.substring(n,n+1));
    }
}
```


### Solution 2
```
class Reverse
{
    public static String reverseWord(String str)
    {
        char[] arr = str.toCharArray();
        helper(arr, 0, str.length()-1);
        return String.valueOf(arr);
    }
    
    private static void helper(char[] arr, int start, int end){
        if(start >= end)
            return ;
        swap(arr, start, end);
        helper(arr, start+1, end-1);
    }
    
    private static void swap(char[] arr, int start, int end){
        char c = arr[start];
        arr[start] = arr[end];
        arr[end] = c;
    }
}
```
