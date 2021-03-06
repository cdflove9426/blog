# 一些最佳实践

### PureComponent
React15.3 中新加了一个类`PureComponent`，和 Component 基本一样，只不过会在 render 之前帮组件自动执行一次 `shallowEqual（浅比较）`，来决定是否更新组件，浅比较类似于浅复制，只会比较第一层。使用 PureComponent 相当于省去了写 `shouldComponentUpdate` 函数，当组件更新时,组件的 props 和 state 有如下特点：

+ 引用和第一层数据都没发生改变， render 方法就不会触发，这是我们需要达到的效果。
+ 虽然第一层数据没变，但引用变了，就会造成虚拟 DOM 计算的浪费。
+ 第一层数据改变，但引用没变，会造成不渲染，所以需要很小心的操作数据。

### ImmutableJS
ImmutableJS 最大的两个特性就是：`immutable data structures（持久性数据结构）`与 `structural sharing（结构共享）`，持久性数据结构保证每一个对象都是不可变的，任何添加、修改、删除等操作都会生成一个新的对象。而结构共享是指没有改变的数据共用一个引用，这样既减少了深拷贝的性能消耗，也减少了内存。

应用：
假设现在有一个列表 List,一共5条数据，如果我们

### Suspense
https://www.infoq.cn/article/sVaeA7Y3pei2sYy_lK9e