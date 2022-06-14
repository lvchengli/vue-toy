# vue-toy
a simple toy vue

## reactive

- [x] use proxy to watch data change and exec effect
- [x] track when proxy find data get exec
- [x] trigger when proxy find data set exec
- [x] clean effect dep before effect exec
- [x] add muti effect track

## note

- muti effect. when outer effect change, will set different deps Set, exec more times inner effect fn call
- 

- 多重副作用函数时，猜测是外层的副作用函数，在重新执行函数时，绑定的监听函数和最初的监听函数不会被去重