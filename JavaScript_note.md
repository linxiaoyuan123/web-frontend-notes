# JavaScript笔记

#### 79_数学内置对象Math

```js
<script>
    // 属性
    console.log(Math.PI)
    // 方法
    // ceil 天花板  向上取整 Math.ceil()
    console.log(Math.ceil(1.1)) // 2 
    console.log(Math.ceil(1.5)) // 2 
    console.log(Math.ceil(1.9)) // 2 
    // floor 地板  向下取整 Math.floor()
    console.log(Math.floor(1.1))  // 1
    console.log(Math.floor(1.5))  // 1
    console.log(Math.floor(1.9))  // 1
    console.log(Math.floor('12px'))  // 1
    console.log('----------------')
    // 四舍五入 round Math.round()
    console.log(Math.round(1.1))  // 1
    console.log(Math.round(1.49))  // 1
    console.log(Math.round(1.5))  // 2
    console.log(Math.round(1.9))  // 2
    console.log(Math.round(-1.1))  // -1 
    console.log(Math.round(-1.5))  // -1
    console.log(Math.round(-1.51))  // -2

    // 取整函数 parseInt(1.2)   // 1
    // 取整函数 parseInt('12px')   // 12

    console.log(Math.max(1, 2, 3, 4, 5))
    console.log(Math.min(1, 2, 3, 4, 5))
    console.log(Math.abs(-1));

    // null  类似 let obj = {}
    let obj = null 
  </script>
```



#### 80_随机数函数(重要)

```js
<script>
    // 随机数函数(重要)
    // Math.random()  左闭右开 能取到 0 但是取不到 1 中间的一个随机小数 [0, 1)
    // Math.floor(Math.random() * (10 + 1))   0~ 10  之间的整数
    // Math.floor(Math.random() * (5 + 1)) + 5   5~ 10 之间的整数
    // Math.floor(Math.random() * (M - N + 1)) + N   取到 N ~ M 的随机整数


    // 左闭右开 能取到 0 但是取不到 1 中间的一个随机小数 [0, 1)
    // console.log(Math.random())


    // 0~ 10 之间的整数
    // console.log(Math.floor(Math.random() * 11))


    // let arr = ['red', 'green', 'blue']
    // let random = Math.floor(Math.random() * arr.length)
    // // console.log(random)
    // console.log(arr[random])


    // 取到 N ~ M 的随机整数
    function getRandom(N, M) {
      return Math.floor(Math.random() * (M - N + 1)) + N
    }
    console.log(getRandom(4, 8))
  </script>
```



#### 85_术语解释和数据类型存储

```js
<script>
    /* 
    1.术语解释

      关键字            在js中有特殊意义的词汇            let、var、function、if、else等

      保留字            在目前js没意义，但未来可能有意义   int、short、long、char

      标识(标识符)      变量名、函数名的另一种叫法          无

      表达式            能产生值的代码，一般配合运算符出现   10 + 3 、 age >= 18

      语句              一段可以执行的代码                 if() for()

    2.数据类型
      基本数据类型(简单数据类型，值类型)
        1)在存储时变量中存储的是值本身，因此叫做值类型
          eg：string，number，boolean，undefine的，null

      引用数据类型(复杂类型，引用类型)
        1)在存储时变量中存储的仅仅是地址(引用),因此叫做引用数据类型
          eg：object，function，array等

    3.堆栈空间分配区别：
      栈(操作系统)：由操作系统自动分配释放存放函数的参数值、局部变量的值等
        简单数据类型存放在栈里面

      堆(操作系统)：存储复杂类型(对象),一般由程序员分配释放，若程序员不释放，由垃圾回收机制回收
        引用数据类型存放在堆里面

    */
  </script>
```

![图1](D:\学习\study_everyday\assets\JavaScript_note\image-20250629182907674.png)

```js
<script>
    //简单数据类型栈赋值例子
    let num1 = 10
    let num2 = num1
    num2 = 20
    console.log(num1) // 结果是 10
</script>
```

![image-20250629183020390](D:\学习\study_everyday\assets\JavaScript_note\image-20250629183020390.png)

```js
<script>
    //复杂数据类型堆例子
	let obj1 = {
      age: 18
    }
    let obj2 = obj1
    // 修改属性
    obj2.age = 20
    console.log(obj1.age) // 20
</script>
```

![image-20250629183047226](D:\学习\study_everyday\assets\JavaScript_note\image-20250629183047226.png)



#### 86_let或const声明

```js
<script>
    /* 
      变量声明：var、let和const（var直接pass）
    
      1.声明变量优先用const，若后面发现它需要被修改则再改为let

      2.const声明的对象可以修改里面的值原因：
        1)对象是引用类型，里面存储的是地址，只要地址不变，就不会报错
        2)建议数组和对象使用const来声明

      3.使用let声明变量的情况：
        1)如果一个基本数据类型的值或者引用类型的地址发生变化时，需要用let
        2)一个变量进行加减运算，如for循环中的 i++
        
      4.使用const声明：
        1)const声明的值不能改变，而且const声明变量的时候需要里面进行初始化
        2)但对于引用数据类型，const声明的变量，里面存的不是值，而是地址
    */
    //eg1
    const arr = ['red', 'pink']
    // arr.push('blue')
    // console.log(arr)
    
	//eg2
    // arr = [1, 2, 4]
    // console.log(arr)  // 错误
  </script>
```

1.eg1不报错的原因:

![image-20250629190201242](D:\学习\study_everyday\assets\JavaScript_note\image-20250629190201242.png)

2.eg2报错的原因:

![image-20250629190223539](D:\学习\study_everyday\assets\JavaScript_note\image-20250629190223539.png)



#### 87_Web_APIs和dom对象

```js
<script>
    /* 
    一、Web APIs:
      1.作用：使用JS去操作html和浏览器
      2.分类：DOM(文档对象模型)、BOM(浏览器对象模型)

    二、DOM(Document Object Model——文档对象模型):
      1.定义：用于呈现以及任意HTML或XML文档交互的API
        简单来说，DOM是浏览器提供的一套专门用来 操作网页内容 的功能

      2.作用：开发网页内容特效实现用户交互
    
    三、DOM树
      1.定义：
        1)将HTML文档以树状结构直观的表现出来，我们称之为文档树或DOM树
        2)描述网页内容关系的名词
      2.作用：文档树直观的体现了标签与标签之间的关系

    四、**DOM对象**：
      1.定义：浏览器根据html标签生成的js对象
        1)所有的标签属性都可以在这个对象上面找到
        2)修改这个对象的属性会自动映射到标签身上
      
      2.DOM核心思想：把网页内容当作 对象 来处理

      3.document对象：
        1)是DOM里提供的一个对象
        2)所以它提供的属性和方法都是用来访问和操作网页内容的
        3)网页所有内容都在document里面
    */


    const div = document.querySelector('div')
    // 打印对象
    console.dir(div)  // dom 对象
  </script>
```



#### 88_获取DOM元素

```js
<script>

    /* 
      法一：根据CSS选择器来获取DOM元素(重点)
        1.选择匹配第一个元素
          document.querySelector('CSS选择器')
          参数：包含一个或多个有效的CSS选择器 字符串
          返回值：CSS选择器匹配的第一个元素，一个HTMLElement对象
          可以直接操作
        2.选择匹配多个元素
          document.querySelectorAll('CSS选择器')
          参数：包含一个或多个有效的CSS选择器 字符串
          返回值：CSS选择器匹配的NodeList 对象集合
          返回值是一个伪数组，需要遍历得到每一个元素
          (有长度有索引号的数组，但是没有pop(),push()等数组方法)

      法二：其他获取DOM元素方法(了解) ————Elements获取的都是伪数组
        1.根据id获取一个元素: document.getElementById('nav')
        2.根据标签获取一类元素，获取页面所有div: document.getElementsByTagName('div')
        3.根据类名获取元素，获取页面所有类名为w的:document.getElementsByClassName('w')

    */

    // 1. 获取匹配的第一个元素
    // const box = document.querySelector('div')
    // const box = document.querySelector('.box')
    // console.log(box)

    // const nav = document.querySelector('#nav')
    // console.log(nav)

    //获取一个DOM元素之后，能直接修改，但如果是querySelectorAll('CSS选择器')获取多个，
    // 则只能通过遍历的方式一次给里面的元素作修改
    // nav.style.color = 'red'

    // 1. 我要获取第一个小 ulli, 获取一个DOM元素, querySelector('CSS选择器')
    // const li = document.querySelector('ul li:first-child')
    // console.log(li)

    // 2. 选择所有的小li, 获取多个DOM元素, querySelectorAll('CSS选择器')
    // const lis = document.querySelectorAll('ul li')
    // console.log(lis)

    // 1.获取元素
    const lis = document.querySelectorAll('.nav li')
    // console.log(lis)
    for (let i = 0; i < lis.length; i++) {
      console.log(lis[i]) // 每一个小li对象
    }

    const p = document.querySelectorAll('#nav')
    // console.log(p)
    // p[0].style.color = 'red'
  </script>
```



#### 89_修改对象内容

```js
<body>
  <div class="box">我是文字的内容</div>
  <script>

    /* 
      设置/修改DOM元素内容的两种方法：
        1. 元素.innerText  不解析标签  显示纯文本
        2. 元素.innerHTML  解析标签(用法2即可)
    */

    // 1. 获取元素
    const box = document.querySelector('.box')

    // 2. 修改文字内容  对象.innerText 属性
    //    显示纯文本，不解析标签
    console.log(box.innerText)  // 获取文字内容
    //box.innerText = '我是一个盒子'  // 修改文字内容
    //box.innerText = '<strong>我是一个盒子</strong>'  // 不解析标签

    // 3. innerHTML 解析标签
    console.log(box.innerHTML)
    // box.innerHTML = '我要更换'
    box.innerHTML = '<strong>我要更换</strong>'
  </script>
</body>
```



#### 91_修改元素常见的属性

```js
<body>
  <img src="./images/1.webp" alt="">
  <script>

    /* 
      还可以通过JS设置/修改标签元素属性，比如通过src更换图片
      最常见的属性比如：href、title、src等
      语法：对象.属性 = 值
    */

    // 1. 获取图片元素
    const img = document.querySelector('img')
    // 2. 修改图片对象的属性   对象.属性 = 值
    img.src = './images/2.webp'
    img.title = 'pink老师的艺术照'

    //案例随机显示图片
    const random = Math.floor(Math.random() * 7) + 1
    img.src = `./images/${random}.webp`
  </script>
</body>
```



#### 93_通过style属性修改样式

```js
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .box {
      width: 200px;
      height: 200px;
      /* background-color: pink; */
    }
  </style>
</head>

<body>
  <div class="box"></div>
  <script>

    /* 
      操作元素样式属性(重要)
        1.语法：对象.style.样式属性 = '值'  别忘了跟单位
        2.多组单词的采取 小驼峰命名法 eg:CSS里写background-color的，js中写backgroundColor

      因为页面里整一个body是唯一的，所以获取body元素可以用document.body
    */

    // 1. 获取元素
    const box = document.querySelector('.box')
    //2. 修改样式属性 对象.style.样式属性 = '值'  别忘了跟单位
    box.style.width = '300px'
    // 多组单词的采取 小驼峰命名法
    //box.style.backgroundColor = 'hotpink'
    box.style.border = '2px solid blue'
    box.style.borderTop = '2px solid red'

    //盒子刷新，盒子随机更换背景图片

    // 1.封装一个获取随机数的函数
    function getRandom(N,M) {
      return Math.floor(Math.random() * (M - N) + 1) + N
    }

    // 2.获取随机数
    const random = getRandom(1,6)

    // 3.修改样式属性
    box.style.backgroundImage = `url(./images/${random}.webp)`
  </script>
</body>

</html>
```

