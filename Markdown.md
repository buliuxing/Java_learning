# Markdown基本语法

## 一、标题

设置为标题的文字前加#来表示

```markdown
# 这是一级标题
## 这是二级标题
............
```

## 二、字体

* **加粗**

  要加粗的文字左右分别用两个*号包起来

  ```markdown
  **这是要加粗的文字**
  ```

* **斜体**

  要倾斜的文字左右分别用一个*号包起来

  ```markdown
  *这是倾斜的文字*
  ```

* **倾斜加粗**

  要倾斜和加粗的文字左右分别加三个*号包起来

  ```markdown
  ***这是倾斜加粗的文字***
  ```

## 三、引用

在引用的文字前加>即可，可嵌套

```markdown
>这是引用的内容
```

## 四、超链接

```markdown
[这是百度超链接](http://www.baidu.com)
```

## 五、列表

* **无序列表**

  无序列表用- + * 任意一种都可以

  ```markdown
  - 列表内容
  + 列表内容
  * 列表内容
  
  ps: 注意空格
  ```

* **有序列表**

  数字加点

  ```markdown
  1. 列表内容
  2. 列表内容
  3. 列表内容
  
  ps：注意空格
  ```

* **列表嵌套**

  上一级和下一级之间敲三个空格即可

## 六、表格

MAC使用快捷键 option+command+T

| **表格** | 列一 | 列二 |
| :------: | :--: | :--: |
|   行一   |      |      |
|   行二   |      |      |

## 七、代码

MAC使用快捷键 option+command+C

```java
public class Main{
    public static viod main(String[] args){
        //this is code
    }
}
```

## 八、图片

MAC插入图片使用快捷键 control+command+I

![这是图片](/Users/yangzengrui01/Downloads/保罗.jpg)