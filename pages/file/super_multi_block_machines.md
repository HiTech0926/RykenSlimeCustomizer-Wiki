# 超大多方块机器(super_multi_block_machines.yml)

<mark style="color:red;">**注意：**</mark>该页面由 AI 生成，经人工部分检查，若发现错误请在 issues 中提出。

<mark style="color:red;">**注意：**</mark>带\*为必填

> 相较原版多方块，该多方块支持更大的立体结构，脚本检测等功能。
> 注：多方块结构不能重叠，即一个方块只能由一个超大多方块结构占用，不能同时用于搭建多个超大多方块。

**示例：**

```yaml
RSC_EXAMPLE_SUPER_MULTIBLOCK_MACHINE:
  item_group: rsc_example_normal_group
  item:
    material: DIAMOND_BLOCK
    name: "&6超大多方块机器"
    lore:
      - "&7一个强大的多方块机器"
      - "&7需要特定结构才能激活"
  recipe_type: ENHANCED_CRAFTING_TABLE
  recipe:
    1:
      material_type: mc
      material: IRON_BLOCK

  capacity: 10000
  energyPerCraft: 500
  speed: 1

  hideAllRecipes: false

  script: super_machine_script

  input: [19, 20]
  output: [24, 25]

  displayProjectiles: true
  checkFormed: true
  openMenuWhenClickedParts: true
  noMenuWhenNotFormed: true
  allowSwitchDisplayLayer: true
  defaultNotice: true
  ticker_type: recipe

  structure:
    -
      - "__ b1 __"
      - "a1 b1 c1"
      - "__ b1 __"
    -
      - "c1 b1 a1"
      - "c1 o  a1"
      - "c1 b1 a1"
    -
      - "b1 a1 c1"
      - "b1 a1 c1"
      - "b1 a1 c1"

  mapping:
    o:
      material_type: slimefun
      material: RSC_EXAMPLE_SUPER_MULTIBLOCK_MACHINE # 引用自身
      core: true

    a1:
      material_type: mc
      material: minecraft:furnace[lit=true]

    b1:
      material_type: mc
      material: REDSTONE_BLOCK

    c1:
      material_type: custom
      material: minecraft:stone

  recipes:
    example_recipe:
      seconds: 5
      input:
        1:
          material_type: mc
          material: IRON_BLOCK
      output:
        1:
          material_type: mc
          material: IRON_BLOCK
          amount: 1
          chance: 100
        2:
          material_type: mc
          material: REDSTONE_DUST
          amount: 2
          chance: 50
```

| 内容 | 描述 | 有效输入 |
| --- | ----------- | ----------------- |
| \*`RSC_EXAMPLE_SUPER_MULTIBLOCK_MACHINE` | 超级多方块机器的ID。<br>该ID不能与任何其他物品的ID相同! | **仅支持大写字母、数字、下划线!** |
| \*item_group | 物品所在[物品组（分类）](file/groups.md)的ID。 | |
| \*item.# | [通用物品格式](format/universal-item-format.md)| 可选择性添加`modelId`、`lore`、`glow`等。 |
| recipe_type | 见[配方类型](file/recipe_type.md)。 | |
| recipe | 设置机器的合成配方。详见[**配方**](../format/recipe.md) | |
| recipeOutput | 设置合成配方的输出物品 | [通用物品格式](format/universal-item-format.md) |
| capacity | 设置机器可储存的能量，最大为 2147483647。设置为 0 时，机器为不耗电机器！ | |
| energyPerCraft | 机器每粘液刻消耗的电量。 | |
| speed | 机器运行速度，最大为 2147483647，数值越大，机器运行的越快。<br>即你不需要更改每个工作配方的seconds。更改此项即可 *升级机器* |
| hideAllRecipes | 隐藏所有输入输出配方。 | |
| script | 物品引用的脚本，设置物品对应的脚本文件，双引号内填脚本对应的文件名称。 | |
| \*input | 物品输入的对应槽位。<br>**请不要在菜单中为这些槽位设置物品！** | |
| \*output | 物品输出的对应槽位。<br>**请不要在菜单中为这些槽位设置物品！** | |
| displayProjectiles | 是否显示方块投影。默认 `true` | |
| checkFormed | 机器tick是否需要检测是否搭建完成。默认 `true` | |
| openMenuWhenClickedParts | 点击机器部件时是否同样打开核心菜单。默认 `true` | |
| noMenuWhenNotFormed | 结构未形成时是否禁止打开菜单。默认 `true` | |
| allowSwitchDisplayLayer | 是否允许切换方块投影显示层。默认 `true` | |
| defaultNotice | 是否显示默认提示信息。默认 `true` | |
| baseDirection | 指定放置初对多方块投影的旋转方向。默认 north | {north, east, south, west} |
| ticker_type | 指定使用的配方读取器，默认 `recipe` | recipe (配方机器) / linked_recipe (强配方机器) / workbench (工作台) / template_recipe (模板机器) / material_generator (材料生成器) |
| \*structure | 多方块机器的3D结构布局，每一层为一个列表，每一行用字符串表示，每个字符代表一个方块位置。其中，若干个 "_" 组成的字符串表示空位 | |
| \*mapping | 结构中字符到方块的映射，定义每个字符代表的方块类型。 | |
| mapping.#.material_type | 方块材质类型，支持`mc`(原版物品)、`slimefun`(粘液物品)、`custom`(脚本检测)。 | |
| mapping.#.material | 方块显示材质/投影显示数据。 | |
| mapping.#.core | 是否为核心方块，标记为`true`的方块是机器的核心，放置该方块后检测结构。 | |
| recipes.#.seconds | 合成所需时间，最大为 2147483647。 **实际合成时间(单位：粘液刻)：(秒数×2) / 机器运行速度** | |
| recipes.#.input | 合成所需的输入物品。 | |
| recipes.#.output | 合成输出的物品。 | |
| recipes.#.output.chance | 物品产出的概率。有效范围 1~100 | |
| recipes.#.chooseOne | 当随机出多个产物的时候从中选一个作为最终产物。 | |
| recipes.#.forDisplay | 仅供展示的配方，可以用于在配方中写关于机器的描述/使用方法等。类似于乱码科技。 | |
| recipes.#.hide | 隐藏此输入输出配方。 | |
| recipes.#.noConsume | 当设置为true时，所有的输入物品在输出产物时将不再消耗。注意：amount不能为0 | |
| recipes.#.input.noConsume | 当设置为true时，仅单个物品不消耗，其它输入物品正常消耗。 | |
| script | 机器引用的脚本，设置机器对应的脚本文件，双引号内填脚本对应的文件名称。 详见 [脚本基础 - ACM机器](scripts-basic/acm_machine.md) |
| recipes_import_from | 从指定的机器中导入所有配方 | 指定的机器的粘液 ID (限当前 yml) |

## 注意事项

### 结构布局说明

`structure`字段用于定义多方块机器的3D结构：

1. **分层结构**：每一个外层列表项代表一层，从上到下排列
2. **每行表示**：每层中的每个字符串代表一行
3. **字符映射**：每行中以空格分隔的每个字符串对应`mapping`中定义的方块类型
4. **空格分隔**：每个方块表示之间用空格分隔，如`"a1 b1 c1"`表示一行有三个方块，分别对应`a1`、`b1`、`c1`
5. **空位置**：使用若干个`_`表示空位置，不放置任何方块

### 映射配置说明

`mapping`字段定义结构中字符到方块的对应关系：

1. **核心方块**：必须有且仅有一个方块标记为`core: true`，这个方块是机器的核心，玩家放置该方块后会自动检测周围结构是否匹配
2. **材质类型**：
   - `mc`：使用原版方块
   - `slimefun`：使用粘液科技方块
   - `custom`：使用自定义脚本检测
3. **投影显示数据**：可以使用方块数据 (如`minecraft:furnace[lit=true]`) 或 方块ID (`iron_block`), 适用于`mc`和`custom`材质类型

### 工作原理

1. 玩家首先按照`recipe`配置合成超级多方块机器的核心物品
2. 玩家将核心物品放置在世界中
3. 系统自动检测核心物品周围的方块结构是否与`structure`配置匹配
4. 如果结构匹配，机器激活，显示方块投影效果（如果`displayProjectiles: true`）
5. 玩家可以在机器界面中放入输入物品，机器按照`recipes`配置进行合成

## 脚本

详见[脚本基础-超大多方块](scripts-basic/super_multiblock_machines.md)