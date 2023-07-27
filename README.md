# SS



package sunbeam;

class SinglyList {
	static class Node {
		private int data;
		private Node next;
		public Node() {
			this.data = 0;
			this.next = null;
		}
		public Node(int val) {
			this.data = val;
			this.next = null;
		}
	}
	
	private Node head;
	public SinglyList() {
		head = null;
	}
	public void addLast(int val) {
		Node newNode = new Node(val);
		if(head == null)
			head = newNode;
		else {
			Node trav = head;
			while(trav.next != null)
				trav = trav.next;
			trav.next = newNode;
		}
	}
	public void display() {
		System.out.print("List: ");
		Node trav = head;
		while(trav != null) {
			System.out.print(trav.data + " -> ");
			trav = trav.next;
		}
		System.out.println("");
	}
	public void reverse() {
		// consider current list as old and new list as empty.
		Node oldhead = head;
		head = null;
		while(oldhead != null) {
			// delete first (temp) from old list
			Node temp = oldhead;
			oldhead = oldhead.next;
			// add first (temp) to new list
			temp.next = head;
			head = temp;
		} // repeat until old list is finished
	}
	
	private Node recReverse(Node h) {
		if(h.next == null) {
			head = h;
			return h;
		}
		Node t = recReverse(h.next);
		t.next = h;
		h.next = null;
		return h;
	}
	public void recReverse() {
		if(head != null)
			recReverse(head);
	}
	
	private void revDisplay(Node h) {
		if(h == null)
			return;
		revDisplay(h.next);
		System.out.print(h.data + " -> ");
	}
	public void revDisplay() {
		System.out.print("List: ");
		revDisplay(head);
		System.out.println("");
	}
	
	public int findMid() {
		Node fast = head, slow = head;
		while(fast != null && fast.next != null) {
			slow = slow.next;
			fast = fast.next.next;
		}
		return slow.data;
	}
}

public class LinkedListMain {
	public static void main(String[] args) {
		SinglyList list = new SinglyList();
		list.addLast(10);
		list.addLast(20);
		list.addLast(30);
		list.addLast(40);
		list.addLast(50);
		list.display();
		
//		list.reverse();
//		list.display();

//		list.recReverse();
//		list.display();

//		list.revDisplay();
//		list.display();

		System.out.println("Middle: " + list.findMid());
	}
}
==================================================================  

                                Stack
package sunbeam;

import java.util.Scanner;

class Stack {
	private int[] arr;
	private int top;

	public Stack(int size) {
		arr = new int[size];
		top = -1;
	}
	public void push(int val) {
		if(isFull())
			throw new RuntimeException("Stack is Full.");
		top++;
		arr[top] = val;
	}
	public void pop() {
		if(isEmpty())
			throw new RuntimeException("Stack is Empty.");
		top--;
	}
	public int peek() {
		if(isEmpty())
			throw new RuntimeException("Stack is Empty.");
		return arr[top];
	}
	public boolean isEmpty() {
		return top == -1;
	}
	public boolean isFull() {
		return top == arr.length-1;
	}
}

public class StackMain {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		Stack s = new Stack(6);
		int choice, val;
		do {
			System.out.println("\n0. Exit\n1. Push\n2. Pop\n3. Peek\nEnter choice: ");
			choice = sc.nextInt();
			switch(choice) {
			case 1: // push
				try {
					System.out.print("Enter value to push: ");
					val = sc.nextInt();
					s.push(val);
				} catch (Exception e) {
					System.out.println(e.getMessage());
				}
				break;
			case 2: // pop
				try {
					val = s.peek();
					s.pop();
					System.out.println("Popped: " + val);
				} catch (Exception e) {
					System.out.println(e.getMessage());
				}
				break;
			case 3: // peek
				try {
					val = s.peek();
					System.out.println("Peek: " + val);
				} catch (Exception e) {
					System.out.println(e.getMessage());
				}
				break;
			}
		}while(choice != 0);
		sc.close();
	}
}
==================================================================
linear Quque

package sunbeam;

import java.util.Scanner;

class LinearQueue {
	private int[] arr;
	private int rear, front;
	
	public LinearQueue(int size) {
		arr = new int[size];
		rear = -1;
		front = -1;
	}
	public boolean isFull() {
		return rear == arr.length - 1;
	}
	public boolean isEmpty() {
		return rear == front;
	}
	public void push(int val) {
		if(isFull())
			throw new RuntimeException("Queue is Full.");
		rear++;
		arr[rear] = val;
	}
	public void pop() {
		if(isEmpty())
			throw new RuntimeException("Queue is Empty.");
		front++;
	}
	public int peek() {
		if(isEmpty())
			throw new RuntimeException("Queue is Empty.");
		return arr[front + 1];
	}
}


public class LinearQueueMain {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		LinearQueue q = new LinearQueue(6);
		int choice, val;
		do {
			System.out.println("\n0. Exit\n1. Push\n2. Pop\n3. Peek\nEnter choice: ");
			choice = sc.nextInt();
			switch(choice) {
			case 1: // push
				try {
					System.out.print("Enter value to push: ");
					val = sc.nextInt();
					q.push(val);
				} catch (Exception e) {
					System.out.println(e.getMessage());
				}
				break;
			case 2: // pop
				try {
					val = q.peek();
					q.pop();
					System.out.println("Popped: " + val);
				} catch (Exception e) {
					System.out.println(e.getMessage());
				}
				break;
			case 3: // peek
				try {
					val = q.peek();
					System.out.println("Peek: " + val);
				} catch (Exception e) {
					System.out.println(e.getMessage());
				}
				break;
			}
		}while(choice != 0);
		sc.close();
	}
}
==================================================================
                      DOublyL

package sunbeam;

import java.util.Scanner;

class DoublyList {
	// Node class
	static class Node {
		// Node class fields
		private int data;
		private Node next;
		private Node prev;
		// Node class methods
		public Node() {
			data = 0;
			next = null;
			prev = null;
		}
		public Node(int val) {
			data = val;
			next = null;
			prev = null;
		}
	}
	
	// List class fields
	private Node head;
	
	// List class methods
	public DoublyList() {
		head = null;
	}
	
	public void displayForward() {
		System.out.println("Fwd List: ");
		Node trav = head;
		while(trav != null) {
			System.out.println(trav.data);
			trav = trav.next;
		}
	}

	public void displayReverse() {
		System.out.println("Rev List: ");
		// special 1: if empty list, return.
		if(head == null)
			return;
		// traverse till last node
		Node trav = head;
		while(trav.next != null)
			trav = trav.next;
		// print all nodes in rev direction
		while(trav != null) {
			System.out.println(trav.data);
			trav = trav.prev;
		}	
	}
	
	public boolean isEmpty() {
		return head == null;
	}
	
	public void addLast(int val) {
		// create new node & init it
		Node newNode = new Node(val);
		// special 1: if list is empty, make new node as first node of list
		if(head == null) {
			head = newNode;
		}
		// general: add node at the end
		else {
			// traverse till last node
			Node trav = head;
			while(trav.next != null)
				trav = trav.next;
			// add new node after trav (trav.next)
			trav.next = newNode;
			// newnode's prev to last node (trav)
			newNode.prev = trav;
		}
	}

	void addFirst(int val) {
		// create new node and init it
		Node newNode = new Node(val);
		// special 1: if list is empty
		if(isEmpty()) {
			head = newNode;
		}
		// general: add node at the start
		else {
			// new node next should point to head
			newNode.next = head;
			// head's prev to newNode
			head.prev = newNode;
			// head should point to new node
			head = newNode;
		}
	}

	public void addAtPos(int val, int pos) {
		// special 1: if list is empty, add node at the start
		// special 2: if pos<=1, add node at the start
		if(head == null || pos <= 1)
			addFirst(val);
		// general: add node at given pos
		else {
			// allocate & init new node
			Node newNode = new Node(val);
			// traverse till pos-1 (trav)
			Node temp, trav = head;
			for(int i=1; i < pos-1; i++) {
				// special 3: if pos > length of list, add node at the end.
				if(trav.next == null)
					break;
				trav = trav.next;
			}
			// take temp pointer to node after trav
			temp = trav.next;
			// newnode's next should point to trav's next i.e. temp
			newNode.next = temp;
			// newnode's prev to trav
			newNode.prev = trav;
			// trav's next should pointer to new node
			trav.next = newNode;
			// temp's prev to newNode
			if(temp != null) // special 3: if adding at end, next line is not required.
				temp.prev = newNode;
		}
	}
	
	public void delFirst() {
		// special 1: if list is empty, throw exception
		if(head == null)
			throw new RuntimeException("List is empty.");
		// special 2: if list has single node, make head null
		if(head.next == null)
			head = null;
		// general: 
		else {
			// make head pointing to next node.
			head = head.next;
			// note: the old first node will be garbage collected.
			// second node (new head) prev should be null
			head.prev = null;
		}
	}

	public void delAtPos(int pos) {
		// special 1: if pos = 1, delete first node
		if(pos == 1)
			delFirst();
		// special 2: if list is empty or pos < 1, then throw exception.
		if(head == null || pos < 1)
			throw new RuntimeException("List is empty or Invalid position.");
		Node trav = head;
		// traverse till pos (trav)
		for(int i = 1; i < pos; i++) {
			// special 3: if pos is beyond list length, then throw exception.
			if(trav == null)
				throw new RuntimeException("Invalid position.");
			trav = trav.next;
		}
		// trav's previous node's next to trav's next node
		trav.prev.next = trav.next;
		// trav's next node's prev to trav's previous node
		if(trav.next != null) // special 3: while deleting last node, skip next line.
			trav.next.prev = trav.prev;
		// trav node will be garbage collected
	}

	// Lab Assignment: delLast()
}

public class DoublyListMain {
	public static void main(String[] args) {
		int choice, val, pos;
		DoublyList list = new DoublyList();
		Scanner sc = new Scanner(System.in);
		do {
			System.out.println("\n0. Exit\n1. Display\n2. Add First\n3.  Add Last\n4. Add At Pos\n5. Del First\n6.  Del Last\n7. Del At Pos\n8. Del All\nEnter choice: ");
			choice = sc.nextInt();
			switch (choice) {
			case 1: // Display
				list.displayForward();
				list.displayReverse();
				break;
			case 2: // Add First
				System.out.print("Enter new element: ");
				val = sc.nextInt();
				list.addFirst(val);
				break;
			case 3: // Add Last
				System.out.print("Enter new element: ");
				val = sc.nextInt();
				list.addLast(val);
				break;
			case 4: // Add At Pos
				System.out.print("Enter new element: ");
				val = sc.nextInt();
				System.out.print("Enter element position: ");
				pos = sc.nextInt();
				list.addAtPos(val, pos);				
				break;
			case 5: // Del First
				try {
					list.delFirst();
				} catch (Exception e) {
					System.out.println(e.getMessage());
				}
				break;
			case 6: // Del Last
//				try {
//					list.delLast();
//				} catch (Exception e) {
//					System.out.println(e.getMessage());
//				}
				break;
			case 7: // Del At Pos
				System.out.print("Enter element position: ");
				pos = sc.nextInt();
				try {
					list.delAtPos(pos);
				} catch (Exception e) {
					System.out.println(e.getMessage());
				}
				break;
			case 8: // Del All
//				list.delAll();
				break;
			}
		} while(choice!=0);
		sc.close();
	}
}


