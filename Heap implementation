import java.util.Scanner;

class Heap {
    private int[] heap;
    private int size;
    private boolean isMinHeap;

    public Heap(int capacity, boolean isMinHeap) {
        heap = new int[capacity];
        size = 0;
        this.isMinHeap = isMinHeap;
    }

    private int parent(int i) { return (i - 1) / 2; }
    private int leftChild(int i) { return (2 * i) + 1; }
    private int rightChild(int i) { return (2 * i) + 2; }
    
    private boolean compare(int a, int b) {
        return isMinHeap ? (a < b) : (a > b);
    }

    public void insert(int value) {
        if (size == heap.length) {
            System.out.println("Heap is full");
            return;
        }
        heap[size] = value;
        heapifyUp(size);
        size++;
    }

    private void heapifyUp(int i) {
        while (i > 0 && compare(heap[i], heap[parent(i)])) {
            swap(i, parent(i));
            i = parent(i);
        }
    }

    public int removeRoot() {
        if (size == 0) {
            throw new IllegalStateException("Heap is empty");
        }
        int root = heap[0];
        heap[0] = heap[size - 1];
        size--;
        heapifyDown(0);
        return root;
    }

    private void heapifyDown(int i) {
        int left = leftChild(i);
        int right = rightChild(i);
        int extreme = i;

        if (left < size && compare(heap[left], heap[extreme])) {
            extreme = left;
        }
        if (right < size && compare(heap[right], heap[extreme])) {
            extreme = right;
        }
        if (extreme != i) {
            swap(i, extreme);
            heapifyDown(extreme);
        }
    }

    private void swap(int i, int j) {
        int temp = heap[i];
        heap[i] = heap[j];
        heap[j] = temp;
    }

    public void printHeap() {
        for (int i = 0; i < size; i++) {
            System.out.print(heap[i] + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter capacity of heap:");
        int capacity = scanner.nextInt();
        System.out.println("Enter 1 for MinHeap, 0 for MaxHeap:");
        boolean isMinHeap = scanner.nextInt() == 1;
        Heap heap = new Heap(capacity, isMinHeap);

        while (true) {
            System.out.println("\nHeap Operations:");
            System.out.println("1. Insert");
            System.out.println("2. Remove Root");
            System.out.println("3. Print Heap");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            
            switch (choice) {
                case 1:
                    System.out.print("Enter value to insert: ");
                    int value = scanner.nextInt();
                    heap.insert(value);
                    break;
                case 2:
                    try {
                        System.out.println("Removed root: " + heap.removeRoot());
                    } catch (IllegalStateException e) {
                        System.out.println(e.getMessage());
                    }
                    break;
                case 3:
                    heap.printHeap();
                    break;
                case 4:
                    System.out.println("Exiting...");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}
