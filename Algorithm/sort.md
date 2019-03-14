# 第2节：排序



+ ### 冒泡排序

比较相邻的两个元素，如果前面的比后面的大着进行交换；

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

