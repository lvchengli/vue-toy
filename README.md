# vue-toy
a simple toy vue

## reactive

### reactive system

reactive system use proxy to create a reactive object，use effect to change str by side effect such as call function、modify dom.

### feature

- [x] use proxy to watch data change and exec effect
- [x] use WeakMap - Map - Set to store dependence, store target(data) in WeakMap, store key(foo) in Map, store effectFn(console.log) in Set
- [x] track when proxy find data get exec
- [x] trigger when proxy find data set exec
- [x] clean effect dep before effect exec
- [x] add muti effect track
- [x] add scheduler to custom effect exec (ex: delay and combine effect)
- [x] add computed to lazy compute effectFn, store computed in WeakMap, store value in Map.
- [x] add watch, which can watch obj's modify or a getter function trigger, calc newValue and oldValue, pass to cb.
- [x] add immediate option to watch's third param, can trigger cb immediately.
- [x] add onInvalidate param on watch cb's third param, can tell old watch's cb there is a new trigger so it's invalidate now.

#### note

- muti effect. when outer effect change, will set different deps Set, exec more times inner effect fn call
- 

- 疑问？多重副作用函数时，副作用deps不会被去重。猜测是外层的副作用函数，在重新执行函数时，绑定的监听函数和最初的监听函数不会被去重
- 通过console.log观察执行过程时，可能会触发get行为，造成死循环或者其他问题
- 遇到问题可以通过手绘执行过程来观察依赖追踪的问题。WeakMap树，effectStack堆栈，全局effect和内部的deps，当前执行的callStack
- 后续可以考虑把这几个内容通过可视化界面展示出来，更加直观呈现依赖追踪

### reactive system in 原始值

基于 proxy ，考虑对数组、Map、Set、WeakMap、WeakSet 等类型进行响应式代理.

- [x] add `has` `deleteProperty` `ownKeys` function to reactive `new property` `delete property` `for in` grammar
- [x] 兼容 Object property's modify with prototype, use receiver.raw to judge if current target is the reactive obj of receiver
- [x] add deep reactive and readonly feature
- [ ] 兼容 Array Set Map WeakSet WeakMap (jump)
- [ ] 兼容 BaseType, such as String Number 

#### note

- 疑问？例子里面有 deleteProperty 用来删除被代理对象的属性，但是如果不增加这个逻辑，被代理对象依旧会被删除，没看懂这里的用处。
