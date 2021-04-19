---
title: 我的Java笔记
date: 2021-04-19 18:23:36
index_img: /img/default.png
tags: Java
categories: Java笔记
---

# 	JavaScript

## 1.快速入门

### 1.1基本语法入门

- JS严格区分大小写
- JS语句以英文分号结尾

```javascript
   <script>
        alert("hello");
        document.write("hello");//页面输出
        console.log("hello");//控制台输出
    </script>

```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
<!--    定义变量  变量类型  变量名=变量值-->
    <script>
        var num =78;
        // alert(num);
        if (num>60 && num<70){
            alert("及格");
        }else if (num>70 && num<80){
            alert("良好");

        }else if(num>80 && num<100){
            alert("优秀");
        }else {
            alert("不及格");
        }
    </script>
</head>
<body>
</body>
</html>
```

**变量**

```javascript
var //使用var关键词，变量名不能以数字开头
//定义变量： 
//变量类型  变量名=变量值;
```

**标识符**

- 在JS中所有的可以由我们自主命名的都可以称为标识符
- 类如：变量名、函数名、属性明名都属于标识符
- 命名规则：

1. 标识符中可以含有字母、数字、_、$
2. 标识符不能数字开头
3. 标识符不能是ES中的关键字或保留字
4. 标识符一般采用驼峰命名法，类如：xxxYyyZzz



### 1.2数据类型

>JS中一共有六种数据类型
>
>String   字符串
>
>Number  数值
>
>Boolean   布尔值
>
>Null   空值
>
>Undefined   未定义
>
>Object    对象          //引用类型，其他为基本数据类型

==String字符串==

- 需要用引号引起来，可用单引号或者双引号，引号不可嵌套

```javascript
在字符串中我们可以使用\作为转义字符
\"  表示  "
\'  表示  '
\n  表示换行
\t  制表符(空格)
\\  表示\
```

==number==

- 在JS中number类型包括整数和浮点数（小数）
- 用typeof检查数据类型 

```html
<script>
        var a = 123;
        var b = "123";
        alert(typeof a); //返回number
        alert(typeof b) //返回string
    </script>
```

```javascript
123   //整数123
123.1 //浮点数
-11  //负数
NaN  //not a number
Infinity //表示无限大
```

==布尔值==

- 逻辑判断

```javascript
true  表示真
false  表示假
```

==null和undefined==

- null 空
- undefined  未定义 //当声明一个变量不给赋值就返回undefined

==强转类型转换==

- 一般转换为String Number Boolean类型

>==将其他的类型转换为String==
>
>- 方法一：
>
>--调用被转换数据类型的tostring()方法
>
>--注意：null和undefined没有tostring方法
>
>- 方法二
>
> --调用string()函数，将要被转换的数据作为参数传递给函数
>
> --对于null和undefined有效

>==将其他的数据类型转换为Number==
>
>- 转换方法一
>
>使用Number()函数
>
>字符串  ---->  数字
>
>1. 如果是纯数字就会转换为数字
>2. 如果字符串中有非数字就会转换为NaN
>3. 如果字符串是空串或者空格就会转换为0
>
>布尔  ------>   数字
>
>- true 转换 1 
>
>- false  转换为 0
>
> null ---> 数字 0 
>
> undefined  ---》数字NaN
>
>- 转换方法二
>
>parseInt()  把一个字符串转换为整数
>
>parseFloat() 把一个字符串转换为一个浮点数

>==将其他类型转换为Boolean
>
>使用Boolean()函数
>
>- 数字>>>>>>布尔     除了0和NaN,其余的都是true
>- 字符串>>>>>布尔   除了空串其余都是true
>- null和undefined都会转换为false

==进制的表示==

- 十六进制    0x开头
- 八进制    0xff开头
- 二进制    0b开头

==逻辑运算==



```javascript
&& //两个为真，结果为真

|| //一个为真，结果为真
    
!  //真即假，假即真
```

==比较运算符==

```javascript
=
==   //等于(类型不一样，值一样，也会判断位ture)
===   //绝对等于(类型一样，值一样，结果为true)
```

这是js的一个缺陷，坚持不要使用==比较

须知：

- NaN==NaN,这个与所有的数值都不相等，包括它自己
- 只能通过isNaN(NaN)来判断这个数是否NaN

==数组==

Java的数值必须相同类型的对象，js中不需要这样

```javascript
//保证代码可读性，尽量使用[]
var arr = [1,2,3,'hello',null,true];
//取数组下标，如果越界了，就会undefined
```

==对象==

对象是大括号数组是中括号

>每个属性用逗号隔开，最后一个不用逗号

 ```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">ch
    <title>Title</title>
    <script>
    var person = {
    name:"小明",
    age:10,
    tags:['js','java','javascript']
    }
    alert(person.name);
    </script>
</head>
<body>
</body>
</html>
 ```

### 1.3严格检查模式

- 前提：idea需要设置es6语法
- 'use strict';严格检查模式，预防JavaScript的随意性导致产生的一些问题
- 必须写在JavaScript的第一行；
- 局部变量都是用let 去定义

```javascript
'use stritic';
let i = 1;
```



## 2.JavaScript基本运算符

### 2.1算数运算符

- 当对非Number类型的值进行运算时，会将这些值转换为Number然后再运算
- 任何值和NaN做运算时都得NaN

>+:
>
>- 如果对两个字符串加法运算，则会拼串
>- 任何得值和字符串做加法运算，都会先转换为字符串，然后再和字符串品拼接

>-*/:运算时都会自动转换为Number
>
>%:取模运算(取余数)

### 2.2自增和自减

自增：++

- 通过自增可以时变量再自身的基础上增加1
- 对于一个变量自增后，原变量的值会立即自增1
- 自增分为两种：后++(a++)和前++(++a) 它们都可以立即使变量自增1

==注意==

- a++的值等于原变量的值(自增前的值)
- ++a的值等于新的值(自增后的值)

自减：和自增刚好相返，大同小异

练习

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script>
        var a = 20;
         //20 22 22
        a =a++ + ++a + a;
        console.log(a);
        var n1 = 10 , n2 = 20;
        var n = n1++;
        console.log(n);
        console.log(n1);
        n = ++n1;
        console.log(n);
        console.log(n1);
        n = n2--;
        console.log(n);
        console.log(n2);
        n = --n2;
        console.log(n);
        console.log(n2);
    </script>
</head>
<body>
</body>
</html>
```

### 2.3逻辑运算符

JS中提供了三种逻辑运算符

==！非==

- 非运算符就是取反 类如：true变成false ，false变成true
- 如果对非布尔值进行运算时，先将其转换位布尔值，然后取反

==&& 与==

- 如果两个值中有一个false就返回false，只有两个true时才返回false
- 如果第一个为false时，则不会看第二个

==|| 或==

- 两个值只要有一个true，就返回true，两个值都为false时才返回false
- 如果第一个值为true时，则不会检查第二个

==&& || 非布尔值的情况==

- 对于非布尔值进行运算时，先将其转换为布尔值，然后进行运算

- &&运算时：

  ==如果第一个值为true，则直接返回第二个值

  ==如果第一个值为false，则直接返回第一个值

- ||运算时：

  ==如果第一个值为true，则直接返回第一个值

  ==如果第一个值为false，则直接返回第二个值

### 2.4赋值运算符

- +=     a +=  5 等价于  a = a+5
- -=       a -= 5 等价于  a = a-5
- *=       a *=  5 等价于 a = a *5

### 2.5关系运算符

==非数值情况==

- 对于非数值进行比较时，会将其转换位数字然后进行比较
- 如果两侧都是字符串，不会将其转换为数值进行比较，而回分别比较字符串的字符串Unicode编码

==注意==

- 比较字符编码Unicode是一位一位进行比较
- 如果两位一样会比较下一位
- 在比较两个字符串的数字时，一定一定一定要转型，不然会达不到预期效果

```javascript
console.log("111111"<+"5")
```

### 2.6相等运算符

==相等====

- 如果相等返回true，如果不相等则返回false
- 如果值得类型不相等时，会先转换为相同得类型进行比较

==不相等!===

- 如果不相等返回true，如果相等返回false
- 如果值得类型不相等时，会先转换为相同得类型进行比较

==全等=====

- 判断两个值是否全等，他不会进行类型转换，如果两个类型不相等，则返回false

==不全等!====

- 如果两个值得类型不同，则返回true

==注意==

- undefined衍生自null，所以两个值判断时，会返回true
- NaN不和任何值相等，包括它本身，可以通过isNaN()函数判断一个值是否是NaN

### 2.7三元运算符

- 规则：true ？语句一 ：语句二
- 如果true为真则输出语句一否则输出语句二

```javascript
   <script>
       var a = 10;
       var b = 20;
       var c =40;
       // a>b ? alert("a大"):alert("b大");
       var max = a>b ? a:b;
       var max = c>max ? c:max
       console.log(max)
   </script>
```

## 3.JavaScript基本语句

### 3.1if语句(prompt())

==if语句==：if(判断条件){

正确执行语句一

}else{

错误执行语句二

}

- if语句练习

```javascript
        <script>
        /*
        * prompt()函数可以弹出一个输入文本提示框
        * 用户可以在其输入文字，该函数需要一个字符串作为参数
        * */
        var scop = prompt("请输入期末成绩");
        if (scop>100 || scop<0 || isNaN(scop)){
            alert("不合法");
        }else {
            if (scop == 100){
                alert("奖励你一辆跑车");
            }else if (scop>80 && scop<99 ){
                alert("奖励你一个苹果手机");
            }else if(scop>60 && scop<80){
                alert("奖励你一本参考书");
            }else {
                alert("什么都没有");
            }
        }
    </script>
```

- if练习二

```javascript
    <script>
        var num1 = +prompt("请输入第一个数字：");
        var num2 = +prompt("请输入第一个数字：");
        var num3 = +prompt("请输入第一个数字：");
        if (num1<num2 && num1<num3){
            //num1最小
            if (num2<num3){
                //num2最小
                alert(num1+","+num2+","+num3);
            }else {
                alert(num1+","+num3+","+num2);
            }
        }else if (num2<num1 && num2<num3){
            //num2最小
            if (num1<num3){
                alert(num2+","+num1+","+num3);
            }else {
                alert(num2+","+num3+","+num1);
            }
        }else {
            //num3最小
            if (num1<num2){
                alert(num3+","+num1+","+num2);
            }else {
                alert(num3+","+num2+","+num1);
            }
        }
    </script>
```

### 3.2条件分支语句

- 也叫switch语句

- 语法：switch(条件表达式){

  case 表达式：

  语句

  break；

  default：

  语句

  break；

  }

- 进行全等比较，结果为true则从当前case处开始执行代码

==注意==

- case后边要跟上一个break关键字否则都会执行后面的语句
- 如果比较结果都为false则会执行default后的语句

```javascript
    <script>
        var num ="abc";
        switch (num) {
            case 1:
                alert("壹");
                break;
            case  2:
                alert("贰");
                break;
            default :
                alert("不合法");
                break;
        }

    </script>
```

### 3.3while循环语句

- 语法：while(条件表达式){

  语句

  }

- 进行条件判断，true执行循环体，false则终止循环体

  ==注意==：避免死循环

- 与do  while 语句区别：

  1. 两者相似，不同的是do  while是先执行后判断
  2. do  while能保证循环体执行一次

  ==创建循环体的步骤==

- 创建初始化一个变量

- 在循环体中设置条件语句

- 定义一个更新表达式，每次更新初始化变量

```javascript
    <script>
        var num = 1;
        while (num<=10){
            alert(num);
            num++;
        }
    </script>
```

### 3.4for循环语句

语法：for(初始表达式；条件表达式；更新表达式){

语句；

}

==执行流程==

- 执行表达式，初始化变量(执行表达式只会执行一次)
- 执行条件表达式，判断是否执行循环，true执行循环，false终止循环
- 执行更新表达式，更新表达式执行完毕后继续重复第二个步骤

```javascript
    <script>
        var num =0;
        for (var i = 0; i <=100 ; i++) {
            if (i%2 != 0 ){
               
            }
            num = num+i;
        }
        console.log(num);
    </script>
```

```javascript
    var num = 0;
        var count = 0;
        for (var i = 1; i <= 100; i++) {
            if (i % 7 == 0){
                num = num+i;
                count++;
            }
        }
        console.log(num);
        console.log(count);
```

```javascript
//水仙花数
    <script>
        for (var j = 100; j <1000 ; j++) {

            var bai = parseInt(j/100);
            var shi = parseInt((j-bai*100)/10);
            var ge = j%10;
            if (bai*bai*bai +shi*shi*shi +ge*ge*ge == j){
                console.log(j);
            }
        }
    </script>
```

```javascript
    <script>
        for (var i = 0; i < 5; i++) {
            /*
            * 在循环内部建一个循环来控制图形的宽度
            * 目前外部for循环执行1次，内部for循环执行5次
            * 外部for循环控制高度
            * */
            for (var j = 0; j < i + 1; j++) {
                document.write("*&nbsp;")
            }
            document.write("<br />")
        }
    </script>
```

```javascript
     for (var i = 1; i <= 9; i++) {
            for (var j = 1; j <= i ; j++) {
                document.write(j+"*"+i+"="+j*i+"&nbsp;&nbsp;&nbsp;")
            }
            document.write("<br />")

        }
```

### 3.5break continue关键字

==break==

- break关键字可以用来退出switch或循环语句
- 不能在if语句中使用break和continue
- break关键字，会立即终止离他最近的那个循环语句

==continue==

- continue关键字可以用来跳过当次循环
- 同样continue也是默认只会对离他最近的循环起作用

## 4.对象

### 4.1对象的定义

- 如果使用基本数据类型的数据，我们所创建的变量都是独立的，不能成为一个整体
- 对象属于一种复合的数据类型，在对象中可以保存多个不同的数据类型的属性

==分类==

1. 内建对象：

- 由ES标准定义好的对象，在任何的ES的实现中都可以使用
- 比如：Math String Number Boolean Function...

1. 宿主对象：

- 由JavaScript的运行环境提供的对象，主要有浏览器提供的对象
- 比如BOM DOM

1. 自定义对象：

- 有开发 人员自己创建的对象

### 4.2对象的基本操作

==创建对象==

- 使用new关键字调用的函数，是构造函数constructor
- 构造函数时专门用来创建对象的函数

==保存属性==

- 在对象保存的值称为属性
- 向对象添加属性  语法：对象.属性=属性值

==读取属性==

- 读取对象的属性 语法：对象.属性名

```javascript
    <script>
        var obj = new Object();
        obj.name = "tom";
        obj.gender = "男";
        obj.age =18;
        console.log(obj.name);
    </script>
```

==创建对象方法二==

- 语法 var 变量名 = {

  属性名：属性值，属性名：属性值，

  }

- 属性名的最后一位不加任何符号

==批量生产对象==

```javascript
        //通过该方法创建批量对象
        function createPerson(name,age,gender) {
            //创建一个新的对象
            var obj = new Object();
            //向对象中添加属性
            obj.name = name;
            obj.age = age;
            obj.gender = gender;
            obj.sayName = function () {
                alert(this.name);
            }
            //将新的对象返回
            return obj;
        }
        var obj1 = createPerson("小明",18,"男");
        var obj2 = createPerson("小红",19,"女");
        console.log(obj1);
```



### 4.3类型存储

==基本数据类型==

- 基本数据类型的值直接保存在栈内存中存储
- 值与值之间时独立存在的，在修改一个变量不会影响其他变量

==引用类型(对象)==

- 变量都是保存到栈内存中的

- 对象时保存到堆内存中的，每创建一个新的对象，就会在堆内存中开辟一个新的空间
- 而变量保存的对像的内存地址(对象的引用)，如果两个变量保存同一个对象引用，当一个通过一个变量修改属性时，另一个叶会受影响

==注意==

- 当比较两个基本数据类型的值时，就是比较值
- 当比较两个引用数据类型时，它是比较对象的内存地址
- 如果两个一摸一样，但地址不同，它也会返回false

## 5.函数

### 5.1函数基本语法

==定义==

- 函数也是一个对象
- 函数中可以封装一些功能(代码)，在需要时可以执行这些功能(代码)

==基本语法==

- 使用函数声明来创建一个函数

- 语法：  function 函数名(形参1，形参2，形参3.....){

  语句.......

  }

- 调用语法：函数对象()

```javascript
        function fun() {
            console.log("这是用声明的方式创建一个函数");
        }
        fun();
```

### 5.2函数的参数

==形参==

- 可以在函数的()中来指定一个或多个形参(形式参数)
- 多个形参用逗号隔开，不用赋值

==实参==

- 在调用函数时，可以在()中指定实参(实际参数)
- 实参赋值给函数中对应的形参

```javascript
    function sum(a,b) {
            console.log(a+b);
        }
        sum(4,5)
```

```javascript
      function f(o) {
            console.log("我是"+o.name+",今年"+o.age+"我是一个"+o.gender+"人"+"家住在"+o.address);
        }
        var obj = {
            name:"孙悟空",
            age:19,
            gender:"男",
            address:"花果山"
        }
        f(obj);
//通过对象传对象获得值
```



### 5.3返回值

- 可以使用return来设置函数的返回值
- return后的值将会作为函数的执行结果返回，可以定义一个变量来接受结果

```javascript
  function sun(a,b,c) {
            var d =a+b+c;
            return d;
        }
        var result = sun(1,2,3);
        console.log(result);
```

### 5.4立即执行函数

- 函数定义完后，立即被调用执行
- 只会执行一次

```javascript
 	 (function() {
            alert("我是一个匿名函数");
        })();
```

### 5.5枚举对象的属性

==语法==

- 使用for   ...   in 语句

```javascript
      var obj ={
            name:"孙悟空",
            age:13,
            gender:"男",
            address:"花果山"
        }
        for (var n in obj){
            console.log("属性名："+n);
            console.log("属性值："+obj[n]);
        }
```

### 5.6作用域

==全局作用域==

- 直接编写script标签中的JavaScript代码都在全局作用域
- 全局作用域在页面打开时创建，页面关闭时销毁
- 全局作用域中有一个全局对象window，可以直接使用
- 全局作用域中的变量都是全局变量在任意部分都可以访问

==函数作用域==

- 调用函数时创建函数作用域，函数执行完毕后，函数作用域销毁
- 每次调用函数就会创建i虚拟的函数作用域，之间互相独立
- 函数作用域可以访问全局作用域，而全局作用域却不能访问函数作用域
- 当在函数作用域操作变量时，先会找自身作用域来使用，没有就往上一级寻找，直到找到全局作用域

==注意==

- 全局和函数作用域都有声明提前的特性
- 使用var关键字声明的变量，会在函数中所有代码执行之前被声明
- 函数声明也会在函数中所有的代码之前被执行
- 在函数中，不适用var声明的变量都会成为全局变量
- 定义形式参数相当于在函数作用域中声明了变量

### 5.7构造函数

==构造函数的形式==

- 构造函数就是一个普通的函数，创建方式习惯上首字母大写
- 构造函数与普通函数的调用方式不同，需要使用new关键字来调用

==构造函数的执行流程==

- 它会立即创建一个新的对象
- 将新建的对象设置为函数中的this，在构造函数中可以使用this来引用新建的对象
- 按顺序执行函数中的代码
- 见新建的对象作为返回值返回

==扩展==

- 使用同一个构造函数创建对象时，我i们称为一类对象，也将一个构造函数称为一个类
- 我们将通过一个构造函数创建的对象，称为时该类的实例

==this的总结==

- 当以函数的形式调用时，this是window
- 当以方法的形式调用时，谁调用方法this就是谁
- 当以构造函数的形式调用时，this就是新创建的那个对象

```javascript
        function Person(name,age,gender) {
            this.name = name;
            this.age = age;
            this.gender = gender;
                  this.sayName = function ()   {
                alert(this.name);
        }
        }
        var per = new Person("小明",12,"男");
        console.log(per);
```

```javascript
//修改后的，为了更好释放空间
        function Person(name,age,gender) {
            this.name = name;
            this.age = age;
            this.gender = gender;
            this.sayName = fun;
        }
         function fun () {
            alert(this.name);
        }
        var per = new Person("小明",12,"男");
        console.log(per);
        per.sayName();
```

### 5.8原型对象

- 我们所创建的函数，解析器都会为函数添加一个属性prototype，这个属性对应的对象就是原型对象
- 函数对于普通函数调用prototype没有任何意义，只有构造函数调用时会有一个隐含的属性
- 原型对象相当于公共部分，所有同一个类的实例都可以访问原型对象
- 当我们访问对象的一个属性或方法时，它会先找自身中，没有就直接使用原型对象中
- 这样以后就可以把公共部分提取到原型对象中，就不会影响全局作用域了

```javascript
    function Person() {

        }
        var mc = new Person();
        Person.prototype.a = 123;
        //向Person的原型中添加属性a
        mc.a="我是mc中的123";
        //向Person的原型中添加一个方法
        Person.prototype.sayHello = function(){
            alert("hello");
        }
        mc.sayHello();
        alert(mc.a);
```

==判断属性的扩展==

```javascript
  function Person() {

        }
        Person.prototype.name = "我是原型中的名字";

        var  per = new Person();
        per.age = 18;
        //用in检查对象中是否含有某个属性时，如果对象中没有原型中有，也会返回true
        console.log("name" in per);
        //可以使用对象的hasOwnProperty()来检查自身中是否有该属性
        console.log(per.hasOwnProperty("age"));
```

## 6.数组

### 6.1数组的基本操作

==定义==

- 数组(Array)也是一个对象，用来存储一些值
- 跟普通对象的区别是，普通对象使用字符串作为属性名，而数组使用数字作为索引来操作元素
- 索引是从0开始的

```javascript
        //创建数组对象
        var arr = new Array();
        //使用typeof检查一个数组
        console.log(typeof arr);

        /*
        * 向数组中添加元素
        * 语法：数组[索引] = 值
        * */
        arr[0] = 1;
        arr[1] = 2;
        arr[2] =10;
        /*
        * 读取数组中的元素
        * 语法：数组[索引]
        * */
        console.log(arr[1]);
        /*
        * 可以使用length属性获取数组长度
        * 但是只限于连续的数组
        * */
        console.log(arr.length);
        //向数组的最后一个位置添加元素
        arr[arr.length] = 10;
```

### 6.2数组的六个方法

```javascript
        //使用字面量来创建数组
        var arr = ["孙悟空","小明","小红"]
        console.log(arr);
        //该方法中可以向数组的末尾添加一个或多个元素并返回数组新的长度
        result =arr.push("白骨金","沙和尚","猪八戒");
        console.log(arr);
        console.log(result);
        //该方法可以删除数组的最后一个元素，并将被删除的元素作为返回值返回
        arr.pop();
        console.log(arr);
        //该方法向数组的开头添加一个或多个元素，并返回新的数组长度
        arr.unshift("小绿","小黄");
        console.log(arr);
        //该方法可以删除第一个元素并将被删除的元素作为返回值 返回
        arr.shift();
        console.log(arr);
```

```javascript
        var arr = ["孙悟空","小明","小红"]
        /**
         * slice()
         * 可以用来从数组提取指定的元素
         * 方法不会改变元素数组，而建截取到的元素封装到一个新的数组中返回
         * 参数
         *     截取开始的位置索引，包含开始索引，不包含结束的索引
         */
       var result = arr.slice(1,3);
        console.log(result);

        /**
         * splice()会影响原数组，会将指定的元素从元素组中删除
         * 并将被删除的元素作为返回值返回
         * 参数：
         *    1.第一个，表示开始位置的索引
         *    2.第二个，表示删除的数量
         *    3.第三个，表示可以传递新的元素
         */
        //
        // arr.splice(1,2);
        // console.log(arr);
        var rel = arr.splice(0,1,"沙和尚","牛魔王");
        console.log(arr);
        console.log(rel);
```



### 6.3遍历数组

```javascript
       var arr = ["小明","小红","tom","marry","bod"]
        for (var i = 0; i < arr.length; i++) {
            console.log(arr[i])
        }
```

### 6.4ForEach

- 这个方法只支持IE8以上的浏览器
- 这个方法需要一个函数作为参数
- 我们创建的但是不由我们调用的，称为回调函数
- 浏览器会回调函数中传递三个参数
  1. 当前正在遍历的元素
  2. 当前正在遍历的索引
  3. 正在遍历的数组

```javascript
 var arr = ["小明","小红","tom","marry","bod"]
        arr.forEach(function (value, index, array) {
            //1. 当前正在遍历的元素
             //   2. 当前正在遍历的索引
               // 3. 正在遍历的数组
            console.log(value);
            console.log(index);
            console.log(array);

        })
```

### 6.5数组去重

```javascript
        var arr = [1,3,4,2,3,3,5,4,6,8,5,1]
        //获取数组中的每一个元素
        for (var i = 0; i < arr.length; i++) {
            //获取数组当前后的所有元素
            for (var j =i+1; j < arr.length; j++) {
                //判断两个元素是否相等
                if (arr[i] == arr[j]){
                    //如果相等，则删除J对应的元素
                    arr.splice(j,1);
                    //当删除了当前J所在元素后，后边的元素会自动补位
                    //此时要再次比较一次j所在位置的元素
                    j--;
                }
            }
        }
        console.log(arr);
```

### 6.6数组剩余的方法

```javascript
    <script type="text/javascript">
        /**
         * concat()可以连接两个或多个数组，并将新的数组返回
         * ---该方法不会对原数组产生影响
         */
        var arr = ["小明","小红","小白"];
        var arr1 =["小孩","小绿","小黄"];
        var arr3 = ["小子","好家伙"];
        var result = arr.concat(arr1,arr3);
        console.log(result);
    </script>
```

```javascript
       /**
         *join() 该方法可以将数组转换为一个字符串
         * ---该方法不会对原数组产生影响，而是转换为字符串作为结果返回
         *---在join()中可以指定一个字符串作为参数，将作为数组中元素的连接
         * ---如果不指定默认为逗号
         */
        ss = ["孙悟空","猪八戒","沙和尚"];
        var a = ss.join("-");
        console.log(a);

```

```javascript
/**
         * reverse()
         * ----该方法用来反转数组(前面的去后面，后面的去前面)
         * ----该方法直接修改原数组
         */
        ss = ["孙悟空","猪八戒","沙和尚"];
        ss.reverse();
        console.log(ss);
```

```javascript
   /**
         * sort()
         * ---可以在数组中的元素进行排序
         * ---也会影响原数组，按照Unicode编码进行排序
         * ---对数字不管用
         */
        dd = ["e","c","a","b","d"];
        dd.sort();
        console.log(dd);

```

### 6.7函数的方法

==this的情况==

- 以函数形式调用时，this永远都是window
- 以方法的形式调用时，this是调用方法的对象
- 以构造函数的形式调用时，this是新创建的那个对象
- 使用call()和apply()调用时，this是指定的那个对象

```javascript
  <script type="text/javascript">
        /**
         * call()和apply()方法
         *  这两个方法都是函数对象的方法，需要通过函数对象来调用
         *  当对函数调用call()和apply()都用调用函数执行
         *  在调用call()和apply()可以将一个对象指定为第一个参数
         *      此时这个对象会成为函数执行的this
         *   call()方法可以将实参在对象之后一次传递
         *   apply()方法需要将实参封装到一个数组中统一传递
         */
        function fun() {
            alert(this.name);
        }
        var obj = {name:"obj1"};
        var obj2 = {name:"obj2"};

        fun.call(obj2);
        // fun.apply();
        // fun();
    </script>
```

```javascript
       function f(a,b) {
            console.log("a="+a);
            console.log("b="+b);
        }
        var obj = {};
        f.call(obj,2,3);
        f.apply(obj,[2,3]);
```

### 6.8 arguments

- 在调用函数时，浏览器每次都会传递进两个隐含的参数

1. 函数上下文对象this
2. 封装实参的对象arguments

- arguments是一个类数组对象，它也可以通过索引来操作数据，也可以获取长度
- 在调用函数时，我们所传递的实参都会在arguments中保存
- arguments.length可以用来获取实参的长度
- 我们即使不定义形参，也可以通过arguments来使用实参
- 只不过比较麻烦    arguments[0] 表示第一个实参
- 它里面有个属性callee  这个属性对应一个函数对象，就是当前正在指向的函数对象

```javascript
    <script>
        function fun() {
            console.log(arguments.length);
            console.log(arguments[0]);
        }
        fun("jj","123");
    </script>
```

### 6.9Date方法

```javascript
 <script>
        /**
         * Date对象 在js中表示时间
         * 创建一个date对象 则会进行封装为当前代码执行的时间
         */
        var d = new Date();
        /**
         * 创建一个指定的事件对象
         * 日期格式 月/日/年 时：分：秒
         */
        var d2 = new Date("1/14/2021 22:09:55");
        var data = d2.getDate();//获取当前日期对象时几日
        var day = d2.getDay();//获取当前日期对象是周几，0表示周日
        var month = d2.getMonth();//获取当前是几月
        var time = d2.getTime();//获取当前时间戳
        var start = Date.now();//获取当前时间戳
        console.log(d);
        console.log(d2);
        console.log(data);
        console.log(day);
        console.log(month);
        console.log(time);
        console.log(start);
    </script>
```

### 6.10 Math

```javascript
    <script>
        /**
         * Math 和其他的对象不同，他不是一个构造函数
         * 它属于一个工具类不同创建对象，它里边封装了数学运算相关的属性和方法
         */
        console.log(Math.PI);//表示圆周率
        console.log(Math.abs(-1));//计算一个数的绝对值
        console.log(Math.ceil(1.2));//向上取整
        console.log(Math.floor(1.7));//向下取整
        console.log(Math.round(1.4));//四舍五入
        var max = Math.max(10,2,45,4);//选出最大的
        console.log(max);
    </script>
```



