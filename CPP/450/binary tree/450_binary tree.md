

|     |     |     |
| --- | --- | --- |
 
|Binary Trees|[level order traversal](https://practice.geeksforgeeks.org/problems/level-order-traversal/1)|
`void levelOrderTraversal(node* root) {
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
`
|Binary Trees|[Reverse Level Order traversal](https://practice.geeksforgeeks.org/problems/reverse-level-order-traversal/1)|
pehle queue bana kar root->right->left then stack me dall ke pop kar liya
`vector<int> reverseLevelOrder(Node *root)`
`{`
  `vector<int> result;`
  `stack<Node*>S;`
  `queue<Node*>Q;`
  `Q.push(root);`
  `while(!Q.empty()){`
      `root=Q.front();`
      `Q.pop();`
      `S.push(root);`
      `if(root->right)`
      `Q.push(root->right);`
      `if(root->left)`
      `Q.push(root->left);`
  `}`
  `while(!S.empty()){`
      `root=S.top();`
      `result.push_back(root->data);`
      `S.pop();`
  `}`
  `return result;`
`}``

|Binary Trees|[Height of a tree](https://practice.geeksforgeeks.org/problems/height-of-binary-tree/1)|
[[hight of binary tree]]
|Binary Trees|[Diameter of a tree](https://practice.geeksforgeeks.org/problems/diameter-of-binary-tree/1)|
[[diameater of a binary tree]]
|Binary Trees|[Mirror of a tree](https://www.geeksforgeeks.org/create-a-mirror-tree-from-the-given-binary-tree/)|
traverce kar ke swap kar lo
`if(node==NULL) return;
        mirror(node->left);
        mirror(node->right);
        swap(node->left,node->right);`
|Binary Trees|[Inorder Traversal of a tree both using recursion and Iteration](https://www.techiedelight.com/inorder-tree-traversal-iterative-recursive/)|
stack ko he bolte h
|Binary Trees|[Preorder Traversal of a tree both using recursion and Iteration](https://www.techiedelight.com/preorder-tree-traversal-iterative-recursive/)stack ko he bolte h
|Binary Trees|[Postorder Traversal of a tree both using recursion and Iteration](https://www.techiedelight.com/postorder-tree-traversal-iterative-recursive/)|stack ko he bolte h
|Binary Trees|[Left View of a tree](https://practice.geeksforgeeks.org/problems/left-view-of-binary-tree/1)|
[[left/right view]]
|Binary Trees|[Right View of Tree](https://practice.geeksforgeeks.org/problems/right-view-of-binary-tree/1)|
[[left/right view]]
|Binary Trees|[Top View of a tree](https://practice.geeksforgeeks.org/problems/top-view-of-binary-tree/1)|
[[top view/bottom view]]
|Binary Trees|[Bottom View of a tree](https://practice.geeksforgeeks.org/problems/bottom-view-of-binary-tree/1)|
[[top view/bottom view]]
|Binary Trees|[Zig-Zag traversal of a binary tree](https://practice.geeksforgeeks.org/problems/zigzag-tree-traversal/1)|
[[zig zag traversal]]
|Binary Trees|[Check if a tree is balanced or not](https://practice.geeksforgeeks.org/problems/check-for-balanced-tree/1)|
[[check for balance tree]]
|Binary Trees|[Diagnol Traversal of a Binary tree](https://www.geeksforgeeks.org/diagonal-traversal-of-binary-tree/)|
![[Pasted image 20240329012539.png]]
|Binary Trees|[Boundary traversal of a Binary tree](https://practice.geeksforgeeks.org/problems/boundary-traversal-of-binary-tree/1)|
[[boundary traversal]]
|Binary Trees|[Construct Binary Tree from String with Bracket Representation](https://www.geeksforgeeks.org/construct-binary-tree-string-bracket-representation/)|
#missinh
|Binary Trees|[Convert Binary tree into Doubly Linked List](https://practice.geeksforgeeks.org/problems/binary-tree-to-dll/1)|
flow me ja

|Binary Trees|[Convert Binary tree into Sum tree](https://practice.geeksforgeeks.org/problems/transform-to-sum-tree/1)|
``int` `toSumTree(node *Node)`

`{`

    `// Base case`

    `if``(Node == NULL)`

    `return` `0;`

    `// Store the old value`

    `int` `old_val = Node->data;`

    `// Recursively call for left and`

    `// right subtrees and store the sum as`

    `// old value of this node`

    `Node->data = toSumTree(Node->left) + toSumTree(Node->right);`

    `// Return the sum of values of nodes`

    `// in left and right subtrees and`

    `// old_value of this node`

    `return` `Node->data + old_val;`

`}``
|Binary Trees|[Construct Binary tree from Inorder and preorder traversal](https://practice.geeksforgeeks.org/problems/construct-tree-1/1)|
[[from inorder and preorder find post order]]
|Binary Trees|[Find minimum swaps required to convert a Binary tree into BST](https://www.geeksforgeeks.org/minimum-swap-required-convert-binary-tree-binary-search-tree/#:~:text=Given%20the%20array%20representation%20of,it%20into%20Binary%20Search%20Tree.&text=Swap%201%3A%20Swap%20node%208,node%209%20with%20node%2010.)|
#missing
|Binary Trees|[Check if Binary tree is Sum tree or not](https://practice.geeksforgeeks.org/problems/sum-tree/1)|
[[sum tree]]
|Binary Trees|[Check if all leaf nodes are at same level or not](https://practice.geeksforgeeks.org/problems/leaf-at-same-level/1)|
![[Pasted image 20240401021523.png]]
|Binary Trees|[Check if a Binary Tree contains duplicate subtrees of size 2 or more [ IMP ]](https://practice.geeksforgeeks.org/problems/duplicate-subtree-in-binary-tree/1)
#missing
|Binary Trees|[Check if 2 trees are mirror or not](https://practice.geeksforgeeks.org/problems/check-mirror-in-n-ary-tree/0)|
[[if mirror or not]]
|Binary Trees|[Sum of Nodes on the Longest path from root to leaf node](https://practice.geeksforgeeks.org/problems/sum-of-the-longest-bloodline-of-a-tree/1)|
[[blood line]]
|Binary Trees|[Check if given graph is tree or not.  [ IMP ]](https://www.geeksforgeeks.org/check-given-graph-tree/#:~:text=Since%20the%20graph%20is%20undirected,graph%20is%20connected%2C%20otherwise%20not.)|
#missing
|Binary Trees|[Find Largest subtree sum in a tree](https://www.geeksforgeeks.org/find-largest-subtree-sum-tree/)|

|Binary Trees|[Maximum Sum of nodes in Binary tree such that no two are adjacent](https://www.geeksforgeeks.org/maximum-sum-nodes-binary-tree-no-two-adjacent/)|
|Binary Trees|[Print all "K" Sum paths in a Binary tree](https://www.geeksforgeeks.org/print-k-sum-paths-binary-tree/)|
|Binary Trees|[Find LCA in a Binary tree](https://practice.geeksforgeeks.org/problems/lowest-common-ancestor-in-a-binary-tree/1)|
|Binary Trees|[Find distance between 2 nodes in a Binary tree](https://practice.geeksforgeeks.org/problems/min-distance-between-two-given-nodes-of-a-binary-tree/1)|
|Binary Trees|[Kth Ancestor of node in a Binary tree](https://www.geeksforgeeks.org/kth-ancestor-node-binary-tree-set-2/)|
|Binary Trees|[Find all Duplicate subtrees in a Binary tree [ IMP ]](https://practice.geeksforgeeks.org/problems/duplicate-subtrees/1)|
|Binary Trees|[Tree Isomorphism Problem](https://practice.geeksforgeeks.org/problems/check-if-tree-is-isomorphic/1)|