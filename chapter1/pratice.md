# 第一章 练习

## 1.3.1 为FixedCapacityStackOfStrings添加一个方法isFull()

答：
当数据长度与数组长度相等时不能继续添加数据

```
public boolean isFull() {
    return N == a.length;
}
```

## 1.3.2 给定以下输入，java Stack的输出是什么？

it was - the best - of times - - - it was - the - -

答：

```
was best times of the was the it (1 left on stack)
```

## 1.3.3 假设某个用例程序还会进行一系列入栈和出栈的混合操作。入栈操作会将整数0到9按顺序压入栈：出栈操作会打印出返回值。下面哪种序列是不可能产生的？

a: 4 3 2 1 0 9 8 7 6 5
b: 4 6 8 7 5 3 2 9 0 1
c: 2 5 6 7 4 8 9 3 1 0
d: 4 3 2 1 0 5 6 7 8 9
e: 1 2 3 4 5 6 9 8 7 0
f: 0 4 6 5 3 8 1 7 2 9
g: 1 4 7 9 8 6 5 3 0 2
h: 2 1 4 3 6 5 8 7 9 0

答：
b是错误的

```
public class Practice {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack();
        // 生成从0 到 9的数组 
        Integer[] nums = new Integer[10];
        for (int i = 0; i < 10; i++) {
            nums[i] = i;
        }
        // 指向还没有加入到栈中的第一个数
        int index = 0;
        while(!StdIn.isEmpty()) {
            int num = StdIn.readInt();
            // 如果在stack中存在直接弹出
            if (inStack(stack, num)) {
                StdOut.print(stack.pop() + " ");
            } else {// 不在栈中将比num小的数添加到栈中
                // 数不在栈中且
                if (num < index) {
                    throw new RuntimeException("num: "+ num +" 小于 index: " + index);
                }
                for (int i = index; i <= num; i++) {
                    stack.push(i);
                }
                index = num + 1;
                StdOut.print(stack.pop() + " ");
            }
        }
    }

    // 遍历栈查看数字是否在栈中
    private static boolean inStack(Stack<Integer> stack, int num) {
        boolean result = false;
        for (Integer item : stack) {
            if (item == num) result = true;
        }

        return result;
    }
}
```

根据此段代码将每个选项一次填入，输入与输出不相同的为错误项。

## 1.3.4 编写一个Stack的用例Parentheses,从标准输入中读取一个文本流并使用栈判定其中的括号是否配对完整。

答：

```
public class Practice134 {
    public static void main(String[] args) {
        Stack<Character> stack = new Stack();
        // 存放左括号
        ArrayList<Character> leftChar = new ArrayList(){{
            add('(');
            add('{');
            add('[');
        }};
        // 存放右括号
        ArrayList<String> rightChar = new ArrayList(){{
            add(')');
            add('}');
            add(']');
        }};
        while (!StdIn.isEmpty()) {
            boolean result = true;
            String sChar = StdIn.readLine();
            char[] chars = sChar.toCharArray();
            for (char aChar : chars) {
                // 左括号放入栈中
                if (leftChar.contains(aChar)) {
                    stack.push(aChar);
                } else if(rightChar.contains(aChar)) {// 每遇到一个右括号就从栈里拿出一个括号
                    if (stack.size() != 0) {
                        // 两个括号index相同则是匹配的
                        if (leftChar.indexOf(Character.valueOf(stack.pop())) != rightChar.indexOf(Character.valueOf(aChar))) {
                            result = false;
                            StdOut.println("false");
                            break;
                        }
                    } else {
                        result = false;
                        StdOut.println("false");
                        break;
                    }
                }
            }
            // 如果循环后栈中还有括号则是错误的
            if (result == true) {
                if (stack.size() != 0) {
                    StdOut.println("false");
                } else {
                    StdOut.println("true");
                }
            }
            // 清空栈
            while(stack.size() != 0) {
                stack.pop();
            }
        }
    }
}
```

## 1.3.5 当N为50时下面这段代码会打印什么？

```
Stack<Integer> stack = new Stack<Integer>();
while(N > 0) {
    stack.push(N % 2);
    N = N / 2;
}
for (int d : stack) StdOut.print(d);
StdOut.println();
```

答： 
50的二进制表示 110010

## 1.3.6 这段代码对队列q进行了什么操作？

```
Stack<String> stack = new Stack();
while (!q.isEmpty())
    stack.push(q.dequeue);
while (!stack.isEmpty)
    q.enqueue(stack.pop())
```

答：
倒序排列

## 1.3.7 为Stack添加一个方法peek()，返回栈中最近添加的元素(而不弹出它)

答： 

```
public Item peek() {
   return first.item;    
}
```

## 1.3.10 编写一个过滤器InfixToPostfix,将算数表达式由中序表达式转为后序表达式。

答：
```

```