
**LINK** : [String Permutations](https://practice.geeksforgeeks.org/problems/permutations-of-a-given-string-1587115620/1?page=2&category[]=Recursion&sortBy=submissions&utm_source=youtube&utm_medium=collab_codefromscratch_description&utm_campaign=submissions)

```
class Solution
{
    public ArrayList<String> permutation(String S)
    {
        ArrayList<String> result = new ArrayList<>();
        helper(S.toCharArray(), 0, result);
        Collections.sort(result);
        return result;
    }
    
    private void helper(char[] arr, int index, ArrayList<String> result){
        if(index == arr.length-1){
            result.add(new String(arr));
        }
        for(int i=index; i<arr.length; i++){
            swap(arr, i, index);
            helper(arr, index+1, result);
            swap(arr, i, index);
        }
    }
    
    private void swap(char[] arr, int i, int j){
        char temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
	   
}
```
