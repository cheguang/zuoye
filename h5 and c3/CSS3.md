## 选择器
### 属性选择器
* 属性选择器 通过属性来选择元素
  * div[attr]
  * div[attr=str] 
  * div[attr*=str] 选择所有包含str的
  * div[attr^=str] 开始位置
  * div[attr$=str] 结束位置
* 伪类选择器
  * 结构伪类
    * ele:first-child   ele的父元素的第一个子元素
    * ele:last-child   最后一个子元素
    * ele:nth-child(n)  第n个子元素
    * ele:nth-last-child(n) 倒数第n个
  * 目标伪类
    * E:target 集合锚点进行使用
  * 伪元素 ele::before , ele::after 默认行内样式 content:" " 必须写
    * ele::first-letter 文本的第一个字母或字
    * ele::first-line 文本第一行
    * ele::selection 选中文本改变样式
    * " : " 与" :: "区别在于区分伪类和伪元素
### 颜色
三种颜色的表达方式
```
rgba(0,0,0,0)/rgb(0,0,0)  Red、Green、Blue、Alpha 即 RGBA
hsla(0,20%,50%,.7)  Hue、Saturation、Lightness、Alpha 即 HSLA
H 色调 取值范围 0~360			360表示红色、120表示绿色、240表示蓝色
S 饱和度 取值范围 0%~100%
L 亮度 取值范围 0%~100%
A 透明度 取值范围 0~1

关于透明度：
1、 opacity只能针对整个盒子设置透明度，子盒子及内容会继承父盒子的透明度
2、 transparent 不可调节透明度，始终完全透明

一般元素透明使用 opacity, 制作制作遮罩层常用 rgba, 制作三角形常用  transparent
```
### 阴影
* 文本阴影
```
text-shadow: h-shadow(x) v-shadow(y) blur(模糊半径) color(颜色)
	1、X轴偏移量 正值向右 负值向左
	2、Y轴偏移量 正值向下 负值向上
	3、模糊半径是不能为负值
```
* 盒子阴影
```
box-shadow: x y (模糊半径) (扩展范围) color(颜色) inset(是否内嵌,可省略) 
```
### 盒模型
css3中可以通过box-sizing 来指定盒模型,即可指定为ccontent-box ,border-box
```
content-box: 对象的实际宽度等于设置的 width 值和 border、padding 之和  (默认方式)
border-box： 对象的实际宽度就等于设置的 width 值，即使定义有 border 和 padding 也不会改变对象的实际宽度，即 ( Element width = width ) 
我们把这种方式叫做 css3 盒模型
```
### 浏览器内核
```
Trident内核: 主要代表为 IE 浏览器         前缀-ms
Gecko内核：主要代表为 Firefox 	           前缀-moz
Presto内核：主要代表为 Opera              前缀-o
Webkit内核：产要代表为 Chrome 和 Safari   前缀-webkit
```
## 边框图片
### 边框
border-image 属性时一个简写属性,用于设置以下属性
* border-image-source 图片
* border-image-slice 图片边框内偏移量 不写单位,默认像素,也可以是百分比
* border-image-width 边框宽度
* border-image-outset 边框图像区域超出边框的量
* border-image-repeat 是否平铺(repeated) , 铺满(rounded)  拉伸(stretched 默认)可以写俩值,一个水平方向,一个垂直方向
### 渐变
1. 线性渐变 沿着某条直线朝一个方向产生渐变效果
```
语法: background:linear-gradient(方向,color-stop1,color-stop2,...)
           direction: 方向 可以是 角度(10deg)顺时针  也可以是 to                  top/left/right/bottom
      颜色后面可以跟百分比,表示从百分几开始渐变
      渐变的兼容写法 方向是相反的  而且不带to: background: -webkit-linear-gradient(right ,red 60%,orange 80%);
      
      重复渐变: background: repeating-linear-gradient(to right,red 0, red 10%, purple 10%, purple 20%)
      一般是通过ui设计稿 直接提取的渐变 角度 颜色比重
```
1. 径向渐变 从一个中心点开始沿着四周产生渐变效果
```
语法: bakground:radial-gradient((shape?size?(at position?))?,start-color,...last-color)

  shape 渐变形状 : circle | ellipse(椭圆)
  size 渐变大小:
  	closest-side（指定径向渐变的半径长度为从圆心到离圆心最近的边）
  	closest-corner （指定径向渐变的半径长度为从圆心到离圆心最近的角）
  	farthest-side（指定径向渐变的半径长度为从圆心到离圆心最远的边）
  	farthest-corner（指定径向渐变的半径长度为从圆心到离圆心最远的角）
  	也可指定大小: 需要注意的是 若渐变形状为圆形，则该渐变大小只能设置一个数且不能为百分数，而椭圆既可以为具体数值也可以为百分数
  	
  	注意: 只传一个值默认形状为圆形,传入的是半径大小,不能为百分比;
  				传两个值则代表形状为椭圆形,第一个是x轴半径,第二个是y轴半径
  				圆心位置参数一定要置于radial-gradient()第一个参数的末尾，顺序千万不能放反了
  				
  	重复渐变 : background: repeating-radial-gradient(circle at center,#f00 0,#f00 10%,#ff0 10%,#ff0 20%);
```
### 背景图片加强
```
background:url repeat position 
background-iamge
background-size
background-origin
background-clip
background-att

 1.background-size设置背景图片的尺寸  注意:是需要根据高度还是宽度适配
               cover 会自动调整缩放比例,始终填充满背景区域,溢出部分隐藏
               contain 自动调整缩放,始终完整显示在背景区域
 2.background-origin(原点,起点) 设置背景定位的原点
               border-box 以边框做为参考原点
               padding-box 内边距做为参考原点
               content-box 内容区为原点
 3.background-clip 设置背景区域clip(裁切)
               border-box 裁切边框以内为背景区域
               padding-box 裁切内边距为背景区域
               content-box 裁切内容区作为背景区域
 4、以逗号分隔可以设置多背景，可用于自适应局
	background: url("img/1.jpg") no-repeat left top, url(img/2.jpg) no-repeat right top;
```
### 过渡
```
transition: transition-property transition-duration transition-timing-function transition-delay
		transition-property   规定应用过渡的 CSS 属性的名称 (一般都写 all);
		transition-duration   定义过渡效果花费的时间。默认是 0
		transition-timing-function: 规定过渡效果的时间曲线。默认是 "ease"。
					linear|ease|ease-in|ease-out|ease-in-out|cubic-bezier(n,n,n,n);
		transition-delay 			规定过渡效果何时开始。默认是 0
```
### 2D转换
```
缩放 scale(x, y) 可以对元素进行水平和垂直方向的缩放，x、y的取值可为小数，不可为负值
移动 translate(x, y) 可以改变元素的位置，x、y可为负值
旋转 rotate(deg) 可以对元素进行旋转，正值为顺时针，负值为逆时针
倾斜 skew(x-angle,y-angle)	定义沿着 X 和 Y 轴的 2D 倾斜转换。
		skewX(x-angle) 	定义沿着 X 轴的 2D 倾斜转换。
		skewY(y-angle)	定义沿着 Y 轴的 2D 倾斜转换。
```
## 3D转换
rotateX/Y   沿X/Y/Z轴旋转
translateX/Y/Z  沿X/Y/Z轴移动
### 透视
1. 作为一个属性,设置给父元素(perspective: 1000px) ,作用于所有3D转换打的子元素. perspective-origin 可以指定视角原点
2. 作为 transform 属性的一个值(transform-style: preserve-3d),作用与元素自身,子元素的3D效果可呈现
3. 透视会产生近大远小的效果

backface-visibility: visible / hidden 设置元素背面是否可见
### 动画
1. 必要元素:
  1. 通过@keyframes 指定动画序列
  2. 通过百分比将动画序列分割成多个节点  亦可以使用from/to 不推建
  3. 在各节点中分别定义各属性
  4. 通过animation将动画应用于相应元素
2. 关键属性:
  * animation-name 动画名称
  * animation-duration 动画持续时间(必填)
  * animation-timing-function
    * liner / ease / ease-in / ease-out / ease-in-out / cubic-bezier(n,n,n,n): 贝塞尔曲线
  * animation-delay 动画延迟(只是第一次)
  * animation-iteration-count  重复次数  infinite无限次
  * animation-direction 动画是否重置后再开设播放
    * alernate 动画直接从上一次停止的位置开始执行,倒着来
    * normal 动画第二次直接跳到0%的状态开始执行
  * animation-fill-mode 动画执行完毕后状态
    * forwards 当动画完成后,保持最后一个属性值
    * backwards 在animation-delay 所指定的一段时间内,在动画显示之前,应用开始属性
    * both 守则对象状态为动画结束或开始的状态,结束时状态优先

语法: animation: name duration timing-function delay iteration-count direction fill-mode;
name duration   必须写 
animation-play-state  播放状态(running 播放 和 paused 暂停)
* stiming-function还可以取steps()函数
  * steps(n,start/end) 第一个参数 number 为指定的间隔数，即把动画分为 n 步阶段性展示，第二个参数默认为 end，设置最后一步的状态，start 为结束时的状态，end 为开始时的状态(不用记,第二个参数不写就行)  n必须是正整数
1. 动画监听

ele.addEventListener("animationend", myStartFunction);
动画的事件:
* animationstart- CSS 动画开始后触发
* animationiteration - CSS动画重复播放时触发
* animationend - CSS 动画完成后触发
1. 过渡监听
```
过渡只有监听结束的方法,  start 和 run 的监听方法在开发状态
d2.addEventListener('transitionstart',function () {
	console.log('过渡开始...');
})
d2.addEventListener('transitionrun', function() {
	console.log("过渡执行中");
});
d2.addEventListener('transitionend',function () {
	console.log('过渡结束...');
```
## 遇到问题
学的属性内容太多 记不住
### 学习心得
