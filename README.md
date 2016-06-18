# KSFramework

[**K**Engine](https://github.com/mr-kelly/KEngine) + [**S**Lua](https://github.com/mr-kelly/KEngine)+ **Framework** = KSFramework

KSFramework是一个整合KEngine、SLua和一些开发组件组成的全功能Unity 5开发框架，适合有一定规模的团队使用。

热重载是KSFramework的开发重点——在不重启游戏的前提下，重载代码、配置表可立刻看到修改效果，最大限度的提升开发、调试的速度，并且在运营阶段方便的进行产品热更新。

# 教程

- [KSFramework: Unity3D框架快速入门](http://www.jianshu.com/p/ccb491ed4260)
- [KEngine策划指南: 配置表格的编辑与编译](http://www.jianshu.com/p/ead1a148b504)
- [KEngine: 资源的打包、加载、调试监控](http://www.jianshu.com/p/ce3b5d0bdf8c)
- [KSFramework常见问题：Lua脚本热重载，内存状态数据会不会丢失？](http://www.jianshu.com/p/eebd5cfce87f)
- [KSFramework常见问题：Excel如何进行SVN协作、差异比较？](http://www.jianshu.com/p/2ea5468e9d5b)

# 结构组成

![KSFramework由KEngine和SLua结合组成](Docs/Structure.png)

[View on ProcessOn](https://www.processon.com/view/link/57634e3ce4b07fa2f3bb0ee8)

# 功能特性

## 资源模块

- Unity 5中一键打包Asset Bundle
- AssetBundle加载器，加载时自动处理依赖关系
- 资源路径约定，含热更新资源机制
- 手动的、引用计数的资源释放策略
- ~~资源运行时重载（减引用计数）~~

## UI模块

- 约定优于配置式的UI框架
- 快速导出当前编辑的UI
- 支持热重载，运行时修改UI脚本无需重启

## 配置表模块

- 自动编译Excel，支持在表中添加注释
- Excel表头，可设置数据类型（如int, array的声明）
- 自动生成配置表读取代码
- 支持惰式加载，无初始化的时间消耗
- 支持热重载，运行时修改配置表立刻生效

## 脚本模块

- 路径约定，通过import函数进行加载
- 缓存机制配合import函数，可实现所有脚本的热重载

## 多语言模块

- 基于配置表模块
- 约定好多语言字符串的机制
- ~~多语言字符串收集器~~

## Unity编辑器强化

- 编辑代码后，返回正在运行的游戏，强制停到正在运行的游戏，避免崩溃的出现
- 封装Unity编辑器的各种事件，如编译前、播放前、暂停时等

# 工程建议

- 建议创建两个Unity工程：code和product，一个用于代码编辑，一个用于美术编辑并导出AssetBundle。

# 键盘快捷键

- Ctrl+Alt+E: 在编辑UI场景时，导出UI成AssetBundle
- Ctrl+Alt+R: 在运行时，热重载所有LuaUIController
- Ctrl+Alt+Shift+R: 在运行时，热重载所有LuaUIController，并且把所有打开状态UI关闭后重新开启
- Ctrl+Alt+I: 在编辑器，打开Game.unity主运行场景
- Ctrl+Alt+O: 在编辑器，打开Ctrl+Alt+I前的一个场景


## KEngine和KSFramework

### 定位不一样

KEngine:为了减低Unity 4.x中AssetBundle的加载、打包复杂度；

KSFramework:一站式的开发框架，可以开箱即用，整合KEngine和SLua。只支持Unity 5。

### 提供的模块不同

KEngine: 提供基础的资源加载（ResourceModule）功能，并以之为基础，增加配置表（SettingModule）、UI模块（UIModule）这两个核心模块；另外还有针对Unity 4.x的资源依赖打包模块。

KSFramework：基于KEngine的资源、UI、配置表模块，实现更直接的、面向具体项目的常用功能模块，并搭配SLua。
