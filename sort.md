``````java
public class MySort {
    public static void quickSort(int[] arr) {
        quickSort(arr, 0, arr.length-1);
    }

    public static void quickSort(int[] arr, int left, int right) {
        if (left < right) {
            int i = split(arr, left, right);
            quickSort(arr, left, i - 1);
            quickSort(arr, i + 1, right);
        }
        
    }

    public static int split(int[] arr, int left, int right) {

        int baseValue = arr[left];

        while (left < right) {
            while (left < right && arr[right] >= baseValue) { right--; }
            swap(arr, left, right);
            while (left < right && arr[left] <= baseValue) { left++; }
            swap(arr, left, right);           
        }

        return left;
    }

    public static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }


    public static void mergeSort(int[] arr) {
        mergeSort(arr, 0, arr.length - 1);
    }

    public static void mergeSort(int[] arr, int left, int right) {
        if (left == right) return;

        int middle = (right + left)/2;
        mergeSort(arr, left, middle);
        mergeSort(arr, middle + 1, right);
        merge(arr, left, middle, right);
    }

    public static void merge(int[] arr, int leftStart, int leftEnd, int rightEnd) {
        int[] temp = new int[rightEnd - leftStart + 1];

        int i = leftStart, j = leftEnd + 1, k = 0;

        while (i <= leftEnd && j <= rightEnd) {
            if (arr[i] < arr[j]) {
                temp[k++] = arr[i++];
            } else {
                temp[k++] = arr[j++];
            }
        }

        while (i <= leftEnd) {
            temp[k++] = arr[i++];
        }

        while (j <= rightEnd) {
            temp[k++] = arr[j++];
        }

        for (int m = 0; m < temp.length; m++) {
            arr[leftStart + m] = temp[m];
        }
    }

    public static void heapSort(int[] arr) {
        int len = arr.length - 1;
        for (int i = len/2; i >= 0; i--) {
            heapify(arr, i, len);
        }

        for (int i = 0; i <= len; i++) {
            swap(arr, 0, len - i);
            heapify(arr, 0, len - 1 - i);
        }
    }

    public static void heapify(int[] arr, int i, int end) {
        int left = 2*i + 1;
        int right = left + 1;
        int maxIndex = i;

        if (left <= end && arr[left] > arr[maxIndex]) {
            maxIndex = left;
        }
        if (right <= end && arr[right] > arr[maxIndex]) {
            maxIndex = right;
        }
        
        if (maxIndex != i) {
            swap(arr, i, maxIndex);
            heapify(arr, maxIndex, end);
        }
    }
}
``````

