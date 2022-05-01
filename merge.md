合并两个有序列表的写法

```java
public List<Integer> mergeList(List<Integer> list1, List<Integer> list2) {
        List<Integer> ans = new ArrayList<>();

        int i = 0, j = 0;

        while (true) {
            if (i == list1.size()) {
                while (j < list2.size()) ans.add(list2.get(j++));
                break;
            }

            if (j == list2.size()) {
                while (i < list1.size()) ans.add(list1.get(i++));
                break;
            }

            if (list1.get(i) < list2.get(j)) {
                ans.add(list1.get(i++));
            } else {
                ans.add(list2.get(j++));
            }
        }

        return ans;
}
```

