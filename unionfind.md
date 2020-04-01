# 并查集算法总结
0. 并查集用于解决连通性、等价类等问题
1. 常规并查集写法（路径压缩&&加权）
    ```java
        int[] unionfind;
        int[] size;
        int find(int p){
           int res = p;
           while(unionfind[res] != res) res = unionfind [res];
           int temp = unionfind[p];
           while(temp != res) {
               unionfind[p] = res;
               p = temp;
               temp = unionfind[temp];
           }
           return res;
       }
       void union(int p, int q){
           int pRoot = find(p), qRoot = find(q);
           if(pRoot == qRoot) return;
           if(size[pRoot] < size[qRoot]){
               unionfind[pRoot] = qRoot;
               size[qRoot] += size[pRoot];
           }else{
               unionfind[qRoot] = pRoot;
               size[pRoot] += size[qRoot];
           }
       }
       //正式使用要初始化unionfind[] 和 size[]
    ```
2. 并查集存在诸多变式
    1. s只有当节点可化为为从零起的连续正整数时，才用整型数组存放并查集结构，其他情况多用 `HashMap<ClassA, ClassA>`存放，用`HashMap`存放时，可以用到其`containskey(key)`常数级调用的特点(leetcode 0399)
    2. 有时题目答案可通过改造函数获得，例如为`union()`增加返回值(leetcode 0128)
