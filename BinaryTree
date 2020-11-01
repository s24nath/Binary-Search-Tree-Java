public class BinaryTree {

    Node root = null;

//---------------------------------------------Driver functions---------------------------------------------------------//

    public boolean isTreeEmpty() {
        return (root == null);
    }

    public void push(int data) {
        root = insert(root,data); /** Assigning the local variable of root after the function finished it's job,
        * to the instance variable of the main root variable of the class */
    }

    public void printTreeInOrdr() {
        inOrder(root);
    }

    public boolean search(int data) {
        return dataExist(root,data);
    }

    public void delete(int data) {
        root = deleteNode(root,data); /** Assigning the local variable of root after the function finished it's job,
         * to the instance variable of the the main root variable of the class */
    }

//---------------------------------------------Normal working functions---------------------------------------------------------//

    private Node insert(Node node, int data) {
        if(node == null) {
            node = new Node(data);
            return node; // Making new node and returning it
        }

        else {
            if(data <= node.data) {
                node.leftNode = insert(node.leftNode,data); /** Going to the left node till it become null
                 * and adding a new node there, and assigning the node created to the left node, then
                 * chaining up all the nodes with each other in a tree while back tracing */
            }

            else {
                node.rightNode = insert(node.rightNode,data); /** Going to the right node till it become null
                 * and adding a new node there, and assigning the node created to the left node, then
                 * chaining up all the nodes with each other in a tree while back tracing */
            }
        }
        return node; // Returning the root to it's parent root.
    }


    private boolean dataExist(Node node, int data) {
        if(node == null) {
            return false; // If the tree is already empty then return false
        }

        else if(node.data == data) {
            return true; // If we got the data then return true
        }

        else if(node.data > data) {
            return dataExist(node.leftNode, data); /** Here we are recurring or going to the left node till the last
             * node. Then returning the boolean value to their parent node or root node */
        }

        else {
            return dataExist(node.rightNode, data); /** Here we are recurring or going to the right node till the last
             * node. Then returning the boolean value to their parent node or root node */
        }
    }

    private void inOrder(Node node) {
        if(node == null) {
            System.out.println("Empty tree");
        }
        else {
            if (node.leftNode != null)
                inOrder(node.leftNode);

            System.out.println(node.data);

            if (node.rightNode != null)
                inOrder(node.rightNode);
        }
    }

    private Node inOrderSuccessor(Node node) {

        /** Here we are going/reccuring to the left most node of the root then returning the function value
        * which is the node, to it's parent root */

        if(node.leftNode != null) {
            return node.leftNode;
        }
        else
            return node;
    }

    private Node deleteNode(Node node, int data) {
        // Searching for the value, if found we go ahead and delete it else we return null.
        if(node == null) {
            return node;
        }
        else if(data < node.data) {
            node.leftNode = deleteNode(node.leftNode,data); /** Here we are recurring or going to the left node till the last
             * node. While deleting a node or a root we have actually replaced the address of the currrent node or the root
             * with other node or root address. So, now we have a new node address which we need to assign again with the
             * parent node or root and create a new tree by chaining up all the nodes with each other in a tree while back tracing */
        }
        else if(data > node.data) {
            node.rightNode = deleteNode(node.rightNode,data); /** Here we are recurring or going to the right node till the last
             * node. While deleting a node or a root we have actually replaced the address of the currrent node or the root
             * with other node or root address. So, now we have a new node address which we need to assign again with the
             * parent node or root and create a new tree by chaining up all the nodes with each other in a tree while back tracing */
        }
        // If we finally found the value that we are going to delete
        else {
            // Case 1 : If it's a leaf node. The node/root with no children.
            if((node.rightNode == null) && (node.leftNode == null)) {
                node = null; // We just delete the node. We take the current node and set it to null.
            }

            // Case 2A : If the node/root has only one child and that's only the right node.
            else if(node.leftNode == null) {
                node = node.rightNode; /** Here we go ahead and replace the current node with it's right node. We actually
                 * get the address of the right node of the current root and assign that right node address to the reference variable
                 * that is referring to the current node, which will replace the current node address with the right node address
                 * then it will return the replaced node address and pass the node address which will be assigned to it's
                 * parent node or root node as a new node address */
            }

            // Case 2B : If the node/root has only one child and that's only the left node.
            else if(node.rightNode == null) {
                node = node.leftNode; /** Here we go ahead and replace the current node with it's left node. We actually
                 * get the address of the left node of the current root and assign that left node address to the reference variable
                 * that is referring to the current node, which will replace the current node address with the left node address
                 * then it will return the replaced node address and pass the node address which will be assigned to it's
                 * parent node or root node as a new node address */
            }

            // Case 3 : If the node/root has 2 children.
            else {
                Node temp = inOrderSuccessor(node.rightNode); // Getting the inorder successor of the current node into temp variable
                node.data = temp.data; // Replacing the data of the current node with it's inorder successor node
                node.rightNode = deleteNode(node.rightNode,temp.data); // Deleting the inorder successor node.
            }
        }
        return node;
    }

}
