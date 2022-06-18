# vue-toy
a simple toy vue

## reactive

- [x] use proxy to watch data change and exec effect
- [x] use WeakMap - Map - Set to store dependence, store target(data) in WeakMap, store key(foo) in Map, store effectFn(console.log) in Set
- [x] track when proxy find data get exec
- [x] trigger when proxy find data set exec
- [x] clean effect dep before effect exec
- [x] add muti effect track
- [x] add scheduler to custom effect exec (ex: delay and combine effect)
- [x] add computed to lazy compute effectFn, store computed in WeakMap, store value in Map.
- [x] add watch, which can watch obj's modify or a getter function trigger, calc newValue and oldValue, pass to cb.

## note

- muti effect. when outer effect change, will set different deps Set, exec more times inner effect fn call
- 

- 多重副作用函数时，猜测是外层的副作用函数，在重新执行函数时，绑定的监听函数和最初的监听函数不会被去重
- 通过console.log观察执行过程时，可能会触发get行为，造成死循环或者其他问题
- 遇到问题可以通过手绘执行过程来观察依赖追踪的问题。WeakMap树，effectStack堆栈，全局effect和内部的deps，当前执行的callStack
- 后续可以考虑把这几个内容通过可视化界面展示出来，更加直观呈现依赖追踪