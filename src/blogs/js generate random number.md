---
publishAt: "2023-08-03"
title: "JS 如何获得随机数"
---

## 限定最大值

假设我们想从 1 2 3 4 5 6 中随机获得一个数字，就像我们扔骰子时尘埃落定后那个正面朝上的点数，我们可以这样做：

```js
const max = 6;
const x = Math.random();
const random = x * max;
const int = Math.floor(random);

console.log(ran, random, int);
// 0.8941575833797062 5.364945500278237 5
```

让我们逐步分析下这段程序。

首先是：`Math.random()` 方法会返回一个大于等于 0 且小于 1 的数，也就是说 `0 ≤ x < 1` 。

```js
const x = Math.random();
```

然后是：因为 max 等于 6，因此 `0 ≤ random < 6` 。

```js
const random = x * max;
```

最后是：`Math.floor()` 方法会将一个小数的小数位都去掉后返回一个整数，比如 `Math.floor(0.985)` 会返回 0，`Math.floor(3.1415)` 会返回 3 。由于 `0 ≤ random < 6` ，所以 int 可能是 0 1 2 3 4 5 中的任意一个数字。

```js
const int = Math.floor(random);
```

## 限定最小值

这里我们得到的是从 0 到 5 的某个数，如果我们想要得到从 1 到 5 的某个数，可以这样做：

```js
const min = 1;
const max = 6;
const x = Math.random();
const random = x * max + min;
const int = Math.floor(random);

console.log(ran, random, int);
// 0.8406554082399766 6.043932449439859 6
```

我们对 random 的获得做了改动：

```js
const random = x * max + min;
// 0 ≤ x < 1
// 0 ≤ 6x < 6
// 1 ≤ 6x + 1 < 7
```

## 从数组中随机获得一个元素

假设有个数组为 `[3, 4, 1, 5, 9, 2, 6]`，要从中随机选中一个元素，可以这样做：

```js
const list = [3, 4, 1, 5, 9, 2, 6];
const random = Math.floor(Math.random() * list.length);
const item = list[random];

console.log(random);
console.log(item);
// 3
// 5
```

这里的关键在于：我们通过 `list.length` 可以得到数组一共包含了多少个元素，这个例子里是 7 个。因此，`Math.random() * list.length` 的范围会是 `0 ≤ < 7` ，于是最后可以得到 0 1 2 3 4 5 6 中的任意一个数。

```js
const random = Math.floor(Math.random() * list.length);
```

接着通过 `list[random]` 得到元素就可以了。比如 random 如果是 3 的话，item 就是 5 了。
