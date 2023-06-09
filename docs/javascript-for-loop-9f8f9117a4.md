# JavaScript — For 循环

> 原文：<https://medium.com/nerd-for-tech/javascript-for-loop-9f8f9117a4?source=collection_archive---------13----------------------->

![](img/f6400c0b62a06dc04a55397165ef2132.png)

For 循环允许您为数组的每个元素迭代某些函数。For 循环由四部分组成:初始化、条件、最终表达式和语句。让我们用一个例子来看看每一个。

```
for (let i = 0; i < 9; i++) {
   console.log(i);
   // returns 0, 1, 2, 3, 4, 5, 6, 7, 8
}
```

1.  用括号括起来，变量 I 被声明为零——这是一个初始化，它告诉你希望它从什么值开始。
2.  `i < 9;`:这是您在执行语句之前想要检查的条件。只要条件返回 true，就会执行该语句。
3.  `i++`:每循环一次，I 加 1。
4.  `console.log(i);`:用{}括起来，这是条件为真时要执行的语句。

> ***Q .用下面的说明做一个函数“findSmallestElement”。***
> 
> *1。* `*findSmallestElement*` *函数的* `*arr*` *参数是一个由数字组成的数组。
> 2。从* `*arr*` *返回最小的元素。
> 3。如果* `*arr*` *为空，返回 0。
> 4。例如，如果下面的数组作为参数输入，则应该返回 1。*
> 
> `*[20, 200, 23, 1, 3, 9]*`

**答:我为这个练习想出的解决方案是:**

```
function findSmallestElement(arr) {

if(arr.length === 0){
 return 0;
} else {
 let min = arr[0];
 for(let i = 0; i < arr.length; i++){ 
 if(arr[i] < min){
 min = arr[i];
 }
 }
 return min;
}
}
```

1.  首先，我为数组为空(选项 3)的情况编写了一个 if 语句，因为这是最简单的情况。就效率而言，最好先编写简单的条件，否则执行会花费更多的时间，因为更复杂的语句会先执行。
2.  在 else 语句中，我使用了 for 循环。为了使用 for 循环从数组中获得最小的数字，我们需要比较每个元素。因此，第一个元素`arr[0]`被声明为变量`min`。for 循环需要根据数组的长度进行迭代。所以，条件写成`i < arr.length`。如果数组有 3 个元素(长度= 3 ), for 循环将迭代 3 次，因为`i`从 0(索引)开始并继续，直到它递增到 2。
3.  在 for 循环内部，使用 if 语句编写语句，因为它需要检查当前元素是否小于另一个元素。最初，`min`被声明为`arr[0]`。当执行第一个循环时，min 与等于`arr[0]`的`arr[i]`进行比较。当`arr[i]`的值等于`min`时，`min`保持不变。
4.  如果`arr[i]`小于`min`，则`min`应该重新分配给`arr[i]`。在对数组长度的 for 循环进行迭代后，返回`min`。

我花了很多时间来思考如何从数组中获取最小的元素，并想出了将每个元素与其他元素进行比较以获得答案的想法。此外，在哪个范围内声明`min`也令人困惑。我最初在 for 循环中声明了它，这返回了一个错误。我发现我应该很清楚变量的范围。