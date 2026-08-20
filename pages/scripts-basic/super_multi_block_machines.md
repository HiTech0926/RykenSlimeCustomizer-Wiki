# 脚本基础 - 超大多方块

<mark style="color:red;">**注意：**</mark>该页面由 AI 生成，经人工部分检查，若发现错误请在 issues 中提出。

## 概述

超大多方块机器脚本支持以下函数：

* `onTick(block, machine, ctx)` - 每粘液刻触发
* `onFormed(partLocation, machine)` - 多方块结构形成时触发
* `onUnformed(partLocation, machine)` - 多方块结构破坏时触发
* `onDestroy(machine)` - 多方块结构破坏或核心破坏时触发
* `onInteract(event, machine)` - 玩家交互时触发
* `isOfPart(location, multiblock)` - 检查位置是否为多方块的一部分
* `cannotStartSuperMultiBlock(location, machine)` - 多方块无法开始搭建时触发
* `onClickedPartBlock(event, machine)` - 点击部件方块时触发
* `onClickedPartBlockNotFormed(event, machine)` - 多方块结构未形成时，点击部件方块触发
* `autoSwitchedDisplayLayer(layer, machine)` - 自动切换显示层时触发
* `switchDisplayLayer(layerIndex, machine)` - 手动切换显示层时触发
* `formedLayer(layer, machine)` - 一层搭建完成时触发

其中：
* `ctx` = TickContext
* `event` = PlayerInteractEvent
* `machine` = [CustomSuperMultiBlockMachine](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/customs/CustomSuperMultiBlockMachine.java)
* `multiblock` = [SuperMultiBlock](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/super_multiblock/SuperMultiBlock.java)

---

## onTick

当粘液计算刻时触发，用于每刻执行逻辑。

### 方法体

```js
function onTick(block, machine, ctx) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|block|[Block](https://jd.papermc.io/paper/26.2/org/bukkit/block/Block.html)|多方块机器的核心方块|
|machine|[CustomSuperMultiBlockMachine](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/customs/CustomSuperMultiBlockMachine.java)|超大多方块机器的实例|
|ctx|[TickContext](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/objects/customs/machine/TickContext)|脚本上下文，用于控制默认调用|

## onFormed

当超大多方块结构搭建完成时触发。

### 方法体

```js
function onFormed(partLocation, machine) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|partLocation|[Location](https://jd.papermc.io/paper/26.2/org/bukkit/Location.html)|部件位置|
|machine|[CustomSuperMultiBlockMachine](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/customs/CustomSuperMultiBlockMachine.java)|超大多方块机器的实例|

## onUnformed

当超大多方块结构被破坏时触发

### 方法体

```js
function onUnformed(partLocation, machine) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|partLocation|[Location](https://jd.papermc.io/paper/26.2/org/bukkit/Location.html)|部件位置|
|machine|[CustomSuperMultiBlockMachine](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/customs/CustomSuperMultiBlockMachine.java)|超大多方块机器的实例|

## onDestroy

当超大多方块结构破坏或核心破坏时触发

### 方法体

```js
function onDestroy(machine) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|machine|[CustomSuperMultiBlockMachine](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/customs/CustomSuperMultiBlockMachine.java)|超大多方块机器的实例|

## onInteract

当玩家与超大多方块机器交互时触发。（包括所有组成超大多方块机器的方块）

### 方法体

```js
function onInteract(event, machine) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|event|[PlayerInteractEvent](https://jd.papermc.io/paper/26.2/org/bukkit/event/player/PlayerInteractEvent.html)|玩家交互事件|
|machine|[CustomSuperMultiBlockMachine](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/customs/CustomSuperMultiBlockMachine.java)|超大多方块机器的实例|

## isOfPart

检查指定位置是否为多方块机器的一部分。

### 方法体

```js
function isOfPart(location, multiblock) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|location|[Location](https://jd.papermc.io/paper/26.2/org/bukkit/Location.html)|要检查的位置|
|multiblock|[SuperMultiBlock](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/super_multiblock/SuperMultiBlock.java)|超大多方块实例|

### 返回值

|类型|描述|
|--|---|
|boolean|如果指定位置是多方块机器的一部分，返回true；否则返回false|

## cannotStartSuperMultiBlock

当超大多方块无法开始搭建时被调用。

### 方法体

```js
function cannotStartSuperMultiBlock(location, machine) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|location|[Location](https://jd.papermc.io/paper/26.2/org/bukkit/Location.html)|多方块机器核心的位置|
|machine|[CustomSuperMultiBlockMachine](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/customs/CustomSuperMultiBlockMachine.java)|超大多方块机器的实例|

## onClickedPartBlock

当玩家点击部件方块时触发。

### 方法体

```js
function onClickedPartBlock(event, machine) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|event|[PlayerInteractEvent](https://jd.papermc.io/paper/26.2/org/bukkit/event/player/PlayerInteractEvent.html)|玩家交互事件|
|machine|[CustomSuperMultiBlockMachine](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/customs/CustomSuperMultiBlockMachine.java)|超大多方块机器的实例|

## onClickedPartBlockNotFormed

当玩家点击未形成的部件方块，且多方块结构未搭建完成，且 `noMenuWhenNotFormed = true` 时触发。

### 方法体

```js
function onClickedPartBlockNotFormed(event, machine) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|event|[PlayerInteractEvent](https://jd.papermc.io/paper/26.2/org/bukkit/event/player/PlayerInteractEvent.html)|玩家交互事件|
|machine|[CustomSuperMultiBlockMachine](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/customs/CustomSuperMultiBlockMachine.java)|超大多方块机器的实例|

## autoSwitchedDisplayLayer

当 RSC 自动调用切换显示层时触发。

### 方法体

```js
function autoSwitchedDisplayLayer(layer, machine) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|layer|int|指定的层的y|
|machine|[CustomSuperMultiBlockMachine](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/customs/CustomSuperMultiBlockMachine.java)|超大多方块机器的实例|

## switchDisplayLayer

当玩家手动切换显示层时触发。

### 方法体

```js
function switchDisplayLayer(layerIndex, machine) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|layerIndex|int|切换的层的索引，其中 `-999` 表示显示全部投影|
|machine|[CustomSuperMultiBlockMachine](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/customs/CustomSuperMultiBlockMachine.java)|超大多方块机器的实例|

## formedLayer

当某一层完全搭建完成时触发。

### 方法体

```js
function formedLayer(layer, machine) {

}
```

### 入参

|字段|类型|描述|
|--|---|--|
|layer|int|搭建完成的层的y值|
|machine|[CustomSuperMultiBlockMachine](https://github.com/balugaq/RykenSlimeCustomizer/blob/main/src/main/java/org/lins/mmmjjkx/rykenslimefuncustomizer/customs/CustomSuperMultiBlockMachine.java)|超大多方块机器的实例|