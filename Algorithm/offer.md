# 第1节：剑指offer



+ #### 二维数组的查找

  **题目**：在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

  **思路**：从右上角开始进行查询比较，如果数字大于查找的数字，则列数减一；如果数字小于查找的数字，则行数加一；

  ```java
  public class Main{
      
      public static boolean findNum(int[][] matrix, int num){
          //输入参数检查
          if(matrix == null || matrix.length < 1 || matrix[0].length < 1){
              return false;
          }
          
          //数组行数
          int rows = matrix.length;
          //数组列数
          int cols = matrix[1].length;
          //起始行
          int row = 0;
          //起始列
          int col = cols - 1;
          
          //查找数字在数组中的位置
          while(row >= 0 && row < rows && col >= 0 && col < cols){
              if(matrix[row][col] == num){
                	return true;
              }else if(matrix[row][col] > num){
                  col--;
              }else{
                  row++;
              }
          }
          return false;
      }
  }
  ```

+ #### 替换空格

  **题目**：请实现一个函数，把字符串中的每个空格替换成"%20"，例如“We are happy.”，则输出 “We%20are%20happy.”。

  **思路**：首先判断空间大小，如果空间满足维护一个指针从后往前，遇到空格进行替换；

  ```java
  采用思路方法：
  public class Main{
      public static String replaceWhiteBlank(String str){
  		//输入检查
          if(str == null || str.length() <= 0){
          	return "error";
          }
          
          int length = str.length();
          int whiteCount = 0;
          for(int i = 0; i < length; i++){
              //计算空格
              if(str.charAt(i) == ' '){
  				whiteCount++;
              }
          }
          //如果没有空格，直接返回
          if(whiteCount == 0){
           	return str;
          }
          
          int targetLength = whiteCount * 2 + length;
          char[] array = new char[targetLength];
          
          //从后往前处理字符串
          length--;
          targetLength--;
          while(length >=0 && targetLength >=0){
              if(str.charAt(length) == ' '){
  				array[targetLength--] = '0';
  				array[targetLength--] = '2';
  				array[targetLength-- = '%';
              }else{
                  array[targetLength--] = str.charAt[length];
              }
              length--;
          }
          return String.valueOf(array);
      }
  }
  
  使用StringBuffer的方法：
  public class Main{
      public static String replaceBlank(String str){
          //输入检查
          StringBuffer result = new StringBuffer(str);
          if(result.length() <= 0){
          	return "error";
          }
          
          int index = result.indexOf(" ");
          while(index != -1){
          	result.replace(index, index + 1, "%20");
          	index = result.indexOf(" ", index);
          }
          return result.toString(); 
      }
  }
  ```

+ #### 从尾到头打印链表

  **题目**：输入个链表的头结点，从尾到头反过来打印出每个结点的值。

  **思路**：使用栈的方式进行，将链表从头到尾压入栈内，出栈的过程就对应着从尾到头。

  ```java
  public class Main{
      //定义链表节点
      public static class ListNode{
          int value;
          ListNode next;
      }
      
      public static void printList(ListNode root){
          //输入检查
          if(root == null){
              return;
          }
          
          Stack<ListNode> stack = new Stack<>();
          //入栈
          while(root != null){
              stack.push(root);
              root = root.next;
          }
          ListNode temp;
          //出栈
          while(!stack.isEmpty()){
              temp = stack.pop();
              System.out.println(temp.value + " ");
          }
      }
  }
  ```

+ #### 二叉树的深度

  **题目**：输入一棵二叉树的根结点，求该树的深度。从根结点到叶子点依次经过的结点（含根、叶结点）形成树的一条路径，最长路径的长度为树的深度。

  ```java
  public static int treeDepth(BinaryTreeNode root){
      if(root == null){
          return 0;
      }
      
      int left = treeDepth(root.left);
      int right = treeDepth(root.right);
      
      return left > right ? (left + 1) : (right + 1);
  }
  ```

+ **List转二叉树**

  **题目**：给你一个User，包含id，name，parentId。然后给你一个List<User>，要求将它转换成一棵树的结构。只有一个跟节点，parentId=-1；

  **思路：**先遍历查找父节点，然后递归查找子节点

  ```java
  public class TreeeNode<T>{
      T value;
      TreeNode children;
      //省略
  }
  
  public static TreeNode<User> listToTree(List<User> list){
      if(list == null){
          return null;
      }
      
      TreeNode<User> root = null;
      
      for(User user : list){
          if(user.parentId == -1){
              root = new TreeNode<User>(user);
              findChildren(root, list);
          }
      }
      return root;
  } 
  
  public static void findChildren(TreeNode<User> root, List<User> list){
      for(User user : list){
          if(user.parentId() == root.parentId()){
              TreeNode<User> son = new TreeNode<User>(user);
              root.setChildren(son);
              findChildren(son, list);
          }
      }
  }
  ```

+ #### 二分查找

  **题目**：排序数组

  ```java
  public static Boolean findNums(int[] nums, int K){
      if(nums == null || nums.length <= 0){
          return false;
      }
      
      int start = 0;
      int end = nums.length - 1;
      int mid = 0;
      
      while(start <= end){
          mid = (start + end) / 2;
          if(nums[mid] == K){
              return true;
          }else if(nums[mid] < K){
              start = mid + 1;
          }else{
              end = mid - 1;
          }
      }
      return false;
  }
  ```

+ 