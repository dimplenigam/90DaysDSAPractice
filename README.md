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


Q: Permutations (https://leetcode.com/problems/permutations/submissions/) 
```
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        helper(nums, 0, result);
        return result;
    }
    
    private void helper(int[] arr, int i, List<List<Integer>> result){
        if(i == arr.length){
            result.add(Arrays.stream(arr).boxed().collect(Collectors.toList()));
            return;
        }
        
        for(int j=i; j<arr.length; j++){
            swap(arr, i, j);
            helper(arr, i+1, result);
            swap(arr, i, j);
        }
    }
    
    private static void swap(int[] arr, int i, int j){
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
```



Q: Possible words from Phone digits (https://practice.geeksforgeeks.org/problems/possible-words-from-phone-digits-1587115620/1/#)
```
class Solution
{
    static String[] keys = { "", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
    
    //Function to find list of all words possible by pressing given numbers.
    static ArrayList<String> possibleWords(int a[], int N)
    {
        ArrayList<String> result = new ArrayList<>();
        helper(a, 0, "", result);
        return result;
    }
    
    private static void helper(int arr[], int index, String str, ArrayList<String> result){
        if(index == arr.length){
            result.add(str);
            return;
        }
        
        for(int i=0; i<keys[arr[index]].length(); i++){
            String s = Character.toString(keys[arr[index]].charAt(i));
            //System.out.println(s);
            helper(arr, index+1, str+s, result);
        }
    }
}
```



Q: Combinatipnal Sum (https://leetcode.com/problems/combination-sum/submissions/)
```
/*explained by Striver*/
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();
        helper(candidates, target, 0, new ArrayList<Integer>(), result);
        return result;
    }
    
    
    void helper(int[] arr, int target, int index, List<Integer> list, List<List<Integer>> result){
        
        if(index == arr.length){
            if(target == 0)
                result.add(new ArrayList<>(list));
            return;
        }
        
        if(arr[index] <= target){
            //pick-inclusion
            list.add(arr[index]);
            helper(arr, target-arr[index], index, list, result);
            list.remove(list.size()-1);
        }
        
        //not pick - exclusion
        helper(arr, target, index+1, list, result);
        return;
    }
}
```

```
/* Solution by me*/
class Solution {
    static int required_sum = 0;
    static int[] arr;
    
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        required_sum = target;
        arr = candidates;
        List<List<Integer>> result = new ArrayList<>();
        helper(0, 0, new ArrayList<Integer>(), result);
        return result;
    }
    
    
    private static void helper(int i, int temp_sum, ArrayList<Integer> list, List<List<Integer>> result){
        
        if(i == arr.length || temp_sum > required_sum)
            return;
        
        if(temp_sum == required_sum){
            result.add(new ArrayList<>(list));
            return;
        }
        
        
        for(int j=i; j<arr.length; j++){
            list.add(arr[j]);
            int s = temp_sum+arr[j];
            helper(j, temp_sum+arr[j], list, result);
            list.remove(list.size()-1);
        }
        
        
        return;
    }
}
```

```
Changes for GFG SUbmission :
static ArrayList<ArrayList<Integer>> combinationSum(ArrayList<Integer> A, int B)
    {
        HashSet <Integer> hs = new HashSet<>(A);
        ArrayList <Integer> new_A = new ArrayList<>(hs);
        Collections.sort(new_A);
        
        ArrayList<ArrayList<Integer>> result = new ArrayList<>();
        helper(new_A, B, 0, new ArrayList<Integer>(), result);
        return result;   
    }
```



Q: N Queen (https://practice.geeksforgeeks.org/problems/n-queen-problem0315/1)
```
class Solution{

    static ArrayList<ArrayList<Integer>> nQueen(int n) {
        ArrayList<ArrayList<Integer>> result = new ArrayList<>();
        int[][] board = new int[n][n];
        helper(0, n, result, board);
        return result;
    }
    
    private static void helper(int row, int n, ArrayList<ArrayList<Integer>> result, int[][] board){
        if(row == n){
			ArrayList<Integer> list = new ArrayList<Integer>();
			for(int i=0; i<n; i++){
				for(int j=0; j<n; j++){
					if(board[i][j] == 1){
						list.add(j+1);	//why not i+1
					}
				}
			}
            result.add(list);
            return;
        }
        
        for(int i=0; i<n; i++){
            if(isSafe(board, row, i, n)){
                board[row][i] = 1;
                helper(row+1, n, result, board);
                board[row][i] = 0;
            }
        }
        return;
    }
    
    private static boolean isSafe(int[][] board, int row, int col, int n){
		for(int i=0; i<row; i++){
			if(board[i][col] == 1)
				return false;
		}
		for(int i=row, j=col; i>=0 && j<n; i--, j++){
			if(board[i][j] == 1)
				return false;
		}
		for(int i=row, j=col; i>=0 && j>=0; i--, j--){
			if(board[i][j] == 1)
				return false;
		}
        return true;    
    }
}
```




Q: https://practice.geeksforgeeks.org/problems/rat-in-a-maze-problem/1#
```
class Solution {
    
    static ArrayList<String> result = new ArrayList<>();
    
    public static ArrayList<String> findPath(int[][] arr, int N) {
        if(arr[0][0] == 0)  //unable to enter
            return result;
        int[][] visited = new int[N][N];
        helper(arr, N, 0, 0, "", visited);
        return result;
    }
    
    private static void helper(int[][] arr, int N, int r, int c, String path, int[][] visited){
        if(r==(N-1) && c==(N-1)){ //reached destination
            //System.out.println(r+":"+c+":"+path);
            result.add(path);
            //System.out.println(result.size());
            return;
        }
        
        visited[r][c] = 1;  //mark visited
        
        if(isSafe(arr, r+1, c, N, visited))
            helper(arr, N, r+1, c, path+"D", visited);   //move down
            
        if(isSafe(arr, r, c-1, N, visited))
            helper(arr, N, r, c-1, path+"L", visited);   //move left
            
        if(isSafe(arr, r, c+1, N, visited))
            helper(arr, N, r, c+1, path+"R", visited);   //move right
            
        if(isSafe(arr, r-1, c, N, visited))
            helper(arr, N, r-1, c, path+"U", visited);   //move up    
            
        visited[r][c] = 0;  //mark unvisited
        return;
    }
    
    private static boolean isSafe(int[][] arr, int r, int c, int N, int[][] visited){
        if( r<N && r>=0 && 
            c<N && c>=0 &&
            arr[r][c] == 1 &&
            visited[r][c] == 0)
            return true;
        return false;
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



Q: 
```
```






