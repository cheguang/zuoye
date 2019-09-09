# java script
+        ( JavaScript 是一种轻量级的编程语言 。 解释型语言)
+        (可以用在html页面编辑代码 内嵌 外联)
+        (需要以ES6标准执行)

### 输出方式
    alert() 弹出“警告框”。
    console.log() ：控制台输出。
    prompt()：用户输入语句
### 变量

   任何全局变量都是window的属性
    常量:数字、字符串。
    变量:(变量可以用来保存字面量，而且变量的值可以任意改变。)
```var a =30``` var:关键字  a就是里面的变量
+ 变量的命名规则：必须以字母或是下标符号”_”
 ;不能以数字开头 ;         区分大小写;       用驼峰命名规则
+ 变量的数据类型
     +      数据类型： 基本数据类型（原始数据类型） 和 引用数据类型（复杂数据类型）
     +    基本数据类型：存放在 栈内存（stack） 中，可以直接访问。（String 字符串、Number 数值、Boolean 布尔值、Null 空值、Undefined 未定义。）
    + String字符串
   \\' 表示 '
   \\n 表示换行
   \\r 表示回车
   \\t 表示制表符
   \\b 表示空格
   \\\ 表示\
+ typeof 用于查看返回属性值
+ Number 数值 :整数,和小数
+ NaN 和 isNaN()函数
+ Boolean 布尔值
+ undefined 
+ Object 对象 :属性值 :属性名
#### 变量值的传递
+ a = b;  把 b 的值赋给 a，b 不变。
+  变量的类型转换
方法一：变量+"" 或者 变量+"abc"
方法二：调用 toString()方法
方法三：使用 String()函数
+   其他的数据类型 --> Number
+   方式一：使用 Number()函数
情况一：字符串 --> 数字

1.如果字符串中是纯数字，则直接将其转换为数字。

2.如果字符串中有非数字的内容，则转换为 NaN。（此处可以看到 Number()函数的局限性）

3.如果字符串是一个空串或者是一个全是空格的字符串，则转换为 0。
+ 情况一：字符串 --> 数字
   1.如果字符串中是纯数字，则直接将其转换为数字。
   2.如果字符串中有非数字的内容，则转换为 NaN。（此处可以看到 Number()函数的局限性）
   3.如果字符串是一个空串或者是一个全是空格的字符串，则转换为 0。
+   情况二：布尔 --> 数字
 true 转成 1
 false 转成 0
+  情况三：null --> 数字
结果为：0
+  情况四：undefined --> 数字
结果为：NaN
##### 转换为Boolean
+ 情况一：数字 --> 布尔。除了0和NaN，其余的都是true。
+ 情况二：字符串 ---> 布尔。除了空串，其余的都是true。
+ 情况三：null和undefined都会转换为false。
+ 情况四：对象也会转换为true。
### 算数运算符
+      +  -   *   /   %   (优先级)

result1 = true + 1; // 2 = 1+ 1

result2 = true + false; // 1 = 1+ 0

result3 = 1 + null; // 1 = 1+ 0

result4 = 100 - "1"; // 99
+ 自增和自减   ++     --
+  比较运算符  
  >	  >大于号
<	小于号
>= 	大于或等于
<=  小于或等于
== 	等于
=== 全等于
!=	不等于
!== 不全等于
+ 全等符号的强调
== 不严谨的   ===严谨的
#### Date 对象
var date1 = new Date();
getDate() 获取日 1-31
getDay() 获取星期 0-6（0 代表周日，1 代表周一）
getMonth() 获取月 0-11（0 代表一月）
getFullYear() 获取年份
getHours() 获取小时 0-23
getMinutes() 获取分钟 0-59
getSeconds() 获取秒 0-59
getMilliseconds() 获取毫秒 （1s = 1000ms）
getTime()：获取时间戳
#### Math 对象的用法
+  向下取整（向小取） Math.floor()  向上取整（向大取）Math.ceil()  四舍五入 Math.round()
+ Math.max(x, y, z) 最大值  Math.min(x, y, z) 最小值   Math.pow(x,y) x 的 y 次幂
#### 逻辑运算符
+ && 与 ------------- || 或  --------- ! 非
+ 非布尔值的与或运算:
   会先将其转换为布尔值，然后再运算，但返回结果是原值

#### 流程控制
+ 选择结构 if  switch
    
+ 循环结构  while  for

```
if () {}; //if语句

switch(){
    case 1:
        console.log();
        break;
    default:
        console.log();
        break;   //switch语句
        };

for(初始化表达式; 条件表达式; 更新表达式){
    语句...
};              //for循环语句

while(条件表达式){
	语句...
}               //while 循环
```
##### break 和 continue
+ break 可以用来退出 switch 语句或整个循环语句（循环语句包括 for、while）。
+ 并且会立即终止离它最近的那个循环语句。

+ continue 可以用来跳过当次循环。
## 数组
```
var arr = [1, 2, 3];   //方法1 //直接添加数组
var arr = new Array();  //方法2
```
+ 数组的长度  length
var arr = [21, 22, 23];
+  如果修改的 length 大于原长度，则多出部分会空出来，置为 null
+ 如果修改的 length 小于原长度，则多出的元素会被删除，数组将从后面删除元素。
#### 数组的方法
+ push() 向数组的最后面插入一个或多个元素，返回结果为该数组新的长度。
```
var arr = ["张三", "王二", "李三"];
var result1 = arr.push("王四"); 
```
+ pop() 删除数组中的最后一个元素，返回结果为被删除的元素。
```
var arr = ["张三", "王二", "李三"];
var result1 = arr.pop();
```
+ push() 从后面添加一个元素
+ unshift() 在数组最前面插入一个元素
+ shift() 删除数组中的第一个元素
+ pop()   删除最后的一个元素
+ concat()  连接两个或多个数组
```
新数组 = 数组1.concat(数组2, 数组3 ...);
```
+ join() 将数组转换为字符串,不会改变原来的数组
+ split() 将字符串变成字符串的数组
新数组 = 原字符串.split(分隔符, 数组长度);

+ 遍历数组的方法 
   第一种用for 循环 ..第二种用 for if
```
for(var i in arr){
   console.log('arr数组里面的第'+(parseInt(i)+1)+'个数是'+arr[i])
}
```
#####  数值的高级api
+ reverse()  反转后的数组  =  数组.reverse();
+ sort()      对数组的元素进行从小到大来排序
   按照Unicode 编码排序
   如果在 sort()方法中带参，我们就可以自定义排序规则。
```
var arr3 = [5, 2, 11, 3, 4, 1];

// 自定义排序规则
var result = arr3.sort(function(a, b) {
	return a - b; // 升序排列
	// return b - a; // 降序排列
});

console.log("arr3 =" + arr3); // [1,2,3,4,5,11]
console.log("result =" + result); // [1,2,3,4,5,11]
```
+ slice()
从数组中提取指定的一个或者多个元素，返回结果为新的数组
新数组 = 原数组.slice(开始位置的索引, 结束位置的索引);
var result1 = arr.slice(2); //从下标为2值开始提取
var result3 = arr.slice(2, 4); //从下标为2值开始提取,到4结束 不包含4

+ splice()
从数组中删除指定的一个或多个元素，返回结果为新的数组（会改变原来的数组，会将指定元素从原数组中删除）。
var result1 = arr1.splice(1); //从第index为1的位置开始，删除元素
var result3 = arr3.splice(1, 3); //从第index为1的位置开始删除元素,一共删除三个元素
+indexOf() 和 lastIndexOf()：获取数据的索引

indexOf(value)：从前往后索引，获取 value 在数组中的第一个下标。

lastIndexOf(value) ：从后往前索引，获取 value 在数组中的最后一个下标。

#### 字符串对象的常用方法
+ charAt() 获取相应下标位置的字符
+ charCodeAt() 指定位置字符 的 Unicode 编码
+ indexOf() 返回字符在字符串中的位置  从前到后
+ lastIndexOf()  从后到前
+ concat() 连接字符串
+ slice() 提取字符串的某个部分
+ substr() 截取字符串
+ toUpperCase() 转化成大写
+ toLowerCase() 转化成小写
+ 冒泡算法和选择排序
```
var str = "how are you? and you?";

console.log(str.length); // 21
// charAt()获取相应位置字符
// 空格也 占位置
console.log(str.charAt(5)); // r
// charCodeAt() 方法可返回指定位置字符的 Unicode 编码
console.log(str.charCodeAt(5)); // 114

// indexOf() / lastIndexOf()
// 返回字符在字符串中的位置
console.log(str.indexOf("y")); // 8
console.log(str.lastIndexOf("y")); // 17

//concat() 连接字符串
var str2 = " me too";
console.log(str.concat(str2));

// slice()	  方法可提取字符串的某个部分，并以新的字符串返回被提取的部分
console.log(str.slice(0, 9)); // how are y
console.log(str.slice(0)); // how are you? and you?
console.log(str.slice(1, 4)); // 'ow '

// substr(起始位置,[取的个数])  截取字符串 返回截取的字符串
console.log(str.substr(0)); // 截取 整个字符串
console.log(str.substr(1, 4)); // ow a

// 转换大小写
console.log(str.toUpperCase()); // HOW ARE YOU? AND YOU?
console.log(str);
console.log(str.toLowerCase()); // how are you? and you?
```


      冒泡算法
      比较相邻的元素 .如果第一个元素比第二个元素大.用一个中间值作为交换.把他们两个交换...使其从大到小排序.
      针对所有的元素 重复上面的操作
      ```
      for(var i=0 ,i<arr.length;i++){
         if(arr[i]>arr[i+1]){
            var temp =arr[i];  //用中间值取最大值
            arr[i]=arr[i+1];  //让最小值赋值给最大值
            arr[i+1]=temp;    //让已经取好的最大值 重新赋值给最小的值,这样 arr[i+1]就是最大值了
         }
      }
```
      选择排序
      声明一个变量,从一次待排序的元素中选择出最大的一个元素,存放在起始的位置.
```
      for(var i=0,i<arr.length;i++){
         var c =j;
         for(var j=0;j<arr.length;j++ ){
            if(arr[c]<arr[i]){
               c = i;
            }
         }
      }

+  函数 
   function(){} 直接声明一个函数 ,然后这样函数可以被调用
   var a = function(){}  .需要调用的 时候 ,直接调用 a();  这个函数也是一个匿名函数
   
   函数是由形参 和里面的内容构成的 ,本身是本占据位置的 ,相当于一个模板.引用的时候需要把实参调用出来 .函数不调用 就是等于白写
```
function 函数的名字(){};
function 
```
+  函数的返回值.
   return 是英语的返回的意思.
   函数里面可以没有returen  .但是 如果有return 是最多 只能有一个.为啥呢?
   因为 renturn完了 以后.就不能再书写程序了 .就是说 后面写的都不会生效.

+  函数的变量提升
   什么是变量的提升?
   在函数体内 ,声明一个变量 ,会把该声明提升到函数体的最顶端.
```
   var a =10;
   function f1(){
      var b =9;
      console.log(a);
      console.log(b);
      var a ='996';
   };
   f1();
```
这个函数打印的结果是
    undefined   和   9;  为什么不是10呢? 因为函数里面已经有a了 .会首先查询到这个变量a,但是它又是从上到下的正常顺序排序的 所有查询到的a 是没有赋值的.
+ 变量的作用域
   根据变量的作用范围, 可以分为 全局变量 和 局部的变量
+ 函数的声明提升, 使用 var  .或者function .里面的内容
+ 函数不调用的时候 不执行..   函数名就等于这个函数   参数相当于局部变量    就近原则使用变量   两个平级函数中的变量不会互相影响

+  函数的进阶
   函数是一种类型 (function 类型 实际是是function 对象的一个实列)
+ 递归的函数
```
        var fib = function jiechen(n) {
            if (n == 1) {
                return 1  //这个是跳出的条件
            }
            return n * jiechen(n - 1)
        }

        console.log(fib(6));
```
+ 对象


   原始对象的属性无法直接修改
   对象的作用是用于：封装信息用的.
   对象具有属性 还有行为。它是保存在堆内存当中。每当创建一个新的对象，就会在堆内存当中开辟一个新空间 。变量往往是保存的对象的内存地址。
   如果两个变量保存的是同一个对象引用，当一个通过一个变量修改属性时，另一个也会受到影响
```
var obj = new Object();
obj.name = "张三";

var newName = obj;

//修改obj的name属性
obj.name = "王五";
```
此时 newName中的数值应该是 王5;

   var obj = new Object();   //用new创建一个对象
   var obj = {属性名：属性值，属性名：属性值};   //使用对象字面量来创建一个对象
+ 修改对象中的属性
对象.属性名 = 属性值;
+ 获取对象属性
console.log(obj.属性名)
+ 删除对象的属性
 delete obj.属性名
+  for in
```
   var x
var mycars = new Array()
mycars[0] = "Saab"
mycars[1] = "Volvo"
mycars[2] = "BMW"

for (x in mycars)
{
document.write(mycars[x] + "<br />")
}
```
for (变量 in 对象)
{
    在此执行代码
}

+json 对象
json 是存储和传输数据的格式。 经常在数据从服务器发送到网页时使用
 JavaScript Object Notation
```
{
"employees":[
    {"firstName":"Bill", "lastName":"Gates"}, 
    {"firstName":"Steve", "lastName":"Jobs"},
    {"firstName":"Alan", "lastName":"Turing"}
]
}
```
+ json
+   JSON.stringify(jsonObj) ==> 可以把json类型的对象转换为文本
+ JSON 文本转换为 JavaScript 对象
   var obj = JSON.parse(text);
   声明变量 然后赋值.用 JSON.parse 的方法














