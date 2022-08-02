
**LINK** : [Power Set](https://practice.geeksforgeeks.org/problems/power-set4302/1?utm_source=youtube&utm_medium=collab_codefromscratch_description&utm_campaign=power-set)

```
class Solution
{
    public List<String> AllPossibleStrings(String s)
    {
        List<String> list = new ArrayList<>();
        helper(s, list, 0, "");
        Collections.sort(list);
        return list;
    }
    
    private void helper(String str, List<String> list, int i, String temp){
        if(i == str.length()){
            if(!temp.isEmpty())
                list.add(temp);
            return;
        }
        //pick 
        helper(str, list, i+1, temp+str.substring(i, i+1));
        //not pick
        helper(str, list, i+1, temp);
    }
}
```
