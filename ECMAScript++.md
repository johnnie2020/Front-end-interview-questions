### 1. 根据下面 _ES6_ 构造函数的书写方式，要求写出 _ES5_ 的

```javascript
class Example { 
  constructor(name) { 
    this.name = name;
  }
  init() { 
    const fun = () => { console.log(this.name) }
    fun(); 
  } 
}
const e = new Example('Hello');
e.init();
```
> 参考答案：

```javascript
function Example(name) {
   'use strict';
   if (!new.target) {
        throw new TypeError('Class constructor cannot be invoked without new');
   }
   this.name = name;
}

Object.defineProperty(Example.prototype, 'init', {
   enumerable: false,
   value: function () {
        'use strict';
        if (new.target) {
            throw new TypeError('init is not a constructor');
        }
        var fun = function () {
            console.log(this.name);
        }
        fun.call(this);
   }
})
```
> 此题的关键在于是否清楚 _ES6_ 的 _class_ 和普通构造函数的区别，记住它们有以下区别，就不会有遗漏： 
> 1.  _ES6_ 中的 _class_ 必须通过 _new_ 来调用，不能当做普通函数调用，否则报错
因此，在答案中，加入了 _new.target_ 来判断调用方式 
> 1.  _ES6_ 的 _class_ 中的所有代码均处于严格模式之下 
> 
因此，在答案中，无论是构造函数本身，还是原型方法，都使用了严格模式
> 3.  _ES6_ 中的原型方法是不可被枚举的
因此，在答案中，定义原型方法使用了属性描述符，让其不可枚举 
> 3.  原型上的方法不允许通过 _new_ 来调用
因此，在答案中，原型方法中加入了 _new.target_ 来判断调用方式 

### 2. 数组去重有哪些方法？
```javascript
// 数字或字符串数组去重，效率高
function unique(arr) {
   var result = {}; // 利用对象属性名的唯一性来保证不重复
   for (var i = 0; i < arr.length; i++) {
        if (!result[arr[i]]) {
            result[arr[i]] = true;
        }
   }
   return Object.keys(result); // 获取对象所有属性名的数组
}

// 任意数组去重，适配范围光，效率低
function unique(arr) {
   var result = []; // 结果数组
   for (var i = 0; i < arr.length; i++) {
        if (!result.includes(arr[i])) {
            result.push(arr[i]);xi
        }
   }
   return result;
}

// 利用ES6的Set去重，适配范围广，效率一般，书写简单
function unique(arr) {
   return [...new Set(arr)]
}
```

### 3. 描述下列代码的执行结果

```javascript
console.log(typeof b);//ReferenceError: Cannot access 'b' before initialization
let b = 0;
```

### 4. 描述下列代码的执行结果

```javascript
class Foo {
    constructor(arr) { 
        this.arr = arr; 
    }
    bar(n) {
        return this.arr.slice(0, n);
    }
}
var f = new Foo([0, 1, 2, 3]);
console.log(f.bar(1));
console.log(f.bar(2).splice(1, 1));//虽然splice改变原数组，但是这里只是打印
console.log(f.arr);
```


### 5. 描述下列代码的执行结果

```javascript
function f(count) {
    console.log(`foo${count}`);
    setTimeout(() => {
        console.log(`bar${count}`);
    });
}
f(1);
f(2);
setTimeout(() => {
    f(3);
});
```
>  这个完全是考察的异步的知识。调用 _f(1)_ 的时候，会执行同步代码，打印出 _foo1_，然后 _03_ 行的 _setTimeout_ 被放入到异步执行队列，接下来调用 _f(2)_ 的时候，打印出 _foo2_，后面 _03_ 行的 _setTimeout_ 又被放入到异步执行队列。然后执行 _07_ 行的语句，被放入到异步执行队列。至此，所有同步代码就都执行完毕了。
>  
> 接下来开始执行异步代码，那么大家时间没写，就都是相同的，所以谁先被放入到异步队列，谁就先执行，所以先打印出 _bar1_、然后是 _bar2_，接下来执行之前 _07_ 行放入到异步队列里面的 _setTimeout_，先执行 _f_ 函数里面的同步代码，打印出 _foo3_，然后是最后一个异步，打印出 _bar3_


### 6. 描述下列代码的执行结果

```javascript
var a = 2;
var b = 5;
console.log(a === 2 || 1 && b === 3 || 4);
```
> 在 || 里面，只要有一个为真，后面的**直接短路**，都不用去计算。所以 _a === 2_ 得到 _true_ 之后直接短路了，返回 _true_。

### 7. 描述下列代码的执行结果

```javascript
export class ButtonWrapper {
    constructor(domBtnEl, hash) {
        this.domBtnEl = domBtnEl;
        this.hash = hash;
        this.bindEvent();
    }
    bindEvent() {
        this.domBtnEl.addEventListener('click', this.clickEvent, false);
    }
    detachEvent() {
        this.domBtnEl.removeEventListener('click', this.clickEvent);
    }
    clickEvent() {
        console.log(`The hash of the button is: ${this.hash}`);
    }
}
```

> 上面的代码导出了一个 _ButtonWrapper_ 类，该类在被实例化的时候，实例化对象上面有两个属性，分别是 _domBtnEl_ 和 _hash_，_domBtnEl_ 是一个 _DOM_ 节点，之后为这个 _domBtnEl_ 绑定了点击事件，点击后打印出 _The hash of the button is: hash_ 那句话。_detachEvent_ 是移除点击事件，当调用实例化对象的 _detachEvent_ 方法时，点击事件就会被移除。

### 10. _new_ 操作符都做了哪些事？
> _new_ 运算符创建一个用户定义的对象类型的实例或具有构造函数的内置对象的实例。
> _new_ 关键字会进行如下的操作：
步骤 _1_：创建一个空的简单 _JavaScript_ 对象，即 { } ;
步骤 _2_：链接该对象到另一个对象（即设置该对象的原型对象）；
步骤 _3_：将步骤 _1_ 新创建的对象作为 _this_ 的上下文；
步骤 _4_：如果该函数没有返回对象，则返回 _this_。


### 11. _call、apply、bind_ 的区别 ？

> - _fn.call(obj, arg1, arg2, ...)_ 调用一个函数, 具有一个指定的 _this_ 值和分别地提供的参数(参数的列表)。
> - _fn.apply(obj, [argsArray])_ 调用一个函数，具有一个指定的 _this_ 值，以及作为一个数组（或类数组对象）提供的参数。
> 
_bind_ 和 _call/apply_ 有一个很重要的区别，一个函数被 _call/apply_ 的时候，会直接调用，但是 _bind_ 会创建一个新函数。当这个新函数被调用时，_bind( )_ 的第一个参数将作为它运行时的 _this_，之后的一序列参数将会在传递的实参前传入作为它的参数。

### 13. 你了解 _node_ 中的事件循环机制吗？_node11_ 版本以后有什么改变
> _Node.js_ 在主线程里维护了一个**事件队列，**当接到请求后，就将该请求作为一个事件放入这个队列中，然后继续接收其他请求。当主线程空闲时（没有请求接入时），就开始循环事件队列，检查队列中是否有要处理的事件，这时要分两种情况：如果是非 _I/O_ 任务，就亲自处理，并通过回调函数返回到上层调用；如果是 _I/O_ 任务，就从**线程池**中拿出一个线程来处理这个事件，并指定回调函数，然后继续循环队列中的其他事件。
>  
> 当线程中的 _I/O_ 任务完成以后，就执行指定的回调函数，并把这个完成的事件放到事件队列的尾部，等待事件循环，当主线程再次循环到该事件时，就直接处理并返回给上层调用。 这个过程就叫 **事件循环** (_Event Loop_)。
>  
> 无论是 _Linux_ 平台还是 _Windows_ 平台，_Node.js_ 内部都是通过**线程池**来完成异步 _I/O_ 操作的，而 _LIBUV_ 针对不同平台的差异性实现了统一调用。因此，**_Node.js_ 的单线程仅仅是指 _JavaScript_ 运行在单线程中，而并非 _Node.js_ 是单线程。**
>  
> _Node.JS_ 的事件循环分为 _6_ 个阶段：
>  
> - _timers_ 阶段：这个阶段执行 _timer_（ _setTimeout、setInterval_ ）的回调
> - _I/O callbacks_ 阶段：处理一些上一轮循环中的少数未执行的 _I/O_ 回调
> - _idle、prepare_ 阶段：仅 _Node.js_ 内部使用
> - _poll_ 阶段：获取新的 _I/O_ 事件, 适当的条件下 _Node.js_ 将阻塞在这里
> - _check_ 阶段：执行 _setImmediate( )_ 的回调
> - _close callbacks_ 阶段：执行 _socket_ 的 _close_ 事件回调
> 

> 事件循环的执行顺序为：
>  
> 外部输入数据 –-> 轮询阶段（ _poll_ ）-–> 检查阶段（ _check_ ）-–> 关闭事件回调阶段（ _close callback_ ）–-> 定时器检测阶段（ _timer_ ）–-> _I/O_ 事件回调阶段（ _I/O callbacks_ ）-–>闲置阶段（ _idle、prepare_ ）–->轮询阶段（按照该顺序反复运行）...
>  
> 浏览器和 _Node.js_ 环境下，微任务任务队列的执行时机不同
>  
> - _Node.js_ 端，微任务在事件循环的各个阶段之间执行
> - 浏览器端，微任务在事件循环的宏任务执行完之后执行
> 

> _Node.js v11.0.0_ 版本于 _2018_ 年 _10_ 月，主要有以下变化：
>  
> 1. _V8_ 引擎更新至版本 _7.0_
> 1. _http、https_ 和 _tls_ 模块默认使用 _WHESWG URL_ 解析器。
> 1. 隐藏子进程的控制台窗口默认改为了 _true_。
> 1. _FreeBSD 10_不再支持。
> 1. 增加了多线程 _Worker Threads_

### 14. 什么是函数柯里化？ 
> 柯里化（_currying_）又称部分求值。一个柯里化的函数首先会接受一些参数，接受了这些参数之后，该函数并不会立即求值，而是继续返回另外一个函数，刚才传入的参数在函数形成的闭包中被保存起来。待到函数被真正需要求值的时候，之前传入的所有参数都会被一次性用于求值。
