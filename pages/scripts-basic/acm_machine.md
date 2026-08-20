# 脚本基础 - ACM 机器
ACM (AdvancedCustomMachine) 包括
- 配方机器
- 强配方机器
- 模板机器
- 工作台
- 材料生成器
- 超大多方块机器

以上机器均有以下方法

## onTick

粘液计算刻的时候触发

### 方法体

```js
function onTick(location) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|location|[Location](https://jd.papermc.io/paper/26.2/org/bukkit/Location.html)|机器的位置|

其中，当方法无返回值时，执行默认逻辑（配方查找等）
方法有返回值时，不执行默认逻辑
其中，超大多方块还会另外执行 `onTick(block, machine, ctx)`，详见[脚本基础 - 超大多方块](scripts-basic/super_multi_block_machines.md)
