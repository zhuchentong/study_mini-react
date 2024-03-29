Day-06: 03.提前检测 减少不必要的更新
---

- 在如果action返回值没有变化的情况下，其实我们并没有必要重新生成新的Dom节点，但是现在的逻辑是每次执行setState时都会重新生成新的Dom节点，所以为了减少不必要的更新，我们可以判断action的返回值是否鱼原始值一致，来判断是否应该去更新当前节点。

- 在本章的代码中，我们使用了一个变量`eargeState`来获取action返回值，如果action返回值和`eargeState`一致，则不更新当前节点。

- 但是也存在如下问题，在执行多次`setState`时，本次都是与原始值进行比较，但是实际我们应该与之比较的是上一次`setState`返回的结果，所以我们需要每次从`queue`中获取最后的结果来进行计算而不是直接使用`stateHook.state`来比较。