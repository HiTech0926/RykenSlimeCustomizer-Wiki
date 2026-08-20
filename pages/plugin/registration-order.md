# 配置注册顺序

在同一个附属中无需在意加载顺序，详见[差异](plugin/comparison.md)

在现在的加载逻辑中，实际加载顺序为：

T1
- 物品组 (及其 lateinit 配置)
- 配方类型 (及其 lateinit 配置)
- 菜单 (及其 lateinit 配置)

T2 （异步同时加载，在 RSC 加载机制下，互相引用可保证有效）
- 盔甲
- 电容
- 食物
- 世界生成
- 发电机
- GEO 自然资源
- 物品
- 强配方机器
- 机器
- 材料生成器
- 生物掉落
- 多方块机器
- 配方机器
- 简单机器
- 太阳能发电机
- 超大多方块机器
- 继承物品
- 模板机器
- 工作台

T3 （异步同时加载，在 RSC 加载机制下，互相引用可保证有效）
- 盔甲 (lateinit 配置)
- 电容 (lateinit 配置)
- 食物 (lateinit 配置)
- 世界生成 (lateinit 配置)
- 发电机 (lateinit 配置)
- GEO 自然资源 (lateinit 配置)
- 物品 (lateinit 配置)
- 强配方机器 (lateinit 配置)
- 机器 (lateinit 配置)
- 材料生成器 (lateinit 配置)
- 生物掉落 (lateinit 配置)
- 多方块机器 (lateinit 配置)
- 配方机器 (lateinit 配置)
- 简单机器 (lateinit 配置)
- 太阳能发电机 (lateinit 配置)
- 超大多方块机器 (lateinit 配置)
- 继承物品 (lateinit 配置)
- 模板机器 (lateinit 配置)
- 工作台 (lateinit 配置)

T4 
- 研究 (及其 lateinit 配置)
