在 `Flutter` 中，Widget 是整个视图描述的基础，在 `Flutter` 的世界里，包括应用、视图、视图控制器、布局等的概念，都建立在 Widget 之上。 `Flutter` 的核心设计思想便是一切皆是 Widget.

为什么 `StatefulWidget` 与 `StalelessWidget` 的接口设计会有这样的区别：

> Widget 需要依赖数据才能完成构建，而对于 StatefulWidget 来说，其依赖的数据在 Widget 生命周期中可能会频繁地发生变化。由 State 创建 Widget，以数据驱动视图更新，而不是直接操作 UI 更新视觉属性，代码表达可以更精炼，逻辑也可以更清晰。
