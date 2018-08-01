# awesome-web
[![licensebuttons by](https://licensebuttons.net/l/by/3.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)  
web常见知识（问题）整理，可以作为日常自测使用，提供的答案和文章仅供学习和参考，不作为权威解释。对于有问题的，欢迎指正。
> 部分涉及的文章和链接版权归原作者所有，如有侵权，请联系删除。

## JS
- js的基本类型  
JavaScript 内置了7种类型：null, undefined , boolean, number, string, object以及 symbol (ES6).
```js
typeof 0              // number
typeof true           // boolean
typeof 'Hello'        // string
typeof Math           // object
typeof null           // object  !!
typeof Symbol('Hi')   // symbol (New ES6) 
```

- 闭包和闭包用途  
**闭包**是指有权访问另一个函数作用域中的变量的函数。
> 注意闭包和匿名函数的区别。

参考资料：
> * JavaScript高级程序设计（第3版） 7.2闭包

- 原型链
- 作用域链，结合this说明


- 改变this指向的方法  
> 1. call()
> 2. apply()
> 3. 使用箭头函数
> 4. bind()

思考：with 语句用于设置代码在特定对象中的作用域，那么with是否能改变this指向？
```js
var sMessage = "hello";
with(sMessage) {
  console.log(this) // this  ---> window
  alert(toUpperCase());	//输出 "HELLO"
}
```
是不可以的。


- call 和 apply 的区别  
都能改变this指向，区别是参数不同。  
```js
call(obj, arg1, arg2);
// apply 接收的第二个参数是数组
apply(obj, [arg1, arg2])
```

- Debounce & Throttle（去抖和节流）
```
debounce：将触发频繁的事件合并成一次执行。debounce适用于诸如input事件，当用户输入时需要响应ajax请求，多次input只响应一次回调方法
throttle： 设置一个阀值，在阀值内，将触发的事件合并成一次执行；且当到达阀值，必定执行一次事件。throttle适用于resize或者鼠标移动事件，防止浏览器频繁响应事件，严重拉低性能

原文: http://ghmagical.com/article/page/id/4qrB9JeihTKD © ghmagical.com

```
参考：  
[Debounce vs Throttle](https://segmentfault.com/a/1190000010205669)  
[函数去抖(debounce)与函数节流(throttle)](https://juejin.im/post/5ada1b9f518825673b61946d)  


- 一些常用方法的polyfill  
要熟悉一些基础方法的使用和实现方式，如：[Array.prototype.reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

- ES6+ 用过哪些
- Promise
- async/ await


- ajax如何上传文件  
主要是使用 `FormData()`方法。  
具体可参考：[通过Ajax方式上传文件(input file)，使用FormData进行Ajax请求](https://www.cnblogs.com/LoveTX/p/7081515.html)

- fetch 与 ajax 的区别  
ajax 是使用 `XMLHttpRequest` 对象来请求数据。  
fetch是 window的一个方法，基于 Promise来处理结果/回调。  
fetch返回的promise不会拒绝HTTP错误状态（404,500），仅在网络故障或任何阻止请求完成时，才会拒绝。  

参考： 
[ajax](http://www.runoob.com/ajax/ajax-xmlhttprequest-send.html)  
[fetch和ajax比较](https://www.cnblogs.com/September-9/p/7099975.html)

- ajax 是否可以设置请求头  
可以通过 `setRequestHeader`设置请求头，但不是什么都可以设置的。
具体参考：[ajax中的setRequestHeader设置请求头](https://www.cnblogs.com/cdwp8/p/5157377.html)


- h5如何实现视频多倍播放  
```js
video.playbackRate = 2.0; // 主要是这一行代码
```
参考： [揭秘视频网站video视频倍速播放的实现](https://www.zhangxinxu.com/wordpress/2018/07/html5-video-double-speed-play/)

- 前端如何压缩图片  
核心使用 `canvas`的`drawImage()`方法实现
```javascript
var canvas = document.createElement('canvas');
var context = canvas.getContext('2d');
canvas.width = 400;
canvas.height = 300;
// 核心JS就这个
context.drawImage(img,0,0,400,300);
```
具体可参考：[HTML5 file API加canvas实现图片前端JS压缩并上传](https://www.zhangxinxu.com/wordpress/2017/07/html5-canvas-image-compress-upload/)


- 移动端300毫秒延迟/点击穿透的问题解决方法  
> 常见的解决办法是使用 FastClick 库，所以最好能够了解下其实现原理。  
下面的CSS声明可以用来避免浏览器300ms延时问题。
```css
html {
    touch-action: manipulation;
}
```
touch-action的属性可以参考：https://www.zhangxinxu.com/wordpress/2018/07/chrome-safari-touchmove-preventdefault-treated-as-passive/


- CMD、UMD和AMD
AMD：Asynchronous Module Definition，异步模块定义。requireJS就是AMD的实现。  
commonJS: Nodejs使用的规范。一个js文件就是一个模块。  
CMD：seajs推广而来的。  
UMD: Universal Module Definition，通用模块定义，用来表示模块定义的方式。当一个文件需要兼容不同的加载规范的时候，就可以使用UMD的方式定义。它兼容AMD和CommonJS规范，和浏览器全局变量形式。

参考：https://blog.csdn.net/Real_Bird/article/details/54869066

### React
- React的生命周期
> 16.3 新的生命周期和之前的生命周期不同点

```
去掉了3个方法:
componentWillMount
componentWillReceiveProps
componentWillUpdate
增加了2个方法:
static getDerivedStateFromProps(nextProps, prevState)
getSnapshotBeforeUpdate(prevProps, prevState)
更改了1个方法，增加了第3个参数:
componentDidUpdate(prevProps, prevState, snapshot)
```

参考：  
[图解ES6中的React生命周期](https://juejin.im/post/5a062fb551882535cd4a4ce3)  
[React V16.3生命周期](https://segmentfault.com/a/1190000014637616)


### Vue


### Angular

## CSS
- 盒模型  
```
（1）有两种： IE 盒子模型、W3C（标准）盒子模型；
（2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)；
（3）区  别： IE的content部分把 border 和 padding计算了进去（box-sizing: border-box）, W3C 是 content-box;
```

- css优先级  
选择器**特指度** 用来度量css选择器识别元素的精确性。用(a, b, c, d)标识特指度。
> 用style属性应用样式，a =1,否则 a=0;  
> b 为ID选择器的数量；  
> c 为类选择器、属性选择器和伪类的数量  
> d 为类型选择器和伪元素的数量
比较特指度时，左侧的选择器特指度最高。(1,0,0,0)高于(0,1,1,3)，(0,1,1,3)高于(0,1,1,1)

如果一个元素的样式对应的两个特指度相同，那么在样式表中靠声明的属性优先级较高。  
行内style优先级高于特指度  
!important 优先级更高，如果有多个!important，最后声明的优先级高。  

参考：《css: 样式表性能调优》 第2章 级联

- position 有哪些值？都有哪些作用
```
absolute
生成绝对定位的元素，相对于值不为 static的第一个父元素进行定位。
fixed （老IE不支持）
生成绝对定位的元素，相对于浏览器窗口进行定位。
relative
生成相对定位的元素，相对于其正常位置进行定位。
static
默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right z-index 声明）。
inherit
规定从父元素继承 position 属性的值。
```
- 清除浮动的方法  
清除浮动是为了清除使用浮动元素产生的影响。浮动的元素，高度会塌陷，而高度的塌陷使我们页面后面的布局不能正常显示。
```css
#container::after{
  content:"";
  display:block;
  clear:both;
}
```

- css层级规则

- px、rem、em区别

## HTML
- H5有哪些新特性？


## Node
- 如何实现上传下载功能


## HTTP
- post 和 get 区别？还有哪些其他的请求方法？


- HTTP与 HTTPS 的区别？
```
1、https协议需要到ca申请证书，一般免费证书较少，因而需要一定费用。
2、http是超文本传输协议，信息是明文传输，https则是具有安全性的ssl加密传输协议。
3、http和https使用的是完全不同的连接方式，默认端口也不一样，前者是80，后者是443。
4、http的连接很简单，是无状态的；HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，比http协议安全。
5、HTTPS可以有效的防止运营商劫持，解决了防劫持的一个大问题。
```
参考：https://www.cnblogs.com/wqhwe/p/5407468.html

## 综合性
- 在浏览器输入一个URL，会发生什么？