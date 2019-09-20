ECMAScript 6.0（以下简称 ES6）是 JavaScript 语言的下一代标准，已经在 2015 年 6 月正式发布了。它的目标，是使得 JavaScript 语言可以用来编写复杂的大型应用程序，成为企业级开发语言。
# let 和 const
## let声明变量和作用域
### let不存在变量提升
```
<script>
  for (var i = 0; i < 10; i++) {
        setTimeout(function(){
            console.log(i)  // 10次10
        },1000)
      }
      for (let j = 0; j < 10; j++) {
        setTimeout(function(){
            console.log(j)  // 0,1,2,3,4,5,6,7,8,9
        },1000)
      }
</script>
```
### let/const
* let/const声明的变量不能重新被定义 let可以重新赋值 const不可以赋值
* 如果确定值不会改变  就使用const 如果确定改变的话就使用let
# 箭头函数
```
var f = v => v;
// 等同于
var f = function (v){
  return v
}
```
## 1.不带参数的写法
```
<script>
  var f = () =>{
    return
  } 
    
  var f = function(){
    return
  }
</script>
```
## 2.带一个参数的写法
```
<script>
  var f = a => {
    console.log(a)
  }
  var f = function(a){
    console.log(a)
  }
</script>
```
## 3.带多个参数的写法
```
<script>
  var f = (a,b) => {
    console.log(a+b)
  }
  
  var f = funtion(a,b){
    console.log(a+b)
  }
</script>
```
## 4.return 多行写法
```
<script>
  var age = a => a;
  var age = function(a){
    return a
  }
</script>
```
## 5.this指向
1. 箭头函数的this指向 settimeout会改变this的指向 如果我们用箭头函数 箭头函数就指向父级。
在setInterval和setTimeout中传入函数时，函数中的this会指向window对象。
箭头函数的this指向是父级 
## 6.字符串模板
传统字符串的缺点:
1. 传统的字符串拼接不能正常换行
2. 传统的字符串拼接不能友好的插入变量 ${}
3. 传统的字符串拼接不能友好的处理单引号、双引号互相嵌套的问题。
```
// 插入变量
var s1 = `hello vue`;
var html = `xxx ${s1} xxx` 
```
## 7.变量解构赋值  (变量的取出)
### 1.数组的结构 (与下标有关,对应不了 值为undefined)
```
var arr = [1,2,3]
[a,b,c] =arr;  1 2 3
```
### 2.对象结构 (与下标无关)
* 解构定义的变量与属性名称有关
```
let { bar, foo } = { foo: 'aaa',bar:'bbb'} 
foo: aaa
bar: bbb
```
# 数组的扩展
## 1.spread
将一个数组转为 用'逗号'分割的参数序列
```
// 常用 合并两个数组
var arr = [1,2]
var arrs = [3,4]
var newArr = [...arr,...arrs]
```
## 2.Array.from
Array.from方法用于将 "类对象" 转为真正的数组
```
var arr = Array.from(arguments)
```
## 3.find / findIndex
1. find

数组实例的find方法，用于找出第一个符合条件的数组成员。它的参数是一个回调函数，所有数组成员依次执行该回调函数，直到找出第一个返回值为true的成员，然后返回该成员。如果没有符合条件的成员，则返回undefined。 find方法的回调函数可以接受三个参数，依次为当前的值、当前的位置和原数组。
```
var ele = [1,5,10,15].find(function(value,index,arr){
  return value > 9
})
console.log(ele)  // 10
```
1. findIndex

数组实例的findIndex方法的用法与find方法非常类似，返回第一个符合条件的数组成员的下标，如果所有成员都不符合条件，则返回-1。
```
[1,5,10,15].findIndex(function(value,index,arr){
  return value >9
}) // 2
```
# 常用数组操作 
## map  filter  foreach  some  every  includs  find  findIndex  reduce
## 1.map
数组map()方法主要创建一个新的数组使用调用此数组中的每个元素上所提供的函数的结果。即对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组。对数据进行操作 返回新的数据
```
var list = [1,2,3,4];   
var newList = list.map(ele=>{    // 不改变原数据
  return ele*2   
});
console.log(list,newList)  // [1,2,3,4] [2,4,6,8]
```
## 2.filter  过滤
创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。

```
var list = [1,2,3,4];   
var newList = list.filter(ele=>ele>2);  // [3,4] 不改变原数组
// 把符合条件的元素全部过滤出来 返回的数据结构是数组 不符合条件 返回的是空数组
```
## 3.foreach
1. 对数据进行循环  相当于for循环  没有返回值
2. 不能对元素进行修改
3. break 不能终止
```
var arr = ['a','b','c']
arr.forEach(function(ele){
  console.log(ele)    // 'a' 'b' 'c'
})
```
## 4.every / some
### every() 全为true 返回true
是对数组中每一项运行给定函数，如果该函数对每一项返回true,则返回true。
```
var arr = [1,2,3,4,5,6]
console.log( arr.every ( function( item, index, array ){
  return item > 3 
}));  // false
```
### some() 任一项为true 返回true
是对数组中每一项运行给定函数，如果该函数对任一项返回true，则返回true。
```
var arr = [1,2,3,4,5,6]
console.log( arr.some ( function( item, index, array ){
  return item > 3 
}));  // true
```
## 5.includes
用来判断一个数组是否包含一个指定的值，如果是返回 true，否则false。
```
[1, 2, NaN].includes(NaN); // true
[1, 2, 3].includes(4);     // false
```
## 6.reduce
reduce() 方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。
```
var arr = [1,2,3,4];
// 对total赋予一个初值 current从第一项开始
var total = arr.reduce((total,current)=>{
  return total + current;
  // total 求和的结果 current 当前循环的数据
},0)
```




# Set / Map 数据结构
## Set
它类似于数组，但是成员的值都是唯一的，没有重复的值。
Set 本身是一个构造函数，用来生成 Set 数据结构。
1. set.add()  向set结构添加数据
2. set.size()  代表set结构的大小  理解为数组的length
3. set.delete()  向set数据结构珊瑚数据
4. set.clear() 清空set数据结构内容
```
// 数组去重
var set = new Set();
var arr = [0,1,2,2,4,4];
for(var i = 0; i< arr.length ; i++){
  set.add(arr[i])
}
var newArr = Arrar.from(set);
console.log(newArr) // 0,1,2,4  
```
## Map
它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。也就是说，Object 结构提供了“字符串—值”的对应，Map 结构提供了“值—值”的对应，是一种更完善的 Hash 结构实现。如果你需要“键值对”的数据结构，Map 比 Object 更合适。
1. map.size()   返回结构的成员总数
2. map.set()    向map结构添加属性或方法  
3. map.get()    获取map结构的数据 
4. map.has()   判断map数据结构是否包含某个属性或者方法 返回布尔值 true具有 false没有
5. map.delete(key) 删除map结构里面的数某个键 返回true  失败返回false
6. map.clear()  清除所有成员

