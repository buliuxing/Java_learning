# 第2节：排序



+ ### 冒泡排序

比较相邻的两个元素，如果前面的比后面的大着进行交换；

时间复杂度 O(n^2) 

优化方式：

​		1、记录最有一次交换发生的点K；

​		2、增加哨兵，监控是否还存在交换，如果没有则表示排序完成；

```java
public static void bubbleSort(int[] num){
    //输入条件判断
    if(num == null num.length < 1){
        return;
    }
    
    int temp = 0;
    int length = num.length;
    int flag = true;  //哨兵
    int k = length -1; //记录最后一次交换点
        
    for(int i = 0; i < length - 1 && flag; i++){
        flag = false;
    	for(int j = 0; j < k ; j++){
            if(num[j] > num[j + 1]){
                //交换相邻两个位置
                temp = num[j];
                num[j] = num[j + 1];
                num[j + 1] = temp;
                k = j;
                flag = true;
            }
        }
    }
}
```



- ### 选择排序

在要排序的数字中，选择最小的一个数与第一个位置的数交换；然后再剩下的数当中找再找最小的数和第二个位置的交换，如此循环；

时间复杂度 O(n^2) 

```java
public static void selectSort(int[] num){
    //数组的长度
    int size = num.length;
    //临时变量
    int temp = 0;
    for(int i = 0; i < size -1; i++){
        //待确定的位置
        int k = i;
        //选择出应该在第一位置的数
        for(int j = size -1; j > i; j--){
            if(num[j] < num[k]){
                k = j;
            }
        }
        //交换位置
        temp = num[i];
        num[i] = num[k];
        num[k] = temp;
    }
    
}
```

- ### 插入排序

每步将一个待排序的记录，按其顺序码大小插入到前面已经排序的字序列的合适位置，知道全部插入排序位置；

时间复杂度 O(n^2) 

```java
public static void insertSort(int[] num){
   //数组长度
    int size = num.length;
    //临时变量
    int temp = 0;
    //记录位置
    int j = 0;
    for(int i = 1; i < size; i++){
        temp = num[i];
        //如果temp比前面的值下，则将前面的位置后移
        for(j = i; j > 0 && temp < num[j - 1]; j--){
            num[j] = num[j - 1];
        }
        num[j] = temp;
    }
}
```

- ### 堆排序

初始时把要排序的数的序列看作是一棵顺序存储的二叉树，调整它们的存储序，使之成为一个 堆，这时堆的根节点的数最大。然后将根节点与堆的最后一个节点交换。然后对前面(n-1)个数重新调整使之成为堆。依此类推，直到只有两个节点的堆，并对 它们作交换，最后得到有n个节点的有序序列。从算法描述来看，堆排序需要两个过程，一是建立堆，二是堆顶与堆的最后一个元素交换位置。所以堆排序有两个函数组成。一是建堆的渗透函数，二是反复调用渗透函数实现排序的函数。

时间复杂度 O(nlogn) 

```java
public static void heapSort(int[] a){
    int arrayLength = a.length;
    //循环建堆
    for(int i = 0; i < arrayLength - 1; i++){
        //建堆
        buildMaxHeap(a, arrayLength - 1- i);
        //交换堆顶和最后一个元素
        swap(a, 0, arrayLength - 1 - i);
        System.out.println(Arrays.toString(a));
    }
}
//建立堆
public static void insertSort(int[] num， int lastIndex){
   //从lastIndex处节点的父节点开始
    for(int i = (lastIndex - 1) / 2; i >= 0; i--){
        //K保存正在判断的节点
        int k = i;
        //如果当前k节点的子节点存在
        while(k * 2 + 1 <= lastIndex){
            //k节点的左子节点的索引
            int biggerIndex = 2 * k + 1;
            //如果biggerIndex小于lastIndex,即biggerIndex+1代表的k节点的右子节点存在
            if(biggerIndex < lastIndex){
               // 若果右子节点的值较大
                if (data[biggerIndex] < data[biggerIndex + 1]) {
                    // biggerIndex总是记录较大子节点的索引
                    biggerIndex++;
                } 
            }
            // 如果k节点的值小于其较大的子节点的值
            if (data[k] < data[biggerIndex]) {
                // 交换他们
                swap(data, k, biggerIndex);
                // 将biggerIndex赋予k，开始while循环的下一次循环，重新保证k节点的值大于其左右子节点的值
                k = biggerIndex;
            } else {
                break;
            }
        }
    }
}
//交换
private static void swap(int[] num, int i, int j){
    int temp = num[i];
    num[i] = num[j];
    num[j] = temp;
}
```

- ### 快速排序

其中一部分记录的关键字均比另一部分关键字小，则分别对这两部分继续进行排序，直到整个序列有序。

时间复杂度 O(nlogn) 

```java
public static void quick(int[] nums){
    //输入检查
    if(nums.length > 0){
        quickSort(nums, 0, nums.length - 1);
    }
}

public static void quickSort(int[] nums, int low, int high){
    if(low >= high){
        return;
    }
    //将数组分为两部分
    int middle = getMiddle(nums, low, high);
    quickSort(nums, low, middle - 1);
    quickSort(nums, middle + 1, high);
}

public static int getMiddle(int[] numbers, int low, int high){
    int temp = numbers[low]; // 数组的第一个作为中轴
    while (low < high) {
        while (low < high && numbers[high] > temp) {
            high--;
        }
        numbers[low] = numbers[high];// 比中轴小的记录移到低端
        while (low < high && numbers[low] < temp) {
            low++;
        }
        numbers[high] = numbers[low]; // 比中轴大的记录移到高端
    }
    numbers[low] = temp; // 中轴记录到尾
    return low; // 返回中轴的位置
}
```

