# awesome-web
[![licensebuttons by](https://licensebuttons.net/l/by/3.0/88x31.png)](https://creativecommons.org/licenses/by/4.0)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)  
web常见知识（问题）整理，可以作为日常自测使用，提供的答案和文章仅供学习和参考，不作为权威解释。对于有问题的，欢迎指正。
> 部分涉及的文章和链接版权归原作者所有，如有侵权，请联系删除。

## JS
- 闭包和闭包用途  
**闭包**是指有权访问另一个函数作用域中的变量的函数。
> 注意闭包和匿名函数的区别。

参考资料：
> * JavaScript高级程序设计（第3版） 7.2闭包

- 原型链
- 作用域链，结合this说明
- call 和 apply 的区别
- ES6+ 用过哪些
- Promise
- async/ await


- ajax如何上传文件  
主要是使用 `FormData()`方法。  
具体可参考：[通过Ajax方式上传文件(input file)，使用FormData进行Ajax请求](https://www.cnblogs.com/LoveTX/p/7081515.html)

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


### React
- React的生命周期
> 16.3 新的生命周期和之前的生命周期不同点


### Vue


### Angular

## CSS
- 盒模型  
```
（1）有两种： IE 盒子模型、W3C（标准）盒子模型；
（2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)；
（3）区  别： IE的content部分把 border 和 padding计算了进去（`box-sizing: border-box`）, W3C 是 `content-box`;
```

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
```
参考：https://www.cnblogs.com/wqhwe/p/5407468.html

## 综合性
- 在浏览器输入一个URL，会发生什么？