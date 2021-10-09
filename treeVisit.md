``````java
import java.util.*;
 
/*
 * public class TreeNode {
 *   int val = 0;
 *   TreeNode left = null;
 *   TreeNode right = null;
 * }
 */
 
public class Solution {
    /**
     *
     * @param root TreeNode类 the root of binary tree
     * @return int整型二维数组
     */
    public int[][] threeOrders (TreeNode root) {
        // write code here
        ArrayList<Integer> resA = new ArrayList<>();
        Stack<TreeNode> stackA = new Stack<>();
        stackA.push(root);
        while(!stackA.isEmpty()) {
            TreeNode node = stackA.pop();
            resA.add(node.val);
            if (node.right != null) {
                stackA.push(node.right);
            }
            if (node.left != null) {
                stackA.push(node.left);
            }
        }
         
        ArrayList<Integer> resB = new ArrayList<>();
        Stack<TreeNode> stackB = new Stack<>();
        stackB.push(root);
        TreeNode cur = root;
        while(!stackB.isEmpty() || cur != null) {
            if (cur != null) {
                stackB.push(cur);
                cur = cur.left;
            } else {
                cur = stackB.pop();
                resB.add(cur.val);
                cur = cur.right;
            }
        }
         
        ArrayList<Integer> resC = new ArrayList<>();
        Stack<TreeNode> stackC = new Stack<>();
        stackC.push(root);
        while(!stackC.isEmpty()) {
            TreeNode node = stackC.pop();
            resC.add(node.val);
            if (node.left != null) {
                stackC.push(node.left);
            }
            if (node.right != null) {
                stackC.push(node.right);
            }
        }
         
        int num = resA.size();
         
        int[][] re = new int[3][num];
         
        for (int i = 0; i < num; i++) {
            re[0][i] = resA.get(i);
            re[1][i] = resB.get(i);
            re[2][i] = resC.get(num -i - 1);
        }
         
        return re;
    }
}
``````

