---
publishAt: "2023-08-02"
title: "JS 如何让 0 返回 true"
---

我有一个函数，这个函数会遍历一个数组，当找到第一个值为 0 的元素时，就返回该元素的索引。

```js
function fn(list) {
  for (let index = 0; index < list.length; index++) {
    if (list[index] === 0) {
      return index;
    }
  }
}
```

然后，当索引存在时，就会做一些事情。

```js
const list = [1, 0, 2, 3];
const index = fn(list);
if (index) {
  console.log("do something.");
}
```

```js
const list = [1, 2, 3, 4];
const index = fn(list);
if (index) {
  console.log("do something.");
}
```

上面的代码可以正常运行，但如果给函数 `fn` 传入的数组的第一个值就是 0 的话，就会出现问题： 由于 index 的值为 0，而 0 是一个 falsy value，所以 if 语句内部不会运行。

```js
const list = [0, 1, 2, 3];
const index = fn(list);
if (index) {
  console.log("do something.");
}
```

那么要如何解决这个问题呢？

##

```js
if (index !== undefined) { .. }
```

##

```js
if (index >= 0) { ... }
```

这种方式可能存在意外，因为：

```txt
Input | >= 0
------------
"1"   | true
false | true
null  | true
[]    | true
""    | true
```

##

```js
if (typeof index === "number") {
  // DO SOMETHING
}
```
