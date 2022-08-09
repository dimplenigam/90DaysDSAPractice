**LINK** : [Sum of Binary Tree](https://practice.geeksforgeeks.org/problems/sum-of-binary-tree/1)

```
class BinaryTree
{
    static int sumBT(Node head){
    
        if(head == null) return 0;
        return head.data + 
            (head.left != null ? sumBT(head.left) : 0 ) + 
            (head.right != null ? sumBT(head.right) : 0 );
    }
}
```
