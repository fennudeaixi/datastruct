# datastruct
## 排序原理
排序的本质就是消除逆序数
采用“交换相邻元素”的办法来消除逆序，每次正好只消除一个，因此必须执行O(n2)的交换次数，这就是为什么冒泡、插入等算法只能到平方级别的原因，反过来，基于交换元素的排序要想突破这个下界，必须执行一些比较，交换相隔比较远的元素，使得一次交换能消除多个逆序，希尔、快排、堆排等等算法都是交换比较远的元素，只不过规则各不同罢了
### 例子
假设从小到大排序，简单起见设数组元素两两不等
现在发现了a[i]>a[j]，i<j，考虑下标闭区间[i,j]这个范围的j-i+1个元素，对任意i<k<j，考虑a[k]
若a[k]<a[j]，交换a[i]和a[j]后，三者的逆序数从2变为1（例如3 1 2变成2 1 3）
若a[k]>a[i]，交换a[j]和a[i]后，三者的逆序数从2变为1（例如2 3 1变成1 3 2）
若a[i]>a[k]>a[j]，交换a[i]和a[j]后，三者的逆序数从3变为0（例如3 2 1变成1 2 3）
当然，上面每条都重复计算了a[i]和a[j]的逆序关系，但是减掉重复计算的数量，每次交换，逆序数也必然是递减的，除非你去交换两个本来就有序的元素


## 一些疑问 待解决
### shellsort 
for (j =i; j >=d && arr[j-d] > e; j -= d) {//j>=d? 