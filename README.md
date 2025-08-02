# Arraylist


      import java.util.ArrayList;
       import java.util.Scanner;

        public class ArrayListDemo {
        public static void main(String[] args) {
        double StartTime=System.nanoTime();
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the size of the ArrayList: ");
        int size = scanner.nextInt();

        ArrayList<Integer> list = new ArrayList<>();

        System.out.println("Enter " + size + " elements:");

        long startTime = System.nanoTime();

        for (int i = 0; i < size; i++) {
            System.out.print("Element " + (i + 1) + ": ");
            int element = scanner.nextInt();
            list.add(element);
        }

        System.out.println("The ArrayList is: " + list);

        System.out.print("Enter the position of the element to display (0 to " + (size - 1) + "): ");
        int pos = scanner.nextInt();

        if (pos >= 0 && pos < size) {
            System.out.println("Element at position " + pos + " is: " + list.get(pos));
        } else {
            System.out.println("Invalid position! Please enter a position between 0 and " + (size - 1));
        }

        long endTime = System.nanoTime();

        long elapsedTime = endTime - startTime;

        System.out.println("Execution time (nanoseconds): " + elapsedTime);
        

        scanner.close();
    double StopTime=System.nanoTime();
    System.out.println("Total execution Time"+(StopTime-StartTime));
    }
    }




//Linkedlist



        import java.util.Scanner;

class Node {
    int data;
    Node next;

    Node(int d) {
        data = d;
        next = null;
    }
}

class MyLinkedList {
    private Node head;

    public MyLinkedList() {
        head = null;
    }

    public void insertAtBeginning(int data) {
        Node n = new Node(data);
        n.next = head;
        head = n;
        System.out.println(data + " inserted at beginning");
    }

    public void insertAtEnd(int data) {
        Node n = new Node(data);
        if (head == null) {
            head = n;
            System.out.println(data + " inserted at end");
            return;
        }
        Node t = head;
        while (t.next != null) {
            t = t.next;
        }
        t.next = n;
        System.out.println(data + " inserted at end");
    }

    public void insertAtPosition(int data, int position) {
        if (position <= 0) {
            System.out.println("Invalid position");
            return;
        }
        if (position == 1) {
            insertAtBeginning(data);
            return;
        }
        Node n = new Node(data);
        Node t = head;
        for (int i = 1; i < position - 1 && t != null; i++) {
            t = t.next;
        }
        if (t == null) {
            System.out.println("Position out of bounds");
            return;
        }
        n.next = t.next;
        t.next = n;
        System.out.println(data + " inserted at position " + position);
    }

    public void printList() {
        if (head == null) {
            System.out.println("List is empty");
            return;
        }
        Node t = head;
        System.out.print("LinkedList: ");
        while (t != null) {
            System.out.print(t.data);
            if (t.next != null) System.out.print(" -> ");
            t = t.next;
        }
        System.out.println();
    }
    }

    public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        MyLinkedList list = new MyLinkedList();

        int n = sc.nextInt();
        for (int i = 0; i < n; i++) {
            list.insertAtEnd(sc.nextInt());
        }
        list.printList();

        int choice;
        do {
            System.out.println("1.Begin 2.End 3.Position 4.Display 0.Exit");
            choice = sc.nextInt();
            switch (choice) {
                case 1:
                    list.insertAtBeginning(sc.nextInt());
                    list.printList();
                    break;
                case 2:
                    list.insertAtEnd(sc.nextInt());
                    list.printList();
                    break;
                case 3:
                    int data = sc.nextInt();
                    int pos = sc.nextInt();
                    list.insertAtPosition(data, pos);
                    list.printList();
                    break;
                case 4:
                    list.printList();
                    break;
                case 0:
                    break;
                default:
                    System.out.println("Invalid");
            }
        } while (choice != 0);
        sc.close();
    }
}




