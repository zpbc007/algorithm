# 第一章 基础

## 栈的实现

栈为后进先出(LIFO)策略的集合类型。

### 定容字符串栈的实现

#### API

|返回值类型|函数名|描述|
|---|---|---|
||FixedCapacityStackOfStrings(int cap)|创建一个容量为cap的空栈|
|void|push(String item)|添加一个字符串|
|String|pop()|删除最近添加的字符串|
|boolean|isEmpty()|栈是否为空|
|int|size()|栈中的字符串数量|
