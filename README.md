import java.util.Arrays;
import java.util.Random;
import java.util.Scanner;
public class Sortiing {
    
    public static void main(String[] args) {
  Scanner sc = new Scanner(System.in);
  Random rd = new Random();
  System.out.print("enter the array size : ");
  int n = sc.nextInt();
  
        int[] arrayToSort = new int[n];
  for(int i=0 ; i<n; i++)
   arrayToSort[i] = rd.nextInt(10*n);
  System.out.println("the unsorted array :");
  for(int i = 0 ; i< n ; i++)
   System.out.print(arrayToSort[i]+ " , ");
  System.out.println("\n\n");
  
  
        // Measure time for Bubble Sort
  int[] arr = arrayToSort.clone();
  System.out.println("----Bubble sort algorithm-----------");
        long startTime = System.nanoTime();
        bubbleSort(arr);
        long endTime = System.nanoTime();
        System.out.println("Bubble Sort Time: " + (endTime - startTime) + " nanoseconds");
  System.out.println("Sorted array :");
  for(int i = 0 ; i< n ; i++)
   System.out.print(arr[i] + " , ");
  System.out.println("\n\n");
  
        // Measure time for Insertion Sort
        arr = arrayToSort.clone();
  System.out.println("----Insertion sort algorithm-----------");
        startTime = System.nanoTime();
        insertionSort(arr);
        endTime = System.nanoTime();
        System.out.println("Insertion Sort Time: " + (endTime - startTime) + " nanoseconds");
  System.out.println("Sorted array :");
  for(int i = 0 ; i< n ; i++)
   System.out.print(arr[i]+ " , ");
  System.out.println("\n\n");
  
  
        // Measure time for Merge Sort
  arr = arrayToSort.clone();
  System.out.println("----Merg sort algorithm-----------");
        startTime = System.nanoTime();
        mergeSort(arr);
        endTime = System.nanoTime();
        System.out.println("Merge Sort Time: " + (endTime - startTime) + " nanoseconds");
  System.out.println("Sorted array :");
  for(int i = 0 ; i< n ; i++)
   System.out.print(arr[i]+ " , ");
  System.out.println("\n\n");
  
  
        // Measure time for Heap Sort
  arr = arrayToSort.clone();
  System.out.println("----heap sort algorithm-----------");
  startTime = System.nanoTime();
        heapSort(arr);
        endTime = System.nanoTime();
        System.out.println("Heap Sort Time: " + (endTime - startTime) + " nanoseconds");
  System.out.println("Sorted array :");
  for(int i = 0 ; i< n ; i++)
   System.out.print(arr[i]+ " , ");
  System.out.println("\n\n");
    }

    public static void bubbleSort(int[] array) {
        int n = array.length;
        boolean swapped;

        do {
            swapped = false;
            for (int i = 1; i < n; i++) {
                if (array[i - 1] > array[i]) {
                    int temp = array[i - 1];
                    array[i - 1] = array[i];
                    array[i] = temp;
                    swapped = true;
                }
            }
            n--;
        } while (swapped);
    }

    public static void insertionSort(int[] array) {
        int n = array.length;
        for (int i = 1; i < n; ++i) {
            int key = array[i];
            int j = i - 1;

            while (j >= 0 && array[j] > key) {
                array[j + 1] = array[j];
                j = j - 1;
            }
            array[j + 1] = key;
        }
    }

    public static void mergeSort(int[] array) {
        if (array.length > 1) {
            int mid = array.length / 2;
            int[] left = Arrays.copyOfRange(array, 0, mid);
            int[] right = Arrays.copyOfRange(array, mid, array.length);

            mergeSort(left);
            mergeSort(right);

            merge(array, left, right);
        }
    }

    private static void merge(int[] array, int[] left, int[] right) {
        int i = 0, j = 0, k = 0;

        while (i < left.length && j < right.length) {
            if (left[i] <= right[j]) {
                array[k++] = left[i++];
            } else {
                array[k++] = right[j++];
            }
        }

        while (i < left.length) {
            array[k++] = left[i++];
        }

        while (j < right.length) {

array[k++] = right[j++];
        }
    }

    public static void heapSort(int[] array) {
        int n = array.length;

        for (int i = n / 2 - 1; i >= 0; i--) {
            heapify(array, n, i);
        }

        for (int i = n - 1; i > 0; i--) {
            int temp = array[0];
            array[0] = array[i];
            array[i] = temp;

            heapify(array, i, 0);
        }
    }

    private static void heapify(int[] array, int n, int i) {
        int largest = i;
        int left = 2 * i + 1;
        int right = 2 * i + 2;

        if (left < n && array[left] > array[largest]) {
            largest = left;
        }

        if (right < n && array[right] > array[largest]) {
            largest = right;
        }

        if (largest != i) {
            int swap = array[i];
            array[i] = array[largest];
            array[largest] = swap;

            heapify(array, n, largest);
        }
    }
}
    


 

