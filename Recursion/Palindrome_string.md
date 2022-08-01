**LINK** : [Palindrome String](https://practice.geeksforgeeks.org/problems/palindrome-string0817/1)

```
class Solution {
    int isPalindrome(String S) {
        return helper(S.toCharArray(), 0, S.length()-1);
    }
    
    static int helper(char[] arr, int start, int end){
        if(start >= end)
            return 1;
        if(arr[start] != arr[end])
            return 0;
        return helper(arr, start+1, end-1);
    }
};
```
