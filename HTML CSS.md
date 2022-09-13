#### 1. 什么是 <!DOCTYPE>？是否需要在 _HTML5_ 中使用？ 
> 它是 _HTML_ 的文档声明，通过它告诉浏览器，使用哪一个 _HTML_ 版本标准解析文档。
> 而文档声明有多种书写格式，对应不同的 _HTML_ 版本，<!DOCTYPE> 这种书写是告诉浏览器，_HTML5_ 的标准进行解析。

#### 2. 什么是可替换元素，什么是非可替换元素，它们各自有什么特点？
>  可替换元素是指这样一种元素，它在页面中的大部分展现效果不由 _CSS_ 决定。
> 比如 _img_ 元素就是一个可替换元素，它在页面中显示出的效果主要取决于你连接的是什么图片，图片是什么它就展示什么，_**CSS**_** 虽然可以控制图片的尺寸位置，但永远无法控制图片本身**。
> 再比如，_**select**_** 元素也是一个典型的可替换元素**，它在页面上呈现的是用户操作系统上的下拉列表样式，因此，它的展现效果是由操作系统决定的。所以，同一个 _select_ 元素，放到不同操作系统的电脑上会呈现不同的外观。
> _**img、video、audio**_**、大部分表单元素都属于可替换元素。**
> **非可替换元素就是指的普通元素，它具体在页面上呈现什么，完全由 **_**CSS**_** 来决定。**

#### 3. _src_ 和 _href_ 的区别（京东） 
> _src_ 是 _source_ 的缩写，它通常用于 _img、video、audio、script_ 元素，通过 _src_ 属性，可以指定外部资源的来源地址
> _href_ 是 _hyper reference_ 的缩写，意味「**超引用**」，它通常用于 _a、link_ 元素，通过 _href_ 属性，可以标识文档中引用的其他超文本。

#### 4. 说说常用的 _meta_ 标签 
> _meta_ 标签提供关于HTML文档的元数据。元数据**不会显示在页面上**，但是对于**机器是可读的。它可用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他 **_**web**_** 服务。**
> 1. _content_ ，设置或返回 _meta_ 元素的 _content_ 属性的值 。
> 1. _http-equiv_，把 _content_ 属性连接到一个 _HTTP_ 头部。
> 1. _name_，把 _content_ 属性连接到某个名称。

```html
<meta charset="UTF-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
#### 5. 说说对 _html_ 语义化的理解 
> - 用正确的标签做正确的事情！
> - _html_ 语义化就是让页面的内容结构化，**便于对浏览器、搜索引擎解析；**
> - 搜索引擎的爬虫依赖于标记来确定上下文和各个关键字的权重，**利于 **_**SEO**_**。**
> - **便于阅读维护理解**

#### 6. _label_ 的作用是什么？是怎么用的？ 
> 如果您在 _label_ 元素内点击文本，就会触发此控件。
> 就是说，当用户选择该标签时，浏览器就会自动将焦点转到和标签相关的表单控件上。 

> 最常用 _label_ 标签的地方，应该就是表单中选择性别的单选框了。

#### 7. _iframe_ 框架有那些优缺点？ 
> - _iframe_ 会**阻塞主页面的 **_**Onload**_** 事件；**
> - _**iframe**_** 和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。**
> - 使用 _iframe_ 之前需要考虑这两个缺点。如果需要使用 _iframe_，最好是通过 _**javascript**_** 动态给 **_**iframe**_** 添加 **_**src**_** 属性值**，这样可以可以绕开以上两个问题。

#### 8. _HTML_ 与 _XHTML_ 二者有什么区别，你觉得应该使用哪一个并说出理由。 不同于XML
> **关于功能上的差别**，主要是 _XHTML_ 可兼容各大浏览器、手机以及 _PDA_，并且浏览器也能快速正确地编译网页。
> _**XHTML**_** 的规则。**
> 下面列出了几条容易犯的错误，供理解。
> 1. **所有标签都必须小写**
> 
在 _XHTML_ 中，所有的标签都必须小写，不能大小写穿插其中，也不能全部都是大写。
> 2. **标签必须成双成对**
> 3. **标签顺序必须正确**
> 4. **所有属性都必须使用双引号**

#### 9. _HTML5_ 的 _form_ 如何关闭自动完成功能？
> _HTML_ 的输入框可以拥有自动完成的功能，当你往输入框输入内容的时候，浏览器会从你以前的同名输入框的历史记录中查找出类似的内容并列在输入框下面，这样就不用全部输入进去了，直接选择列表中的项目就可以了。
> **使用 **_**autocomplete="off"**_**（给不想要提示的 **_**form**_** 或某个 **_**input**_** 设置为 **_**autocomplete=off**_**。）**
> 很多时候，需要对客户的资料进行保密，防止浏览器软件或者恶意插件获取到；
> 可以在 _input_ 中加入 _autocomplete=“off”_ 来关闭记录系统需要保密的情况下可以使用此参数
> 提示：_autocomplete_ 属性有可能在 _form_ 元素中是开启的，而在 _input_ 元素中是关闭的。

#### 10. _title_ 与 _h1_ 的区别、_b_ 与 _strong_ 的区别、_i_ 与 _em_ 的区别？ 
> - _title_ 属性表示网页的标题，_h1_ 元素则表示层次明确的页面内容标题，对页面信息的抓取也有很大的影响
> - _strong_ 是标明重点内容，**有语气加强的含义**，使用阅读设备阅读网络时：<strong>会重读，而 <b>是展示强调内容
> - _i_ 内容展示为斜体，_em_ 表示强调的文本
> 
** 相似的还有如下的元素：**
> 自然样式标签：_b、i、u、s、pre_
> 语义样式标签：_strong、em、ins、del、code_

#### 11. 请描述下 _SEO_ 中的 _TDK_ 
> 在 _SEO_ 中，所谓的 _TDK_ 其实就是 _title、description、keywords_ 这三个标签，_title_ 标题标签，_description_ 描述标签，_keywords_ 关键词标签。

#### 13. 什么是严格模式与混杂模式？ 
> -  严格模式：以浏览器支持的最高标准运行 
> -  混杂模式：页面以宽松向下兼容的方式显示，模拟老式浏览器的行为 

#### 14. 对于 _WEB_ 标准以及 _W3C_ 的理解与认识问题  
> 1. 学习成本降低，只学习标准即可，否则将学习各个浏览器厂商的标准。
> 1. 统一开发流程，用标准化工具开发（例如 _VSCode、WebStorm、Sublime_ 等）再用标准化的浏览器测试，便于多人协作。
> 1. 简化网站代码的维护。
> 1. 跨平台，可方便迁移到不同设备中

#### 15. 列举 _IE_ 与其他浏览器不一样的特性？
> -  _IE_ 的排版引擎是 _Trident_ （又称为 _MSHTML_） 
> -  _Trident_ 内核曾经几乎与 _W3C_ 标准脱节 
> -  _Trident_ 内核的大量 _Bug_ 等安全性问题没有得到及时解决 
> -  _JS_ 方面，有很多独立的方法，例如绑定事件的 _attachEvent_、创建事件的 _createEventObject_ 等 
> -  _CSS_ 方面，也有自己独有的处理方式，例如设置透明，低版本 _IE_ 中使用滤镜的方式，盒模型也和 _W3C_ 规定的盒模型不同 

#### 17. 页面可见性（_Page Visibility_）_API_ 可以有哪些用途？
> 常用的 _API_ 有三个，_document.hidden_ 返回一个布尔值，如果是 _true_，表示页面可见，_false_ 则表示页面隐藏。不同页面之间来回切换，会触发 _visibilitychange_ 事件，还有一个 _document.visibilityState_，表示页面所处的状态。

#### 19. _div+css_ 的布局较 _table_ 布局有什么优点？
> -  页面**加载速度更快**、结构化清晰、页面显示简洁。 
> -  **表现与结构相分离**。 
> -  易于优化**（**_**SEO**_**）**搜索引擎更友好，排名更容易靠前。 
> - ** 符合 **_**W3C**_** 标准。**

#### 24. _HTML_ 全局属性(_global attribute_)有哪些
> 所谓全局属性，就是指每个 _HTML_ 元素都拥有的属性，大致有如下的属性：
> - _class_ :为元素设置类标识
> - data-* : 为元素增加⾃定义属性
> - _draggable_ : 设置元素是否可拖拽
> - _id_ : 元素 _id_ ，⽂档内唯⼀
> - _lang_ : 元素内容的的语⾔
> - _style_ : ⾏内 _css_ 样式
> - _title_ : 元素相关的建议信息

#### 28.  _iframe_ 的作用 
> **优点**
> - 重载页面时不需要重载整个页面，只需要重载页面中的一个框架页(减少了数据的传输，增加了网页下载速度)
> - 方便制作导航栏
> 
**缺点**
> - 浏览器的后退按钮无效
> - 无法被一些搜索引擎索引到
> 
**目前框架的所有优点完全可以使用 **_**Ajax**_** 实现，因此已经没有必要使用 **_**iframe**_** 框架了。**

#### 29. _img_ 上 _title_ 与 _alt_ 
> -  _alt_：如果无法显示图像，浏览器将显示 _alt_ 指定的内容 
> -  _title_：在鼠标移到元素上时显示 _title_ 的内容 

#### 31. 行内元素和块级元素区别，有哪些，怎样转换？（顶呱呱）
> 块级元素：
> - 独占一行
> - 高度，行高以及外边距和内边距都可控制；
> - 宽度缺省是它的容器的 _100%_，除非设定一个宽度。
> - 它可以容纳内联元素和其他块元素
> 
行内元素
> - 不换行
> - 高，行高及外边距和内边距不可改变；
> - 宽度就是它的文字或图片的宽度，不可改变
> - 内联元素只能容纳文本或者其他内联元素
> 
对行内元素，需要注意如下：
> - 设置宽度 _width_ 无效。
> - 设置高度 _height_ 无效，可以通过 _line-height_ 来设置。
> - **设置 **_**margin**_** 只有左右 **_**margin**_** 有效，上下无效。**
> - **设置 **_**padding**_** 只有左右 **_**padding**_** 有效，上下则无效。注意元素范围是增大了，但是对元素周围的内容是没影响的。**
> 
通过 _display_ 属性对行内元素和块级元素进行切换(主要看第 _2、3、4_ 个值)： 
> _html_ 中常见的块级元素：_p、div、form、ul、ol、table_
> _html_ 中常见的行内元素：_a、img、span、button_

#### 34.  _h5_ 和 _html5_ 区别
> _H5_ 是一个产品名词，包含了最新的 _HTML5、CSS3、ES6_ 等新的技术来制作的**应用。 **
> _HTML5_ 是一个技术名词，指代的就仅仅是第五代 _HTML_。

#### 35. _form_ 表单上传文件时需要进行什么样的声明
```html
enctype="multipart/form-data"
```
#### 37. 如何在一张图片上的某一个区域做到点击事件
> 可以使用图片热区技术。步骤如下：
> 1、插入图片，并设置好图像的有关参数，且在 <img> 标记中设置参数 _usemap="#Map"_，以表示对图像地图（_Map_）的引用；
2、用 <map> 标记设定图像地图的作用区域，并取名为：_Map_；
3、分别用 <area> 标记针对相应位置划分出多个矩形作用区域，并设定好其链接参数 _href_。

#### 39. 什么是锚点？
> 锚点（_anchor_）是一种特殊连接，能定位到 _HTML_ 文档中某个特定位置，通过 HTML 元素的 _id_ 来设置锚点。

#### 40. 图片与 _span_ 元素混排图像下方会出现几像素的空隙的原因是什么？
> 参考答案：
> _img_ 作为可替换元素，它没有自己的基线，如果与不可替换元素混合排列，其行盒底端与基线对齐。**由于与基线对齐**，图像下方就会出现几像素的空隙。

#### 41. _a_ 元素除了用于导航外，还可以有什么作用？
> 当然，_a_ 元素最常见的两个应用就是做锚点和下载文件。发短信，打电话
> 锚点可以在点击时快速定位到一个页面的某一个位置，而下载的原理在于 _**a**_** 标签所对应的资源浏览器无法解析，于是浏览器会选择将其下载下来。**

### 1.  介绍下 _BFC_ 及其应用
> 所谓 _BFC_，指的是一个独立的布局环境，_BFC_ 内部的元素布局与外部互不影响。 
> 触发 _BFC_ 的方式有很多，常见的有：
> - 设置浮动
> - _overflow_ 设置为 _auto、scroll、hidden_
> - _positon_ 设置为 _absolute、fixed_
> - **display: flow-root; 没有副作用，专门为BFC**
> 
常见的 _BFC_ 应用有： 
> - 解决浮动元素令父元素高度坍塌的问题
> - 解决非浮动元素被浮动元素覆盖问题
> - 解决外边距垂直方向重合的问题

BFC block formatting Context 块级格式化上下文
新的渲染规则：BFC包裹子元素 (浮动元素，margin塌陷, margin合并)
BFC + 浮动实现多栏布局
BFC 兄弟元素,位置分明
```css
.father{
  width: 100px;
  border: 1px solid;
  float: left;
  /*设置浮动之后，父级不能包裹子集了 height由子集撑开。怎么才能保住？
  1. 清除浮动
  2. 触发BFC
  */
  /*overflow: hidden;
  position: absolute;
  display: inline-block
  display: flex; 只要display不是block
  display: flow-root; 没有副作用，专门为BFC
  */
}
.son{
  width: 50px;
  height: 50px;
  background: #fac;
}
```

```css
.father{
  width: 100px;
  height: 100px;
  background-color: red;
  margin-top: 100px;
  /*display: flow-root;*/
}
.son{
  width: 50px;
  height: 50px;
  background: #fac;
  margin-top: 200px;
  /*margin-top: 100px;
  margin:和父级margin-top比较，谁大，按谁;
  */
}
```

BFC多栏布局，左右固定，中间自适应；左侧固定，中间自适应

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
  </head>
  <body>
    <style>
      .left, .right {
        width: 100px;
        height: 100px;
        background: #fac;
        float: left;
      }
      .right {
        float: right;
      }
      /*浮动了，脱离文档流*/
      .center {
        height: 150px;
        background: #cfa;
        overflow: hidden; 
        display: flow-root;
      }
    </style>
    <div class="wrapper">
      去掉任何一个实现两栏布局
      <div class="left"></div>
      <div class="right"></div>
      <div class="center"></div>
    </div>
  </body>
</html>
```

### 2. 介绍下 _BFC、IFC、GFC_ 和 _FFC_ 
> - _BFC_：块级格式上下文，指的是一个独立的布局环境，_BFC_ 内部的元素布局与外部互不影响。
> 1. _BFC_ 有隔离作用，内部元素不受外部元素影响，反之亦然。
> 1. 一个元素只能存在于一个 _BFC_ 中，如果能同时存在于两个 _BFC_ 中，那么就违反了 _BFC_ 的隔离原则。
> 1. _BFC_ 内的元素按正常流排列，元素间的间隙由元素外边距控制。
> 1. _BFC_ 中的内容不会与外面的浮动元素重叠。
> 1. 计算 _BFC_ 的高度需要包括 _BFC_ 内的浮动子元素的高度。
> 
> - _IFC_：行内格式化上下文，将一块区域以行内元素的形式来格式化。
> - _GFC_：网格布局格式化上下文，将一块区域以 _grid_ 网格的形式来格式化
> - _FFC_：弹性格式化上下文，将一块区域以弹性盒的形式来格式化

### 3. _flex_ 骰子
### 5. 分析比较 _opacity: 0、visibility: hidden、display: none_ 优劣和适用场景。 
> -  结构： display:none: 会让元素完全从渲染树中消失，渲染的时候**不占据任何空间, 不能点击**， visibility: hidden:不会让元素从渲染树消失，**渲染元素继续占据空间，只是内容不可见，不能点击** opacity: 0: 不会让元素从渲染树消失，**渲染元素继续占据空间，只是内容不可见，可以点击 **
> -  继承： display: none和opacity: 0：是**非继承属性**，子孙节点消失由于元素从渲染树消失造成，通过修改子孙节点属性无法显示。 visibility: hidden：是**继承属性**，子孙节点消失由于继承了hidden，通过设置visibility: visible;可以让子孙节点显式。 
> -  性能： displaynone : 修改元素会造成文档**回流,**读屏器不会读取display: none元素内容，性能消耗较大 visibility:hidden: 修改元素只会造成本元素的**重绘**,性能消耗较少读屏器读取visibility: hidden元素内容 opacity: 0 ： 修改元素会造成重绘，性能消耗较少 
> 1. display: none (不占空间，不能点击)（场景，显示出原来这里不存在的结构）
> 1. visibility: hidden（占据空间，不能点击）（场景：显示不会导致页面结构发生变动，不会撑开）
> 1. opacity: 0（占据空间，可以点击）（场景：可以跟transition搭配）

### 6. 已知如下代码，如何修改才能让图片宽度为 _300px_ ？注意下面代码不可修改。

```html
<img src="1.jpg" style="width:480px!important;”>
```
> **CSS 方法**
> - _max-width:300px;_ 覆盖其样式
> - _transform: scale(0.625)_ 按比例缩放图片；
> - **利用 **_**CSS**_** 动画的样式优先级高于 **_**!important**_** 的特性**
> 
**JS 方法** 
> - _document.getElementsByTagName("img")[0].setAttribute("style","width:300px!important;")_

### 7. 如何用 _css_ 或 _js_ 实现多行文本溢出省略效果，考虑兼容性

> CSS 实现方式 
> 单行：

```css
overflow: hidden;
text-overflow:ellipsis;
white-space: nowrap;
```
> 多行：
> 

```css
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 3; //行数
overflow: hidden;
```
> 兼容：
> JS 实现方式：
> - 使用split + 正则表达式将单词与单个文字切割出来存入words
> - 加上 '...'
> - 判断scrollHeight与clientHeight，超出的话就从words中pop一个出来

```css
p{position: relative; line-height: 20px; max-height: 40px;overflow: hidden;}
p::after{content: "..."; position: absolute; bottom: 0; right: 0; padding-left: 40px;
background: -webkit-linear-gradient(left, transparent, #fff 55%);
background: -o-linear-gradient(right, transparent, #fff 55%);
background: -moz-linear-gradient(right, transparent, #fff 55%);
background: linear-gradient(to right, transparent, #fff 55%);
}
```

### 8. 居中为什么要使用 _transform_（为什么不使用 _marginLeft/Top_）（阿里） 
> transform 属于合成属性（composite property），对合成属性进行 transition/animation 动画将会创建一个**合成层**（composite layer），这使得被动画元素在一个独立的层中进行动画。通常情况下，浏览器会将一个层的内容先绘制进一个位图中，然后再作为纹理（texture）上传到 GPU，只要该层的内容不发生改变，就没必要进行重绘（repaint），浏览器会通过重新复合（recomposite）来形成一个新的帧。
>  
> **top/left属于布局属性，该属性的变化会导致重排**（reflow/relayout），所谓重排即指对这些节点以及受这些节点影响的其它节点，进行CSS计算->布局->重绘过程，浏览器需要为整个层进行重绘并重新上传到 GPU，造成了极大的性能开销。

### 10. 说出 _space-between_ 和 _space-around_ 的区别？（携程）
> 这个是 _flex_ 布局的内容，其实就是一个边距的区别，按水平布局来说，`space-between`是两端对齐，在左右两侧没有边距，而`space-around`是每个 子项目左右方向的 margin 相等，所以两个item中间的间距会比较大。

### 11. _CSS3_ 中 _transition_ 和 _animation_ 的属性分别有哪些
### 12. 隐藏页面中的某个元素的方法有哪些？
> 1. 隐藏类型
> 
屏幕并不是唯一的输出机制，比如说屏幕上看不见的元素（隐藏的元素），其中一些依然能够被读屏软件阅读出来（因为读屏软件依赖于可访问性树来阐述）。为了消除它们之间的歧义，我们将其归为三大类：
> - 完全隐藏：元素从渲染树中消失，不占据空间。
> - 视觉上的隐藏：屏幕中不可见，占据空间。
> - 语义上的隐藏：读屏软件不可读，但正常占据空。
> 
**完全隐藏**
> (1) display 属性
> (2) hidden 属性
HTML5 新增属性，相当于 display: none
> **视觉上的隐藏**
> (1) 设置 posoition 为 absolute 或 fixed，通过设置 top、left 等值，将其移出可视区域。
> (2) 设置 position 为 relative，通过设置 top、left 等值，将其移出可视区域。 
> (3) 设置 margin 值，将其移出可视区域范围（可视区域占位）。
>  
> 语义上隐藏
> _aria-hidden 属性_
>  读屏软件不可读，占据空间，可见。

```html
<div aria-hidden="true">
</div>
```
### 13. 层叠上下文
> **层叠上下文概念**
> 在 _CSS2.1_ 规范中，每个盒模型的位置是三维的，分别是平面画布上的 _X_ 轴，_Y_ 轴以及表示层叠的 _Z_ 轴。
> 一般情况下，元素在页面上沿 _X_ 轴 _Y_ 轴平铺，我们察觉不到它们在 _Z_ 轴上的层叠关系。而一旦元素发生堆叠，这时就能发现某个元素可能覆盖了另一个元素或者被另一个元素覆盖。
> **层叠上下文触发条件**
> - _HTML_ 中的根元素 _HTML_ 本身就具有层叠上下文，称为“根层叠上下文”。
> - 普通元素设置 _position_ 属性为非 _static_ 值并设置 _z-index_ 属性为具体数值，产生层叠上下文
> - _CSS3_ 中的新属性也可以产生层叠上下文
> 
**层叠顺序**
> “层叠顺序”（_stacking order_）表示元素发生层叠时按照特定的顺序规则在 _Z_ 轴上垂直显示。
> 说简单一点就是当元素处于同一层叠上下文内时如何进行层叠判断。
> 具体的层叠等级如下图：

### 15. 讲一下_png8、png16、png32_的区别，并简单讲讲 _png_ 的压缩原理
> PNG图片主要有三个类型，分别为 PNG 8/ PNG 24 / PNG 32。
> - `PNG 8`：PNG 8中的8，其实指的是8bits，相当于用28（2的8次方）大小来存储一张图片的颜色种类，28等于256，也就是说PNG 8能存储256种颜色，一张图片如果颜色种类很少，将它设置成PNG 8得图片类型是非常适合的。
> - `PNG 24`：PNG 24中的24，相当于3乘以8 等于 24，就是用三个8bits分别去表示 R（红）、G（绿）、B（蓝）。R(0-255),G(0-255),B(0-255)，可以表达256乘以256乘以256=16777216种颜色的图片，这样PNG 24就能比PNG 8表示色彩更丰富的图片。但是所占用的空间相对就更大了。
> - `PNG 32`：PNG 32中的32，相当于PNG 24 加上 8bits的透明颜色通道，就相当于R（红）、G（绿）、B（蓝）、A（透明）。R(0255),G(0255),B(0255),A(0255)。比PNG 24多了一个A（透明），也就是说PNG 32能表示跟PNG 24一样多的色彩，并且还支持256种透明的颜色，能表示更加丰富的图片颜色类型。
> 
PNG图片的压缩，分两个阶段：
> - `预解析（Prediction）`：这个阶段就是对png图片进行一个预处理，处理后让它更方便后续的压缩。
> - `压缩（Compression）`：执行Deflate压缩，该算法结合了 LZ77 算法和 Huffman 算法对图片进行编码。

### 16. 说说渐进增强和优雅降级

> 渐进增强相当于向上兼容，优雅降级相当于向下兼容。向下兼容指的是高版本支持低版本，或者说后期开发的版本能兼容早期开发的版本。
>  
> 渐进增强：针对低版本浏览器进行页面构建，保证基本功能，再针对高级浏览器进行效果、交互等改进和追加功能，达到更好的用户体验。
> 优雅降级：一开始就构建完整的功能，再针对低版本浏览器进行兼容。
> 区别：优雅降级是从复杂的现状开始并试图减少用户体验的供给，而渐进增强则是从一个基础的、能够起到作用的版本开始再不断扩充，以适应未来环境的需要。
> 绝大多少的大公司都是采用渐进增强的方式，因为业务优先，提升用户体验永远不会排在最前面。
> - 例如新浪微博网站这样亿级用户的网站，前端的更新绝不可能追求某个特效而不考虑低版本用户是否可用。一定是确保低版本到高版本的可访问性再渐进增强。
> - 如果开发的是一面面向青少面的软件或网站，你明确这个群体的人总是喜欢尝试新鲜事物，喜欢炫酷的特效，喜欢把软件更新至最新版本，这种情况再考虑优雅降级。

### 17. 介绍下 _positon_ 属性
> position 属性主要用来定位，常见的属性值如下：
> -  `absolute` 绝对定位，相对于 `static` 定位以外的第一个父元素进行定位。 
> -  `relative` 相对定位，相对于其自身正常位置进行定位。 
> -  `fixed` 固定定位，相对于浏览器窗口进行定位。 
> 
注意：fixed 元素一定是相对视口定位的吗？[https://juejin.cn/post/6844904046663303181](https://juejin.cn/post/6844904046663303181)
> -  `static` 默认值。没有定位，元素出现在正常的流中。 
> -  `inherit` 规定应该从父元素继承 position 属性的值。 
> -  `sticky` 粘性定位，当元素在容器中被滚动超过指定的偏移值时，元素在容器内固定在指定位置。 
> 
在屏幕范围（viewport）时该元素的位置并不受到定位影响（设置是top、left等属性无效），当该元素的位置将要移出**偏移范围时，定位又会变成fixed**，根据设置的left、top等属性成固定位置的效果。
> - 该元素**并不脱离文档流**，仍然保留元素原本在文档流中的位置。
> - 元素固定的相对偏移是相对于离它最近的具有滚动框的祖先元素，如果祖先元素都不可以滚动，那么是相对于viewport来计算元素的偏移量

### 19. 如何实现一个自适应的正方形 
> **方法1：利用 CSS3 的 vw 单位**
> `vw` 会把视口的宽度平均分为 100 份

```css
.square {
width: 10vw;
height: 10vw;// 注意这里是vw
background: red;
}
```
> **方法2：利用 margin 或者 padding 的百分比计算是参照父元素的 width 属性** 

```
.square {
width: 10%;
padding-bottom: 10%; 
height: 0; // 防止内容撑开多余的高度
background: red;
}
```

- 利用vw来实现：

```css
.square {
  width: 10%;
  height: 10vw;
  background: tomato;
}
复制代码
```

- 利用元素的margin/padding百分比是相对父元素width的性质来实现：

```css
.square {
  width: 20%;
  height: 0;
  padding-top: 20%;
  background: orange;
}
复制代码
```

- 利用子元素的margin-top的值来实现：

```css
.square {
  width: 30%;
  overflow: hidden;
  background: yellow;
}
.square::after {
  content: '';
  display: block;
  margin-top: 100%;
}
复制代码
```

### 20. 如何实现三栏布局
>  三栏布局是很常见的一种页面布局方式。左右固定，中间自适应。实现方式有很多种方法。
>  **第一种：flex**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .container {
            display: flex;
        }

        .left {
            flex-basis: 200px;
            background: green;
        }

        .main {
            flex: 1;
            background: red;
        }

        .right {
            flex-basis: 200px;
            background: green;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="left">left</div>
        <div class="main">main</div>
        <div class="right">right</div>
    </div>

</body>

</html>
```

>  **第二种：position + margin**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body,
        html {
            padding: 0;
            margin: 0;
        }

        .left,
        .right {
            position: absolute;
            top: 0;
            background: red;
        }

        .left {
            left: 0;
            width: 200px;
        }

        .right {
            right: 0;
            width: 200px;
        }

        .main {
            margin: 0 200px;
            background: green;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="left">left</div>
        <div class="right">right</div>
        <div class="main">main</div>
    </div>

</body>

</html>
```
>  **第三种：float + margin** 

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        body,
        html {
            padding: 0;
            margin: 0;
        }

        .left {
            float: left;
            width: 200px;
            background: red;
        }

        .main {
            margin: 0 200px;
            background: green;
        }

        .right {
            float: right;
            width: 200px;
            background: red;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="left">left</div>
        <div class="right">right</div>
        <div class="main">main</div>
    </div>

</body>

</html>
```

双飞翼布局
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
  </head>
  <body>
    <style>
      .left, .right {
        width: 100px;
        height: 100px;
        background: #fac;
        float: left;
      }
      .right {
        float: right;
      }
      /*浮动了，脱离文档流*/
      .center {
        height: 150px;
        background: #cfa;
        overflow: hidden; 
        display: flow-root;
      }
    </style>
    <div class="wrapper">
      去掉任何一个实现两栏布局
      <div class="left"></div>
      <div class="right"></div>
      <div class="center"></div>
    </div>
  </body>
</html>
```
圣杯布局
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      * {
        padding: 0;
        margin: 0;
      }

      .wrapper {
        resize: both;
        overflow: hidden;
        width: 300px;
        height: 300px;
        border: 1px solid black;
        display: flex;
        flex-direction: column;
      }

      .header,
      .footer,
      .left,
      .right {
        flex: 0 0 20%; /*不参与伸缩，占20%*/
        border: 1px solid black;
        box-sizing: border-box;
      }

      .contain {
        flex: 1 1 auto;
        display: flex;
      }

      .center {
        flex: 1 1 auto;
      }
    </style>
  </head>

  <body>
    <div class="wrapper">
      <div class="header">header</div>
      <div class="contain">
        <div class="left">left</div>
        <div class="center">center</div>
        <div class="right">right</div>
      </div>
      <div class="footer">footer</div>
    </div>
  </body>
</html>
```
### 21. _import_ 和 _link_ 区别
> 1. 从属关系区别
> 
`@import`是 CSS 提供的语法规则，**只有导入样式表的作用**；`link`是HTML提供的标签，不仅可以加载 CSS 文件，**还可以定义 RSS、rel 连接属性等**。
> 2. 加载顺序区别
> 
加载页面时，`link`标签引入的 CSS 被**同时加载**；`@import`引入的 CSS 将在页面**加载完毕后被加载**。
> 3. 兼容性区别
> 
`@import`是 CSS2.1 才有的语法，故只可在 IE5+ 才能识别；`link` 标签作为 HTML 元素，**不存在兼容性**问题。
> 4. DOM可控性区别
> 
可以通过 JS 操作 DOM ，插入`link`标签来改变样式；由于DOM方法是基于文档的，无法使用`@import`的方式插入样式。

### 23. 清除浮动的方法 
> -  给浮动元素父级设置高度 
> -  父级同时浮动（需要给父级同级元素添加浮动） 
> -  父级设置成inline-block，其margin: 0 auto居中方式失效 
> -  给父级添加overflow:hidden 清除浮动方法 
> -  万能清除法 after 伪类清浮动（现在主流方法，推荐使用） 

### 使用 clear 属性清除浮动的原理？
使用clear属性清除浮动，其语法如下：
```css
clear:none|left|right|both
复制代码
```

如果单看字面意思，clear:left 是“清除左浮动”，clear:right 是“清除右浮动”，实际上，这种解释是有问题的，因为浮动一直还在，并**没有清除。**
官方对clear属性解释：“**元素盒子的边不能和前面的浮动元素相邻**”，对元素设置clear属性是为了避免浮动元素对该元素的影响，而不是清除掉浮动。

还需要注意 clear 属性指的是元素盒子的边不能和前面的浮动元素相邻，注意这里“**前面的**”3个字，也就是clear属性对“后面的”浮动元素是不闻不问的。考虑到float属性要么是left，要么是right，不可能同时存在，同时由于clear属性对“后面的”浮动元素不闻不问，因此，当clear:left有效的时候，clear:right必定无效，也就是此时clear:left等同于设置clear:both；同样地，clear:right如果有效也是等同于设置clear:both。由此可见，clear:left和clear:right这两个声明就没有任何使用的价值，至少在CSS世界中是如此，直接使用clear:both吧。
clear属性**只有块级元素**才有效的，而**::after等伪元素默认都是内联**水平，这就是借助伪元素清除浮动影响时需要设置display属性值的原因。
### 对requestAnimationframe的理解
实现动画效果的方法比较多，Javascript 中可以通过定时器 setTimeout 来实现，CSS3 中可以使用 transition 和 animation 来实现，HTML5 中的 canvas 也可以实现。除此之外，HTML5 提供一个专门用于请求动画的API，那就是 requestAnimationFrame，顾名思义就是**请求动画帧**。
MDN对该方法的描述：
> window.requestAnimationFrame() 告诉浏览器——你希望执行一个动画，并且要求浏览器在下次重绘之前调用指定的回调函数更新动画。该方法需要传入一个回调函数作为参数，该回调函数会在浏览器下一次重绘之前执行。

**语法：** `window.requestAnimationFrame(callback);`  其中，callback是**下一次重绘之前更新动画帧所调用的函数**(即上面所说的回调函数)。该回调函数会被传入DOMHighResTimeStamp参数，它表示requestAnimationFrame() 开始去执行回调函数的时刻。该方法属于**宏任务**，所以会在执行完微任务之后再去执行。
**取消动画：** 使用cancelAnimationFrame()来取消执行动画，该方法接收一个参数——requestAnimationFrame默认返回的id，只需要传入这个id就可以取消动画了。
**优势：**

- **CPU节能**：使用SetTinterval 实现的动画，当页面被隐藏或最小化时，SetTinterval 仍然在后台执行动画任务，由于此时页面处于不可见或不可用状态，刷新动画是没有意义的，完全是浪费CPU资源。而RequestAnimationFrame则完全不同，当页面处理未激活的状态下，该页面的屏幕刷新任务也会被系统暂停，因此跟着系统走的RequestAnimationFrame也会停止渲染，当页面被激活时，动画就从上次停留的地方继续执行，有效节省了CPU开销。
- **函数节流**：在高频率事件( resize, scroll 等)中，为了防止在一个刷新间隔内发生多次函数执行，RequestAnimationFrame可保证每个刷新间隔内，函数只被执行一次，这样既能保证流畅性，也能更好的节省函数执行的开销，一个刷新间隔内函数执行多次时没有意义的，因为多数显示器每16.7ms刷新一次，多次绘制并不会在屏幕上体现出来。
- **减少DOM操作**：requestAnimationFrame 会把每一帧中的所有DOM操作集中起来，在一次重绘或回流中就完成，并且重绘或回流的时间间隔紧紧跟随浏览器的刷新频率，一般来说，这个频率为每秒60帧。

**setTimeout执行动画的缺点**：它通过设定间隔时间来不断改变图像位置，达到动画效果。但是容易出现卡顿、抖动的现象；原因是：

- settimeout任务被放入异步队列，只有当主线程任务执行完后才会执行队列中的任务，因此实际执行时间总是比设定时间要晚；
- settimeout的固定时间间隔不一定与屏幕刷新间隔时间相同，会引起丢帧。
### 伪元素和伪类的区别和作用？

- 伪元素：在内容元素的前后插入额外的元素或样式，但是这些元素实际上并不在文档中生成。它们只在外部显示可见，但不会在文档的源代码中找到它们，因此，称为“伪”元素。例如：
- 伪类：将特殊的效果添加到特定选择器上。它是已有元素上添加类别的，不会产生新的元素。例如：

**总结：** 伪类是通过在元素选择器上加⼊伪类改变元素状态，⽽伪元素通过对元素的操作进⾏对元素的改变。
### 25. _css reset_ 和 _normalize.css_ 有什么区别？ 
> -  两者都是通过重置样式，保持浏览器样式的一致性 
> -  前者几乎为所有标签添加了样式，后者保持了许多浏览器样式，保持尽可能的一致 
> -  后者修复了常见的桌面端和移动端浏览器的 bug：包含了 HTML5 元素的显示设置、预格式化文字的 font-size 问题、在 IE9 中 SVG 的溢出、许多出现在各浏览器和操作系统中的与表单相关的 bug。 
> -  前者中含有大段的继承链 
> -  后者模块化，文档较前者来说丰富 

### 27. 如何避免重绘或者重排？
> 1. **集中改变样式** 改变 class 

```css
// 判断是否是黑色系样式
const theme = isDark ? 'dark' : 'light'

// 根据判断来设置不同的class
ele.setAttribute('className', theme)
```
> 2. **使用 DocumentFragment**
> 
我们可以通过createDocumentFragment创建一个游离于DOM树之外的节点，然后在此节点上批量操作，最后插入DOM树中，因此只触发一次重排

```javascript
var fragment = document.createDocumentFragment();

for (let i = 0;i<10;i++){
  let node = document.createElement("p");
  node.innerHTML = i;
  fragment.appendChild(node);
}

document.body.appendChild(fragment);
```
> 3. **提升为合成层**
> 
将元素提升为合成层有以下优点：
> - 合成层的位图，会交由 GPU 合成，比 CPU 处理要快
> - 当需要 repaint 时，只需要 repaint 本身，不会影响到其他的层
> - 对于 transform 和 opacity 效果，不会触发 layout 和 paint
> 
提升合成层的最好方式是使用 CSS 的 will-change 属性：
> 

```javascript
#target {
  will-change: transform;
}
```
### 28. 如何触发重排和重绘？
> - 添加、删除、更新DOM节点
> - 通过display: none隐藏一个DOM节点-触发重排和重绘
> - 通过visibility: hidden隐藏一个DOM节点-只触发重绘，因为没有几何变化
> - 移动或者给页面中的DOM节点添加动画
> - 添加一个样式表，调整样式属性
> - 用户行为，例如调整窗口大小，改变字号，或者滚动。

### 29. 重绘与重排的区别？
> - 重排: 部分渲染树（或者整个渲染树）需要重新分析并且节点尺寸需要重新计算，表现为重新生成布局，重新排列元素
> - 重绘: 由于节点的几何属性发生改变或者由于样式发生改变，例如改变元素背景色时，屏幕上的部分内容需要更新，表现为某些元素的外观被改变

### 30. 如何优化图片
> 1.  对于很多装饰类图片，尽量不用图片，因为这类修饰图片完全可以用 CSS 去代替。 
> 1.  对于移动端来说，屏幕宽度就那么点，完全没有必要去加载原图浪费带宽。一般图片都用 CDN 加载，可以计算出适配屏幕的宽度，然后去请求相应裁剪好的图片。 
> 1.  小图使用 _base64_ 格式 
> 1.  雪碧图 
> 1.  选择正确的图片格式： 
> - 对于能够显示 WebP 格式的浏览器尽量使用 WebP 格式。因为 WebP 格式具有更好的图像数据压缩算法，能带来更小的图片体积，而且拥有肉眼识别无差异的图像质量，缺点就是兼容性并不好
> - 小图使用 PNG，其实对于大部分图标这类图片，完全可以使用 SVG 代替
> - 照片使用 JPEG

### 34. 什么是渐进式渲染（_progressive rendering_）？
> 渐进式渲染是用于提高网页性能（尤其是提高用户感知的加载速度），以尽快呈现页面的技术。
> 一些举例：
> - 图片懒加载——页面上的图片不会一次性全部加载。当用户滚动页面到图片部分时，JavaScript 将加载并显示图像。
> - 确定显示内容的优先级（分层次渲染）——为了尽快将页面呈现给用户，页面只包含基本的最少量的 CSS、脚本和内容，然后可以使用延迟加载脚本或监听`DOMContentLoaded`/`load`事件加载其他资源和内容。
> - 异步加载 HTML 片段——当页面通过后台渲染时，把 HTML 拆分，通过异步请求，分块发送给浏览器。

### 39. _img_ 标签在页面中有 _1px_ 的边框，怎么处理 
```css
img{
	border: 0;
}
```

### 40. 如何绝对居中（不用定位）
> 方法一：
> 使用 _flex_ 弹性盒来绝对居中
> 方法二：
> 设置 _margin-left_ 为 _calc(50% - 50px);_

### 42. 我有5个div在一行，我要让div与div直接间距10px且最左最右两边的div据边框10px，同时在我改变窗口大小时，这个10px不能变，div根据窗口改变大小（长天星斗）

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <style>
        * {
            margin: 0;
        }

        .container {
            display: flex;
        }

        .container>div {
            outline: 1px solid;
            margin: 0 5px;
            flex-grow: 1;
        }

        .container>div:first-child {
            margin-left: 10px;
        }

        .container>div:last-child {
            margin-right: 10px;
        }
    </style>
    <div class="container">
        <div>1</div>
        <div>2</div>
        <div>3</div>
        <div>4</div>
        <div>5</div>
    </div>
</body>

</html>
```
### 48. _px_ 和 _em_ 的区别
> _px_ 即 _pixel_ 像素，是相对于屏幕分辨率而言的，是一个相对绝对单位，**即在同一设备上每个设备像素所代表的物理长度是固定不变的（绝对性），但在不同设备间每个设备像素所代表的物理长度是可以变化的（相对性）。**
> _em_ 一个相对单位，不是一个固定的值，来源于纸张印刷业，在 _web_ 领域它指代基准字号，浏览器默认渲染文字大小是 16_px_ ，它会继承计算后的父级元素的 font-size。 

### 49. _div_ 之间的间隙是怎么产生的，应该怎么消除？
> 原因：浏览器解析的时候，会把回车换行符解析成一定的间隙，间隙的大小跟默认的字体大小设置有关。
> 解决：其父元素加上 font-size:0 的属性，但是字体需要额外处理

### 24. display:inline-block 什么时候会显示间隙？

- 有空格时会有间隙，可以删除空格解决；
- `margin`正值时，可以让`margin`使用负值解决；
- 使用`font-size`时，可通过设置`font-size:0`、`letter-spacing`、`word-spacing`解决；
### 57. 你怎么处理页面兼容性问题？
> 1. 统一标准模式
> 1. 利用 _CSS_ 重置技术初始化默认样式
> 1. 针对不同浏览器采用不同的解决方案

### 63. 什么是继承？_CSS_ 中哪些属性可以继承？哪些不可以继承？
> - 继承，指元素可以自动获得祖先元素的某些 _CSS_ 属性。通常来说文本类的属性具有继承性。
> - 文本类的样式可以继承：例如 _color、 font-size、 line-height、 font-family、 font-weight、 font-weight、 text-decoration、 letter-spacing、text-align_ 等等
> - _display、 margin、 padding、 border、 background、 position、 float_ 等则不会被继承

### 65. _CSS_ 的计算属性知道吗
> 即 _calc( )_ 函数，主要用于指定元素的长度，支持所有 CSS 长度单位，运算符前后都需要保留一个空格。
> 比如： _width: calc(100% - 50px);_

### 66. 为何 _CSS_ 放在 _HTML_ 头部？
> 为了**尽早让浏览器拿到 **_**CSS**_** 并且生成 **_**CSSOM**_，然后与 _HTML_ 一次性生成最终的 _RenderTree_，渲染一次即可。如果放在 _HTML_ 底部，会出现渲染卡顿的现象影响性能和用户体验。

### 67. _background-size_ 有哪 _4_ 种值类型？
> - _length_：设置背景图片高度和宽度。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为 auto(自动)
> - _percentage_：将计算相对于背景定位区域的百分比。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为“_auto_(自动)”
> - _cover_：此时会保持图像的纵横比并将图像缩放成将完全覆盖背景定位区域的最小大小。
> - _contain_：此时会保持图像的纵横比并将图像缩放成将适合背景定位区域的最大大小。 

### 74. 有一个高度自适应的 div，里面有 2 个 div，一个高度 100px，希望另一个填满剩下的高度？（CSS 实现） 
> 方法一：利用定位

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        html,
        body {
            height: 100%;
            margin: 0px;
            padding: 0px;
        }

        .main {
            position: relative;
            height: 100%;
        }

        .box1 {
            height: 100px;
            background-color: red;
        }

        .box2 {
            position: absolute;
            width: 100%;
            top: 100px;
            bottom: 0px;
            background-color: blue;
        }
    </style>
</head>

<body>
    <div class="main">
        <div class="box1"></div>
        <div class="box2"></div>
    </div>
</body>

</html>
```
> 方法二：利用计算属性_calc_ 

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        html,
        body {
            height: 100%;
            margin: 0px;
            padding: 0px;
        }

        .main {
            height: 100%;
        }

        .box1 {
            height: 100px;
            background-color: red;
        }

        .box2 {
            height: calc(100% - 100px);
            background-color: blue;
        }
    </style>
</head>

<body>
    <div class="main">
        <div class="box1"></div>
        <div class="box2"></div>
    </div>
</body>

</html>
```
### inline 和 block 区别（长宽，padding，margin）  
### 77. 当 margin-top、padding-top 的值是百分比时，分别是如何计算的？
> 可以对元素的margin设置百分数，百分数是相对于父元素的width计算，不管是margin-top/margin-bottom还是margin-left/margin-right。（padding同理） 
> 如果没有为元素声明width，在这种情况下，元素框的总宽度包括外边距取决于父元素的width，这样可能得到“流式”页面，即元素的外边距会扩大或缩小以适应父元素的实际大小。如果对这个文档设置样式，使其元素使用百分数外边距，当用户修改浏览窗口的宽度时，外边距会随之扩大或缩小。

### 81. 在 _rem_ 自适应页面中使用 _sprite_ 会出现背景图不随元素放大缩小的情况，如何解决？
> 将 _backgroud-size_ 也换算为 _rem_ 作为单位

### 98. 如何将大量可变化的图片显示到页面并不影响浏览器性能？
> 使用图片懒加载。将页面中未出现在可视区域的图片先不做加载，等滚动到可视区域后，再加载。

### 99. 图片与图片之间默认存在的间距如何去除？
> 1. 将图片全部脱离文档流
> 1. 将图片父元素设置文字大小为 0

### 102. 不使用 border 属性，使用其他属性模拟边框。
> 使用 _outline_ 或 _box-shadow_ 都可以模拟出边框。

### 103. 阅读代码，计算 ul 的高度。
```
 <ul style="overflow: hidden;">
   <li style="height: 100px; float: left;"></li>
 </ul>
```

> _ul_ 的高度为 100_px_，虽然子级 _li_ 浮动会造成父元素 _ul_ 的高度塌陷，但父元素触发了 _BFC_，所以高度可以自动找回。

### 105. 如何使用媒体查询实现视口宽度大于 320_px_ 小于 640_px_ 时 _div_ 元素宽度变成 30%？
```css
@media screen and (min-width: 320px) and (max-width: 640px){
  div{
    width: 30%;
  }
}
```

### 106. 什么是 _HTML_ 实体？
> 即对当前文档的编码方式不能包含的字符提供一种转义表示。例如对于 “>” 符号，它是 HTML 元素的一部分，如果要在文档中显示就需要进行转义为“&gt;”。

### 109. 在定位属性 _position_ 中，哪个值会脱离文档流?
> _absolute、fixed_。

### 画一条0.5px的线

- **采用transform: scale()的方式**，该方法用来定义元素的2D 缩放转换：

```css
transform: scale(0.5,0.5);
```

- **采用meta viewport的方式**

```css
<meta name="viewport" content="width=device-width, initial-scale=0.5, minimum-scale=0.5, maximum-scale=0.5"/>
```

这样就能缩放到原来的0.5倍，如果是1px那么就会变成0.5px。viewport只针对于移动端，只在移动端上才能看到效果

### 6. 如何解决 1px 问题？
1px 问题指的是：在一些 `Retina屏幕` 的机型上，移动端页面的 1px 会变得很粗，呈现出不止 1px 的效果。原因很简单——CSS 中的 1px 并不能和移动设备上的 1px 划等号。它们之间的比例关系有一个专门的属性来描述：

```html
window.devicePixelRatio = 设备的物理像素 / CSS像素。
```

打开 Chrome 浏览器，启动移动端调试模式，在控制台去输出这个 `devicePixelRatio` 的值。这里选中 iPhone6/7/8 这系列的机型，输出的结果就是2：
![image.png](https://cdn.nlark.com/yuque/0/2022/png/758572/1645668437744-c816038d-7346-4055-98b3-a5c041ce0aa6.png#clientId=ub3fbef71-cb1e-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=83&id=uf53958fe&margin=%5Bobject%20Object%5D&name=image.png&originHeight=166&originWidth=434&originalType=binary&ratio=1&rotation=0&showTitle=false&size=89435&status=done&style=none&taskId=u626309b0-6f50-4d24-a581-9c62e0b93aa&title=&width=217)
这就意味着设置的 1px CSS 像素，在这个设备上实际会用 2 个物理像素单元来进行渲染，所以实际看到的一定会比 1px 粗一些。 解决1px 问题的三种思路：
> 思路一：直接写 0.5px

如果之前 1px 的样式这样写：
```css
border:1px solid #333
```
可以先在 JS 中拿到 window.devicePixelRatio 的值，然后把这个值通过 JSX 或者模板语法给到 CSS 的 data 里，达到这样的效果（这里用 JSX 语法做示范）：

```html
<div id="container" data-device={{window.devicePixelRatio}}></div>
```

然后就可以在 CSS 中用属性选择器来命中 devicePixelRatio 为某一值的情况，比如说这里尝试命中 devicePixelRatio 为2的情况：
```css
#container[data-device="2"] {
  border:0.5px solid #333
}
```

直接把 1px 改成 1/devicePixelRatio 后的值，这是目前为止最简单的一种方法。这种方法的缺陷在于兼容性不行，IOS 系统需要8及以上的版本，安卓系统则直接不兼容。
> 思路二：伪元素先放大后缩小

这个方法的可行性会更高，兼容性也更好。唯一的缺点是代码会变多。
思路是**先放大、后缩小：在目标元素的后面追加一个 ::after 伪元素，让这个元素布局为 absolute 之后、整个伸展开铺在目标元素上，然后把它的宽和高都设置为目标元素的两倍，border值设为 1px。接着借助 CSS 动画特效中的放缩能力，把整个伪元素缩小为原来的 50%。此时，伪元素的宽高刚好可以和原有的目标元素对齐，而 border 也缩小为了 1px 的二分之一，间接地实现了 0.5px 的效果。**

```css
#container[data-device="2"] {
    position: relative;
}
#container[data-device="2"]::after{
      position:absolute;
      top: 0;
      left: 0;
      width: 200%;
      height: 200%;
      content:"";
      transform: scale(0.5);
      transform-origin: left top;
      box-sizing: border-box;
      border: 1px solid #333;
    }
}
复制代码
```

> 思路三：viewport 缩放来解决

这个思路就是对 meta 标签里几个关键属性下手：

```html
<meta name="viewport" content="initial-scale=0.5, maximum-scale=0.5, minimum-scale=0.5, user-scalable=no">
```

这里针对像素比为2的页面，把整个页面缩放为了原来的1/2大小。这样，本来占用2个物理像素的 1px 样式，现在占用的就是标准的一个物理像素。根据像素比的不同，这个缩放比例可以被计算为不同的值，用 js 代码实现如下：
```javascript
const scale = 1 / window.devicePixelRatio;
// 这里 metaEl 指的是 meta 标签对应的 Dom
metaEl.setAttribute('content', `width=device-width,user-scalable=no,initial-scale=${scale},maximum-scale=${scale},minimum-scale=${scale}`);
```

这样解决了，但这样做的副作用也很大，整个页面被缩放了。这时 1px 已经被处理成物理像素大小，这样的大小在手机上显示边框很合适。但是，一些原本不需要被缩小的内容，比如文字、图片等，也被无差别缩小掉了。
### 118. 绝对定位和浮动有什么异同？
> 1. 都会脱离文档流，改变元素盒子类型，将元素变为块级
> 1. 都会创建 _BFC_
> 1. 不同点在于对包含块的定义、兄弟元素间的影响、可摆放的位置、能否设置 _z-index_

### 120. 文本“强制换行”的属性是什么？ 
> _word-break: break-all_;

### 121. 阅读代码，分析最终执行结果 _div_ 的水平、垂直位置距离。
```css
 div{
   width: 200px;
   height: 100px;
   padding: 10px;
   transform: translate(50%, 50%);
 }
```
>  水平位移 _110px_ 垂直位移 _60px_。水平方向参照的是元素的宽度，处置方向参照的是元素的高度。_HTM_L 元素默认都以标准盒模型，当元素存在内边距，计算时还要包含内边距。即 _220_ 的 _50%_ 和 _120_ 的 _50%_。


### 122. 设置了元素的过渡后需要有触发条件才能看到效果，列举出可用的触发条件。 
> 1. _:hover 、:checked_ 等伪类
> 1. 媒体查询，当改变窗口尺寸触发
> 1. _js_ 触发，用脚本更改元素样式

### 123. 怎样把背景图附着在内容上？
> _background-attachment: fixed;_

### 124. _CSS_ 优化、提高性能的方法有哪些？
> 1. 最好使用表示语义的名字。一个好的类名应该是描述他是什么而不是像什么
> 1. 避免 _!important_，可以选择其他选择器
> 1. 使用紧凑的语法
> 1. 避免不必要的命名空间
> 1. 尽可能的精简规则，你可以合并不同类里的重复规则

### 125. 网页中应该使用奇数还是偶数的字体？ 
> **偶数。偶数字号相对更容易与 **_**web**_** 设计的其他部分构成比例关系**

### 126. _margin_ 和 _padding_ 分别适合什么场景使用？ 
> - 使用 _margin_：需要在 _border_ 外侧添加空白、空白处不需要背景色、上下相连的两个盒子之间的空白，需要相互抵消时。
> - 使用 _padding_: 需要在 _border_ 内侧添加空白、空白处需要背景色

### 127. 对于 _line-height_ 是如何理解的？
> - 行高指一行文字的高度，两行文字间基线与基线之间的距离。在 CSS 中，起高度作用的是 _height_ 和 _line-height_
> - 使用行高等于高的方式可以实现单行文字垂直居中
> - 将 _display_ 设置为 _inline-block_ 可以实现多行文本居中

### 128. 如何让 _Chrome_ 支持小于 12px 的文字？ 
> 可以配合 _CSS3_ 中的 _transform_  scale属性来实现

### 129. 如果需要手动写动画，你认为最小时间间隔是多久？
> 多数显示器默认频率是 60_Hz_，即 1_s_ 刷新 60 次，理论上最小间隔为 1/60*1000_ms_ = 16.7_s_ 

### 131. _style_ 标签写在 _body_ 后面与 _body_ 前面有什么区别？
> 页面加载自上而下，当然是先加载样式。写在 _body_ 标签后由于浏览器以逐行方式对 _HTML_ 文档进行解析，当**解析到写在尾部的样式表（外联或写在 **_**style**_** 标签）会导致浏览器停止之前的渲染，等待加载且解析样式表完成之后重新渲染**

### css 如何做一个 loading 动画（关键帧、动画循环）

### left和margin-left哪性能好
left：脱离文档流
### 心跳
```html
<html>
<head>
    <title>demo</title>
    <style type="text/css">
    	*{
    		padding: 0;
    		margin: 0;
    	}
    	body{
    		width: 100vw;
    		height: 100vh;
    		justify-content: center;
    		align-items: center;
    		display: flex;
    	}
    	.love{
    		width: 200px;
    		height: 200px;
    		background: red;
    		position: relative;
            transform: rotate(45deg);
            animation: heartbit 1s infinite;
    	}
    	.love::after, .love::before{
    		content: "";
    		position: absolute;
    		left: 0;
    		top: 0;
    		width: 100%;
    		height: 100%;
    		border-radius: 50%;
            background: red;
    	}
    	.love::after {
    		/*background: blue;*/
    		left: -100px;
    	}
    	.love::before {
    		/*background: blue;*/
    		top: -100px;
    	}

        @keyframes heartbit{
            0%{
                width: 200px;
                height: 200px;
            }
            20%{
                width: 230px;
                height: 230px;
            }
            100%{
                width: 200px;
                height: 200px;
            }
        }
    </style>
</head>
<body>
    <div class="love"></div>
</body>
</html>
```

### 如何写一个移动端html抖音界面和刷视频的功能实现 【手撕代码】 

### flex骰子

```html
<!DOCTYPE html>

<html lang="en">
  <head>
    <meta charset="UTF-8" />

    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <title>骰子布局</title>

    <style>
      body {
        display: flex;
        justify-content: space-around;
      }

      body > div {
        display: flex;

        width: 100px;

        height: 100px;

        border-radius: 4px;

        border: 2px solid red;

        box-sizing: border-box;
      }

      p {
        width: 15px;

        height: 15px;

        background-color: black;

        border-radius: 50%;

        margin: 2px;
      }

      .div1 {
        justify-content: center;

        align-items: center;
      }

      .div2 {
        justify-content: space-around;

        flex-direction: column;

        align-items: center;
      }

      .div3 {
        justify-content: space-around;

        align-items: center;

        padding: 10px;
      }

      .div3 p:first-child {
        align-self: flex-start;
      }

      .div3 p:last-child {
        align-self: flex-end;
      }

      .div4 {
        justify-content: space-around;

        flex-direction: column;

        align-items: center;
      }

      .div4 div {
        display: flex;

        width: 100%;

        justify-content: space-around;
      }

      .div4 p {
        align-self: center;
      }

      .div8 {
        flex-wrap: wrap;

        padding: 2px;
      }

      .div8 div {
        display: flex;

        justify-content: space-between;

        align-items: center;

        flex-basis: 100%;
      }
    </style>
  </head>

  <body>
    <!--骰子1-->

    <div class="div1">
      <p></p>
    </div>

    <!--骰子2-->

    <div class="div2">
      <p></p>

      <p></p>
    </div>

    <!--骰子3-->

    <div class="div3">
      <p></p>

      <p></p>

      <p></p>
    </div>

    <!--骰子4-->

    <div class="div4">
      <div>
        <p></p>

        <p></p>
      </div>

      <div>
        <p></p>

        <p></p>
      </div>
    </div>

    <!--骰子5-->

    <div class="div4">
      <div>
        <p></p>

        <p></p>
      </div>

      <div>
        <p></p>
      </div>

      <div>
        <p></p>

        <p></p>
      </div>
    </div>

    <!--骰子6-->

    <div class="div4">
      <div>
        <p></p>

        <p></p>
      </div>

      <div>
        <p></p>

        <p></p>
      </div>

      <div>
        <p></p>

        <p></p>
      </div>
    </div>

    <!--骰子7-->

    <div class="div4">
      <div>
        <p></p>

        <p></p>

        <p></p>
      </div>

      <div>
        <p></p>
      </div>

      <div>
        <p></p>

        <p></p>

        <p></p>
      </div>
    </div>

    <!--骰子8-->

    <div class="div8">
      <div>
        <p></p>

        <p></p>

        <p></p>
      </div>

      <div>
        <p></p>

        <p></p>
      </div>

      <div>
        <p></p>

        <p></p>

        <p></p>
      </div>
    </div>

    <!--骰子9-->

    <div class="div4">
      <div>
        <p></p>

        <p></p>

        <p></p>
      </div>

      <div>
        <p></p>

        <p></p>

        <p></p>
      </div>

      <div>
        <p></p>

        <p></p>

        <p></p>
      </div>
    </div>
  </body>
</html>
```
### 常见的CSS布局单位
**三者的区别：**

- px是固定的像素，一旦设置了就无法因为适应页面大小而改变。
- em和rem相对于px更具有灵活性，他们是相对长度单位，其长度不是固定的，更适用于响应式布局。
- em是相对于其父元素来设置字体大小，这样就会存在一个问题，进行任何元素设置，都有可能需要知道他父元素的大小。而rem是相对于根元素，这样就意味着，只需要在根元素确定一个参考值。

**使用场景：**

- 对于只需要适配少部分移动设备，且分辨率对页面影响不大的，使用px即可 。
- 对于需要适配各种移动设备，使用rem，例如需要适配iPhone和iPad等分辨率差别比较挺大的设备。

**（2）百分比**（`%`），当浏览器的宽度或者高度发生变化时，通过百分比单位可以使得浏览器中的组件的宽和高随着浏览器的变化而变化，从而实现响应式的效果。一般认为子元素的百分比相对于直接父元素。
**（3）em和rem**相对于px更具灵活性，它们都是相对长度单位，它们之间的区别：**em相对于父元素，rem相对于根元素**

- **em：** 文本相对长度单位。相对于当前对象内文本的字体尺寸。如果当前行内文本的字体尺寸未被人为设置，则相对于浏览器的默认字体尺寸(默认16px)。(相对父元素的字体大小倍数)。
- **rem：** rem是CSS3新增的一个相对单位，相对于根元素（html元素）的font-size的倍数。**作用**：利用rem可以实现简单的响应式布局，可以利用html元素中字体的大小与屏幕间的比值来设置font-size的值，以此实现当屏幕分辨率变化时让元素也随之变化。

**（4）vw/vh**是与视图窗口有关的单位，vw表示相对于视图窗口的宽度，vh表示相对于视图窗口高度，除了vw和vh外，还有vmin和vmax两个相关的单位。

- vw：相对于视窗的宽度，视窗宽度是100vw；
- vh：相对于视窗的高度，视窗高度是100vh；
### img的style里面有important怎么覆盖掉 
### 实现一个布局1+（2，3，4（4是在3的右上角）flex
### 移动端的点击事件的有延迟，时间是多久，为什么会有？ 怎么解决这个 延时？ 
移动端点击有 300ms 的延迟是因为移动端会有双击缩放的这个操作，因此浏览器在 click 之 后要等待 300ms，看用户有没有下一次点击，来判断这次操作是不是双击。 
有三种办法来解决这个问题： 
1.通过 meta 标签禁用网页的缩放。 
2.通过 meta 标签将网页的 viewport 设置为 ideal viewport。 

### 一个span能不能改变长宽高。 --行元素不能改变宽高  假如span已经被position设置好了，能不能改变长宽高 
可以改变的 
### 实现内容多时页面滑动，内容少时保持占据一页
min-height 
### base64优缺点
### 用font-weight和b标签有什么区别
seo
### 移动端fastclick原理是什么 
### grid布局
### 判断元素是否到达可视区域
> - `window.innerHeight` 是浏览器可视区的高度；
> - `document.body.scrollTop || document.documentElement.scrollTop` 是浏览器滚动的过的距离；
> - `imgs.offsetTop` 是元素顶部距离文档顶部的高度（包括滚动条的距离）；
> - 内容达到显示区域的：`img.offsetTop < window.innerHeight + document.body.scrollTop;`
> 
![image.png](https://cdn.nlark.com/yuque/0/2021/png/758572/1638239712970-7828a984-2f2f-4c9f-8473-9e1f42fc4b45.png#clientId=uc6644940-dc60-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=302&id=KZp4Q&margin=%5Bobject%20Object%5D&name=image.png&originHeight=1372&originWidth=1970&originalType=binary&ratio=1&rotation=0&showTitle=false&size=195435&status=done&style=none&taskId=u48d09bc6-eadd-4281-9f94-de329aa4dc5&title=&width=433)
>    ![image.png](https://cdn.nlark.com/yuque/0/2021/png/758572/1638239721307-09f30b47-b9a6-45ff-b5a6-561f5d4cafdc.png#clientId=uc6644940-dc60-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=124&id=rMLmY&margin=%5Bobject%20Object%5D&name=image.png&originHeight=358&originWidth=680&originalType=binary&ratio=1&rotation=0&showTitle=false&size=29226&status=done&style=none&taskId=u94087427-4a05-4354-aa02-c6a8cb9b4e2&title=&width=236)


### 富文本编辑器，文本设置大小不同，怎么设置line-height 
### translate可以设置x y，如果右边也有一个元素，右边元素会不会被挤掉。 
### 图片尺寸不固定（可能比盒子大，小），盒子长宽固定，图片比盒子大，希望长宽达到100%（等比缩放），比盒子小，希望垂直居中。两个class，一个针对图片大，一个针对图片小，js获取图片大小，更改class 

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
      .container{
        width: 600px;
        height: 500px;
        margin: 40px auto;
        border: 1px solid #000;
        text-align: center;
        line-height: 600px;
        font-size: 0;

      }
      .container img{
        max-width: 100%;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <img src="微信图片_20210709201030.png" alt="">
    </div>
  </body>
</html>
```
> ### rem原理 ，rem怎么计算出来的 

> rem计算 基于跟元素做的转换。1rem=37.5px
> css3中的rem单位，表示相对于网页根元素的字体大小。
> 设置html元素：font-size: 13.3333vw
> 从此后，所有需要弹性缩放的尺寸均要使用rem单位，具体的值为设计稿像素值/100 rem
> 例如：某张图片在设计稿中的宽度为152px，则在页面中的宽度为1.52rem

### 
### 清除图片下方出现像素空白间隙
> 行级块元素：行级元素有默认的行高Line-height:normal含有默认的垂直方向的对齐方式
> 方法1：vertical-align: bottom; 
> 方法2：父级line-height: 1px; 
> 方法3：display:block

### 说一下SEO优化
> （1）合理的 title、description、keywords
> （2）语义化的 HTML 代码，符合 W3C 规范：语义化代码让搜索引擎容易理解网页。 （3）重要内容 HTML 代码放在最前
> （4）重要内容不要用 js 输出：爬虫不会执行 js 获取内容 
> （5）少用 iframe
> （6）非装饰性图片必须加 alt 
> （7）提高网站速度：网站速度是搜索引擎排序的一个重要指标


### 浏览器乱码的原因是什么？如何解决？
> **产生乱码的原因：**
> - 网页源代码是gbk的编码，而内容中的中文字是utf-8编码的，这样浏览器打开即会出现html乱码，反之也会出现乱码；
> - html网页编码是gbk，而程序从数据库中调出呈现是utf-8编码的内容也会造成编码乱码；
> - 浏览器不能自动检测网页编码，造成网页乱码。
> 
**解决办法：**
> - 使用软件编辑HTML网页内容；
> - 如果网页设置编码是gbk，而数据库储存数据编码格式是UTF-8，此时需要程序查询数据库数据显示数据前进程序转码；
> - 如果浏览器浏览时候出现网页乱码，在浏览器中找到转换编码的菜单进行转换。

### head 标签有什么作用，其中什么标签必不可少？
> 标签用于定义文档的头部，它是所有头部元素的容器。 中的元素可以引用脚本、指示浏览器在哪里找到样式表、提供元信息等。
> 文档的头部描述了文档的各种属性和信息，包括文档的标题、在 Web 中的位置以及和其他文档的关系等。绝大多数文档头部包含的数据都不会真正作为内容显示给读者。
> 下面这些标签可用在 head 部分：<base>, <link>, <meta>, <script>, <style>, <title>。
> 其中 <title> 定义文档的标题，它是 head 部分中唯一必需的元素。


### 对line-height 的理解及其赋值方式
> **（1）line-height的概念：**
> - line-height 指一行文本的高度，包含了字间距，实际上是下一行基线到上一行基线距离；
> - 如果一个标签没有定义 height 属性，那么其最终表现的高度由 line-height 决定；
> - 一个容器没有设置高度，那么撑开容器高度的是 line-height，而不是容器内的文本内容；
> - 把 line-height 值设置为 height 一样大小的值可以实现单行文字的垂直居中；
> - line-height 和 height 都能撑开一个高度；
> 
**（2）line-height 的赋值方式：**
> - 带单位：px 是固定值，而 em 会参考父元素 font-size 值计算自身的行高
> - 纯数字：会把比例传递给后代。例如，父级行高为 1.5，子元素字体为 18px，则子元素行高为 1.5 * 18 = 27px
> - 百分比：将计算后的值传递给后代

### z-index属性在什么情况下会失效
> 通常 z-index 的使用是在有两个重叠的标签，在一定的情况下控制其中一个在另一个的上方或者下方出现。z-index值越大就越是在上层。z-index元素的position属性需要是relative，absolute或是fixed。
> 
> z-index属性在下列情况下会失效：
> 
> - 父元素position为relative时，子元素的z-index失效。解决：父元素position改为absolute或static；
> - 元素没有设置position属性为非static属性。解决：设置该元素的position属性为relative，absolute或是fixed中的一种；
> - 元素在设置z-index的同时还设置了float浮动。解决：float去除，改为display：inline-block；

### z-index工作原理和适用范围
文档流 定位
### CSS环形进度条
[https://www.cnblogs.com/jr1993/p/4677921.html](https://www.cnblogs.com/jr1993/p/4677921.html)
### 不考虑其它因素，下面哪种的渲染性能比较高?

```css
.box a{
}
a{}
阿里：浏览器查询从右往左
2性能好，只查询a,1不但查询所有a,还要查询.box下的所有a
```

### script标签中defer和async的区别

如果没有defer或async属性，浏览器会立即加载并执行相应的脚本。它不会等待后续加载的文档元素，读取到就会开始加载和执行，这样就阻塞了后续文档的加载。
**defer 和 async属性都是去异步加载外部的JS脚本文件，它们都不会阻塞页面的解析**，其区别如下：

- **执行顺序：** 多个带async属性的标签，不能保证加载的顺序；多个带defer属性的标签，按照加载顺序执行；
- **脚本是否并行执行：*_async属性，表示*_后续文档的加载和执行与js脚本的加载和执行是并行进行的**，即异步执行；defer属性，加载后续文档的过程和js脚本的加载(此时仅加载不执行)是并行进行的(异步)，js脚本需要等到文档所有元素解析完成之后才执行，DOMContentLoaded事件触发执行之前。
### 10. HTML5的离线储存怎么使用，它的工作原理是什么
离线存储指的是：在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。

**原理：**HTML5的离线存储是基于一个新建的 `.appcache` 文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像cookie一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示

**使用方法：** （1）创建一个和 html 同名的 manifest 文件，然后在页面头部加入 manifest 属性：

```html
<html lang="en" manifest="index.manifest">
复制代码
```

（2）在 `cache.manifest` 文件中编写需要离线存储的资源：

```html
CACHE MANIFEST
    #v0.11
    CACHE:
    js/app.js
    css/style.css
    NETWORK:
    resourse/logo.png
    FALLBACK:
    / /offline.html
复制代码
```

- **CACHE**: 表示需要离线存储的资源列表，由于包含 manifest 文件的页面将被自动离线存储，所以不需要把页面自身也列出来。
- **NETWORK**: 表示在它下面列出来的资源只有在在线的情况下才能访问，他们不会被离线存储，所以在离线情况下无法使用这些资源。不过，如果在 CACHE 和 NETWORK 中有一个相同的资源，那么这个资源还是会被离线存储，也就是说 CACHE 的优先级更高。
- **FALLBACK**: 表示如果访问第一个资源失败，那么就使用第二个资源来替换他，比如上面这个文件表示的就是如果访问根目录下任何一个资源失败了，那么就去访问 offline.html 。

（3）在离线状态时，操作 `window.applicationCache` 进行离线缓存的操作。

**如何更新缓存：**

（1）更新 manifest 文件

（2）通过 javascript 操作

（3）清除浏览器缓存

**注意事项：**

（1）浏览器对缓存数据的容量限制可能不太一样（某些浏览器设置的限制是每个站点 5MB）。

（2）如果 manifest 文件，或者内部列举的某一个文件不能正常下载，整个更新过程都将失败，浏览器继续全部使用老的缓存。

（3）引用 manifest 的 html 必须与 manifest 文件同源，在同一个域下。

（4）FALLBACK 中的资源必须和 manifest 文件同源。

（5）当一个资源被缓存后，该浏览器直接请求这个绝对路径也会访问缓存中的资源。

（6）站点中的其他页面即使没有设置 manifest 属性，请求的资源如果在缓存中也从缓存中访问。

（7）当 manifest 文件发生改变时，资源请求本身也会触发更新。

### 浏览器是如何对 HTML5 的离线储存资源进行管理和加载？

- **在线的情况下**，浏览器发现 html 头部有 manifest 属性，它会请求 manifest 文件，如果是第一次访问页面 ，那么浏览器就会根据 manifest 文件的内容下载相应的资源并且进行离线存储。如果已经访问过页面并且资源已经进行离线存储了，那么浏览器就会使用离线的资源加载页面，然后浏览器会对比新的 manifest 文件与旧的 manifest 文件，如果文件没有发生改变，就不做任何操作，如果文件改变了，就会重新下载文件中的资源并进行离线存储。
- **离线的情况下**，浏览器会直接使用离线存储的资源。

-  Flex布局原理 
-  px, rem, em的区别
网页的三层结构有哪些
-请简述媒体查询
- flex:1的1代表什么?闭包,作用域,内存?
```html
<meta http-equiv='X-UA-Compatible' content='lE=edge,chrome=1'/>`作用是什么?
```
项目中音频加载不出来时的优化处理
实现一个球一个白板，实现画笔的功能实现

2. css 上下固定为 100px，中间为自适应高度
2.  Base64 在 html 中的缺点 
2.  500 张图片，如何实现预加载优化 

已知如下代码，如何修改才能让图片宽度为 300px ? 注意下面代码不可修改

```html
<img src="1.jpg" style="width:480px!important;”> 
答:max-width: 300pxtransform: scale(0.625,0.625)
```

- css中的position取值，及区别（字节2020实习）
- 盒模型  top:50%,margin-top:50%,相对什么计算的（字节2020实习）
- 怎么求的盒子的总尺寸（字节2020实习）
- translate的优点（字节2020实习）
- 实现一个球（字节2020校招）
- 一个白板，实现画笔的功能（字节2020校招）
- h5新出的api（字节2020校招）
- 使用cookie，怎么使用？（字节2020校招）
- cookie和localStorage区别，其中说到了 expires 过期时间（字节2020校招）
- CSS哪些属性可以加速GPU？除了absolute、fixed呢？（字节2020校招）
- 重绘重排，什么时候触发重排，transform会触发重排么？为什么？（字节2020校招）
- flex：1 表示什么？详细说下，详细问了 flex-baisit（字节2020校招）
- css左右两栏固定，中间自适应布局怎么做？（字节2020校招）
- 回流重绘的概念和如何减少回流成本（字节2020校招）
- 三列布局（字节2020校招）
- css实现宽高等比例（字节2020校招）
- 说说z-index有什么需要注意的地方，z-index: 0 和z-index：1的区别，z-index为0和1哪个元素在上面
- 三栏布局，说出你能想到的所有方案
- 垂直居中，写出你知道的所有方案
- 两个div，都给margin：20px，这两个div的间距是多少？为什么会产生这种问题？怎么解决？（BFC）
- css画等边三角形（腾讯2020实习）
- css单位有哪些, em如果父元素没有设置font-size呢，如果一直往上找也没有呢（腾讯2020实习）
- 怎么做适配？ （百度2020校招）
- rem？flex?（百度2020校招）
- h5页面白屏（百度2020校招）
- rem和px的区别？（百度2020校招）
- 1px问题的解决？（百度2020校招）

## CSS自适应正方形

> 双重嵌套，外层 relative，内层 absolute


```html
<div class="outer">
  <div class="inner"></div>
</div>
```

```css
.outer {
  padding-top: 50%;
  width: 50%;
  position: relative;
}

.inner {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  background: blue;
}
```

> vw vh


```css
.inner {
  width: 10vw;
  height: 10vw;
  background: blue;
}
```

> css div 垂直水平居中，并完成 div 高度永远是宽度的一半（宽度可以不指定）


```html
<div class="outer">
  <div class="inner">
    <div class="box">hello</div>
  </div>
</div>
```

```css
* {
  margin: 0;
  padding: 0;
}

html,
body {
  width: 100%;
  height: 100%;
}

.outer {
  width: 400px;
  height: 100%;
  background: blue;
  margin: 0 auto;

  display: flex;
  align-items: center;
}

.inner {
  position: relative;
  width: 100%;
  height: 0;
  padding-bottom: 50%;
  background: red;
}

.box {
  position: absolute;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

> padding 撑高画正方形


```css
.outer {
  width: 400px;
  height: 600px;
  background: blue;
}

.inner {
  width: 100%;
  height: 0;
  padding-bottom: 100%;
  background: red;
}
```

```html
<div class="outer">
  <div class="inner"></div>
</div>
```


CSS flex: 1 有什么效果
多行超出自动省略号：Clamp.js
css3怎么创建逐帧动画 

- CSS动画，transition和animation，哪一个性能更好

为什么transform可以减少回流
> translate的优点
>    - 不会脱离文档流
>    - 对gpu也比较友好

flex原理
flex: 1 1 0; 的三个值分别指的是什么？
用css实现立方体，注意，是立方体。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>立方体</title>
</head>
<style>
    #cube {
        width: 300px;
        height: 300px;
        font-size: 80px;
        text-align: center;
        line-height: 300px;
        transform: rotateY(-30deg) rotateX(-35deg);
        transform-style: preserve-3d;
        margin: 300px auto;
    }

    #cube>div {
        width: 300px;
        height: 300px;
        position: absolute;
        left: 0;
        top: 0;
        opacity: 0.5;
    }

    #cube .flat1 {
        background-color: red;
        transform: translateY(-150px) rotateX(90deg);
    }

    #cube .flat2 {
        background-color: orange;
        transform: translateY(150px) rotateX(90deg);
    }

    #cube .flat3 {
        background-color: yellow;
        transform: translateX(-150px) rotateY(90deg);
    }

    #cube .flat4 {
        background-color: green;
        transform: translateX(150px) rotateY(90deg);
    }

    #cube .flat5 {
        background-color: lightgreen;
        transform: translateZ(150px);
    }

    #cube .flat6 {
        background-color: blue;
        transform: translateZ(-150px);
    }
</style>

<body>
    <div id="cube">
        <div class="flat1">上</div>
        <div class="flat2">下</div>
        <div class="flat3">左</div>
        <div class="flat4">右</div>
        <div class="flat5">前</div>
        <div class="flat6">后</div>
    </div>

</body>

</html>
```

rem用过吗？做不同手机的适配怎么做？

- scss实现循环变换颜色

\7. 1px像素

怎么优化 h5 的加载速度,怎么实现 h5 页面秒开？

> [https://juejin.cn/post/7065235287781146654](https://juejin.cn/post/7065235287781146654)
>  
> [https://www.infoq.cn/article/2ETO4QYx82gd1LVfY56A](https://www.infoq.cn/article/2ETO4QYx82gd1LVfY56A)

!important什么时候会使用，什么情况下改不掉样式（内联） 
移动端：

> rem、em、px
> 如何实现 1px 在手机上？使用 transform: scale() + width/height * 2 
>  
> rem：相对于根元素（html）的字体大小。
>  
> em：相对于父元素字体大小。浏览器默认字体尺寸 1em=16px。在body里设置font-size:62.5%则全局1em=10px。
>  
> px：相对于当前显示器屏幕分辨率。
>  
> 如何在移动端实现1像素细线
>  
> rem,em啥区别
>  
> em和rem如何适配？有啥区别？还有其他适配的办法吗？
>  
> 10.CSS的尺寸单位，分别介绍一下；移动端适配可以用哪些单位？
>  
> 如何实现 1px 在手机上？使用 transform: scale() + width/height * 2   **移动端1px问题**
>  
> rem，em。
设备像素占比
>  
> 怎么实现移动端的布局？
>  
> 说一下根结点的字体大小怎么确定
>  
> 点透问题。为什么会有点透现象。
>  
> 3.如何提升移动端用户的使用体验，让用户能更快的看到页面
>  
> 第1个问题是viewport各个属性值的意义，以及如何实现不用viewport控制用户不能缩放，回答用js监听屏幕宽度。
>  
> em rem区别，rem缺点 css
>  
> 移动端原生代码屏幕适配
>  
> 移动端自适应有哪几种方法，优劣是什么


为什么设置font-weight是数字的时候作用会失效？因为用了一些特殊的字体，它们没有实现该粗细的字体

五星好评点几颗星亮几颗，用css

z-index 在什么情况下会失效

一个页面有头部、内容、尾部。想出多种方案，如果内容超过浏览器显示长度则隐藏尾部

离线包怎么更新？怎么知道需要打开哪个离线包？ .

transition的触发条件

> **第一种方式如上**, 使用伪类的方式触发, 包括`hover`,`focus`,`checked`等方式; 但是实际使用当中我们更多的是使用JS或者Jquery直接修改属性, 但是工作中发现这样不行.
>  
> **JS触发**: 如果使用JS或者Jquery直接修改CSS属性并不会触发渐变, JS的触发方式是`toggleClass`; 我的理解是必须元素发生什么改变使得它有了一些不同从而获取到一些新的属性, 对于伪类触发是这样, 对于JS触发方式应当是它的`class`发生改变以至于能够得到新的样式


对css3的剪切属性有了解吗

> background-clip:背景图片从哪块开始截断，从哪块以外的部分都不显示背景图片，即从哪块结束


requestAnimationFrame

> `**window.requestAnimationFrame()**` 告诉浏览器——你希望执行一个动画，并且要求浏览器在下次重绘之前调用指定的回调函数更新动画。该方法需要传入一个回调函数作为参数，**该回调函数会在浏览器下一次重绘之前执行**[https://developer.mozilla.org/zh-CN/docs/Web/API/Window/requestAnimationFrame](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/requestAnimationFrame)
>  
> 和setInterval的区别？


如何实现在图片被加载之前的占位符一个image，宽高比16:9

把一个矩形分成同样大小的正方形,最大边长是多少(用编程思维和数学思维)

float和position一起用是什么效果

H5页面中长列表在下拉过程中为什么会闪一下 ，如何解决？

查询css属性的时候会触发重排么 ？

flex布局 flex布局的原理，怎么理解主轴

回流和重绘机制 浏览器渲染机制是什么 我答：DOM、CSSOM -> 渲染树 -> 排列，布局 -> 绘制 追问：哪些操作会触发回流，位置和大小还有呢

BFC会与float元素相互覆盖吗？为什么？举例说明

浏览器如何构建和渲染页面

浏览器渲染上减少重绘和重排的一些操作，提到了使用opacity和z-index新建图层等。还提到了will-change，面试官说这个他不知道。

js动画相比，优势https://zh.javascript.info/js-animation

1.  一个盒子从中间开始，碰到最左边的边界往右移动，碰到最右边的边界往左移动，如此循环，问怎么做？ 
1.  用过canvas吗，如果要实现一个一笔一画写汉字的效果，应该怎么做？ 
1.  控制字体换行，大小写转换的属性？ [https://blog.csdn.net/qq_45799465/article/details/122667947](https://blog.csdn.net/qq_45799465/article/details/122667947)
transform:translateZ(0)的作用
margin/padding百分比如何计算
addEventListener存在什么问题
[https://blog.csdn.net/NewDayStudy/article/details/78656534](https://blog.csdn.net/NewDayStudy/article/details/78656534)
[https://blog.csdn.net/aa494661239/article/details/103404241?utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control](https://blog.csdn.net/aa494661239/article/details/103404241?utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromMachineLearnPai2~default-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromMachineLearnPai2~default-1.control)
1.3 removeEventListener
1.5 addEventListener的第三个参数
前端路由hash 和 history 模式的区别，以及history出现404的原因和解决方法 
   -  回流/重绘简单介绍 
   -  自问自答：如何避免这种情况，table的绘制时长 
   -  减少回流/重绘的触发
虚拟DOM，统一绘制 
   -  获取offsettop是否会触发回流和重绘（不会）
`last-child` 与 `last-of-type` 的差别 
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .box p:last-child{
            color:green;
        }
        .box1 p:last-of-type {
            color:red;
        }
    </style>
</head>
<body>
    <div class='box'>
        <p>p1</p>
        <p>p2</p>
        123
    </div>
  p会不会被选中。

    <div class="box1">
        <p>11</p>
        <p>22</p>
        <i>5555</i>
    </div>
</body>
</html>
```

为什么用float会影响性能
9.font-size:0可以清除两个行内块盒子空隙的原理
web 里面性能优化，从样式方面说。 

      1. 
    
      1.  移动端开发中，边框1px 问题，有的特别细有的特别粗。怎么解决？ 
         -  如果要生成海报，并能保存到本地。应该如何实现？
transform不准确 
            1. 先进行定位，再用transform，相对于自身的位移，怎么实现垂直居中呢？ 
               1. 父容器开启absolute，左上角移位，偏一点，在使用margin，-50%

边有40万人，另一边有60万人，这个村庄每天有100万通电话，假设每个人打给其他人电话的概率相同，问每天有多少通跨河电话2-3-5穷举 

盒模型 top:50%,margin-top:50%,相对什么计算的

clientWidth,offsetWidth,scrollWidth的区别

- clientWidth 元素可视区域的宽度 不包含滚动条
- offsetWidth 元素所占据的宽度 包含滚动条
- scrollWidth 元素没有滚动条时的宽度 包含里面所有内容展开的宽度有一道关于transform的题，transform-origin

加载JS资源、CSS资源对页面有什么影响吗（阻不阻塞）：JS资源，讲了async和defer；CSS资源是在啥时候解析的，会不会阻塞DOM结点的构建？（寄，我觉得是并行的）不会阻塞解析还是渲染？

CSS哪些元素可以继承？

结合media媒体查询，将html的font-size设置为 (屏幕宽度/设计图宽度)*16px

行内元素： margin、padding左右有效，上下无效 ,不能包含其他元素

为什么css要使用字面量。(从渲染流程解释，在计算样式的阶段可以减少标准化css样式表的时间)

为什么transform和opacity能够优化动画。(transform生成的图层会直接交给合成线程，不影响主线程，不会发送回流和重绘)

- 页面的回流和重绘知道吗？有什么区别？（回流必重绘，重绘不一定回流，回答了一下什么是回流，什么是重绘，这点之前看过文章，结合dom tree和css rules结合的render tree相关知识，*_说的还是比较好的*_）
- 有什么好的办法优化页面渲染？（这个答得很烂，提了一些感觉不在点子上，说了一下少用css嵌套，css继承的属性不用重复设置，合并css文件，图标类用css spires？是不是这样拼的我也忘记了，只用加载一个大的图，大图中定位小的图标的一种技术）

4.实现一个单行容器内：左边一行文字，右边一个btn，文字边长过程中，不会把btn挤下去，而是文字超出省略

```html
#wrapper {
  display: flex;
}

#text {
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
  flex: 1;
}

<div id="wrapper">
  <div id="text">
    长文本长文dbsgvkjdabkajgbkjdalbsgkljfbkljadsbgkbadskljbgkljadsb hewfoihngfewakjoh ;ewoia 
  </div>
  <button>test</button>
</div>
```

说说block元素和in-line元素？ 二者的不同点和特征有哪些?

扩展：img是行内元素吗？为什么可以设置宽高呢

> img确实是行内元素 但它也是置换元素 。置换元素就是浏览器根据元素的标签和属性，来决定元素的具体显示内容。例如浏览器会根据标签的src属性的值来读取图片信息并显示出来，而如果查看(X)HTML代码，则看不到图片的实际内容；又例如根据标签的type属性来决定是显示输入框，还是单选按钮等。所以 img  input  select  textarea  button  label 等，他们被称为可置换元素（Replaced element）。他们区别一般inline元素是：这些元素拥有内在尺寸 内置宽高 他们可以设置width/height属性。他们的性质同设置了display:inline-block的元素一致。


scale(0.5) scale(2) scale(1) 分别是怎么样的 ，那scale(-1)呢 scale(x) 当x为负值时，整个是颠倒过来的】

屏幕正中间有个元素A, 随着屏幕宽度的增加，
始终需要满足以下条件：

- A元素垂直居中于屏幕***；
- A元素距离屏幕左右边距各10px；
- A元素里面的文字”A”的font-size:20px；水平垂直居中;
- A元素的高度始终是A元素宽度的50%; (如果搞不定可以实现为A元素的高度固定为200px;)

实现一个左右布局，左边固定100PX，右边可伸缩，高度沾满整个屏幕。右侧正中间有个长方形，长方形长宽比4：3，长是父元素的50%

元素层叠顺序是如何计算的

百分比translate是根据什么值计算的

display:inline-block元素和父元素上下存在间隙，产生原因及解决方案

css文件加载的话会阻塞dom树渲染吗？会阻塞渲染树吗？

css为什么要从右往左匹配；

absolution计算时包括父元素margin吗？（把margin换成padding）

css性能优化

absolute和relative对于重排重绘 那个性能好点
