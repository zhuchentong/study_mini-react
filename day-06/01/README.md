Day-06: 01.搞定useState
---

- 之前章节使用update来更新数据，本章节来实现useState，useState主要包括两部分，数据state以及setState，需要做的就是使用state存储数据然后在调用setState来更新数据。

- 更新数据的方式时设置开始更新的Fiber节点后，设置为nextWorkUnit即可，需要注意的是，每次重新生成Dom树都会重新执行useState函数，但第二次执行时应该获取上一次计算的数据而不是初始数据，所以在fiber.stateHooks来存储上一次的数据

- 因为一个函数组件上可能有多个useState，所以需要使用fiber.stateHooks来存储数据，同时需要使用fiber.stateHookIndex来记录当前是第几个useState，当执行setState时，需要获取当前useState的索引，然后获取上一次的数据，同时更新数据。
