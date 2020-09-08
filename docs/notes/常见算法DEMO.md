### 排序算法

#### [快速排序](https://blog.csdn.net/shujuelin/article/details/82423852)

> 通过一趟排序将要排序的数据分割成独立的两部分，其中一部分的所有数据都比另外一部分的所有数据都要小，然后再按此方法对这两部分数据分别进行快速排序，整个排序过程可以递归进行，以此达到整个数据变成有序序列

> 快速排序的每一轮处理其实就是将这一轮的基准数归位，直到所有的数都归位为止

> 快速排序之所比较快，因为相比冒泡排序，每次交换是跳跃式的。每次排序的时候设置一个基准点，将小于等于基准点的数全部放到基准点的左边，将大于等于基准点的数全部放到基准点的右边。这样在每次交换的时候就不会像冒泡排序一样每次只能在相邻的数之间进行交换，交换的距离就大的多了。因此总的比较和交换次数就少了，速度自然就提高了。当然在最坏的情况下，仍可能是相邻的两个数进行了交换。因此快速排序的最差时间复杂度和冒泡排序是一样的都是O(N2)，它的平均时间复杂度为O(NlogN)。其实快速排序是基于一种叫做“二分”的思想。

``` java

public class QuickSort {
    public static void quickSort(int[] arr,int low,int high){
        int i,j,temp,t;
        if(low>high){
            return;
        }
        i=low;
        j=high;
        //temp就是基准位
        temp = arr[low];
 
        while (i<j) {
            //先看右边，依次往左递减
            while (temp<=arr[j]&&i<j) {
                j--;
            }
            //再看左边，依次往右递增
            while (temp>=arr[i]&&i<j) {
                i++;
            }
            //如果满足条件则交换
            if (i<j) {
                t = arr[j];
                arr[j] = arr[i];
                arr[i] = t;
            }
 
        }
        //最后将基准为与i和j相等位置的数字交换
         arr[low] = arr[i];
         arr[i] = temp;
        //递归调用左半数组
        quickSort(arr, low, j-1);
        //递归调用右半数组
        quickSort(arr, j+1, high);
    }
 
 
    public static void main(String[] args){
        int[] arr = {10,7,2,4,7,62,3,4,2,1,8,9,19};
        quickSort(arr, 0, arr.length-1);
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

---

#### [冒泡排序](https://www.cnblogs.com/LearnAndGet/p/10237399.html)

> 从首尾起，一次比较两个元素，如果顺序错误就交换；比较n-1轮，直到全部交换

> ![image](730DA58282E64BE29DBA72C46AEF33AB)

``` java
private static void bubbleSort(int[] values) {

    int temp;
    //外层循环，是需要进行比较的轮数，一共进行5次即可
    for(int i = 0; i < values.length -1; i++) {

        boolean flag = true;
        //内存循环，是每一轮中进行的两两比较
        //并且每一轮结束后，下一次的两两比较中可以少比较一次
        for(int j = 0; j < values.length -1 -i;j++) {
            if(values[j] > values[j + 1]) {
                temp = values[j];
                values[j] = values[j + 1];
                values[j + 1] = temp;

                flag = false;
            }
        }
        System.out.println("第"+(i+1)+"轮排序后的数组为: "+Arrays.toString(values));

        //判断数组是否有序，如果有序，则退出；无序，则继续循环
        if(flag) {
            System.out.println("本轮中的两两比较未发生元素互换，排序已经完成啦");
            break;
        }
    }
}
```

---

#### 归并排序
``` java

```

### 常用

#### N的阶乘

``` java
//普通
int cheng = 1;
for(int i = 1; i <= n; i++) {
    cheng *= i;
}

//采用循环连乘法
public static int fact(int num){
	int temp=1;
	int factorial=1;
	while(num>=temp){
		factorial=factorial*temp;
		temp++;
	}
	return factorial;
}

//采用递归法
public static int recurrence(int num){
	if(num<=1)
		return 1;
	else
		return num*recurrence(num-1);
}
```

---

