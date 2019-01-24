```typescript

class Node<E> {
  element: E;
  next: Node<E>;
  constructor(e: E) {
    this.element = e;
  }
}

class LinkedList<E> {
  private head: Node<E>;
  private tail: Node<E>;
  private size = 0;
  
  addFirst(e: E) {
    const newNode = new Node(e);
    newNode.next = this.head;
    this.head = newNode;
    if (!this.tail) {
      this.tail = this.head;
    }
    this.size++;
  }
  
  addLast(e: E) {
    const newNode = new Node(e);
    
    if (!this.tail) { // The only node in list
      this.head = this.tail = newNode;
    } else {
      this.tail.next = newNode; // Link the new node with the last node
      this.tail = this.tail.next; // tail now points to the last node
    }
    this.size++;
  }
  
  add(index: number, e: E) {
    if (index === 0) {
      this.addFirst(e);
    } else if (index >= size) {
      this.addLast(e);
    } else {
      const current = this.head;
      for(var i = 1; i < index; i++) {
        current = current.next;
      }
      const temp = current.next;
      current.next = new Node(e);
      (current.next).next = temp;
    }
    this.size++;
  }
  
  removeFirst(): E {
    if (this.size === 0) {
      return null;
    } else {
      const temp = this.head;
      this.head = this.head.next;
      this.size--;
      if (this.head === null) {
        this.tail = null;
      }
      return temp.element;
    }
  }
  
  removeLast(): E {
  if (this.size === 0) {
    return null;
  } else if (this.size === 1) {
    const temp = this.head;
    this.head = this.tail = null;
    this.size = 0;
    return temp.element;
  } else {
    var current = this.head;
    for(var i = 0 ; i < this.size - 2; i++) {
      current = current.next;
    }
    const temp = current.next;
    this.tail = current;
    current.next = null;
    this.size--;
    return temp.element;
  }
  
  remove(index: number) {
    if(index < 0 || index >= size) { 
      return null;
    } else if(index === 0) {
      this.removeFirst();
    } else if(index === size - 1) {
      this.removeLast();
    } else {
      var previous = this.head;
      for(var i = 1; i < index; i++) {
        previous = previous.next;
      }
      const current = previous.next;
      previous.next = current.next;
      this.size--;
      return current.element;
    }
  }
  
  getFirst(): E {
    if (this.size === 0) return null;
    else return this.head.element;
  }
  
  
  getLast(): E {
    if (this.size === 0) return null;
    else return this.tail.element;
  }
  
  clear(): void {
    this.head = this.tail = null;
    this.size = 0;
  }
  
  get(index: number): E {
    if(index < 0 || index >= this.size) return null;
    var current = this.head;
    for(var i = 0; i < index; i++) {
      current = current.next;
    }
    return current.element;
  }
  
  indexOf(e: E): number {
    var index = 0;
    var current = this.head;
    while(current) {
      if(current.element === e) {
        return index;
      } else {
        current = current.next;
        index++;
      }
    }
    return -1;
  }
  
  lastIndexOf(e: E): number {
    var index = 0;
    var lastIndex = -1;
    var current = this.head;
    while(current) {
      if(current.element === e) {
        lastIndex = index;
      } else {
        current = current.next;
      }
      index++;
    }
    return lastIndex;
  }
  
  contains(e: E): boolean {
    if (this.size === 0) return false;
    var current = this.head;
    while(current) {
      if (current.element === e) {
        return true;
      } else {
        current = current.next;
      }
    }
    return false;
  }
  
  set(index: number, e: E): E {
    if(index < 0 || index >= this.size) return null;
    var current = this.head;
    for(var i = 0; i < index; i++) {
      current = current.next;
    }
    current.element = e;
    return current;
  }
  
  isEmpty(): boolean {
    return this.size === 0;
  }
  
  size(): number {
    return this.size;
  }
  
  
}
