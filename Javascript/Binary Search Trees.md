```javascript
class TreeNode<E> {
  element: E;
  left: TreeNode;
  right: TreeNode;
  
  constructor(e: E) {
    this.element = e;
  }
}

class BST {

  private root: TreeNode<E>;
  private size = 0;
  
  constructor(arr: E[]) {
    arr.forEach(e => this.insert(e));
  }
  
  search(e: E): boolean {

    let current = root; // Start from the root
    while(current) {
      if (e < current.element) {
        current = current.left; // Go left
      } else if ( e > current.element) {
        current = current.right; // Go right
      } else { // Element matches current.element
        return true; // Element is found
      }
    }
    return false; // Element is not in the tree
  }

  insert(e: E): boolean {
    let parent: TreeNode<E> = null;
    let current: TreeNode<E> = root;
    if(!root) {
      root = new TreeNode(e);
      return true;
    } else {
      
      while(!current) {
        if (e < current.element) {
          parent = current; // Keep the parent
          current = current.left; // Go left
        } else if (e > current.element) {
          parent = current; // Keep the parent
          current = current.right; // Go right
        } else {
          return false; // Duplicate node not inserted
        }
      }
      if(e < current.element) {
        parent.left = new TreeNode(e);
      } else {
        parent.right = new TreeNode(e);
      }
      
      return true;
    }

  }
}
```
