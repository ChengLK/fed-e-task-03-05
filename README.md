### 1、Vue 3.0 性能提升主要是通过哪几方面体现的？

1. 通过摇树优化核心库体积；

2. 响应式系统升级，使用Proxy重写响应式系统；

3. 重写虚拟dom与diff算法，标记和提升静态节点，即可跳过静态节点，只处理动态节点，缓存事件处理函数， 提高diff性能；



### 2、Vue 3.0 所采用的 Composition Api 与 Vue 2.x使用的Options Api 有什么区别？

Composition Api，较于Options Api，可使功能代码模块化，整体化，便于复用，而不再零散放置，方便统一管理；可解决mixins命名冲突；



### 3、Proxy 相对于 Object.defineProperty 有哪些优点？

1. Proxy可以直接监听对象，而非属性，即可以监听动态添加的属性，监听属性的删除；
2. Proxy 返回的是一个新对象,我们可以只操作新的对象达到目的，而 Object.defineProperty 只能遍历对象属性直接修改；
3. Proxy可以监听数组的变化，即通过索引和length导致的数组变化；
4. Proxy 的第二个参数可以有 13 种拦截方法，比 Object.defineProperty 要更加丰富；
5. Proxy 也是**不支持嵌套的**，这点和 Object.defineProperty 是一样的。因此也需要通过逐层遍历来解决。Proxy 的写法是在 get 里面递归调用 Proxy 并返回；



### 4、Vue 3.0 在编译方面有哪些优化？

1. PatchFlag，在动态标签末尾加上相应的标记，只能带patchFlag 的节点才被认为是动态的元素，会被追踪属性的修改，能快速的找到动态节点，而不用逐个逐层遍历；
2. 静态节点提升-hoistStatic，当使用hoistStatic时，所有 静态的节点都被提升到render方法之外。这意味着，只会在应用启动的时候被创建一次，而后随着每次的渲染被不停的复用；
3. 事件监听缓存-cacheHandler，避免每次触发都要重新生成全新的function去更新之前的函数；
4. 通过摇树优化核心库体积，减少不必要的代码量；



### 5、Vue.js 3.0 响应式系统的实现原理？

Vue.js 3.0响应式系统的实现原理，是通过Proxy监听对象，实现响应式系统，其核心函数；

1. reactive、ref、toRefs、computed
2. effect
3. track
4. trigger