Array.map() `map`方法会得到一个==新数组==，新数组中的==每个元素==是原数组元素经过回调函数==执行==并==返回==的结果

Array.filter()  `filter()` 方法创建一个==新数组==, 其包含通过所提供函数实现的测试的所有元素。 



两者的区别就是：map回调函数返回的是执行函数体后的结果，而filter回调函数返回Boolean，只有当返回值为true时，对应原数组元素会被添加到新数组。

