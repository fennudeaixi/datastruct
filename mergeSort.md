# mergesort

思想:

![image-20201209212117879](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201209212117879.png)

**CODE**



假设数组不为空

```cpp
class sloution {

public:
	//对 arr[left...right]进行排序
	void mergeSort(int arr[], int left, int right) {

		if (left >= right)
			return;
		//将数组分成两个部分,并且进行排序
		int mid = left + (right - left) / 2;//防止溢出
		mergeSort(arr, left, mid);
		mergeSort(arr, mid + 1, right);
		combine(arr, left, mid, right);

	}
private:
	void combine(int arr[], int left, int mid, int right) {

		int length = right - left + 1;
		int* temp = new int[length];

		int i = left, j = mid + 1, k = 0;
		for (; k < length; k++) {

			if (i > mid)
				temp[k] = arr[j++];
			else if (j > right)
				temp[k] = arr[i++];
			else if (arr[i] < arr[j])
				temp[k] = arr[i++];
			else
				temp[k] = arr[j++];
		}

		copy(temp, temp + length, arr+left);
		delete[] temp;
	}

};
```

<br />
<br />

![image-20201209212239864](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201209212239864.png)

TIME  横线以上 O(1+2+4+....n)=o(n)  横线以下 有logN层  T(O)=O(NlogN)

![image-20201209212347327](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201209212347327.png)



计算这个之前要先明确一点,计算机的指令是一条一条执行的.在执行这条语句时

mergeSort(arr, left, mid);递归并不是多线程的,而是会经历深度优先遍历,上图粉色的这部分,计算空间复杂度横线以上 space total=O(n/2+n/4+n/8+ . ....1)=O(n),横线以下一共logN层 所以 O(n)=O(NlogN)

### 拓展

### rainbowSort

**CODE**

```c++
#include <iostream>
#include <algorithm>
using namespace std;

//对arr[left..right]进行排序  用 1 2 3 代替 A B C
void rainbowSort(int arr[], int left, int right) {

    //三个部分 arr[left...i)=1 arr[i...j]=2 arr(j...right)=3
    int i = left, j = right, k = left;

    while (k <= j) {
        if (arr[k] == 1)
            swap(arr[k++], arr[i++]);
        else if (arr[k] == 3) {
            swap(arr[k], arr[j]);
            j--;
        }
        else //arr[k]==2
            k++;
    }

}

int main() {

    int a[10]{ 3,2,1,1,2,3,3,2,1,2 };
    rainbowSort(a, 0, 9);
    for (auto i : a) {
        cout << i << " ";
    }

}
```

**A1B2C3D4->ABCD1234**



**ABCD1234->A1B2C3D4**

