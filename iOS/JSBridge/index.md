### 什么是高阶组件

强化组件，复用逻辑，提升渲染性能等





强化组件方式

react-mixins

![image-20210929152528924](/Users/lyc/Desktop/F/backup/blog/前端/React/高阶组件/image-20210929152528924.png)

- 1 mixin引入了隐式依赖关系。
- 2 不同mixins之间可能会有先后顺序甚至代码冲突覆盖的问题
- 3 mixin代码会导致滚雪球式的复杂性



extends

![image-20210929152509958](/Users/lyc/Desktop/F/backup/blog/前端/React/高阶组件/image-20210929152509958.png)

HOC

![image-20210929154036556](/Users/lyc/Desktop/F/backup/blog/前端/React/高阶组件/image-20210929154036556.png)



自定义 hooks

![image-20210929154301117](/Users/lyc/Desktop/F/backup/blog/前端/React/高阶组件/image-20210929154301117.png)



什么是高阶组件，它解决了什么问题

高阶组件（HOC）是 React 中用于复用组件逻辑的一种高级技巧。HOC 自身不是 React API 的一部分，它是一种基于 React 的组合特性而形成的设计模式。

**复用逻辑**

**强化props**

混入 props

最常用的功能，承接上层的`props`,在混入自己的`props`，来强化组件

抽离state 控制更新



**赋能组件**

**控制渲染**





有几种高阶组件，它们优缺点是什么？

装饰器模式和函数包裹模式
属性代理：组件包裹一层代理组件
优点
可以和业务组件低耦合，零耦合
可以嵌套使用
完全隔离业务组件的渲染

缺点


反向继承




如何写一个优秀高阶组件？





`hoc`怎么处理静态属性，跨层级`ref`等问题？





高阶组件怎么控制渲染，隔离渲染？





高阶组件怎么监控原始组件的状态？









[一文吃透React高阶组件(HOC)](https://juejin.cn/post/6940422320427106335)