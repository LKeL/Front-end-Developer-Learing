#阿里巴巴篇
1、创建一个1-100的数组，按顺序递增

```javascript
var a = Array.from(new Array(100), (v,i)=>{return i+1})
```

-
2、说说前端跨域的解决方式

- CORS
- JSONP
- iframe
- document.domain
- window.name
- window.postMessag

> 常用cors && jsonp

-

3、JavaScript实现继承的常用方法有哪些？你推荐的是哪一种？

es6 - extends
es5 - 原型链继承、构造继承、实例继承、拷贝继承、组合继承、寄生组合继承

es5 面向对象直接采用极简法

```javascript
var Animal = { 
    Animalcommon: 'Animalcommon',
    createNew: function (){ 
        var animal = {}; 
        var Animalprivate = 'Animalprivate';
        animal.Animalvariable = 'Animalvariable';
        animal.Animalfunc = function(){console.log(Animalprivate)};
        animal.getAnimalCommon = function(){return Animal.Animalcommon};
        return animal;
    } 
}; 
var Cat = { 
    Catcommon: 'Catcommon',
    createNew: function (){
        var cat = Animal.createNew(); //继承
        var Catprivate = 'Catprivate';
        cat.Catvariable = 'Catvariable';
        cat.Catfunc = function(){console.log(Catprivate)};
        cat.getCatCommon = function(){return Cat.Catcommon};
        cat.changeCatCommon = function() {Cat.Catcommon='CatcommonChange'};
        return cat;
    } 
}; 

var cat = Cat.createNew();
```

-

4、在项目开发完成之后，根据雅虎性能优化规则，需要对html，JS，CSS，图片需要做出怎样的处理？是否可以借助构建工具实现自动化？

雅虎军规：
- 尽量减少HTTP请求次数
- 使用CDN
- 为文件头指定Expires或Cache-Control，使内容具有缓存性 
- 避免空的src和href
- 使用gzip压缩内容
- 把CSS放到顶部
- 把JS放到底部
- 避免使用CSS表达式
- 将CSS和JS放到外部文件中
- 减少DNS查找次数
- 精简CSS和JS
- 避免跳转
- 剔除重复的JS和CSS
- 配置ETags
- 使AJAX可缓存
- 尽早刷新输出缓冲
- 使用GET来完成AJAX请求
- 延迟加载
- 预加载
- 减少DOM元素个数
- 根据域名划分页面内容
- 尽量减少iframe的个数
- 避免404
- 减少Cookie的大小
- 使用无cookie的域
- 减少DOM访问
- 开发智能事件处理程序
- 用link代替@import
- 避免使用滤镜
- 优化图像
- 优化CSS Spirite
- 不要在HTML中缩放图像
- favicon.ico要小而且可缓存
- 保持单个内容小于25K
- 打包组件成复合文本

可借助自动化工具对JS，CSS，图片进行压缩，
但如延迟加载就引用LazyLoad插件，图片格式优化根据具体使用情况优化，删除不必要的沉冗代码，提高性能只能借助实时性能检测工具局部分析优化，良好的编程习惯，完善的开发框架与方案可以有效降低工作量

-
5、说说前端中的事件流？
浏览器的事件流，有两种事件模式，捕获和冒泡，现代浏览器大多为冒泡，即让DOM树最底层的目标元素最先接收到事件，然后往上传递

不知道js的事件队列算不算事件流

```javascript
for(var i = 0; i < 999; i++){
	console.log(i)
	setTimeout(()=>console.log('settimeout'),500)
}
```
先输出i，最后输出settimeout

-

6、JS 中的原型链是什么？
在js中，使用原型继承法实现继承，利用原型对象使一个引用类型继承另一个引用类型的属性和方法，实例对象在调用一个方法时会首先在自身里寻找是否有该方法，由于js属于实现继承而不是抽象继承，若没有找到该方法，则去原型链上去寻找，依次层层递进

-
7、有一个长度为100的数组，请以优雅的方式求出该数组的前10个元素之和

```javascript
var b = 0;
a.every((v,i)=>{return (b+=v) && (i < 9)});
```

-

8、了解过flex布局吗？说说它和传统布局的有何不同？

09年w3c发布的方案，flexbox能更好的实现响应式设计，flexbox可以控制在容器内的子元素的对齐方式、排列方式以及排序顺序，即使其子元素的尺寸是未知或者动态的情况下。弹性容器的主要特点就是能够调整其子元素的宽度或者高度以使其能在**不同分辨率的屏幕**下能用最好的方式去填充可用空间。
Flex布局的主要思想是让容器能使其子元素的宽高（或其他属性）能够以最好的方式去填充可用空间（主要是去适应不同的设备跟分辨率）。一个Flex弹性盒子能让子元素填充可用空间或者为了阻止子元素超出区域而进行收缩

相比于gird布局，我觉得gird能解决的flex也能解决，Bootstrap4使用了flexbox来实现grid布局

在我现在做的移动端项目中已经基本全面使用flexbox

-

9、移动端的图片优化实践方式有哪些？


- 去掉无意义的图片，少用非内容性质图片
- 使用矢量图替代位图
- 使用恰当的图片格式
- 使用data url
- 按照HTTP协议设置合理的缓存
- 使用lazyload延迟异步加载
- css sprite减少总大小
- 提升图片的 DNS 解析时间

-

10、 请编写一个JavaScript函数 parseQueryString，它的用途是把URL参数解析为一个对象

```javascript
function parseQueryString(url) {
    var str = url.split("?")[1];
    var items = str.split("&");  
    var result = {};  
    var arr;  
    for (var i = 0; i < items.length; i++) {  
        arr = items[i].split("=");  
        result[arr[0]] = arr[1];  
    }  
    return result;  
}
```

-

11、xss和csrf分别是什么？

csrf:跨站点伪装请求
xss:跨站点攻击

csrf类似于钓鱼，让用户在不知情的情况下攻击自己已登录的一个系统，CSRF成功的前提用户必须登录到目标站点，且用户浏览了攻击者控制的站点

XSS攻击的主要目的则是，想办法获取目标攻击网站的cookie，因为有了cookie相当于有了seesion，有了这些信息就可以在任意能接进互联网的pc登陆该网站，并以其他人的生份登陆，做一些破坏


-

12、说说前端如何解决异步回调地狱
    
用promise或Generator，[大神的写法](https://github.com/tj/co)

-

13、淘宝那里的商品项，如图片，滚动到了才加载，你知道怎么实现么

即lazyload，核心原理是：

1 设置一个定时器，计算每张图片是否会随着滚动条的滚动，而出现在视口（也就是浏览器中的 展现网站的空白部分 ）中；

2 为<img>标签设置一个暂存图片URL的自定义属性（例如loadpic），当图片出现在视口时，再将loadpic的值赋给图片的src属性；

-

14、实现1px 像素线条
    
能用border-width: 0.5px就用

伪类 + transform，原理是把原先元素的 border 去掉，然后利用:before或者:after重做 border ，并 transform 的 scale 缩小一半，原先的元素相对定位，新做的 border 绝对定位

-

15、你知道什么是CSS reset么？

即重制浏览器默认样式，用不用CSS reset，取决于“是否需要依赖浏览器默认样式”，至于额外的计算成本可基本忽略



