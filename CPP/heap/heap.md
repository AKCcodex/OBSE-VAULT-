[[450heap]]
heap is a complete binary three

MAX heap 
MIN heap

node=i
left child=2xi
right child=(2xi)+1
parent = i/2

incertion
![[Pasted image 20240411003747.png]]

delition
![[Pasted image 20240412235521.png]]
heapyfi

![[Pasted image 20240414164614.png]]![[Pasted image 20240415025038.png]]
```
// Back-end Complete Function template for C++

class Solution {
  public:
    // Function to count the number of nodes in a binary tree
    unsigned int countNodes(struct Node* root) {
        if (root == NULL) return (0);
        return (1 + countNodes(root->left) + countNodes(root->right));
    }

    // Function to check if the binary tree is a valid heap
    bool isValid(Node* tree, int level, int no) {
        if (tree == NULL) return true;
        if (level >= no) return false;
        return isValid(tree->left, 2 * level + 1, no) and
               isValid(tree->right, 2 * level + 2, no);
    }
    
    /* Function to get diameter of a binary tree */

    // Function to check if each node in the binary tree satisfies the heap property
    bool propHoldes(Node* root) {
        if (!root->left and !root->right) return true;
        if (root->right == NULL)
            return root->data > root->left->data;
        else {
            if (root->data >= root->left->data and
                root->data >= root->right->data)
                return propHoldes(root->left) and propHoldes(root->right);
            else
                return false;
        }
    }

    // Function to check if the binary tree is a valid heap
    bool isHeap(struct Node* tree) {
        if (tree == NULL) return true;
        int no_of_nodes = countNodes(tree);

        // Check if tree is a valid heap and satisfies the heap property
        if (isValid(tree, 0, no_of_nodes) and propHoldes(tree)) return true;
        return false;
    }
};

```