Day-04: 02.实现更新porps
---

- 更新props的原理就是在需要时重新构建一颗新的Dom树，将两颗Dom树相应的节点进行对比，存在并且值改变的属性进行更新，不存在的属性进行删除即可。

- 我们通过WipRoot和CurrentRoot来记录两颗Dom树的根节点，通过在每个节点添加alternate属性来将新生成树的节点与之前的节点进行关联。

- 当执行`update`时，我们需要执行的操作就是：1.生成一颗新的Dom树 2.将旧的Dom的节点与新的Dom树的节点进行关联 3.通过对比原节点与新节点的属性的差别进行更新或删除属性。

- 当更新事件时，需要先删除旧节点上绑定的事件，并进行重新绑定。
