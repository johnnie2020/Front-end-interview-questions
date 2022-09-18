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

### 15. _promise.all_ 方法的使用场景？数组中必须每一项都是 _promise_ 对象吗？不是 _promise_ 对象会如何处理 ？
> **_promise.all(promiseArray)_** 方法是 _promise_ 对象上的静态方法，该方法的作用是将多个 _promise_ 对象实例包装，生成并返回一个新的 _promise_ 实例。
> 此方法在集合多个 _promise_ 的返回结果时很有用。
> 返回值将会按照参数内的 _promise_ 顺序排列，而不是由调用 _promise_ 的完成顺序决定。
> **_promise.all_ 的特点**
> **接收一个**_**Promise**_**实例的数组或具有**_**Iterator**_**接口的对象**
> 如果元素不是_Promise_对象，则使用_Promise.resolve_转成_Promise_对象
> 如果全部成功，状态变为_resolved_，返回值将组成一个数组传给回调
> 只有有一个失败，状态就变为 _rejected_，返回值将直接传递给回调  _all( )_的返回值，也是新的 _promise_ 对象

### 16. _this_ 的指向哪几种 ？ 
> - 在函数体中，非显式或隐式地简单调用函数时，在严格模式下，函数内的 _this_ 会被绑定到 _undefined_ 上，在非严格模式下则会被绑定到全局对象 _window/global_ 上。
> - 一般使用 _new_ 方法调用构造函数时，构造函数内的 _this_ 会被绑定到新创建的对象上。
> - 一般通过 _call/apply/bind_ 方法显式调用函数时，函数体内的 _this_ 会被绑定到指定参数的对象上。
> - 一般通过上下文对象调用函数时，函数体内的 _this_ 会被绑定到该对象上。
> - 在箭头函数中，_this_ 的指向是由外层（函数或全局）作用域来决定的。

### 18. 什么是事件监听 
> 首先需要区别清楚事件监听和事件监听器。
> 在绑定事件的时候，我们需要对应的书写一个事件处理程序，来应对事件发生时的具体行为。
> 这个事件处理程序我们也称之为事件监听器。
> 当事件绑定好后，程序就会对事件进行监听，当用户触发事件时，就会执行对应的事件处理程序。
> 关于事件监听，_W3C_ 规范中定义了 _3_ 个事件阶段，依次是捕获阶段、目标阶段、冒泡阶段。
> -  **捕获**阶段：在事件对象到达事件目标之前，事件对象必须从 _window_ 经过目标的祖先节点传播到事件目标。 这个阶段被我们称之为捕获阶段。在这个阶段注册的事件监听器在事件到达其目标前必须先处理事件。 
> -  **目标** 阶段：事件对象到达其事件目标。 这个阶段被我们称为目标阶段。一旦事件对象到达事件目标，该阶段的事件监听器就要对它进行处理。如果一个事件对象类型被标志为不能冒泡。那么对应的事件对象在到达此阶段时就会终止传播。 
> -  **冒泡** 阶段：事件对象以一个与捕获阶段相反的方向从事件目标传播经过其祖先节点传播到 _window_。这个阶段被称之为冒泡阶段。在此阶段注册的事件监听器会对相应的冒泡事件进行处理。 
> 

### 19. 什么是 _js_ 的闭包？有什么作用？
> 一个函数和对其周围状态（_lexical environment_，词法环境）的引用捆绑在一起（或者说函数被引用包围），这样的组合就是**闭包**（_closure_）。也就是说，闭包让你可以在一个内层函数中访问到其外层函数的作用域。在 _JavaScript_ 中，每当创建一个函数，闭包就会在函数创建的同时被创建出来。
> 闭包的用处：
> 1. 匿名自执行函数
> 1. 结果缓存
> 1. 封装
> 1. 实现类和继承


### 20. 事件委托以及冒泡原理
> 事件委托，又被称之为事件代理。在 _JavaScript_ 中，添加到页面上的事件处理程序数量将直接关系到页面整体的运行性能。导致这一问题的原因是多方面的。
>  
> 首先，每个函数都是对象，都会占用内存。内存中的对象越多，性能就越差。其次，必须事先指定所有事件处理程序而导致的 _DOM_ 访问次数，会延迟整个页面的交互就绪时间。
>  
> 对事件处理程序过多问题的解决方案就是事件委托。
>  
> **事件委托利用了事件冒泡，只指定一个事件处理程序，就可以管理某一类型的所有事件。例如，**_**click**_** 事件会一直冒泡到 **_**document**_** 层次。也就是说，我们可以为整个页面指定一个 **_**onclick**_** 事件处理程序，而不必给每个可单击的元素分别添加事件处理程序。**
> 事件冒泡（_event bubbling_），是指事件开始时由最具体的元素（文档中嵌套层次最深的那个节点）接收，然后逐级向上传播到较为不具体的节点（文档）。


### li的事件委托给ul，但是点击的是li里面的按钮，怎么办？
pointer-events：none
### 21. _let const var_ 的区别？什么是块级作用域？如何用？
> 1. _var_ 定义的变量，没有块的概念，可以跨块访问, 不能跨函数访问，有变量提升。
> 1. _let_ 定义的变量，只能在块作用域里访问，不能跨块访问，也不能跨函数访问，无变量提升，不可以重复声明。
> 1. _const_ 用来定义常量，使用时必须初始化(即必须赋值)，只能在块作用域里访问，而且不能修改，无变量提升，不可以重复声明。
> 
最初在 _JS_ 中作用域有：全局作用域、函数作用域。没有块作用域的概念。
> _ES6_ 中新增了块级作用域。块作用域由 { } 包括，_if_ 语句和 _for_ 语句里面的 { } 也属于块作用域。
> 在以前没有块作用域的时候，在 if 或者 for 循环中声明的变量会泄露成全局变量，其次就是 { } 中的内层变量可能会覆盖外层变量。块级作用域的出现解决了这些问题。


### let为什么有块级作用域

### 22. _ES5_ 的方法实现块级作用域（立即执行函数） _ES6_ 呢？
> _ES6_ 原生支持块级作用域。块作用域由 { } 包括，_if_ 语句和 _for_ 语句里面的 { } 也属于块作用域。
> 使用 _let_ 声明的变量或者使用 _const_ 声明的常量，只能在块作用域里访问，不能跨块访问。  

### 基本类型和引用值区别

> 栈和堆的区别在于堆是动态分配内存，内存大小不一，也不会自动释放。栈是自动分配相对固定大小的内存空间，并由系统自动释放。
>  
> 在 _js_ 中，基本数据都是直接按值存储在栈中的，每种类型的数据占用的内存空间的大小是确定的，并由系统自动分配和自动释放。这样带来的好处就是，内存可以及时得到回收，相对于堆来说，更加容易管理内存空间。
>  
> _js_ 中其他类型的数据被称为引用类型的数据（如对象、数组、函数等），它们是通过拷贝和 _new_ 出来的，这样的数据存储于堆中。其实，说存储于堆中，也不太准确，因为，引用类型的数据的地址指针是存储于栈中的，当我们想要访问引用类型的值的时候，需要先从栈中获得对象的地址指针，然后，在通过地址指针找到堆中的所需要的数据。

>  **原始值是表示 _JavaScript_ 中可用的数据或信息的最底层形式或最简单形式。**简单类型的值被称为原始值，是因为它们是**不可细化**的。
> 也就是说，数字是数字，字符是字符，布尔值是 _true_ 或 _false_，_null_ 和 _undefined_ 就是 _null_ 和 _undefined_。这些值本身很简单，不能够再进行拆分。由于原始值的数据大小是固定的，所以**原始值的数据是存储于内存中的栈区里面的。**
> 在 _JavaScript_ 中，对象就是一个引用值。因为对象可以向下拆分，拆分成多个简单值或者复杂值。**引用值在内存中的大小是未知的，因为引用值可以包含任何值，而不是一个特定的已知值，所以引用值的数据都是存储于堆区里面。**
> 最后总结一下两者的区别：
> 1.  访问方式 
>    - 原始值：访问到的是值
>    - 引用值：访问到的是引用地址
> 2.  比较方式 
>    - 原始值：比较的是值
>    - 引用值：比较的是地址
> 3.  动态属性 
>    - 原始值：无法添加动态属性
>    - 引用值：可以添加动态属性
> 4.  变量赋值 
>    - 原始值：赋值的是值
>    - 引用值：赋值的是地址

### 27. _JS_ 的作用域类型

> 在 _JavaScript_ 里面，作用域一共有 4 种：全局作用域，局部作用域、函数作用域以及 _eval_ 作用域。 
> **全局作用域：**这个是默认的代码运行环境，一旦代码被载入，引擎最先进入的就是这个环境。
> **局部作用域：**当使用 _let_ 或者 _const_ 声明变量时，这些变量在一对花括号中存在局部作用域，只能够在花括号内部进行访问使用
> **函数作用域：**当进入到一个函数的时候，就会产生一个函数作用域。函数作用域里面所声明的变量只在函数中提供访问使用。
> **_eval_ 作用域：**当调用 _eval( )_ 函数的时候，就会产生一个 _eval_ 作用域。

### 28. _undefined==null_ 返回的结果是什么？_undefined_ 与 _null_ 的区别在哪？ 
> 通常情况下， 当我们试图访问某个不存在的或者没有赋值的变量时，就会得到一个 _undefined_ 值。_Javascript_ 会自动将声明是没有进行初始化的变量设为 _undifined_。
> 而 _null_ 值表示空，_null_ 不能通过 _Javascript_ 来自动赋值，也就是说必须要我们自己手动来给某个变量赋值为 _null_。

### 29. 写一个函数判断变量类型
```javascript
function getType(data){
  let type = typeof data;
  if(type !== "object"){
    return type
  }
  return Object.prototype.toString.call(data).replace(/^\[object (\S+)\]$/,'$1')
}
```
### 30. _js_ 的异步处理函数
> 在最早期的时候，_JavaScript_ 中要实现异步操作，使用的就是 _Callback_ 回调函数。
> 之后 ES6 推出了 _Promise_ 解决方案来解决回调地狱的问题。不过，虽然 _Promise_ 作为 _ES6_ 中提供的一种新的异步编程解决方案，但是它也有问题。比如，代码并没有因为新方法的出现而减少，反而变得更加复杂，同时理解难度也加大。
> 之后，就出现了基于 _Generator_ 的异步解决方案。不过，这种方式需要编写外部的执行器，而执行器的代码写起来一点也不简单。当然也可以使用一些插件，比如 _co_ 模块来简化执行器的编写。
> _ES7_ 提出的 _async_ 函数，终于让 _JavaScript_ 对于异步操作有了终极解决方案。
> 实际上，_async_ 只是生成器的一种语法糖而已，简化了外部执行器的代码，同时利用 _await_ 替代 _yield_，_async_ 替代生成器的`*`号。

### 31. _defer_ 与 _async_ 的区别
> 按照惯例，所有 _script_ 元素都应该放在页面的 _head_ 元素中。这种做法的目的就是把**所有外部文件（_CSS_ 文件和 _JavaScript_ 文件）的引用都放在相同的地方**。可是，在文档的 _head_ 元素中包含所有 _JavaScript_ 文件，意味着必须等到全部 _JavaScript_ 代码都被下载、解析和执行完成以后，才能开始呈现页面的内容（浏览器在遇到 _body_ 标签时才开始呈现内容）。
>  对于那些需要很多 _JavaScript_ 代码的页面来说，这无疑会导致浏览器在呈现页面时出现明显的延迟，而延迟期间的浏览器窗口中将是一片空白。为了避免这个问题，现在 **_Web_ 应用程序一般都全部 _JavaScript_ 引用放在 _body_ 元素中页面的内容后面**。这样一来，在解析包含的 _JavaScript_ 代码之前，页面的内容将完全呈现在浏览器中。而用户也会因为浏览器窗口显示空白页面的时间缩短而感到打开页面的速度加快了。
>  有了 _defer_ 和 _async_ 后，这种局面得到了改善。
>  **_defer_ （延迟脚本）**
>  延迟脚本：_defer_ 属性只适用于外部脚本文件。
>  如果给 _script_ 标签定义了_defer_ 属性，这个属性的作用是表明脚本在执行时不会影响页面的构造。也就是说，脚本会被延迟到整个页面都解析完毕后再运行。因此，如果 _script_ 元素中设置了 _defer_ 属性，相当于告诉浏览器立即下载，但延迟执行。
>  **_async_（异步脚本）**
>  异步脚本：_async_ 属性也只适用于外部脚本文件，并告诉浏览器立即下载文件。
>  **但与 _defer_ 不同的是：标记为 _async_ 的脚本并不保证按照指定它们的先后顺序执行。**
>  所以总结起来，两者之间最大的差异就是在于脚本下载完之后何时执行，显然 _defer_ 是最接近我们对于应用脚本加载和执行的要求的。
>  _defer_ 是立即下载但延迟执行，加载后续文档元素的过程将和脚本的加载并行进行（异步），但是脚本的执行要在所有元素解析完成之后，_DOMContentLoaded_ 事件触发之前完成。_async_ 是立即下载并执行，加载和渲染后续文档元素的过程将和 _js_ 脚本的加载与执行并行进行（异步）。
> **总结:都用于外部脚本 async异步下载完立即执行 defer异步下载完等dom加载完成后执行 兼容性问题script标签放最底下**

### 33. 原型与原型链 （美团 19年） 
> - 每个对象都有一个 `__proto__` 属性，该属性指向自己的原型对象
> - 每个构造函数都有一个 `prototype` 属性，该属性指向实例对象的原型对象
> - 原型对象里的 `constructor` 指向构造函数本身
> - 

> - 每个对象都有自己的原型对象，而原型对象本身，也有自己的原型对象，从而形成了一条原型链条。
> - 当试图访问一个对象的属性时，它不仅仅在该对象上搜寻，还会搜寻该对象的原型，以及该对象的原型的原型，依次层层向上搜索，直到找到一个名字匹配的属性或到达原型链的末尾。
> 
如下图：

![image.png](https://cdn.nlark.com/yuque/0/2021/png/758572/1638069187324-2fcef6b0-e151-4c99-a3cb-9063e874d238.png#clientId=ub7d735a1-a078-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=211&id=u153653ce&margin=%5Bobject%20Object%5D&name=image.png&originHeight=790&originWidth=1120&originalType=binary&ratio=1&rotation=0&showTitle=false&size=341424&status=done&style=none&taskId=udce5aa06-c186-4996-b71e-55e7269f3d3&title=&width=299)

### 34. 作用域与作用域链
> 作用域是在运行时代码中的某些特定部分中变量，函数和对象的可访问性。换句话说，作用域决定了代码区块中变量和其他资源的可见性。_ES6_ 之前 _JavaScript_ 没有块级作用域，只有全局作用域和函数作用域。_ES6_ 的到来，为我们提供了块级作用域。
>  作用域链指的是作用域与作用域之间形成的链条。当我们查找一个当前作用域没有定义的变量（自由变量）的时候，就会向上一级作用域寻找，如果上一级也没有，就再一层一层向上寻找，直到找到全局作用域还是没找到，就宣布放弃。这种一层一层的关系，就是作用域链 。

### 谈谈你对 _JS_ 执行上下文栈和作用域链的理解 
> **什么是执行上下文？**
>  
> 简而言之，执行上下文是评估和执行 JavaScript 代码的环境的抽象概念。每当 Javascript 代码在运行的时候，它都是在执行上下文中运行。
>  
> **执行上下文的类型**
>  
> JavaScript 中有三种执行上下文类型。
>  
> - **全局执行上下文** — 这是默认或者说基础的上下文，任何不在函数内部的代码都在全局上下文中。它会执行两件事：创建一个全局的 window 对象（浏览器的情况下），并且设置 `this` 的值等于这个全局对象。一个程序中只会有一个全局执行上下文。
> - **函数执行上下文** — 每当一个函数被调用时, 都会为该函数创建一个新的上下文。每个函数都有它自己的执行上下文，不过是在函数被调用时创建的。函数上下文可以有任意多个。每当一个新的执行上下文被创建，它会按定义的顺序（将在后文讨论）执行一系列步骤。
> - **Eval 函数执行上下文** — 执行在 `eval` 函数内部的代码也会有它属于自己的执行上下文。
> 

> **调用栈**
>  
> 调用栈是解析器(如浏览器中的的javascript解析器)的一种机制，可以在脚本调用多个函数时，跟踪每个函数在完成执行时应该返回控制的点。（如什么函数正在执行，什么函数被这个函数调用，下一个调用的函数是谁）
>  
> - 当脚本要调用一个函数时，解析器把该函数添加到栈中并且执行这个函数。
> - 任何被这个函数调用的函数会进一步添加到调用栈中，并且运行到它们被上个程序调用的位置。
> - 当函数运行结束后，解释器将它从堆栈中取出，并在主代码列表中继续执行代码。
> - 如果栈占用的空间比分配给它的空间还大，那么则会导致“栈溢出”错误。
> 

> **作用域链**
>  
> 当访问一个变量时，编译器在执行这段代码时，会首先从当前的作用域中查找是否有这个标识符，如果没有找到，就会去父作用域查找，如果父作用域还没找到继续向上查找，直到全局作用域为止,，而作用域链，就是有当前作用域与上层作用域的一系列变量对象组成，它保证了当前执行的作用域对符合访问权限的变量和函数的有序访问。

### 38. 描述下列代码的执行结果

```javascript
const first = () => (new Promise((resolve, reject) => {
    console.log(3);
    let p = new Promise((resolve, reject) => {
        console.log(7);
        setTimeout(() => {
            console.log(1);
        }, 0);
        setTimeout(() => {
            console.log(2);
            resolve(3);
        }, 0)
        resolve(4);
    });
    resolve(2);
    p.then((arg) => {
        console.log(arg, 5); // 1 bb
    });
    setTimeout(() => {
        console.log(6);
    }, 0);
}))
first().then((arg) => {
    console.log(arg, 7); // 2 aa
    setTimeout(() => {
        console.log(8);
    }, 0);
});
setTimeout(() => {
    console.log(9);
}, 0);
console.log(10);
```
### 39. 如何判断数组或对象（美团 19年） 
> 1. 通过 _instanceof_ 进行判断
> 1. 通过对象的 _constructor_ 属性
> 3. _Object.prototype.toString.call(arr)_ 
> 4. 可以通过 _ES6_ 新提供的方法 _Array.isArray( )_


### _Object.assign_（美团 19年）
> _Object.assign_ 方法可以把任意多个的源对象自身的可枚举属性拷贝给目标对象，然后返回目标对象。但是 _Object.assign_ 方法进行的是浅拷贝，拷贝的是对象的属性的引用，而不是对象本身。

### 42. 说说 _instanceof_ 原理，并回答下面的题目（美团 19年）

```javascript
function A(){}
function B(){}
A.prototype = new B(); 
let a = new A(); 
console.log(a instanceof B) // true of false ?
```

>  _instanceof_  用于检测一个对象是否为某个构造函数的实例。
> 例如：_A instanceof B_
_instanceof_ 用于检测对象 _A_ 是不是 _B_ 的实例，而检测是基于原型链进行查找的，也就是说 _B_ 的 _prototype_ 有没有在对象 _A_ 的__*proto___ 原型链上，如果有就返回 _true_，否则返回 _false

### 43. 内存泄漏（美团 19 年）
> 内存泄漏（_Memory Leak_）是指程序中己动态分配的堆内存由于某种原因程序未释放或无法释放，造成系统内存的浪费，导致程序运行速度减慢甚至系统崩溃等严重后果。
> _Javascript_ 是一种高级语言，它不像 _C_ 语言那样要手动申请内存，然后手动释放，_Javascript_ 在声明变量的时候自动会分配内存，普通的类型比如 _number_，一般放在栈内存里，对象放在堆内存里，声明一个变量，就分配一些内存，然后定时进行垃圾回收。垃圾回收的任务由 _JavaScript_ 引擎中的垃圾回收器来完成，它监视所有对象，并删除那些不可访问的对象。
> 基本的垃圾回收算法称为**“标记-清除”**，定期执行以下“垃圾回收”步骤:
>  
> - 垃圾回收器获取根并**“标记”**(记住)它们。
> - 然后它访问并“标记”所有来自它们的引用。
> - 然后它访问标记的对象并标记它们的引用。所有被访问的对象都被记住，以便以后不再访问同一个对象两次。
> - 以此类推，直到有未访问的引用(可以从根访问)为止。
> - 除标记的对象外，所有对象都被删除。

### 45. _weakmap、weakset_（美团 _19_ 年）
> _WeakSet_ 对象是一些对象值的集合, 并且其中的每个对象值都只能出现一次。在 _WeakSet_ 的集合中是唯一的
> 它和 _Set_ 对象的区别有两点:
> - 与 _Set_ 相比，_WeakSet_ 只能是**对象的集合**，而不能是任何类型的任意值。
> - _WeakSet_ 持弱引用：集合中对象的引用为弱引用。 如果没有其他的对 _WeakSet_ 中对象的引用，那么这些对象会被当成垃圾回收掉。 这也意味着 _WeakSet_ 中没有存储当前对象的列表。 正因为这样，_WeakSet_ 是不可枚举的。
> 
_WeakMap_ 对象也是键值对的集合。它的**键必须是对象类型**，值可以是任意类型。它的键被弱保持，也就是说，当其键所指对象没有其他地方引用的时候，它会被 _GC_ 回收掉。_WeakMap_ 提供的接口与 _Map_ 相同。
> 与 _Map_ 对象不同的是，_WeakMap_ 的键是不可枚举的。不提供列出其键的方法。列表是否存在取决于垃圾回收器的状态，是不可预知

### 56. 闭包、作用域（可以扩充到作用域链）

> 参考答案：
>  
> **什么是作业域?**
>  
> ES5 中只存在两种作用域：全局作用域和函数作用域。在 JavaScript 中，我们将作用域定义为一套规则，这套规则用来管理引擎如何在当前作用域以及嵌套子作用域中根据标识符名称进行变量(变量名或者函数名)查找。
>  
> **什么是作用域链?**
>  
> 当访问一个变量时，编译器在执行这段代码时，会首先从当前的作用域中查找是否有这个标识符，如果没有找到，就会去父作用域查找，如果父作用域还没找到继续向上查找，直到全局作用域为止,，而作用域链，就是有当前作用域与上层作用域的一系列变量对象组成，它保证了当前执行的作用域对符合访问权限的变量和函数的有序访问。
>  
> **闭包产生的本质**
>  
> 当前环境中存在指向父级作用域的引用
>  
> **什么是闭包**
>  
> 闭包是一种特殊的对象，它由两部分组成：执行上下文(代号 A)，以及在该执行上下文中创建的函数 (代号 B)，当 B 执行时，如果访问了 A 中变量对象的值，那么闭包就会产生，且在 Chrome 中使用这个执行上下文 A 的函数名代指闭包。
>  
> **一般如何产生闭包**
>  
> - 返回函数
> - 函数当做参数传递
> 

> **闭包的应用场景**
>  
> - 柯里化 bind
> - 模块


### 58. 实现一个函数,对一个url进行请求,失败就再次请求,超过最大次数就走失败回调,任何一次成功都走成功回调 
```javascript
/**
 @params url: 请求接口地址;
 @params body: 设置的请求体;
 @params succ: 请求成功后的回调
 @params error: 请求失败后的回调
 @params maxCount: 设置请求的数量
*/
function request(url, body, succ, error, maxCount = 5) {
 return fetch(url, body)
     .then(res => succ(res))
     .catch(err => {
         if (maxCount <= 0) return error('请求超时');
         return request(url, body, succ, error, --maxCount);
     });
}

// 调用请求函数
request('https://java.some.com/pc/reqCount', { method: 'GET', headers: {} },
 (res) => {
     console.log(res.data);
 },
 (err) => {
     console.log(err);
 })
```

### 62. promise 代码题

```javascript
new Promise((resolve, reject) => {
    reject(1);
    console.log(2);
    resolve(3);
    console.log(4);
}).then((res) => { console.log(res) })
    .catch(res => { console.log('reject1') })
try {
    new Promise((resolve, reject) => {
        throw 'error'
    }).then((res) => { console.log(res) })
        .catch(res => { console.log('reject2') })
} catch (err) {
    console.log(err)
}
```
### 63. _proxy_ 是实现代理，可以改变 _js_ 底层的实现方式, 然后说了一下和 _Object.defineProperty_ 的区别
> **Proxy 的优势如下:**
> - _Object.defineProperty_ 只能劫持对象的属性,因此我们需要对每个对象的每个属性进行遍历，而 _Proxy_ 可以直接监听对象而非属性；
> - _Object.defineProperty_ 无法监控到数组下标的变化，而 _Proxy_ 可以直接监听数组的变化；
> - _Proxy_ 有多达 _13_ 种拦截方法；
> - _Proxy_ 作为新标准将受到浏览器厂商重点持续的性能优化；


> 两者的区别总结如下： 
> - 代理原理：Object.defineProperty的原理是通过将数据属性转变为存取器属性的方式实现的属性读写代理。而Proxy则是因为这个内置的Proxy对象内部有一套监听机制，在传入handler对象作为参数构造代理对象后，一旦代理对象的某个操作触发，就会进入handler中对应注册的处理函数，此时我们就可以有选择的使用Reflect将操作转发被代理对象上。
> - 代理局限性：Object.defineProperty始终还是局限于**属性层面**的读写代理，对于**对象层面以及属性的其它操作**代理它都无法实现。鉴于此，由于数组对象push、pop等方法的存在，它对于数组元素的读写代理实现的并不完全。**而使用Proxy则可以很方便的监视数组操作。**
> - 自我代理：Object.defineProperty方式可以代理到自身（代理之后使用对象本身即可），也可以代理到别的对象身上（代理之后需要使用代理对象）。Proxy方式只能代理到Proxy实例对象上。这一点在其它说法中是Proxy对象不需要侵入对象就可以实现代理，实际上Object.defineProperty方式也可以不侵入。

> 在 _JavaScript_ 中，通过 _Object.defineProperty_ 方法可以设置对象属性的特性，选项如下：
>  
> - _get_：一旦目标属性被访问时，就会调用相应的方法
> - _set_：一旦目标属性被设置时，就会调用相应的方法
> - _value_：这是属性的值，默认是 _undefined_
> - _writable_：这是一个布尔值，表示一个属性是否可以被修改，默认是 _true_
> - _enumerable_：这是一个布尔值，表示在用 _for-in_ 循环遍历对象的属性时，该属性是否可以显示出来，默认值为 _true_
> - _configurable_：这是一个布尔值，表示我们是否能够删除一个属性或者修改属性的特性，默认值为 _true_ 

> ##### 1、_Object.defineproperty_
> 可以用于监听对象的数据变化
> 语法： **_Object.defineproperty(obj, key, descriptor)_**
> 此外 还有以下配置项 ：
> - _configurable_
> - _enumerable_
> - _value_
> 
缺点：
> 1.  无法监听数组变化 
> 1.  只能劫持对象的属性，属性值也是对象那么需要深度遍历 
> ##### 2、_proxy_ ：可以理解为在被劫持的对象之前 加了一层拦截
> - _proxy_ 返回的是一个新对象， 可以通过操作返回的新的对象达到目的
> - _proxy_ 有多达 _13_ 种拦截方法
> 
**总结：**
> - _Object.defineProperty_ 无法监控到数组下标的变化，导致通过数组下标添加元素，不能实时响应
> - _Object.defineProperty_ 只能劫持对象的属性，从而需要对每个对象，每个属性进行遍历，如果，属性值是对象，还需要深度遍历。_Proxy_ 可以劫持整个对象，并返回一个新的对象。
> - _Proxy_ 不仅可以代理对象，还可以代理数组。还可以代理动态增加的属性。
> 


```javascript
let obj = {
 age: 11
}
let value = 'xiaoxiao';
//defineproperty 有 gettter 和 setter
Object.defineproperty(obj, 'name', {
 get() {
     return value
 },
 set(newValue) {
     value = newValue
 }
})
obj.name = 'pengpeng';
```
```javascript
let proxy = new Proxy({}, {
    get(obj, prop) {
        return obj[prop]
    },
    set(obj, prop, val) {
        obj[prop] = val
    }
})
```

### 深拷贝
> **递归容易造成爆栈，尾部调用可以解决递归的这个问题，**_Chrome_ 的 _V8_ 引擎做了尾部调用优化，我们在写代码的时候也要注意尾部调用写法。递归的爆栈问题可以通过将递归改写成枚举的方式来解决，就是通过 _for_ 或者 _while_ 来代替递归。

```
function deepClone(o1, o2) {
    for (let k in o2) {
        if (typeof o2[k] === 'object') {
            o1[k] = {};
            deepClone(o1[k], o2[k]);
        } else {
            o1[k] = o2[k];
        }
    }
}
// 测试用例
let obj = {
    a: 1,
    b: [1, 2, 3],
    c: {}
};
let emptyObj = Object.create(null);
deepClone(emptyObj, obj);
console.log(emptyObj.a == obj.a);
console.log(emptyObj.b == obj.b);
```
### _instanceof_ 是如何实现？
> 例如：_[ ] instanceof Object_ 返回的也会是 _true_。

```javascript
instanceof (A,B) = {
    varL = A.__proto__;
    varR = B.prototype;
    if(L === R) {
        // A的内部属性 __proto__ 指向 B 的原型对象
        return true;
    }
    return false;
}
```
### 75. _JS_的垃圾回收站机制
> _JS_ 具有自动垃圾回收机制。垃圾收集器会按照**固定的时间间隔周期性**的执行。
> _JS_ 常见的垃圾回收方式：标记清除、引用计数方式。
> 1、标记清除方式：
> -  工作原理：当变量进入环境时，将这个变量标记为“进入环境”。当变量离开环境时，则将其标记为“离开环境”。标记“离开环境”的就回收内存。 
> -  工作流程： 
> -  垃圾回收器，在运行的时候会给存储在内存中的所有变量都加上标记； 
> -  去掉环境中的变量以及被环境中的变量引用的变量的标记； 
> -  被加上标记的会被视为准备删除的变量； 
> -  垃圾回收器完成内存清理工作，销毁那些带标记的值并回收他们所占用的内存空间。 
> 
2、引用计数方式：
> -  工作原理：跟踪记录每个值被引用的次数。 
> -  工作流程： 
> -  声明了一个变量并将一个引用类型的值赋值给这个变量，这个引用类型值的引用次数就是 _1_； 
> -  同一个值又被赋值给另一个变量，这个引用类型值的引用次数加1； 
> -  当包含这个引用类型值的变量又被赋值成另一个值了，那么这个引用类型值的引用次数减 _1_； 
> -  当引用次数变成 _0_ 时，说明没办法访问这个值了； 
> -  当垃圾收集器下一次运行时，它就会释放引用次数是0的值所占的内存。 

### 76. 什么是作用域链、原型链
> **什么是作用域链?**
>  
> 当访问一个变量时，编译器在执行这段代码时，会首先从当前的作用域中查找是否有这个标识符，如果没有找到，就会去父作用域查找，如果父作用域还没找到继续向上查找，直到全局作用域为止,，而作用域链，就是有当前作用域与上层作用域的一系列变量对象组成，它保证了当前执行的作用域对符合访问权限的变量和函数的有序访问。
>  
> **什么原型链?**
>  
> 每个对象都可以有一个原型__*proto*__，这个原型还可以有它自己的原型，以此类推，形成一个原型链。查找特定属性的时候，我们先去这个对象里去找，如果没有的话就去它的原型对象里面去，如果还是没有的话再去向原型对象的原型对象里去寻找。这个操作被委托在整个原型链上，这个就是我们说的原型链。

### 79. 什么是变量提升
> 参考答案：
>  
> 当 _JavaScript_ 编译所有代码时，所有使用 _var_ 的变量声明都被提升到它们的函数/局部作用域的顶部(如果在函数内部声明的话)，或者提升到它们的全局作用域的顶部(如果在函数外部声明的话)，而不管实际的声明是在哪里进行的。这就是我们所说的“提升”。
>  
> 请记住，这种“提升”实际上并不发生在你的代码中，而只是一种比喻，与 _JavaScript_ 编译器如何读取你的代码有关。记住当我们想到“提升”的时候，我们可以想象任何被提升的东西都会被移动到顶部，但是实际上你的代码并不会被修改。
>  
> 函数声明也会被提升，但是被提升到了最顶端，所以将位于所有变量声明之上。
>  
> 在编译阶段变量和函数声明会被放入内存中，但是你在代码中编写它们的位置会保持不变。

### 81. _Object.is_ 方法比较的是什么
> _Object.is_ 方法是 _ES6_ 新增的用来比较两个值是否严格相等的方法，与 === (严格相等)的行为基本一致。不过有两处不同：
> - +0 不等于 -0。
> - _NaN_ 等于自身。
> 
所以可以将_Object.is_ 方法看作是加强版的严格相等。

### 82. 基础数据类型和引用数据类型，哪个是保存在栈内存中？哪个是在堆内存中？
> 在 _ECMAScript_ 规范中，共定义了 _7_ 种数据类型，分为 **基本类型** 和 **引用类型** 两大类，如下所示：
>  
> -  **基本类型**：_String、Number、Boolean、Symbol、Undefined、Null_ 
> -  **引用类型**：_Object_ 
> 

> 基本类型也称为简单类型，由于其占据空间固定，是简单的数据段，为了便于提升变量查询速度，将其存储在栈中，即按值访问。
>  
> 引用类型也称为复杂类型，由于其值的大小会改变，所以不能将其存放在栈中，否则会降低变量查询速度，因此，其值存储在堆(_heap_)中，而存储在变量处的值，是一个指针，指向存储对象的内存处，即按址访问。引用类型除 _Object_ 外，还包括 _Function 、Array、RegExp、Date_ 等等。


### 85. _promise_ 的其他方法有用过吗？如 _all、race_。请说下这两者的区别
> _promise.all_ 方法参数是一个 _promise_ 的数组,只有当所有的 _promise_ 都完成并返回成功，才会调用 _resolve_，当有一个失败，都会进_catch_，被捕获错误，_promise.all_ 调用成功返回的结果是每个 _promise_ 单独调用成功之后返回的结果组成的数组,如果调用失败的话，返回的则是第一个 _reject_ 的结果
>  
> _promise.race_ 也会调用所有的 _promise_，返回的结果则是所有 _promise_ 中最先返回的结果，不关心是成功还是失败。


### 86. _class_ 是如何实现的
> _class_ 是 _ES6_ 新推出的关键字，它是一个语法糖，本质上就是基于这个原型实现的。只不过在以前 _ES5_ 原型实现的基础上，添加了一些 *_classCallCheck、_defineProperties、_createClass*等方法来做出了一些特殊的处理。
> 

```javascript
class Hello {
constructor(x) {
  this.x = x;
}
greet() {
  console.log("Hello, " + this.x)
}
}
```
```javascript
"use strict";

function _classCallCheck(instance, Constructor) {
if (!(instance instanceof Constructor)) {
    throw new TypeError("Cannot call a class as a function");
}
}

function _defineProperties(target, props) {
for (var i = 0; i < props.length; i++) {
    var descriptor = props[i];
    descriptor.enumerable = descriptor.enumerable || false;
    descriptor.configurable = true;
    if ("value" in descriptor)
        descriptor.writable = true;
    Object.defineProperty(target, descriptor.key, descriptor);
}
}

function _createClass(Constructor, protoProps, staticProps) {
console.log("Constructor::",Constructor);
console.log("protoProps::",protoProps);
console.log("staticProps::",staticProps);
if (protoProps)
    _defineProperties(Constructor.prototype, protoProps);
if (staticProps)
    _defineProperties(Constructor, staticProps);
return Constructor;
}

var Hello = /*#__PURE__*/function () {
function Hello(x) {
  _classCallCheck(this, Hello);

  this.x = x;
}

_createClass(Hello, [{
  key: "greet",
  value: function greet() {
    console.log("Hello, " + this.x);
  }
	}]);

	return Hello;
}();
```

### 88. _ES6_ 中模块化导入和导出与 _common.js_ 有什么区别
> CommonJs模块输出的是值的拷贝，也就是说，一旦输出一个值，模块内部的变化不会影响到这个值.
> 你可以看到明明common.js里面改变了count，但是输出的结果还是原来的。这是因为count是一个原始类型的值，会被缓存。除非写成一个函数，才能得到内部变动的值。将common.js里面的module.exports 改写成
> 这样子的输出结果是 1，2，2
> 而在ES6当中，写法是这样的，是利用export 和import导入的
> ES6 模块是动态引用，并且不会缓存，模块里面的变量绑定其所有的模块，而是动态地去加载值，并且不能重新赋值，
> ES6 输入的模块变量，只是一个“符号连接符”，所以这个变量是只读的，对它进行重新赋值会报错。如果是引用类型，变量指向的地址是只读的，但是可以为其添加属性或成员。 
> 另外还想说一个 _export default_
> export与export default的区别及联系：
> 1.  export与export default均可用于导出常量、函数、文件、模块等 
> 1.  你可以在其它文件或模块中通过 import + (常量 | 函数 | 文件 | 模块)名的方式，将其导入，以便能够对其进行使用 
> 1.  在一个文件或模块中，export、import可以有多个，export default仅有一个 
> 1.  通过export方式导出，在导入时要加{ }，export default则不需要。

### 92. 了解过 _js_ 中 _arguments_ 吗？接收的是实参还是形参？
> _JS_ 中的 _arguments_ 是一个伪数组对象。这个伪数组对象将包含调用函数时传递的所有的实参。
>  与之相对的，_JS_ 中的函数还有一个 _length_ 属性，返回的是函数形参的个数。

### 95. 纯函数
> 一个函数，如果符合以下两个特点，那么它就可以称之为**纯函数**： 
> 1. 对于相同的输入，永远得到相同的输出
> 1. 没有任何可观察到的副作用


> 针对上面的两个特点，我们一个一个来看。
>  
> - 相同输入得到相同输出
> 

> 我们先来看一个不纯的反面典型：
> 
> 上面的代码中，_greet('World')_ 是不是永远返回 _Hello World_ ? 显然不是，假如我们修改 _greeting_ 的值，就会影响 _greet_ 函数的输出。即函数 _greet_ 其实是 **依赖外部状态** 的。
>  
> 那我们做以下修改：
> 将 _greeting_ 参数也传入，这样对于任何输入参数，都有与之对应的唯一的输出参数了，该函数就符合了第一个特点。
>  
> - 没有副作用
> 

> 副作用的意思是，这个函数的运行，**不会修改外部的状态**。

### 96. _JS_ 模块化
> 模块化主要是用来抽离公共代码，隔离作用域，避免变量冲突等。
>  模块化的整个发展历史如下：
>  **IIFE**： 使用自执行函数来编写模块化，特点：**在一个单独的函数作用域中执行代码，避免变量冲突**。
>  **AMD**： 使用requireJS 来编写模块化，特点：**依赖必须提前声明好**。
>  **CMD**： 使用seaJS 来编写模块化，特点：**支持动态引入依赖文件**。
>  **CommonJS**： nodejs 中自带的模块化。
>  **UMD**：兼容AMD，CommonJS 模块化语法。
> **webpack(require.ensure)**：webpack 2.x 版本中的代码分割。
> **ES Modules**： ES6 引入的模块化，支持import 来引入另一个 js 。

### 97. 看过 _jquery_ 源码吗？
> 开放题，但是需要注意的是，如果看过 _jquery_ 源码，不要简单的回答一个“看过”就完了，应该继续乘胜追击，告诉面试官例如哪个哪个部分是怎么怎么实现的，并针对这部分的源码实现，可以发表一些自己的看法和感想。

### 101. == 隐试转换的原理？是怎么转换的
> **两个与类型转换有关的函数：valueOf()和toString()** 
> - valueOf()的语义是，返回这个对象逻辑上对应的原始类型的值。比如说，String包装对象的valueOf()，应该返回这个对象所包装的字符串。
> - toString()的语义是，返回这个对象的字符串表示。用一个字符串来描述这个对象的内容。
> 
valueOf()和toString()是定义在Object.prototype上的方法，也就是说，所有的对象都会继承到这两个方法。但是在Object.prototype上定义的这两个方法往往不能满足我们的需求（Object.prototype.valueOf()仅仅返回对象本身），因此js的许多内置对象都重写了这两个函数，以实现更适合自身的功能需要（比如说，String.prototype.valueOf就覆盖了在Object.prototype中定义的valueOf）。当我们自定义对象的时候，最好也重写这个方法。重写这个方法时要遵循上面所说的语义。
>  
> **js内部用于实现类型转换的4个函数**
>  
> 这4个方法实际上是ECMAScript定义的4个抽象的操作，它们在js内部使用，进行类型转换。js的使用者不能直接调用这些函数。
>  
> - ToPrimitive ( input [ , PreferredType ] )
> - ToBoolean ( argument )
> - ToNumber ( argument )
> - ToString ( argument )
> 

> 需要区分这里的 ToString() 和上文谈到的 toString()，一个是 js 引擎内部使用的函数，另一个是定义在对象上的函数。
>  
> （1）ToPrimitive ( input [ , PreferredType ] )
>  
> 将 input 转化成一个原始类型的值。PreferredType参数要么不传入，要么是Number 或 String。**如果PreferredType参数是Number**，ToPrimitive这样执行：
>  
> 1. 如果input本身就是原始类型，直接返回input。
> 1. 调用**input.valueOf()**，如果结果是原始类型，则返回这个结果。
> 1. 调用**input.toString()**，如果结果是原始类型，则返回这个结果。
> 1. 抛出TypeError异常。
> 

> **以下是PreferredType不为Number时的执行顺序。**
>  
> - 如果PreferredType参数是String，则交换上面这个过程的第2和第3步的顺序，其他执行过程相同。
> - 如果PreferredType参数没有传入 
>    - 如果input是内置的Date类型，PreferredType 视为String
>    - 否则PreferredType 视为 Number
> 

> **可以看出，ToPrimitive依赖于valueOf和toString的实现。**
>  
> （2）ToBoolean ( argument )
> ![image.png](https://cdn.nlark.com/yuque/0/2021/png/758572/1638069365210-5a72d2c7-472f-4cca-9a9d-7486a90eac8f.png#clientId=ub7d735a1-a078-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=452&id=u956e7de5&margin=%5Bobject%20Object%5D&name=image.png&originHeight=904&originWidth=1462&originalType=binary&ratio=1&rotation=0&showTitle=false&size=272109&status=done&style=none&taskId=u8ec62db3-9697-4619-9675-b149513bbbe&title=&width=731)
> 
只需要记忆 0, null, undefined, NaN, "" 返回 false 就可以了，其他一律返回 true。
> （3）ToNumber ( argument )
> 
> ToNumber的转化并不总是成功，有时会转化成NaN，有时则直接抛出异常。
> （4）ToString ( argument )
> 
> 当js期望得到某种类型的值，而实际在那里的值是其他的类型，就会发生隐式类型转换。系统内部会自动调用我们前面说ToBoolean ( argument )、ToNumber ( argument )、ToString ( argument )，尝试转换成期望的数据类型。

### 102. ['1', '2', '3'].map(parseInt) 结果是什么，为什么 （字节）
> [1, NaN, NaN]

> 1. _map_ 函数
> 
将数组的每个元素传递给指定的函数处理，并返回处理后的数组，所以 _['1','2','3'].map(parseInt)_ 就是将字符串 _1，2，3_ 作为元素；_0，1，2_ 作为下标分别调用 _parseInt_ 函数。即分别求出 _parseInt('1',0), parseInt('2',1), parseInt('3',2)_ 的结果。
> 2. _parseInt_ 函数（重点）
> 
概念：以第二个参数为基数来解析第一个参数字符串，通常用来做十进制的向上取整（省略小数）如：parseInt(2.7) //结果为2
> 特点：接收两个参数 _parseInt(string,radix)_
> _string_：字母（大小写均可）、数组、特殊字符（不可放在开头,特殊字符及特殊字符后面的内容不做解析）的任意字符串，如 '2'、'2w'、'2!'
> _radix_：解析字符串的基数，基数规则如下：
> 1）   区间范围介于 _2~36_ 之间；
> 2 ）  当参数为 _0_，_parseInt( )_ 会根据十进制来解析；
> 3 ）  如果忽略该参数，默认的基数规则：
> 		如果 _string_ 以 "0x" 开头，parseInt() 会把 string 的其余部分解析为十六进制的整数；parseInt("0xf")   // 15
		如果 _string_ 以 0 开头，其后的字符解析为八进制或十六进制的数字；parseInt("08")   // 8
		如果 _string_ 以 1 ~ 9 的数字开头，parseInt() 将把它解析为十进制的整数；parseInt("88.99f")   // 88
		只有字符串中的第一个数字会被返回。parseInt("10.33")   // 返回10；
		开头和结尾的空格是允许的。parseInt(" 69 10 ")   // 返回69
		如果字符串的第一个字符不能被转换为数字，返回 NaN。parseInt("f")  // 返回 NaN  而 parseInt("f"，16)  // 返回15
>  
> 二、_parseInt_ 方法解析的运算过程
>  
> parseInt('101.55',10); // 以十进制解析，运算过程：向上取整数(不做四舍五入，省略小数)，结果为 101。
>  
> parseInt('101',2);  // 以二进制解析，运算过程：1_2的2次方+0_2的1次方+1*2的0次方=4+0+1=5，结果为 5。
>  
> parseInt('101',8);  // 以八进制解析，运算过程：1_8的2次方+0_8的1次方+1*8的0次方=64+0+1=65，结果为 65。
>  
> parseInt('101',16);  // 以十六进制解析，运算过程：1_16的2次方+0_16的1次方+1*16的0次方=256+0+1=257，结果为 257。
>  
> 三、再来分析一下结果
>  
> _['1','2','3'].map(parseInt)_ 即
>  
> parseInt('1',0); radix 为 0，parseInt( ) 会根据十进制来解析，所以结果为 _1_；
>  
> parseInt('2',1); radix 为 1，超出区间范围，所以结果为 _NaN_；
>  
> parseInt('3',2); radix 为 2，用2进制来解析，应以 _0_ 和 _1_ 开头，所以结果为 _NaN_


### 107. 情人节福利题，如何实现一个 _new_ （字节）

> 参考答案：
首先我们需要明白 _new_ 的原理。关于 _new_ 的原理，主要分为以下几步：
> -  创建一个空对象 。 
> -  由 _this_ 变量引用该对象 。 
> -  该对象继承该函数的原型(更改原型链的指向) 。 
> -  把属性和方法加入到 _this_ 引用的对象中。 
> -  新创建的对象由 _this_ 引用 ，最后**隐式地**返回 _this_ 

```javascript
// 构造器函数
let Parent = function (name, age) {
 this.name = name;
 this.age = age;
};
Parent.prototype.sayName = function () {
 console.log(this.name);
};
//自己定义的new方法
let newMethod = function (Parent, ...rest) {
 // 1.以构造器的prototype属性为原型，创建新对象；
 let child = Object.create(Parent.prototype);
 // 2.将this和调用参数传给构造器执行
 let result = Parent.apply(child, rest);
 // 3.如果构造器没有手动返回对象，则返回第一步的对象
 return typeof result === 'object' ? result : child;
};
//创建实例，将构造函数Parent与形参作为参数传入
const child = newMethod(Parent, 'echo', 26);
child.sayName() //'echo';
//最后检验，与使用new的效果相同
console.log(child instanceof Parent)//true
console.log(child.hasOwnProperty('name'))//true
console.log(child.hasOwnProperty('age'))//true
console.log(child.hasOwnProperty('sayName'))//false
```

### 108. 实现一个 _sleep_ 函数（字节）
> 这种实现方式是利用一个**伪死循环阻塞主线程**。因为 _JS_ 是单线程的。所以通过这种方式可以实现真正意义上的 _sleep_。

```javascript
function sleep(delay) {
 var start = (new Date()).getTime();
 while ((new Date()).getTime() - start < delay) {
     continue;
 }
}

function test() {
 console.log('111');
 sleep(2000);
 console.log('222');
}

test()
```

### 109. 使用 sort() 对数组 [3, 15, 8, 29, 102, 22] 进行排序，输出结果 （字节） 
> _sort_ 方法默认按照 _ASCII_ 码来排序，**如果要按照数字大小来排序，需要传入一个回调函数**，如下：

```javascript
[3, 15, 8, 29, 102, 22].sort((a,b) => {return a - b});
```

### 110. 实现 5.add(3).sub(2) (百度)

> 参考答案：
>  
> 这里想要实现的是链式操作，那么我们可以考虑在 _Number_ 类型的原型上添加 _add_ 和 _sub_ 方法，这两个方法返回新的数
>  
> 示例如下：
>  
>  

```javascript
Number.prototype.add = function (number) {
 if (typeof number !== 'number') {
     throw new Error('请输入数字～');
 }
 return this.valueOf() + number;
};
Number.prototype.minus = function (number) {
 if (typeof number !== 'number') {
     throw new Error('请输入数字～');
 }
 return this.valueOf() - number;
};
console.log((5).add(3).minus(2)); // 6
```

### 111. 给定两个数组，求交集
```javascript
const arr1 = [1, 2, 3]
const arr2 = [2, 3, 4]
const arr = []
arr2.forEach((ele) => {
    if (arr1.includes(ele)) {
        arr.push(ele)
    }
})
console.log(arr)
```
### 112. 为什么普通 _for_ 循环的性能远远高于 _forEach_ 的性能，请解释其中的原因。
> _for_ 循环按顺序遍历，_forEach_ 使用 _iterator_ 迭代器遍历
>  
>  在10万这个级别下，`forEach`的性能是`for`的十倍
>  在100万这个量级下，`forEach`的性能是和`for`的一致
>  在1000万级以上的量级上 ，`forEach`的性能远远低于`for`的性能
>  
> 我们从语法上面来观察：
>  
> 可以看到 _forEach_ 是有回调的，它会按升序为数组中含有效值的每一项执行一次 _callback_，且除了抛出异常以外，**也没有办法中止或者跳出 **_**forEach**_** 循**环。那这样的话执行**就会额外的调用栈和函数内的上下文**。
> **而 **_**for**_** 循环则是底层写法，不会产生额外的消耗。**
> 在实际业务中没有很大的数组时，_for_ 和 _forEach_ 的性能差距其实很小，_forEach_ 甚至会优于 _for_ 的时间，且更加简洁，可读性也更高，一般也会优先使用 _forEach_ 方法来进行数组的循环处理。

```javascript
let arrs = new Array(100000);
console.time('for');
for (let i = 0; i < arrs.length; i++) {
};
console.timeEnd('for');
console.time('forEach');
arrs.forEach((arr) => {
});
console.timeEnd('forEach');

for: 2.263ms
forEach: 0.254ms
```
```javascript
for: 2.263ms
forEach: 0.254ms
```
```javascript
for: 2.844ms
forEach: 2.652ms
```
```javascript
for: 8.422ms
forEach: 30.328m
```
```javascript
arr.forEach(callback(currentValue [, index [, array]])[, thisArg])
```

### 113. 实现一个字符串匹配算法，从长度为 n 的字符串 S 中，查找是否存在字符串 T，T 的长度是 m，若存在返回所在位置。
```javascript
// 完全不用 API
var getIndexOf = function (s, t) {
 let n = s.length;
 let m = t.length;
 if (!n || !m || n < m) return -1;
 for (let i = 0; i < n; i++) {
     let j = 0;
     let k = i;
     if (s[k] === t[j]) {
         k++; j++;
         while (k < n && j < m) {
             if (s[k] !== t[j]) break;
             else {
                 k++; j++;
             }
         }
         if (j === m) return i;
     }
 }
 return -1;
}

// 测试
console.log(getIndexOf("Hello World", "rl"))
```

### 114. 使用_ Proxy_ 实现简单的数据绑定

```html
<body>
  hello,world
  <input type="text" id="model">
  <p id="word"></p>
</body>
<script>
  const model = document.getElementById("model")
  const word = document.getElementById("word")
  var obj= {};
  
  const newObj = new Proxy(obj, {
    get: function(target, key, receiver) {
      console.log(`getting ${key}!`);
      return Reflect.get(target, key, receiver);
    },
    set: function(target, key, value, receiver) {
      console.log('setting',target, key, value, receiver);
      if (key === "text") {
        model.value = value;
        word.innerHTML = value;
      }
      return Reflect.set(target, key, value, receiver);
    }
  });
  
  model.addEventListener("keyup",function(e){
    newObj.text = e.target.value
  })
</script>
```

### 115. 数组里面有 _10_ 万个数据，取第一个元素和第 _10_ 万个元素的时间相差多少（字节）
> 消耗时间几乎一致，差异可以忽略不计 

> - 数组可以直接根据**索引**取的对应的元素，所以不管取哪个位置的元素的**时间复杂度都是 O(1)**
> - _**JavaScript**_** 没有真正意义上的数组，所有的数组其实是对象**，其“索引”看起来是数字，其实会被转换成字符串，作为属性名（对象的 _key_）来使用。所以无论是取第 _1_ 个还是取第 _10_ 万个元素，都是**用 **_**key**_** 精确查找哈希表的过程，**其消耗时间大致相同。

### 116. 打印出 _1~10000_ 以内的对称数
```javascript
function isSymmetryNum(start, end) {
 for (var i = start; i < end + 1; i++) {
     var iInversionNumber = +(i.toString().split("").reverse().join(""));
     if (iInversionNumber === i && i > 10) {
         console.log(i);
     }
 }
}
isSymmetryNum(1, 10000);
```

### 117. 简述同步和异步的区别
> **同步意味着每一个操作必须等待前一个操作完成后才能执行。
异步意味着操作不需要等待其他操作完成后才开始执行。**
在 _JavaScript_ 中，由于单线程的特性导致所有代码都是同步的。但是，有些异步操作（例如：`XMLHttpRequest` 或 `setTimeout`）并不是由主线程进行处理的，他们由本机代码（浏览器 API）所控制，并不属于程序的一部分。但程序中被执行的回调部分依旧是同步的。
> **加分回答：**
> - _JavaScript_ 中的同步任务是指在主线程上排队执行的任务，只有前一个任务执行完成后才能执行后一个任务；异步任务是指进入任务队列（_task queue_）而非主线程的任务，只有当任务队列通知主线程，某个异步任务可以执行了，该任务才会进入主线程中进行执行。
> - _JavaScript_ 的并发模型是基于** “**_**event loop**_**”。**
> - 像 `alert` 这样的方法回**阻塞主线程**，以致用户关闭他后才能继续进行后续的操作。
> - _JavaScript_ 主要用于和用户互动及操作 DOM，多线程的情况和异步操作带来的复杂性相比决定了他单线程的特性。
> - _**Web Worker**_** 虽然允许 **_**JavaScript**_** 创建多个线程，但子线程完全受主线程控制，且不能操作 **_**DOM**_**。因此他还是保持了单线程的特性。**


### 118. 怎么添加、移除、复制、创建、和查找节点
> 1）创建新节点
> _createDocumentFragment_( )  // 创建一个_DOM_ 片段
> _createElement_( )  // 创建一个具体的元素
> _createTextNode_( ) // 创建一个文本节点
> （2）添加、移除、替换、插入
> _appendChild_( )
> _removeChild_( )
> _replaceChild_( )
> _insertBefore_( ) // 在已有的子节点前插入一个新的子节点
> （3）查找
> _getElementsByTagName_( )  //通过标签名称
> _getElementsByName_( ) // 通过元素的 _Name_ 属性的值
> _getElementById_( ) // 通过元素 _Id_，唯一性
> _querySelector_( ) // 用于接收一个 _CSS_ 选择符，返回与该模式匹配的第一个元素
> _querySelectorAll_( ) // 用于选择匹配到的所有元素


### 119. 实现一个函数 _clone_ 可以对 _Javascript_ 中的五种主要数据类型（_Number、string、 Object、Array、Boolean_）进行复制
```javascript
/**
* 对象克隆
* 支持基本数据类型及对象
* 递归方法
*/
function clone(obj) {
    var o;
    switch (typeof obj) {
        case "undefined":
            break;
        case "string":
            o = obj + "";
            break;
        case "number":
            o = obj - 0;
            break;
        case "boolean":
            o = obj;
            break;
        case "object": // object 分为两种情况 对象（Object）或数组（Array）
            if (obj === null) {
                o = null;
            } else {
                if (Object.prototype.toString.call(obj).slice(8, -1) === "Array") {
                    o = [];
                    for (var i = 0; i < obj.length; i++) {
                        o.push(clone(obj[i]));
                    }
                } else {
                    o = {};
                    for (var k in obj) {
                        o[k] = clone(obj[k]);
                    }
                }
            }
            break;
        default:
            o = obj;
            break;
    }
    return o;
}
```

### 121. 写一个返回闭包的函数 
```javascript
function foo() {
 var i = 0;
 return function () {
     console.log(i++);
 }
}
var f1 = foo();
f1(); // 0
f1(); // 1
f1(); // 2
```
### 122. 使用递归完成 1 到 100 的累加 
```javascript
function add(x, y){
 if(x === y){
     return x;
 } else {
     return y + add(x, y-1);
 }
}

console.log(add(1, 100))
```
### 129. 说说严格模式的限制
> 什么是严格模式？
> 严格模式对 _JavaScript_ 的语法和行为都做了一些更改，消除了语言中一些不合理、不确定、不安全之处；提供高效严谨的差错机制，保证代码安全运行；禁用在未来版本中可能使用的语法，为新版本做好铺垫。在脚本文件第一行或函数内第一行中引入"use strict"这条指令，就能触发严格模式，这是一条没有副作用的指令，老版的浏览器会将其作为一行字符串直接忽略。
>  
> 进入严格模式后的限制 
> - 变量必须声明后再赋值
> - 不能有重复的参数名，函数的参数也不能有同名属性
> - 不能使用_with_语句
> - 不能对只读属性赋值
> - 不能使用前缀  _0_表示八进制数
> - 不能删除不可删除的属性
> - _eval_ 不会在它的外层作用域引入变量。
> - _eval_和_arguments_不能被重新赋值
> - _arguments_ 不会自动反应函数的变化
> - 不能使用 _arguments.callee_
> - 不能使用 _arguments.caller_
> - 禁止 _this_ 指向全局对象
> - 不能使用 _fn.caller_ 和 _fn.arguments_ 获取函数调用的堆栈
> - 增加了保留字


### 130. _attribute_ 和 _property_ 的区别是什么？
> property 和 attribute 非常容易混淆，两个单词的中文翻译也都非常相近（property：属性，attribute：特性），但实际上，二者是不同的东西，属于不同的范畴。
>  
> - **property是DOM中的属性，是JavaScript里的对象；**
> - **attribute是HTML标签上的特性，它的值只能够是字符串；**
> 

> 简单理解，Attribute就是dom节点自带的属性，例如html中常用的id、class、title、align等。
> 而Property是这个DOM元素作为对象，其附加的内容，例如childNodes、firstChild等。


### 131. _ES6_ 能写 _class_ 么，为什么会出现 _class_ 这种东西?
告别了直接使用原型对象模仿面向对象中的类和类继承时代。 
> 但是 _JS_ 中并没有一个真正的 _class_ 原始类型， _class_ 仅仅只是对原型对象运用语法糖。
> 之所以出现 _class_ 关键字，是为了使** **_**JS**_** 更像面向对象**，所以 _ES6_ 才引入 _class_ 的概念。

### 135. 为什么 _console.log(0.2+0.1==0.3)  // false_
> **浮点数不能够进行精确的计算**。并且： 
> - 不仅 _JavaScript_，所有遵循 _IEEE 754_ 规范的语言都是如此；
> - **在 **_**JavaScript**_** 中，所有的 **_**Number**_** 都是以 **_**64-bit**_** 的双精度浮点数存储的；**
> - 双精度的浮点数在这 _64_ 位上划分为 _3_ 段，而这 _3_ 段也就确定了一个浮点数的值，_64bit_ 的划分是“_1-11-52_”的模式，具体来说： 
>    - 就是 _1_ 位最高位（最左边那一位）表示符号位，_0_ 表示正，_1_ 表示负；
>    - _11_ 位表示指数部分；
>    - _52_ 位表示尾数部分，也就是有效域部分

### 137. 深拷贝和浅拷贝的区别？如何实现
> -  **浅拷贝**：只是拷贝了基本类型的数据，而引用类型数据，复制后也是会发生引用，我们把这种拷贝叫做浅拷贝（浅复制）
浅拷贝只复制指向某个对象的指针，而不复制对象本身，新旧对象还是共享同一块内存。 
> -  **深拷贝**：在堆中重新分配内存，并且把源对象所有属性都进行新建拷贝，以保证深拷贝的对象的引用图不包含任何原有对象或对象图上的任何对象，拷贝后的对象与原来的对象是完全隔离，互不影响。 
> 
**浅拷贝方法**
> 1. 直接赋值
> 1. _Object.assign_ 方法：可以把任意多个的源对象自身的可枚举属性拷贝给目标对象，然后返回目标对象。当拷贝的 _object_ 只有一层的时候，是深拷贝，但是当拷贝的对象属性值又是一个引用时，换句话说有多层时，就是一个浅拷贝。
> 1. _ES6_ 扩展运算符，当 _object_ 只有一层的时候，也是深拷贝。有多层时是浅拷贝。
> 1. _Array.prototype.concat_ 方法
> 1. _Array.prototype.slice_ 方法
> 1. _jQuery_ 中的 ![](https://g.yuque.com/gr/latex?.extend*%EF%BC%9A%E5%9C%A8%20*jQuery*%20%E4%B8%AD%EF%BC%8C*#card=math&code=.extend%2A%EF%BC%9A%E5%9C%A8%20%2AjQuery%2A%20%E4%B8%AD%EF%BC%8C%2A&id=TtpvW)_.extend(deep,target,object1,objectN)_ 方法可以进行深浅拷贝。_deep_ 如过设为 _true_ 为深拷贝，默认是 _false_ 浅拷贝。
> 

> **深拷贝方法**
>  
> 1. _$.extend(deep,target,object1,objectN)_，将 _deep_ 设置为 _true_
> 1. _JSON.parse(JSON.stringify)_：用 _JSON.stringify_ 将对象转成 _JSON_ 字符串，再用 _JSON.parse_ 方法把字符串解析成对象，一去一来，新的对象产生了，而且对象会开辟新的栈，实现深拷贝。这种方法虽然可以实现数组或对象深拷贝，但不能处理函数。
> 1. 手写递归

### 140. 为什么会出现 _setTimeout_ 倒计时误差？如何减少
> 定时器是属于宏任务(_macrotask_) 。如果**当前执行栈所花费的时间大于定时器时间，那么定时器的回调在宏任务(**_**macrotask**_**) 里，来不及去调用，**所有这个时间会有误差。

### 143. _prototype_ 和 __*proto*__ 区别是什么？
> _prototype_ 是构造函数上面的一个属性，指向实例化出来对象的原型对象。
> __*proto*__ 是对象上面的一个隐式属性，指向自己的原型对象

### 145. 取数组的最大值（_ES5、ES6_）
```javascript
var arr = [3, 5, 8, 1];
// ES5 方式
console.log(Math.max.apply(null, arr)); // 8
// ES6 方式
console.log(Math.max(...arr)); // 8
```

### 
### _Promise_ 有什么优缺点 ?
> _Promise_ 的优点是解决了回调地狱，缺点是代码并没有因为新方法的出现而减少，反而变得更加复杂，同时理解难度也加大。所以后面出现了 _async/await_ 的异步解决方案。

### 152. 如何判断 _img_ 加载完成
>  
> - 为 _img DOM_ 节点绑定 _load_ 事件
> - _readystatechange_ 事件：_readyState_ 为 _complete_ 和 _loaded_ 则表明图片已经加载完毕。测试 _IE6-IE10_ 支持该事件，其它浏览器不支持。
> - _img_ 的 _complete_ 属性：**轮询不断监测 **_**img**_** 的 **_**complete**_** 属性**，如果为 _true_ 则表明图片已经加载完毕，停止轮询。该属性所有浏览器都支持。


### 155. 如何用原生 _js_ 给一个按钮绑定两个 _onclick_ 事件？
> 使用 _addEventListener_ 方法来绑定事件，就可以绑定多个同种类型的事件。

### 156. 拖拽会用到哪些事件 
> 在以前，书写一个拖拽需要用到 _mousedown、mousemove、mouseup_ 这 _3_ 个事件。
> _HTML5_ 推出后，新推出了一组拖拽相关的 _API_，涉及到的事件有 _dragstart、dragover、drop_ 这 _3_ 个事件

### 157. _document.write_ 和 _innerHTML_ 的区别
> _document.write_ 是**直接写入到页面的内容流**，如果在写之前没有调用 _document.open_,  浏览器会自动调用 _open_。每次写完关闭之后重新调用该函数，**会导致页面全部重绘。**
> _innerHTML_ 则是 _DOM_ 页面元素的一个属性，代表该元素的 _html_ 内容。你可以精确到某一个具体的元素来进行更改。如果想修改 _document_ 的内容，则需要修改 _document.documentElement.innerElement_。
> _**innerHTML**_** 很多情况下都优于 **_**document.write**_**，其原因在于不会导致页面全部重绘。**

### 158. _jQuery_ 的事件委托方法 _bind 、live、delegate、one、on_ 之间有什么区别？

> 这几个方法都可以实现事件处理。其中 _on_ 集成了事件处理的所有功能，也是目前推荐使用的方法。
> _one_ 是指添加的是一次性事件，意味着只要触发一次该事件，相应的处理方法执行后就自动被删除。
> _bind_ 是较早版本的绑定事件的方法，现在已被 _on_ 替代。
> _live_ 和 _delegate_ 主要用来做事件委托。_live_ 的版本较早，现在已被废弃。_delegate_ 目前仍然可用，不过也可用 _on_ 来替代它

### 159. _$(document).ready_ 方法和 _window.onload_ 有什么区别？
> 主要有两点区别 
> 1. 执行时机
> 
_window.onload_ 方法是在网页中的所有的元素（包括元素的所有关联文件）都完全加载到浏览器之后才执行。而通过 _jQuery_ 中的`$(document).ready`方法注册的事件处理程序，只要在 _DOM_ 完全就绪时，就可以调用了，比如一张图片只要`<img>`标签完成，不用等这个图片加载完成，就可以设置图片的宽高的属性或样式等。
> _**onload**_** 即加载完成，**_**ready**_** 即 **_**DOM**_** 准备就绪。**
> 2. 注册事件
> 
`$(document).ready`方法可以多次使用而注册不同的事件处理程序，而 _window.onload_ 一次只能保存对一个函数的引用，多次绑定函数只会覆盖前面的函数。

### 160. jquery 中![](https://g.yuque.com/gr/latex?.get()%E6%8F%90%E4%BA%A4%E5%92%8C#card=math&code=.get%28%29%E6%8F%90%E4%BA%A4%E5%92%8C&id=Ad3s5).post()提交有区别吗？ 
> 相同点：都是异步请求的方式来获取服务端的数据
> 不同点：
> - 请求方式不同：`$.get()` 方法使用 _GET_ 方法来进行异步请求的。`$.post()` 方法使用 _POST_ 方法来进行异步请求的。
> - 参数传递方式不同： _GET_ 请求会将参数跟在 _URL_ 后进行传递，而 _POST_ 请求则是作为 _HTTP_ 消息的实体内容发送给 _Web_ 服务器 的，这种传递是对用户不可见的。
> - 数据传输大小不同： _GET_ 方式传输的数据大小不能超过 _2KB_ 而 _POST_ 要大的多
> - 安全问题： _GET_ 方式请求的数据会被浏览器缓存起来，因此有安全问题。


### 161. _await async_ 如何实现 （阿里）
> **async 函数只是 promise 的语法糖，它的底层实际使用的是 generator**，而 generator 又是基于 promise 的。实际上，在 babel 编译 async 函数的时候，也会转化成 generator函数，并使用自动执行器来执行它。
>  关于代码的解析，可以参阅：[_https://blog.csdn.net/xgangzai/article/details/106536325_](https://blog.csdn.net/xgangzai/article/details/106536325)

```javascript
function asyncToGenerator(generatorFunc) {
 return function() {
   const gen = generatorFunc.apply(this, arguments)
   return new Promise((resolve, reject) => {
     function step(key, arg) {
       let generatorResult
       try {
         generatorResult = gen[key](arg)
       } catch (error) {
         return reject(error)
       }
       const { value, done } = generatorResult
       if (done) {
         return resolve(value)
       } else {
         return Promise.resolve(value).then(val => step('next', val), err => step('throw', err))
       }
     }
     step("next")
   })
 }
}
```

### 162. _clientWidth,offsetWidth,scrollWidth_ 的区别
> _clientWidth_ = _width_+左右 _padding_
> _offsetWidth_ = _width_ + 左右 _padding_ + 左右 _boder_
> _scrollWidth_：获取指定标签内容层的真实宽度(可视区域宽度+被隐藏区域宽度)。

### 163. 产生一个不重复的随机数组
> 在上面的代码中，我们封装了一个 _randomArr_ 方法来生成这个不重复的随机数组，该方法接收三个参数，_len、min_ 和 _max_，分别表示数组的长度、最小值和最大值。_randomNumBoth_ 方法用来生成随机数。

```javascript
// 生成随机数
function randomNumBoth(Min, Max) {
    return Min + Math.round(Math.random() * (Max - Min)); //四舍五入
}
// 生成数组
function randomArr(len, min, max) {
    if ((max - min) < len) { //可生成数的范围小于数组长度
        return null;
    }
    var hash = [];
    while (hash.length < len) {
        var num = randomNumBoth(min, max);

        if (hash.indexOf(num) == -1) {
            hash.push(num);
        }
    }
    return hash;
}
// 测试
console.log(randomArr(10, 1, 100));
```


### 165. 如何在 _jquery_ 上扩展插件，以及内部原理（腾讯）
> 通过 _$.extend(object);_ 为整个 _jQuery_ 类添加新的方法。
>  通过 _$.fn.extend(object);_ 给 _jQuery_ 对象添加方法。
> **_extend_ 方法内部原理**
>  对后一个参数进行循环，然后把后面参数上所有的字段都给了第一个字段，若第一个参数里有相同的字段，则进行覆盖操作，否则就添加一个新的字段。

```javascript
$.extend({
	 sayHello: function(name) {
      console.log('Hello,' + (name ? name : 'World') + '!');
  },
  showAge(){
      console.log(18);
  }
})

// 外部使用
$.sayHello(); // Hello,World!  无参调用
$.sayHello('zhangsan'); // Hello,zhangsan! 带参调用
```
```javascript
$.fn.extend({
 swiper: function (options) {
     var obj = new Swiper(options, this); // 实例化 Swiper 对象
     obj.init(); // 调用对象的 init 方法
 }
})

// 外部使用
$('#id').swiper();
```
```javascript
jQuery.extend( target [, object1 ] [, objectN ] )
```
```javascript
// 为与源码的下标对应上，我们把第一个参数称为第0个参数，依次类推
jQuery.extend = jQuery.fn.extend = function() {
 var options, name, src, copy, copyIsArray, clone,
     target = arguments[0] || {}, // 默认第0个参数为目标参数
     i = 1,    // i表示从第几个参数凯斯想目标参数进行合并，默认从第1个参数开始向第0个参数进行合并
     length = arguments.length,
     deep = false;  // 默认为浅度拷贝

 // 判断第0个参数的类型，若第0个参数是boolean类型，则获取其为true还是false
 // 同时将第1个参数作为目标参数，i从当前目标参数的下一个
 // Handle a deep copy situation
 if ( typeof target === "boolean" ) {
     deep = target;

     // Skip the boolean and the target
     target = arguments[ i ] || {};
     i++;
 }

 //  判断目标参数的类型，若目标参数既不是object类型，也不是function类型，则为目标参数重新赋值 
 // Handle case when target is a string or something (possible in deep copy)
 if ( typeof target !== "object" && !jQuery.isFunction(target) ) {
     target = {};
 }

 // 若目标参数后面没有参数了，如$.extend({_name:'wenzi'}), $.extend(true, {_name:'wenzi'})
 // 则目标参数即为jQuery本身，而target表示的参数不再为目标参数
 // Extend jQuery itself if only one argument is passed
 if ( i === length ) {
     target = this;
     i--;
 }

 // 从第i个参数开始
 for ( ; i < length; i++ ) {
     // 获取第i个参数，且该参数不为null，
     // 比如$.extend(target, {}, null);中的第2个参数null是不参与合并的
     // Only deal with non-null/undefined values
     if ( (options = arguments[ i ]) != null ) {

         // 使用for~in获取该参数中所有的字段
         // Extend the base object
         for ( name in options ) {
             src = target[ name ];   // 目标参数中name字段的值
             copy = options[ name ]; // 当前参数中name字段的值

             // 若参数中字段的值就是目标参数，停止赋值，进行下一个字段的赋值
             // 这是为了防止无限的循环嵌套，我们把这个称为，在下面进行比较详细的讲解
             // Prevent never-ending loop
             if ( target === copy ) {
                 continue;
             }

             // 若deep为true，且当前参数中name字段的值存在且为object类型或Array类型，则进行深度赋值
             // Recurse if we're merging plain objects or arrays
             if ( deep && copy && ( jQuery.isPlainObject(copy) || (copyIsArray = jQuery.isArray(copy)) ) ) {
                 // 若当前参数中name字段的值为Array类型
                 // 判断目标参数中name字段的值是否存在，若存在则使用原来的，否则进行初始化
                 if ( copyIsArray ) {
                     copyIsArray = false;
                     clone = src && jQuery.isArray(src) ? src : [];

                 } else {
                     // 若原对象存在，则直接进行使用，而不是创建
                     clone = src && jQuery.isPlainObject(src) ? src : {};
                 }

                 // 递归处理，此处为2.2
                 // Never move original objects, clone them                      
                 target[ name ] = jQuery.extend( deep, clone, copy );

             // deep为false，则表示浅度拷贝，直接进行赋值
             // 若copy是简单的类型且存在值，则直接进行赋值
             // Don't bring in undefined values
             } else if ( copy !== undefined ) {
                 // 若原对象存在name属性，则直接覆盖掉；若不存在，则创建新的属性
                 target[ name ] = copy;
             }
         }
     }
 }

 // 返回修改后的目标参数
 // Return the modified object
 return target;
};
```
### 172. _js_ 有函数重载吗（网易）
> 所谓函数重载，是方法名称进行重用的一种技术形式，其主要特点是“方法名相同，参数的类型或个数不相同”，在调用时会根据传递的参数类型和个数的不同来执行不同的方法体。
> **在 **_**JS**_** 中，可以通过在函数内容判断形参的类型或个数来执行不同的代码块，从而达到模拟函数重载的效果。**

### 173. 给你一个数组，计算每个数出现的次数，如果每个数组返回的数都是独一无二的就返回  _true_  相反则返回的 _flase_
> 输入：arr = [1,2,2,1,1,3]
> 输出：true 
> 解释：在该数组中，1 出现了 3 次，2 出现了 2 次，3 只出现了 1 次。没有两个数的出现次数相同。

```javascript
function uniqueOccurrences(arr) {
 let uniqueArr = [...new Set(arr)]
 let countArr = []
 for (let i = 0; i < uniqueArr.length; i++) {
     countArr.push(arr.filter(item => item == uniqueArr[i]).length)
 }
 return countArr.length == new Set(countArr).size
};

// 测试
console.log(uniqueOccurrences([1, 2, 2, 1, 1, 3])); // true
console.log(uniqueOccurrences([1, 2, 2, 1, 1, 3, 2])); // false
```

### 174. 封装一个能够统计重复的字符的函数，例如  _aaabbbdddddfff_  转化为 _3a3b5d3f_
```javascript
function compression(str) {
 if (str.length == 0) {
     return 0;
 }
 var len = str.length;
 var str2 = "";
 var i = 0;
 var num = 1;
 while (i < len) {
     if (str.charAt(i) == str.charAt(i + 1)) {
         num++;
     } else {
         str2 += num;
         str2 += str.charAt(i);
         num = 1;
     }
     i++;
 }
 return str2;
}
// 测试：
console.log(compression('aaabbbdddddfff')); // 3a3b5d3f
```

### 175. 写出代码的执行结果

```javascript
function a() {
    console.log(1);
}
(function() {
    if (false) {
        function a() {
            console.log(2);
        }
    }
    console.log(typeof a); 
    a(); 
})()
```

> 会报错，_a is not a function_。
> 因为立即执行函数里面有函数 _a_，_a_ 会被提升到该函数作用域的最顶端，但是由于判断条件是 _false_，所以不会进入到条件语句里面， _a_ 也就没有值。所以 _typeof_ 打印出来是 _undefined_。而后面在尝试调用方法，自然就会报错。

### 178. _javascript_ 中什么是伪数组？如何将伪数组转换为标准数组 
var arr = [...arguments];
### 179. _array_ 和 _object_ 的区别
> 数组表示有序数据的集合，对象表示无序数据的集合

### 180. _jquery_ 事件委托
> 在 _jquery_ 中使用 _on_ 来绑定事件的时候，传入第二个参数即可。例如：

```javascript
$("ul").on("click","li",function () {
alert(1);
})
```

### 182. 请实现一个模块 _math_，支持链式调用`math.add(2,4).minus(3).times(2);`
```javascript
class Math {
 constructor(value) {
     let hasInitValue = true;
     if (value === undefined) {
         value = NaN;
         hasInitValue = false;
     }
     Object.defineProperties(this, {
         value: {
             enumerable: true,
             value: value,
         },
         hasInitValue: {
             enumerable: false,
             value: hasInitValue,
         },
     });
 }

 add(...args) {
     const init = this.hasInitValue ? this.value : args.shift();
     const value = args.reduce((pv, cv) => pv + cv, init);
     return new Math(value);
 }

 minus(...args) {
     const init = this.hasInitValue ? this.value : args.shift();
     const value = args.reduce((pv, cv) => pv - cv, init);
     return new Math(value);
 }

 times(...args) {
     const init = this.hasInitValue ? this.value : args.shift();
     const value = args.reduce((pv, cv) => pv * cv, init);
     return new Math(value);
 }

 divide(...args) {
     const init = this.hasInitValue ? this.value : args.shift();
     const value = args.reduce((pv, cv) => pv / cv, init);
     return new Math(value);
 }

 toJSON() {
     return this.valueOf();
 }

 toString() {
     return String(this.valueOf());
 }

 valueOf() {
     return this.value;
 }

 [Symbol.toPrimitive](hint) {
     const value = this.value;
     if (hint === 'string') {
         return String(value);
     } else {
         return value;
     }
 }
}

export default new Math();
```

### 183. 请简述 _ES6_ 代码转成 _ES5_ 代码的实现思路。
> _**Babel**_
> - **将代码字符串解析成抽象语法树，即所谓的 **_**AST**_
> - **对 **_**AST**_** 进行处理，在这个阶段可以对 **_**ES6**_** 代码进行相应转换，即转成 **_**ES5**_** 代码**
> - **根据处理后的 **_**AST**_** 再生成代码字符串**

### 184. 下列代码的执行结果

```javascript
async function async1() {
    console.log('async1 start');
    await async2();//立即执行
    console.log('async1 end');
}
async function async2() {
    console.log('async2');
}
console.log('script start');
setTimeout(function () {
    console.log('setTimeout');
}, 0);
async1();
new Promise(function (resolve) {
    console.log('promise1');
    resolve();
}).then(function () {
    console.log('promise2');
});
console.log('script end');
```
### 185. _JS_ 有哪些内置对象？
> 数据封装类对象：_String，Boolean，Number，Array_ 和 _Object_
> 其他对象：_Function，Arguments，Math，Date，RegExp，Erro_

### 187. _eval_ 是做什么的？

> 此函数可以接受一个字符串 _str_ 作为参数，并把此 _str_ 当做一段 _javascript_ 代码去执行，如果 _str_ 执行结果是一个值则返回此值，否则返回 _undefined_。如果参数不是一个字符串，则直接返回该参数。

```javascript
eval("var a=1");//声明一个变量a并赋值1。
eval("2+3");//5执行加运算，并返回运算值。
eval("mytest()");//执行mytest()函数。
eval("{b:2}");//声明一个对象。
```
### 190. 去除字符串中的空格
> 方法一：_replace_正则匹配方法
> - 去除字符串内所有的空格：`str = str.replace(/\s*/g,"");`
> - 去除字符串内两头的空格：`str = str.replace(/^\s*|\s*$/g,"");`
> - 去除字符串内左侧的空格：`str = str.replace(/^\s*/,"");`
> - 去除字符串内右侧的空格：`str = str.replace(/(\s*$)/g,"");`
> 
方法二：字符串原生 _trim_ 方法
> _trim_ 方法能够去掉两侧空格返回新的字符串，不能去掉中间的空格

### 191. 常见的内存泄露，以及解决方案
> **内存泄露概念**
> 内存泄漏指由于疏忽或错误造成程序**未能释放已经不再使用的内存**。内存泄漏**并非指内存在物理上的消失**，而是应用程序分配某段内存后，由于设计错误，导致在释放该段内存之前就失去了对该段内存的控制，从而造成了内存的浪费。
> 内存泄漏通常情况下只能由获得程序源代码和程序员才能分析出来。然而，有不少人习惯于把任何不需要的内存使用的增加描述为内存泄漏，即使严格意义上来说这是不准确的。
> **_JS_ 垃圾收集机制**
> _JS_ 具有自动回收垃圾的机制，即执行环境会负责管理程序执行中使用的内存。在C和C++等其他语言中，开发者的需要手动跟踪管理内存的使用情况。在编写 _JS_ 代码的时候，开发人员不用再关心内存使用的问题，所需内存的分配 以及无用的回收完全实现了自动管理。
> Js中最常用的垃圾收集方式是标记清除(mark-and-sweep)。当变量进入环境（例如，在函数中声明一个变量）时，就将这个变量标记为“进入环境”。从逻辑上讲，永远不能释放进入环境的变量所占的内存，因为只要执行流进入相应的环境，就可能用到它们。而当变量离开环境时，这将其 标记为“离开环境”。
> **常见内存泄漏以及解决方案** 
> 1. 意外的全局变量
> 
Js处理未定义变量的方式比较宽松：未定义的变量会在全局对象创建一个新变量。在浏览器中，全局对象是window。
> 解决方法：在 JavaScript 程序中添加，开启严格模式'use strict'，可以有效地避免上述问题。
>  
> 注意：那些用来临时存储大量数据的全局变量，确保在处理完这些数据后将其设置为null或重新赋值。与全局变量相关的增加内存消耗的一个主因是缓存。缓存数据是为了重用，缓存必须有一个大小上限才有用。高内存消耗导致缓存突破上限，因为缓 存内容无法被回收。
>  
> 2. 循环引用
> 

> 在js的内存管理环境中，对象 A 如果有访问对象 B 的权限，叫做对象 A 引用对象 B。引用计数的策略是将“对象是否不再需要”简化成“对象有没有其他对象引用到它”，如果没有对象引用这个对象，那么这个对象将会被回收 。
>  
>  
> 但是引用计数有个最大的问题： 循环引用。
>  
>  
> 当函数 func 执行结束后，返回值为 undefined，所以整个函数以及内部的变量都应该被回收，但根据引用计数方法，obj1 和 obj2 的引用次数都不为 0，所以他们不会被回收。要解决循环引用的问题，最好是在不使用它们的时候手工将它们设为空。上面的例子可以这么做：
>  
>  
> 3. 被遗忘的计时器和回调函数
> 

>  
> 上面的例子中，我们每隔一秒就将得到的数据放入到文档节点中去。
>  
> 但在 _setInterval_ 没有结束前，回调函数里的变量以及回调函数本身都无法被回收。那什么才叫结束呢？
>  
> 就是调用了 _clearInterval_。如果回调函数内没有做什么事情，并且也没有被 _clear_ 掉的话，就会造成内存泄漏。
>  
> 不仅如此，如果回调函数没有被回收，那么回调函数内依赖的变量也没法被回收。上面的例子中，_someResource_ 就没法被回收。同样的，_setTiemout_ 也会有同样的问题。所以，当不需要 _interval_ 或者 _timeout_ 时，最好调用 _clearInterval_ 或者 _clearTimeout_。
>  
> 4. _DOM_ 泄漏
> 

> 在 _JS_ 中对_DOM_操作是非常耗时的。因为_JavaScript/ECMAScript_引擎独立于渲染引擎，而_DOM_是位于渲染引擎，相互访问需要消耗一定的资源。  而 _IE_ 的 _DOM_ 回收机制便是采用引用计数的，以下主要针对 _IE_ 而言的。
>  
> **a. 没有清理的 DOM 元素引用**
> 解决办法：_refA = null;_
> **b. 给 DOM 对象添加的属性是一个对象的引用**
>  解决方法：
在 _window.onunload_ 事件中写上: _document.getElementById('mydiv').myProp = null;_
>  
> **c. DOM 对象与 JS 对象相互引用**
>  
>  
> 解决方法： 在 onunload 事件中写上: document.getElementById('myDiv').myProp = null;
>  
> **d. 给 DOM 对象用 attachEvent 绑定事件**
>  
>  
> 解决方法： 在onunload事件中写上: element.detachEvent('onclick', doClick);
>  
> **e. 从外到内执行 appendChild。这时即使调用 removeChild 也无法释放**
>  
>  
> 解决方法： 从内到外执行 appendChild:
>  
>  
> 5. _JS_ 的闭包
> 

> 闭包在 _IE6_ 下会造成内存泄漏，但是现在已经无须考虑了。值得注意的是闭包本身不会造成内存泄漏，但闭包过多很容易导致内存泄漏。闭包会造成对象引用的生命周期脱离当前函数的上下文，如果闭包如果使用不当，可以导致环形引用（_circular reference_），类似于死锁，只能避免，无法发生之后解决，即使有垃圾回收也还是会内存泄露。
>  
> 6. _console_
> 

> 控制台日志记录对总体内存配置文件的影响可能是许多开发人员都未想到的极其重大的问题。记录错误的对象可以将大量数据保留在内存中。注意，这也适用于：
>  
> (1) 在用户键入 JavaScript 时，在控制台中的一个交互式会话期间记录的对象。
(2) 由 console.log 和 console.dir 方法记录的对象。

```javascript
function foo(arg) { 
    bar = "this is a hidden global variable"; //等同于window.bar="this is a hidden global variable"
    this.bar2= "potential accidental global";//这里的this 指向了全局对象（window）,等同于window.bar2="potential accidental global"
}
```
```javascript
let obj1 = { a: 1 }; // 一个对象（称之为 A）被创建，赋值给 obj1，A 的引用个数为 1   
let obj2 = obj1; // A 的引用个数变为 2  

obj1 = 0; // A 的引用个数变为 1  
obj2 = 0; // A 的引用个数变为 0，此时对象 A 就可以被垃圾回收了
```
```javascript
function func() {  
    let obj1 = {};  
    let obj2 = {};  

    obj1.a = obj2; // obj1 引用 obj2  
    obj2.a = obj1; // obj2 引用 obj1  

}
```
```javascript
obj1 = null;  
obj2 = null;
```
```javascript
let someResource = getData();  
setInterval(() => {  
    const node = document.getElementById('Node');  
    if(node) {  
        node.innerhtml = JSON.stringify(someResource));  
    }  
}, 1000);
```
```javascript
var refA = document.getElementById('refA');
document.body.removeChild(refA);
// refA 不能回收，因为存在变量 refA 对它的引用。将其对 refA 引用释放，但还是无法回收 refA。
```
```javascript
var MyObject = {}; 
document.getElementById('mydiv').myProp = MyObject;
```
```javascript
function Encapsulator(element) { 
	this.elementReference = element; 
	element.myProp = this; 
} 
new Encapsulator(document.getElementById('myDiv'));
```
```javascript
function doClick() {} 
element.attachEvent("onclick", doClick);
```
```javascript
var parentDiv = document.createElement("div"); 
var childDiv = document.createElement("div"); 
document.body.appendChild(parentDiv); 
parentDiv.appendChild(childDiv);
```
```javascript
var parentDiv = document.createElement("div"); 
var childDiv = document.createElement("div"); 
parentDiv.appendChild(childDiv); 
document.body.appendChild(parentDiv);
```
