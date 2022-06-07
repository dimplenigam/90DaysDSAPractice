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
1. Recursion :- when a function calls itself
2. 3 steps for recursion:-
	- Find a base case (stopping condition)
	- Find relation between problems and sub problems (f(n) and f(n-1)/f(n+1))
	- Generalise the relation
3. Power set includes empty string/number
4. Subsequence doesnot include it

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



Q: https://practice.geeksforgeeks.org/problems/reverse-a-string/1
```
class Reverse
{
    // Complete the function
    // str: input string
    public static String reverseWord(String str)
    {
        char[] arr = str.toCharArray();
        arr = reverse(arr, 0, arr.length-1);
        return new String(arr);
    }
    
    private static char[] reverse(char[] arr, int start, int end){
        if(start >= end)
            return arr;
        char temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        return reverse(arr, start+1, end-1);
    }
    
}
```



Q : Subset Sum (https://practice.geeksforgeeks.org/problems/subset-sums2234/1/?page=1&difficulty[]=-1&category[]=Recursion&sortBy=submissions)
```
class Solution{
    ArrayList<Integer> subsetSums(ArrayList<Integer> arr, int N){
        ArrayList<Integer> result = new ArrayList<>();
        process(arr, 0, 0, result);
        Collections.sort(result);
        return result;
    }
    void process (ArrayList<Integer> arr, int i, int sum, ArrayList<Integer> result){
        if(i == arr.size()){
            result.add(sum);
            return;
        }
        process(arr, i+1, sum+arr.get(i), result);
        process(arr, i+1, sum, result);
    }
}
```






Q: Power set/ Subsequence (https://practice.geeksforgeeks.org/problems/power-set4302/1/)
```
class Solution
{
    public List<String> AllPossibleStrings(String s)
    {
        List<String> result = new ArrayList<>();
        process(s, "", 0, result);
        result.remove("");
        Collections.sort(result);
        return result;
    }
    
    void process(String str, String subStr, int i, List<String> result){
        if(i == str.length()){
            result.add(subStr);
            return;
        }
        //take condition
        process(str, subStr+str.charAt(i), i+1, result);
        //not take condition
        process(str, subStr, i+1, result);
        
    }
}
```



Q: Juggler Sequence (https://practice.geeksforgeeks.org/problems/juggler-sequence3930/1/?page=1&difficulty[]=-1&category[]=Recursion&sortBy=submissions)
```
class Solution{
    static List<Integer> jugglerSequence(int N){
        List<Integer> list = new ArrayList<>();
        list.add(N);
        helper(N, list, 1);
        return list;
    }
    
    static void helper(int N, List<Integer> list, int i){
        int num = list.get(i-1);
        if(num == 1)
            return;
        
        double val = Math.sqrt(num);
        if(num % 2 == 0)
            list.add(i, (int)Math.floor(val));
        else
            list.add(i, (int)Math.floor(Math.pow(val, 3)));
        helper(N, list, i+1);
    }
}
```



Q: https://practice.geeksforgeeks.org/problems/subsets-1613027340/1/#
```
class Solution
{
    private static ArrayList<ArrayList<Integer>> result = new ArrayList<>();
    
    public static ArrayList<ArrayList<Integer>> subsets(ArrayList<Integer> A)
    {
        ArrayList<Integer> list = new ArrayList<>();
        helper(A, 0, list);
        
        Collections.sort(result, (x, y) -> {
            for (int i = 0; i < Math.min(x.size(), y.size()); i++) {
                if (x.get(i) != y.get(i)) {
                    return x.get(i) - y.get(i);
                }
            }
            return x.size() - y.size();
        });
        
        return result;
    }
    
    private static void helper(ArrayList<Integer> A, int index, 
        ArrayList<Integer> list){
        
        if(index == A.size()){
            result.add(list);
            //list = null;
            return;
        }
        
        
        helper(A, index+1, new ArrayList<Integer>(list));
        list.add(A.get(index));
        helper(A, index+1, new ArrayList<Integer>(list));
        return;
    }
}
```



Q: Subset Sum Problem (https://practice.geeksforgeeks.org/problems/subset-sum-problem-1611555638/1/#)
```
class Solution{
    static Boolean isSubsetSum(int N, int arr[], int sum){
        return helper(arr, 0, 0, sum);
    }
    
    private static boolean helper(int arr[], int index, int calculatedSum, 
                              int requiredSum){
        if(index == arr.length)
            return false;
        if(calculatedSum > requiredSum)
            return false;
        if(calculatedSum == requiredSum)
            return true;
        return helper(arr, index+1, calculatedSum+arr[index], requiredSum) ||
        helper(arr, index+1, calculatedSum, requiredSum);  
    }
}
```


Q: 
```
```



Q: 
```
```



Q: 
```
```



Q: 
```
```




Q: 
```
```



Q: 
```
```






