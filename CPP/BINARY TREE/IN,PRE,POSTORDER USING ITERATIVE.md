//INODER
`// funtion for iterative inorder traversal
void inOrderTraversal(struct treeNode *root)
{
	stack<treeNode *> treeStack;
	treeNode *currentNode = root;

	while (currentNode != NULL || treeStack.empty() == false)
	{
        //condition to check if the node is leftmost node 
		while (currentNode != NULL)
		{
			// step 3 of our algorithm
			treeStack.push(currentNode);
			currentNode = currentNode->leftNode;
		}
		
		currentNode = treeStack.top();
		treeStack.pop();
        // cout statement to print the node data
		cout << currentNode->data <<", ";
        
        // statement to process right subtree 
		currentNode = currentNode->rightNode;
	} 
}

`