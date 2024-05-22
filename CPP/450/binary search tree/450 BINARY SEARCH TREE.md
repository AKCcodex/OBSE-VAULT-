|     |     |
| --- | --- |
 
|Binary Search Trees|[Fina a value in a BST](https://www.geeksforgeeks.org/binary-search-tree-set-1-search-and-insertion/)|

null pe return if data is < node node ke left me ja ke insert kar do or else note->right me.

|Binary Search Trees|[Deletion of a node in a BST](https://leetcode.com/problems/delete-node-in-a-bst/)|
![[Pasted image 20240407150334.png]]
|Binary Search Trees|[Find min and max value in a BST](https://practice.geeksforgeeks.org/problems/minimum-element-in-bst/1)|
![[Pasted image 20240407153420.png]]
|Binary Search Trees|[Find inorder successor and inorder predecessor in a BST](https://practice.geeksforgeeks.org/problems/predecessor-and-successor/1)|
![[Pasted image 20240407154840.png]]

|Binary Search Trees|[Check if a tree is a BST or not](https://practice.geeksforgeeks.org/problems/check-for-bst/1)|
isBST
|Binary Search Trees|[Populate Inorder successor of all nodes](https://practice.geeksforgeeks.org/problems/populate-inorder-successor-for-all-nodes/1)|
![[Pasted image 20240407161018.png]]
|Binary Search Trees|[Find LCA  of 2 nodes in a BST](https://practice.geeksforgeeks.org/problems/lowest-common-ancestor-in-a-bst/1)|
![[Pasted image 20240407161910.png]]
|Binary Search Trees|[Construct BST from preorder traversal](https://www.geeksforgeeks.org/construct-bst-from-given-preorder-traversa/)|

link pe he ja ke padh le #important 

|Binary Search Trees|[Convert Binary tree into BST](https://practice.geeksforgeeks.org/problems/binary-tree-to-bst/1)|

inorder lelo bt ka
sort karo
the sorted inorder ka BSt bana lo

|Binary Search Trees|[Convert a normal BST into a Balanced BST](https://www.geeksforgeeks.org/convert-normal-bst-balanced-bst/)|

inorder to bst

|Binary Search Trees|[Merge two BST [ V.V.V>IMP ]](https://www.geeksforgeeks.org/merge-two-balanced-binary-search-trees/)|

ak array me dalo
sort it
then BST bana do

|Binary Search Trees|[Find Kth largest element in a BST](https://practice.geeksforgeeks.org/problems/kth-largest-element-in-bst/1)|

![[Pasted image 20240408021748.png]]
|Binary Search Trees|[Find Kth smallest element in a BST](https://practice.geeksforgeeks.org/problems/find-k-th-smallest-element-in-bst/1)|

same he h

|Binary Search Trees|[Count pairs from 2 BST whose sum is equal to given value "X"](https://practice.geeksforgeeks.org/problems/brothers-from-different-root/1)|
|Binary Search Trees|[Find the median of BST in O(n) time and O(1) space](https://www.geeksforgeeks.org/find-median-bst-time-o1-space/)|

inorder then median

|Binary Search Trees|[Count BST ndoes that lie in a given range](https://practice.geeksforgeeks.org/problems/count-bst-nodes-that-lie-in-a-given-range/1)
easy

|Binary Search Trees|[Replace every element with the least greater element on its right](https://www.geeksforgeeks.org/replace-every-element-with-the-least-greater-element-on-its-right/)|
#missing 
|Binary Search Trees|[Check preorder is valid or not](https://practice.geeksforgeeks.org/problems/preorder-to-postorder/0)|
|Binary Search Trees|[Check whether BST contains Dead end](https://practice.geeksforgeeks.org/problems/check-whether-bst-contains-dead-end/1)|
|Binary Search Trees|[Largest BST in a Binary Tree [ V.V.V.V.V IMP ]](https://practice.geeksforgeeks.org/problems/largest-bst/1)|
1. left subtree ka min value
2. right subtree ka largest value
3. balanced h ki nhi
4. max size of the subtree

```
  
class info{
public:
int maxi;
int mini;
bool isBST;
int size;
};
info solve(TreeNode<int>* root , int &ans){
if(root==NULL){
return{INT_MAX,INT_MIN,true,0};
}
info left=solve(root->left,ans);
info right=solve(root->right,ans);
info currNode;
currNode.size=left.size+right.size+1;
currNode.mini=min(root->data,left.mini);
currNode.maxi=max(root->data,right.maxi);
if(left.isBST==ture && right.isBST==true && root->data>left.maxi && root->data<right.mini){
currNode.isBST=true;
}
else{
currNode.isBST=false;
}
if(currNode.isBST==ture){
ans= max(currNode.size,ans);
}
return currNode;
}
int largestBST(TreeNode<int>* root)

{
int maxsize = 0;
info temp = solve(root,maxsize);
return maxsize;

}
```
|Binary Search Trees|[Flatten BST to sorted list](https://www.geeksforgeeks.org/flatten-bst-to-sorted-list-increasing-order/)|