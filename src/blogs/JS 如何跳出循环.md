---
publishAt: "2023-08-01"
title: "JS 如何跳出循环"
---

## break with for loop

假设我们有一个数组，里面有 0 到 3 这个四个数字，我们想要打印出这四个数字，可以通过 for 循环来实现。

```js
const list = [0, 1, 2, 3];
for (let i = 0; i < list.length; i++) {
  console.log(list[i]);
}

// 0
// 1
// 2
// 3
```

在这段程序中，我们通过 for 循环，在每次迭代中打印 `list[i]` 的值。

假设现在我们不想打印全部数字了，而是打印到 1 就不再打了，我们可以通过 break 关键字来实现。

```js
const list = [0, 1, 2, 3];
for (let i = 0; i < list.length; i++) {
  if (list[i] === 2) {
    break;
  }
  console.log(list[i]);
}

// 0
// 1
```

break 语句的用法如下：

```js
if (list[i] === 2) {
	break
}

```

这段程序的意思是，当 `list[i]` 的值等于 2 时，break 语句就结束循环。也就是说，**break 语句之后的程序不会再运行，并且之后的迭代也不会再进行**。因此，最后只打印出了 0 和 1，而大于或等于 2 的值则没有打印出来。

## break with for...of loop

break 也可以在 for...of 循环中使用：

```js
const list = [0, 1, 2, 3];
for (const item of list) {
  if (item === 2) {
    break;
  }
  console.log(item);
}

// 0
// 1
```

## break with map method of Array

顺便提一句，数组的 map 方法无法提前跳出循环！
