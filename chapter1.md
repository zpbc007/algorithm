# 第一章 基础

## 1 栈的实现

栈为后进先出(LIFO)策略的集合类型。

### 1.1 定容字符串栈的实现 

#### 1.1.1 API

|返回值类型|函数名|描述|
|---|---|---|
||FixedCapacityStackOfStrings(int cap)|创建一个容量为cap的空栈|
|void|push(String item)|添加一个字符串|
|String|pop()|删除最近添加的字符串|
|boolean|isEmpty()|栈是否为空|
|int|size()|栈中的字符串数量|

#### 1.1.2代码实现

```
package chapter1.stack;

import edu.princeton.cs.algs4.*;

public class FixedCapacityStackOfStrings {
    private String[] data;
    private int N;

    public FixedCapacityStackOfStrings(int cap) {
        data = new String[cap];
        N = 0;
    }

    public void push(String item) {
        data[N++] = item;
    }

    public String pop() {
        return data[--N];
    }

    public isEmpty() {
        return N == 0;
    }

    public static void main(String[] args) {
        FixedCapacityStackOfStrings s;
        s = new FixedCapacityStackOfStrings(100);
        while(!StdIn.isEmpty()){
            String item = StdIn.readString();
            if (!item.equals("-"))
                s.push(item);
            else if (!s.isEmpty()) StdOut.print(s.pop() + " ");
        }
        StdOut.println("(" + s.size() + " left on stack)");
    }
}
```

用String数组data来保存栈的数据，用整形N来存放当前数组中存放的数据的数量。在数组的尾部进行插入和弹出操作。

#### 缺点

- 只能在初始化时指定数组的大小，如果数据过多会溢出，过少空间利用不足。
- 只能用于存放String类型的数据，如果要存放其他类型，还需要重写。
- 不支持迭代

### 1.2 定容栈的实现

在[1.1](###-1.1-定容字符串栈的实现)
