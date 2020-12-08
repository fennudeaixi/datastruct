# selecSort

**思想：**<br />从没有排序中找出最小值，放在没有排序的最左端<br />｛-1，-3，4，7｝<br />iteration 1: min -3  =>  -3{-1,4,7}<br />iteration 2: min  -1 => -3,-1{4,7}<br />iteration 3: min 4    => -3,-1,4{7}<br />iteration 4: min 7     => -3,-1,4,7
<a name="bck4m"></a>
## CODE
```cpp
void selectSort(int arr[], int n) {

	int global;
	for (int i = 0; i < n - 1; i++) {//外层for循环表示要迭代多少次

		global = i;
		for (int j = i + 1; j < n; j++) {//内层for循环,从剩余元素中找到最小值
			if (arr[j] < arr[global])
				global = j;

		}
		//交换元素
		swap(arr[i], arr[global]);

	}
}
```
time   n, n - 1, n - 2, ... , 2, 1 operations → n * (n+1) / 2 → O(n^2)=O(n^2)<br />space O(1)
<a name="hwGsm"></a>
## 拓展
运用两个栈实现堆排序<br />stack 1 3 2 4<br />iterator Ⅰ:<br />stack1  4 2 3 1     global_min =4;<br />stack2  1
