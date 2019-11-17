bom是浏览器对象的模型 ,bom里面有很对浏览器的方法

事件对象 event
bom的事件对象是event
事件的委托,用于


event.type用于返回当前的事件类型

里面有 e.pageY获取相对于页面的位置
e.clientY 相对于可视区域的位置
e.screenX 相对于屏幕的位置
e.offsetX 相对于当前的盒子(触发的对象)




+  三大家族
offset家族是用于检测盒子本身的宽和高
offsetleft top 是检测距离有定位的父级盒子的距离

scrollWidth 用于检测盒子本身 宽高 ,+ padding
scorllTop 需要有滚动条 (用于设置一个元素滚动的像素值))
window.onscroll() 事件 滚动的时候触发
window.scroll(x,y) 设置元素的滚动距离

clientWidth   页面可视区域的宽高
clientTop     内容区域上方的高度(border)
