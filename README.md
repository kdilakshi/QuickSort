# QuickSort

class QuickSort {
    // Partition method
    static int partition(int arr[], int low, int high) {
        int pivot = arr[high];  // Choosing the last element as the pivot
        int i = low - 1;  // Pointer for smaller elements

        for (int j = low; j < high; j++) {
            if (arr[j] < pivot) { // If current element is smaller than pivot
                i++;
                // Swap arr[i] and arr[j]
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
        // Swap pivot element with the element at (i+1)
        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;

        return i + 1; // Returning partition index
    }

    // Quick Sort Recursive Method
    static void quickSort(int arr[], int low, int high) {
        if (low < high) {
            int partitionIndex = partition(arr, low, high);  // Find partition point
            quickSort(arr, low, partitionIndex - 1);  // Recursively sort left subarray
            quickSort(arr, partitionIndex + 1, high); // Recursively sort right subarray
        }
    }

    // Print the array
    static void printArray(int arr[]) {
        for (int num : arr)
            System.out.print(num + " ");
        System.out.println();
    }

    public static void main(String args[]) {
        int arr[] = {10, 7, 8, 9, 1, 5};
        int n = arr.length;

        System.out.println("Original array:");
        printArray(arr);

        quickSort(arr, 0, n - 1);

        System.out.println("Sorted array:");
        printArray(arr);
    }
}
