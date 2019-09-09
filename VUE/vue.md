es6 新方法
let和const
用这两个申明不会产生声明提示
let/const声明的变量不能重新被定义 let 可以重新赋值 const不可以赋值

箭头函数

带一个参数的写法  var f = a => a
带多个参数的写法      var f = (a,b) => a+b
return 多行写法 var f = (a,b) => { return a+b;}
!! 箭头函数的this指向  如settimeout会改变this的指向 在setInterval和setTimeout中传入函数时，函数中的this会指向window对象。

函数默认值
这里的y可以直接赋值 权重低
function log(x ,y="world"){
    console.log(x,y);
}
log('hello');//hello  world

字符串模板
str += `<li>${这里面写入值} </li>`
变量解构赋值--数组
    var arr = [1,2,3];
    var [, , a] =arr 
    里面的a 就是 3
变量解构赋值--对象
let { bar, foo } = { foo: 'aaa', bar: 'bbb' };
foo // aaa   //注意 ,对象的结构方法需要用对应的属性名

数组的扩展
var arr1 =[1,1,5,2,3,5] var arr2= [5.6.4.456.41.4,5,46,5]
var arr3=[...arr1,...arr2] //形成新数组

Array.from 将类数组对象转化成 数组
 function aa(a,b){
        console.log(arguments) //Arguments(2) [1, 2, callee: ƒ, Symbol(Symbol.iterator): ƒ]
        var arr = Array.from(arguments)
        arr.push(3);
        console.log(arr) //arguments.push is not a function
    }
    aa(1,2)  //arguments 是形参对象

数组的新方法
    find
    
    用于找出第一个符合条件的数组成员--找出第一个返回值为true的成员，然后返回该成员。如果没有符合条件的成员，则返回undefined。
     var ele = [1, 5, 10, 15].find(function(value, index, arr) {
      return value > 9;
    })

    findIndex

-Set 和 Map 数据结构 (类似于对象，也是键值对的集合)
 Set。它类似于数组，但是成员的值都是唯一的
 var s = new Set();
[2, 3, 5, 4, 5, 2, 2].forEach(x => s.push(x));
console.log(s)

Promise 是异步编程的一种解决方案-- 简单说就是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果
Promise构造函数接受一个函数作为参数，该函数的两个参数分别是resolve和reject --成功和失败
Promise最大的好处是在异步执行的流程中，把执行代码和处理结果的代码清晰地分离了

function ajax (method , url ,data){
    var xhr =new XMLHttprequest()
    return new Promise(function (resolve, reject){
        xhr.onreadystatechage =funcion(){
            if(xhr.readyState ==4){
                if(xhr.status ==200){
                     resolve(xhr.responseText);
                }else{
                     reject(xhr.status);
                }
            }
        }
    }

    xhr.open(method, url);
    xhr.send(data);
}
 var p =  ajax('GET','http://59.110.138.169/api/douban/movie/in_theaters' )

 filter 
 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。
 var list = [1,2,3,4];
var newList = list.filter(ele => ele > 2);

every()是对数组中每一项运行给定函数，如果该函数对每一项返回true,则返回true。

some()是对数组中每一项运行给定函数，如果该函数对任一项返回true，则返回true。
var arr = [ 1, 2, 3, 4, 5, 6 ]; 
 
console.log( arr.some( function( item, index, array ){ 
    return item > 3; 
}));   // true 

includes 方法用来判断一个数组是否包含一个指定的值，如果是返回 true，否则false。

 reduce() 方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。

 var arr = [1,2,3,4]; 

var newArr= arr.reduce((total,current) => ( return total = total + current ))
total带初始值的写法

var totals = arr.reduce ( (total,current) =>  {
     return total = total + current
},0)


vue

vue渲染方式 
1 通过{{}} 双大括号
2. 指令 <h3 v-text='msg'></h3>
3 . v-html用于输出html

v-if  v-else-if v-show 是用于判断元素的显示和隐藏 ,为true 显示  ,为 false 隐藏
```
//例如
   <div v-if="age>30">
        {{ name }}
    </div>
    <div v-else-if="age == 30">
        {{ name2 }}
    </div>
    <div v-else>
        {{ name1 }}
    </div>
```
v-cloak 解决页面闪烁 ,用于解决 大括号赋值里面的闪烁. 在style里面写入 [v-cloak] {display: none;}
v-bind 给元素绑定属性值, 可以用:   简写
v-on  用于绑定时间的 , 用 @    简写
v-model 用于表单元素的双向绑定 .下拉框选择的时候还需要给里面的 :value 绑定属性
v-once 只渲染一次 ,这可以用于优化更新性能。
<ul>
  <li v-for="i in list" v-once>{{i}}</li>
</ul>
v-for 循环用 ,多次渲染元素或模板块
<div v-for="(item, index) in items"></div> 
---item 值  ----inedx 下标
<div v-for="(item,value , index) in items"></div> 
---值 ---键 ---下标
v-for 默认行为试着不改变整体，而是替换元素。迫使其重新排序的元素，你需要提供一个 key 的特殊属性 用于解决这个问题
<div v-for="item in items" :key="item.id">
  {{ item.text }}
</div>


事件修饰符
.stop       阻止向上冒泡
.prevent    阻止默认的事件
 capture：  捕获冒泡，即有冒泡发生时，有该修饰符的dom元素会先执行，如果有多个，从外到内依次执行，然后再按自然顺序执行触发的事件。
.self       在 event.target 是当前元素自身时触发处理函数
.once       点击的元素只触发一次
按键修饰符
.enter => // enter键
.tab => // tab键
.delete (捕获“删除”和“退格”按键) => // 删除键
.esc => // 取消键
.space => // 空格键
.up => // 上
.down => // 下
.left => // 左
.right => // 右

#### 计算属性

 computed只要在其中引用data中的某个属性 当属性发生变化时 函数可以嗅探到这个变化 并执行某些操作
 特点
 1.计算属性的值会缓存
 2.计算属性所依赖的数据变化必然会触发计算属性的重新求值
 3.计算属性本质是一个方法 但调用的时候不加括号

#### 侦听器

 使用侦听器 可以监听data中数据的变化 然后触发watch中的函数变化

```html
 <div id="app">
           <input type="text" v-model="message">
           {{ message }}
           {{ num }}
    </div>
    <script>
        var message = 11
        var vm = new Vue({
            el:"#app",
            watch: {
                // 如果 `question` 发生改变，这个函数就会运行
                message: function (newVal, oldVal) {
                    console.log("newVal" ,newVal )
                    console.log( "oldVal" ,oldVal)
                    this.num ++
                }
            },
            data(){
                return {
                    num : 10,
                    message
                }
            }
        })
    </script>
```

#### 侦听器与计算属性的不同

1. 计算属性进入页面 就会执行  侦听器只有当数据更改的时候才会执行
2. 侦听器监听的数据不能更改 计算属性当依赖的属性更改的时候会自动执行 
3. 计算属性会缓存结果
4. 计算属性必须return一个值 而watch不需要

小结 : es6 的新方法 和vue的特性 需要多加练习,才能熟练
