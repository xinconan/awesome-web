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
- position 有哪些值？都有哪些作用

- 清除浮动的方法
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



## 综合性
- 在浏览器输入一个URL，会发生什么？