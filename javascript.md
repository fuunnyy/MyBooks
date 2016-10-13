# JavaScript
###javascript一些比较好玩用法小结。
- `===`与`==`区别在于前者会比较对象的类型。后者只会比对两者是否相等不会比较两者类型。
- `alt + command + J`这个快捷键可以快速的在谷歌浏览器中调用Javascript控制台。
- `iterable`类型的对象包含`Array/Map/Set`，这种类型的可以通过`for ... of`来进行遍历拿到对应的Value.同样也可以用以下的代码来进行调用。
````
var a = ['A', 'B', 'C'];
a.forEach(function (element, index, array) {
    // element: 指向当前元素的值
    // index: 指向当前索引
    // array: 指向Array对象本身
    alert(element);
});
````
- Javascript中变量作用域这个东西一定要注意
 - 首先要在函数中定义所有的变量。就算你不定义，系统也是会帮你这样做的；
 - 不在任何函数内定义的变量都具有全局作用域。
 - 全局变量会绑定到window上，不同的JavaScript文件如果使用了相同的全局变量，或者定义了相同名字的顶层函数，都会造成命名冲突，并且很难被发现。减少冲突的一个方法是把自己的所有变量和函数全部绑定到一个全局变量中。例如：
 ````
// 唯一的全局变量MYAPP:
   var MYAPP = {};
// 其他变量:
   MYAPP.name = 'myapp';
   MYAPP.version = 1.0;
// 其他函数:
   MYAPP.foo = function ()
{
   return 'foo';
};
````
 - 利用`let`代替`var`开辟一个块级作用域变量。`const`作为一个常量标识肯定是也有块级变量标识的意思。

