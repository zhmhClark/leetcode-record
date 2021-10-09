``````java
import java.util.*;


public class Solution {
    /**
     * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
     * 将给定数组排序
     * @param arr int整型一维数组 待排序的数组
     * @return int整型一维数组
     */
    public int[] MySort (int[] arr) {
        // write code here
        quickSort(arr, 0, arr.length-1);
        return arr;
    }
    
    public void quickSort(int[] arr, int left, int right) {
        if (left < right) {
            int point = split(arr, left, right);
            quickSort(arr, left, point - 1);
            quickSort(arr, point + 1, right);
        }
    }
    
    public int split(int[] arr, int left, int right) {
        int baseValue = arr[left];
        while (left < right) {
            while (left < right && arr[right] >= baseValue) {
                right--;
            }
            swap(arr, left, right);
            while (left < right && arr[left] <= baseValue) {
                left++;
            }
            swap(arr, left, right);
        }
        return left;
    }
    
    public void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
``````

