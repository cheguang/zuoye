



###  DOM 
(定义了文档对象模型)
DOM 树  一切都是节点
元素节点  ,文本节点 ,属性节点
+ 事件的三要素: 事件源 ,事件 ,事件驱动程序
+ 常见事件  onclick   鼠标点击某个对象
        ondblclick   双击
        onfocs       元素获得焦点
        onkeydown    某个键盘的键被按下
        onkeyup      某个键盘的键被松开
        onload       某个页面或图像被完成加载
        onmousedown  某个鼠标按键被按下
        onmouseup    某个鼠标按键被松开
        onmousemove  鼠标被移动
          onmouseover  鼠标被移到某元素之上
        onmouseout   鼠标从某元素移开
+ 步骤 
+ 获取事件源
    通过 id 获取
    document.getElemntById('box');
    var boxEl =document.getElemntById('box');  //然后用var 变量存储

    通过class获取
    var list =document.getElementsByClassname("li-item");
    console.log(list[0]);//以数组形式存储,可以通过索引选择具体元素

    通过标签名
    var Pel=document.getELementsBy

+ 给事件源绑定 事件
直接绑定:
   box.onclick =functon(){
       this.style.属性 = "属性值"
   }
在html行内绑定
<div id="box1" onclick="fn()"></div>

+ 触发点击事件时 需要做什么

借助dom模型 包装dom对象 ,然后就可以操作对象的属性. 就可以修改页面的格式啦

+ dom运行的内容
   找对象(找元素节点 )
   设置元素的属性值
   设置元素的样式
   动态创建和删除元素
```

function init(el,arr){
   var str=''
   for(var i=0;i<arr.length;i++){
      str +=数值当中的内容
   }el.innerhtml= str
}
```
   事件的触发响应：事件源、事件、事件的驱动程序


+ onload 事件  页面加载完成时 才会执行
  window.onliad = function(){};


+ 通过关系获取节点
   var ulEl= parentNode   //父亲节点
   var li3 =document.getElement;
   log(li3.nextSibling)//换行节点
   log(113.nexElementSibling);//下一个元素节点
   previousSibling//上一个换行节点
   previousElementSibling//上一个换行节点
   firstElementChild 子集元素节点

   childNodes 获取所有的子节点
   children  获取所有的元素子节点

+ 元素的属性
   log(box.getAttribute(""));获取元素属性
   setAttribute("圆属性""新属性");


(外)
+ 节点的增删改查
   1创建节点 新的标签(元素节点) = document.createElement("标签名");
   var imeE1 =document.createElement("img");
   2.插入节点
   父节点.appendChilld(新节点);  //从父节点最后插入
   父节点.insertBefore(新的子节点, 作为参考的子节点);
   3.删除节点
   父节点.removeChild(子节点);
   4.复制节点
   要复制的节点.cloneNode(true); 深复制 ,不带true是潜复制
(内)
+  节点的属性
   1.获取 节点的属性
      方法1 元素节点[属性];
      方法2console.log(节点名.getAttribute("class"));   //用getAttribute
   2.设置节点的属性
      方法1  myNode.src = "images/2.jpg"; //修改src的属性值
      方式2：myNode.setAttribute("class", "image3-box"); //用serAttribute

      方式一操作的是属性而已，方式二操作的是标签本身。

   3. 删除节点的属性
   元素节点.removerAttribute(属性名);
   myNode.removeAttribute("class");


+ DOM 对象的属性
dom对象的属性和html的属性.是一样的.都包含了 src、title、className、href 属性等。
+ innerHTML 和 innerText 
innerHTML 修改标签本身 而 innerText修改里面的文字内容
```
   btn.onclick = function(){
      inputEl.value =math.floor(math.random()*10)
      //修改表单的值 为1-10 的随机数
   }
   btn.onclick = function (){
      var str='嘻嘻嘻嘻'
      boxEl.innerhtml(str)
   }
   btn3.onclick = function() {
	// 插入文本内容
	boxEl.innerText = "今天天气很热";
	boxEl.innerText = "<p></p>"; // 当做了文本处理,并没有解析成标签
	// 每一次innerText 都会替换掉box里边  之前的所有内容
};
```
