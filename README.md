# 90DaysDSAPractice
###### Roadmap : 
https://whimsical.com/dsa-in-90-days-EmPkf5utoFGRMnRqJjM6YV


# DAY1 Time & Space Complexity
###### Links referred :
https://www.youtube.com/watch?v=QovOdd80A4s


# DAY2 Time & Space Complexity
###### Links referred :
https://www.youtube.com/watch?v=vgSKOMsjLbc https://www.youtube.com/watch?v=KXAbAa1mieU 
https://www.geeksforgeeks.org/time-complexity-and-space-complexity/
https://www.youtube.com/watch?v=vgSKOMsjLbc
https://www.youtube.com/watch?v=KXAbAa1mieU


# DAY3 Recursion
###### Links referred :
https://www.youtube.com/watch?v=Mr9MVpSoTGk

###### Theory :
Recursion :- when a function calls itself
3 steps for recursion:-
	- Find a base case (stopping condition)
	- Find relation between problems and sub problems (f(n) and f(n-1)/f(n+1))
	- Generalise the relation

###### Questions :
Q : https://practice.geeksforgeeks.org/problems/print-1-to-n-without-using-loops-1587115620/1/?page=1&difficulty[]=-2&difficulty[]=-1&category[]=Recursion&sortBy=submissions
```
class Solution
{ 
  public void printNos(int N)
    {
        if(N == 0)
            return;
        printNos(N-1);
        System.out.print(N + " ");
    }
}
```

Q: https://practice.geeksforgeeks.org/problems/print-1-to-n-without-using-loops3621/1/?page=1&difficulty[]=-2&difficulty[]=-1&category[]=Recursion&sortBy=submissions
*same as above*

Q: https://www.geeksforgeeks.org/sum-of-the-series-11-22-33-nn-using-recursion/?ref=rp
```
class GFG {
	public static void main (String[] args) {
	    Scanner s = new Scanner(System.in);
	    int n = s.nextInt();
	    long sum = calc(n);
		System.out.println(sum);
	}
	
	private static long calc(int n){
	    if(n==1)
	        return 1;
	   return (long)Math.pow(n,n) + calc(n-1);
	}
}
```


Q: https://practice.geeksforgeeks.org/problems/palindrome-string0817/1/
```
class Solution {
    int isPalindrome(String S) {
       return checkPalindrome(S, 0, S.length()-1);
    }
    
    int checkPalindrome(String S, int start, int end){
        if(start >= end)
            return 1;
        if(S.charAt(start) != S.charAt(end))
            return 0;
        return checkPalindrome(S, start+1, end-1);
    } 
};
```
