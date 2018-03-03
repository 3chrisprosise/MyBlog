---
title: JavaScript
date: 2017-11-05 20:19:26
tags:  JavaScript
---

#JavaScript 知识点总结

1. **var foo = function (){}**  与 **function foo (){}** 的区别

   这个问题涉及到了 JavaScript 编译时提前的问题，在此引用了[知乎][https://www.zhihu.com/question/19878052]上的一篇文章JavaScript在编译时候会对代码做 “**提前**” （hoist）编译的处理 于是就会产生一些意外的效果

   对于 ：

   ```javascript
    var funtion_name = function() {} 
   ```

   而言，function_name 的声明会被提前，而函数的具体定义则不会被提前编译，仅在调用的时候初始化但是赋值号（=）后面的内同不会被提前，匿名函数只会在调用的时候被初始化。

   而对于

   ```javascript
   function function_name() {}
   ```

   函数体的声明过程在整个程序执行之前就会被处理，只要位于同一个作用域下，就可以直接访问到，同样也可以在声明之前调用

   例如：

   ```javascript
   function sayOne(){

   	conso.log("one");

   }

   sayOne();    //OutPut :  tow

   function sayOne(){

   	conso.log("two");

   }
   ```

   编译器在处理时会首先对函数本身进行初始化，然而后定义的函数会覆盖掉先前的定义，相当于编译的过程为：

   ```javascript
   function sayOne(){

   	console.log("one");

   }

   function sayOne(){

   	console.log("two");

   }

   sayOne();
   ```
   这种情况可以理解为声明导致的执行顺序提升，仅有函数声明会被提升，函数表达式则不会

2. Date() 对象

  ```javascript
  let MyDate = new Date()

  myDate.getHours();       //获取当前小时数(0-23)

  myDate.getMinutes();     //获取当前分钟数(0-59)
  ```

3.this的指向问题

​	考虑如下的代码段

```java
	function foo(){
        console.log( this.bar )
    }

   	var bar = 'global'
   	var obj1 = {
        bar: "obj1"
        foo: foo
  	}
    var obj2 = {
       	 bar: "obj2"
   	}

    foo()
    obj1.foo()
    foo.call(obj2)
   	new foo()
```

​	最后四次调用的输出值可以根据foo函数调用时的域来判断，求解的关键要找出 **this** 指向的 **object** ，此时可以将整个区域当作是一个 **object** 内部类似于

```
{
    function foo(){
        console.log( this.bar )
    }

            var bar = 'global'
            var obj1 = {
                bar: "obj1"
                foo: foo
            }
            var obj2 = {
                bar: "obj2"
            }


        foo()
        obj1.foo()
        foo.call(obj2)
        new foo()
}
```

​	这样可以理解直接调用foo时候的this指向全局object， 于是结果为 **global** , 第二此调用时候foo在obj1内部，于是this的指向变为 obj1 内部,则输出结果为obj1，对于 **call** ，**apply** ，**bind** 而言，这三个函数都是用来重新定义this的指向的，于是 **foo.call(obj2)** 的结果变成了在obj2内部调用foo函数，输出结果为obj2，然而对于new 的情况，foo并没有显式或隐式的绑定任何一个对象，所以foo输出值为**undefined**（其实这里this并不为undefined，但是没有任何关于bar的定义，所以结果为undefined）

4.正则表达式

​	（1）.正则表达式格式

```javascript
/正则表达式主体/修饰符（可选）
```

​	（2）字符串正则方法

```javascript
str.search()
str.replace()
```

​	   (3)正则表达式方法（RegExp Object）

```javascript
let reg = /test/
reg.test("string") // 判断字符中是否满足正则条件
reg.exec("string") //输出满足正则匹配的字符
```

​	 