
**LINK** : [Subsets](https://practice.geeksforgeeks.org/problems/subsets-1613027340/0?category=&utm_source=youtube&utm_medium=collab_codefromscratch_description&utm_campaign=category)

```
class Solution
{
    public static ArrayList<ArrayList<Integer>> subsets(ArrayList<Integer> A)
    {
        ArrayList<ArrayList<Integer>> result = new ArrayList<>();
        helper(A, result, 0, new ArrayList<Integer>());
        
        Collections.sort(result, new Comparator<List<Integer>>() {
            @Override
            public int compare(List<Integer> first, List<Integer> second) {
                int comp = 0;
                for(int i = 0; i < Math.min(first.size(), second.size()); i++){
                    comp = Integer.compare(first.get(i), second.get(i));
                    if(comp != 0){
                        return comp;
                    }
                }
                return Integer.compare(first.size(), second.size());
            }
        });
        return result;
    }
    
    private static void helper(ArrayList<Integer> arr, 
                                ArrayList<ArrayList<Integer>> result,
                                int i, ArrayList<Integer> temp){
        if(i == arr.size()){
            ArrayList<Integer> list = new ArrayList<>();
            list.addAll(temp);
            result.add(list);
            return;
        }
        
        temp.add(arr.get(i));
        helper(arr, result, i+1, temp);
        
        temp.remove(temp.size()-1);
        helper(arr, result, i+1, temp);
    }
}
```
