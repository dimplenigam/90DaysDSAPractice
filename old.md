


#DAY4/ (until #DAY10)
Recursion Playlist : https://www.youtube.com/playlist?list=PLgUwDviBIf0rGlzIn_7rsaR2FQ5e6ZOL9
import java.util.*;

public class Solution{
	public static void main(String[] args){
		Scanner scanner = new Scanner(System.in);
		int n = scanner.nextInt();
		//printName(n, 0);
		printNumber(n, 0);
	}


	/*Print name n times
	* 	Time Complexity : O(n) - each function call takes constant time and n time function called
	*	Space Complexity : O(n) - this is for internal memory as stack trace fills for n recursion calls
	*/
	public static void printName(int n, int i){
	if(i == n)
		return;
	System.out.println("Name ");
	printName(n, i+1);
	}


	/* Print linearly from 1 to n
	*	Time Complexity : O(n)
	* 	Space Complexity :O(n)
	*/
	public static void printNumber(int n, int i){
		if(i == n)
			return;
		System.out.println(i+1);
		printNumber(n, i+1);
	}


	/* Print from n to 1
	*/
	public static void printNumberReverse(int n){
		if(n == 0)
			return;
		System.out.println(n);
		printNumberReverse(n-1);
	}


	/* Print from 1 to N by backtrack
	*/
	public static void printNumberBacktrack(int n){
	 	if(n==0)
	 		return;
	 	printNumberBacktrack(n-1);
	 	System.out.println(n);
	}
}


/**Q:https://practice.geeksforgeeks.org/problems/gf-series3535/1/?page=1&difficulty[]=-1&category[]=Recursion&sortBy=submissions#
**/
static void gfSeries(int N){
        
        for(int i=1; i <= N; i++){
            //System.out.print("for i:"+i);
            if(i == N){
                System.out.println(calc(i));
                break;
            }
            System.out.print(calc(i)+" ");
        }
        
    }
    
    static long calc(int N){
        if(N == 1){
            return 0;
        }
        else if(N == 2){
            return 1;
        }
        return ((long)Math.pow(calc(N-2), 2)) - calc(N-1);
        
    }



https://www.geeksforgeeks.org/find-geometric-sum-of-the-series-using-recursion/?ref=rp
https://www.geeksforgeeks.org/sum-digit-number-using-recursion/?ref=rp
https://www.geeksforgeeks.org/print-fibonacci-series-in-reverse-order-using-recursion/?ref=rp
https://www.geeksforgeeks.org/sum-of-even-elements-of-an-array-using-recursion/?ref=rp
https://www.geeksforgeeks.org/program-to-calculate-ex-by-recursion/?ref=rp
https://www.geeksforgeeks.org/sum-of-natural-numbers-using-recursion/?ref=rp
https://www.geeksforgeeks.org/solving-fn-1-23-456-n-using-recursion/?ref=rp
https://www.geeksforgeeks.org/program-for-length-of-a-string-using-recursion/?ref=rp
https://www.geeksforgeeks.org/product-2-numbers-using-recursion/?ref=rp










for recursion
https://www.youtube.com/watch?v=6IIgSFBPQ0U



future playlist to be covered
https://www.youtube.com/playlist?list=PLUcsbZa0qzu3yNzzAxgvSgRobdUUJvz7p
https://www.youtube.com/playlist?list=PLgUwDviBIf0p4ozDR_kJJkONnb1wdx2Ma

RESOURCES TO FOLLOW
Strivers List : https://takeuforward.org/interviews/strivers-sde-sheet-top-coding-interview-problems/
