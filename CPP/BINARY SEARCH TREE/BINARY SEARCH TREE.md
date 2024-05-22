[[450 BINARY SEARCH TREE]]
inorder of BST is sorted
//CREATING NODE

class node {
    public:
        int data;
        node* left;
        node* right;

    node(int d) {
        this -> data = d;
        this -> left = NULL;
        this -> right = NULL;
    }
};

initialization
![[Pasted image 20240405161108.png]]
//LEVEL ORDER TRAVERSAL

void levelOrderTraversal(node* root) {
    queue<node*> q;
    q.push(root);
    q.push(NULL);

    while(!q.empty()) {
        node* temp = q.front();
        q.pop();

        if(temp == NULL) { 
            //purana level complete traverse ho chuka hai==
            cout << endl;
            if(!q.empty()) { 
                //queue still has some child ndoes
                q.push(NULL);
            }  
        }
        else{
            cout << temp -> data << " ";
            if(temp ->left) {
                q.push(temp ->left);
            }

            if(temp ->right) {
                q.push(temp ->right);
            }
        }
    }

}

//WAYS OF TRAVERSAL 
==**//INORDER**==    LNR
`void inorder(node* root) {
    //base case
    if(root == NULL) {
        return ;
    }

    inorder(root->left);
    cout << root-> data << " ";
    inorder(root->right);

}
==//PREORDER==   NLR
void preorder(node* root) {
    //base case
    if(root == NULL) {
        return ;
    }

    cout << root-> data << " ";
    preorder(root->left);
    preorder(root->right);

}
==//POSTORDER==   LRN
void postorder(node* root) {
    //base case
    if(root == NULL) {
        return ;
    }

    postorder(root->left);
    postorder(root->right);
    cout << root-> data << " ";

}

search just go with the flow
base case 
then if chota h root ke left me chal ja
if bara hai root se right me chal ja

????????# Find Inorder Successor and Predecessor 
![[Pasted image 20240405171513.png]]

DELETE A NODE IN BST
![[Pasted image 20240407150334.png]]

checking a BST is valid or not
1. inorder nikal ke check kar le
2. ![[Pasted image 20240405163747.png]]

Kth smallest/kth largest no. BST
1. Inorder kar le
2. morise traversal kar lo ?




LCA(least common ancestor)

![[Pasted image 20240407161906.png]]
- root<a && root<b     (right part)
- root>a && root>b     (left part)
- root>a && root<b or root<a && root>b (root he answer h)


TWO SUM PROBLEM IN BST
inorder sorted hota h so then while se two pointer laga ke solve kar le

NORMAL TO BALANSED BST
inorder lelo
mid nikalo = root
then tree me recursion pe dalte jaao
root->right=inbst(start,end,vector)

#important preorder to BST
range bana bana kar karate jaao
![[Pasted image 20240405184913.png]]
LARGEST BST
is bst wala concept lage g
4factor lo ge 
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