call 和 apply 都是为了改变某个函数运行时的上下文（context）而存在的，换句话说，就是为了改变函数体内部 this 的指向。
JavaScript 的一大特点是，函数存在「定义时上下文」和「运行时上下文」以及「上下文是可以改变的」这样的概念。
举个例子：

```js
function fruits() {}
  
fruits.prototype = {
    color: "red",
    say: function() {
        console.log("My color is " + this.color);
    }
}
  
var apple = new fruits;
apple.say();    //My color is red
```

但是如果我们有一个对象banana= {color : "yellow"} ,我们不想对它重新定义 say 方法，那么我们可以通过 call 或 apply 用 apple 的 say 方法：

```js
banana = {
    color: "yellow"
}
apple.say.call(banana);     //My color is yellow
apple.say.apply(banana);    //My color is yellow
```

所以，可以看出 call 和 apply是为了动态改变this而出现的，当一个object没有某个方法（本栗子中banana没有say方法），但是其他的有（本栗子中apple有say方法），我们可以借助call或apply用其它对象的方法来操作。

---
# 区别
对于 apply、call 二者而言，作用完全一样，只是接受参数的方式不太一样。例如，有一个函数定义如下：

```js
var func = function(arg1, arg2) {
     
};
```

就可以通过如下方式来调用：

```js
func.call(this, arg1, arg2);
func.apply(this, [arg1, arg2])
```

其中 this 是你想指定的上下文，他可以是任何一个 JavaScript 对象(JavaScript 中一切皆对象)，call 需要把参数按顺序传递进去，而 apply 则是把参数放在数组里。
JavaScript 中，某个函数的参数数量是不固定的，因此要说适用条件的话，当你的参数是明确知道数量时用 call 。
而不确定的时候用 apply，然后把参数 push 进数组传递进去。当参数数量不确定时，函数内部也可以通过 arguments 这个数组来遍历所有的参数。

为了巩固加深记忆，下面列举一些常用用法：
1、数组之间追加

```js
var array1 = [12 , "foo" , {name "Joe"} , -2458]; 
var array2 = ["Doe" , 555 , 100]; 
Array.prototype.push.apply(array1, array2); 
/* array1 值为  [12 , "foo" , {name "Joe"} , -2458 , "Doe" , 555 , 100] */
```

2、获取数组中的最大值和最小值

```js
var  numbers = [5, 458 , 120 , -215 ]; 
var maxInNumbers = Math.max.apply(Math, numbers),   //458
    maxInNumbers = Math.max.call(Math,5, 458 , 120 , -215); //458
```

number 本身没有 max 方法，但是 Math 有，我们就可以借助 call 或者 apply 使用其方法。

3、验证是否是数组（前提是toString()方法没有被重写过）

```js
functionisArray(obj){ 
    returnObject.prototype.toString.call(obj) === '[object Array]' ;
}
```

4、类（伪）数组使用数组方法

```js
var domNodes = Array.prototype.slice.call(document.getElementsByTagName("*"));
```







