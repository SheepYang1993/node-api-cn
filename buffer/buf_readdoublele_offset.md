<!-- YAML
added: v0.11.15
changes:
  - version: v10.0.0
    pr-url: https://github.com/nodejs/node/pull/18395
    description: Removed `noAssert` and no implicit coercion of the offset
                 to `uint32` anymore.
-->

* `offset` {integer} 开始读取之前要跳过的字节数。必须满足：`0 <= offset <= buf.length - 8`。**默认值:** `0`。
* 返回: {number}

用指定的字节序格式（`readDoubleBE()` 返回大端序，`readDoubleLE()` 返回小端序）从 `buf` 中指定的 `offset` 读取一个 64 位双精度值。

```js
const buf = Buffer.from([1, 2, 3, 4, 5, 6, 7, 8]);

console.log(buf.readDoubleBE(0));
// 打印: 8.20788039913184e-304
console.log(buf.readDoubleLE(0));
// 打印: 5.447603722011605e-270
console.log(buf.readDoubleLE(1));
// 抛出异常 ERR_OUT_OF_RANGE。
```

