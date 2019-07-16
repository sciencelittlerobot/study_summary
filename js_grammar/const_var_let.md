# const、var、let三者的区别

声明方式 | 变量提升 | 作用域 | 初始值 | 重复定义
:-: | :-: | :-: | :-: | :-:
const | 否 | 块级 | 需要 | 不允许
let | 否 | 块级 | 不需要 | 不允许
var | 是 | 函数级 | 不需要 | 允许

### 变量提升：
const 和 let 必须先声明再使用，不支持变量提升
  <pre>
  console.log(a);  // Uncaught ReferenceError: a is not defined
  console.log(b);  // Uncaught ReferenceError: b is not defined
  console.log(c);  // undefined

  const a = 'a';
  let b = 'b';
  var c = 'c';
  </pre>

### 作用域：
const，let 支持块级作用域，有效避免变量覆盖;
<pre>
  const a = 'a';
  let b = 'b';
  var c = 'c';
    
  if (1 === 1) {
   const a = 'a1';
   let b = 'b1';
   var c = 'c1';

   console.log(a, b, c);   // a1 b1 c1
  }

  console.log(a, b, c); // a b c1
</pre>
块级作用域，在外层不能直接访问内层变量;
<pre>
  if (1 === 1) {
    const a = 'a';
    let b = 'b';
    var c = 'c';
    
    console.log(a, b, c);	// a b c
  }

  console.log(a, b, c);
  // Uncaught ReferenceError: a is not defined
  // Uncaught ReferenceError: b is not defined
  // c
</pre>
const 定义常量，该常量不能赋值，但该常量的属性可以赋值;<br>
全局变量不再设置为顶层对象（window）的属性，有效避免全局变量污染;<br>
符合预期的for循环;
<pre>
  // 输出10次10
  for (var i = 0; i < 10; i ++) {
    setTimeout(function () {
      console.log(i);
    }, 10);
  }
  // 0 1 2 3 4 5 6 7 8 9
  for (let i = 0; i < 10; i ++) {
    setTimeout(function () {
      console.log(i);
    }, 10);
  }
  // 使用var定义变量，使用闭包即可和let输出一样的效果
  for (var i = 0; i < 10; i ++) {
    (function (num) {
      setTimeout(function () {
        console.log(num);
      }, 10);
    })(i);
  }
</pre>

### const用于常量的定义，使用时必须进行初始化，且值后期不可进行修改；定义：
  <pre>
  const a = 'a';
  console.log(a);
  // a

  a = 'b';
  console.log(a);
  // Uncaught TypeError: Assignment to constant variable

  const b;
  console.log(b);
  // Uncaught SyntaxError: Missing initializer in const declaration
  </pre>

### var与let都是作用于作用域，let和const是es6的语法

### 参考
* [参考一](https://www.jb51.net/article/116491.htm)
