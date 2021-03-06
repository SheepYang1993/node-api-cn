<!-- YAML
added: v0.5.5
changes:
  - version: v10.0.0
    pr-url: https://github.com/nodejs/node/pull/18395
    description: Removed `noAssert` and no implicit coercion of the offset
                 to `uint32` anymore.
-->

* `offset` {integer} 开始读取之前要跳过的字节数。必须满足：`0 <= offset <= buf.length - 2`。**默认值:** `0`。
* 返回: {integer}

用指定的字节序格式（`readUInt16BE()` 返回大端序，`readUInt16LE()` 返回小端序）从 `buf` 中指定的 `offset` 读取一个无符号的 16 位整数值。

```js
const buf = Buffer.from([0x12, 0x34, 0x56]);

console.log(buf.readUInt16BE(0).toString(16));
// 打印: 1234
console.log(buf.readUInt16LE(0).toString(16));
// 打印: 3412
console.log(buf.readUInt16BE(1).toString(16));
// 打印: 3456
console.log(buf.readUInt16LE(1).toString(16));
// 打印: 5634
console.log(buf.readUInt16LE(2).toString(16));
// 抛出异常 ERR_OUT_OF_RANGE。
```

