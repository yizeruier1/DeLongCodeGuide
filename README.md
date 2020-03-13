# 前端代码规范




## 命名规则

* 项目名称命名

  全部采用大驼峰命名，例如：MyProjectName。

* 目录命名

  全部采用小驼峰，例如：basicUtils、commonTools，有复数结构时，一定要采用复数结构，例如：images、utils。

* 单文件命名

  同目录命名一样，单文件包括 css、js、html、styl、less、sass、scss、vue、jsx、ts 等文件。

* 变量命名

  变量命名采用小驼峰命名，一定要简明扼要，语义化，一律用英文命名，不要用汉语拼音，例如：

  ```javascript
  // 普通变量
  // bad
  let guize = null;
  let ruleform = null;
  let requestResult = null
  // good 
  let rules = null;
  let ruleForm = null;
  let requestRes = null
  
  // 函数方法命名  小驼峰命名
  function getList(){...}
  const getList = () => {...}
  
  // 构造函数命名和类名首字母必须大写  大驼峰命名
  // bad
  function person(name){
      this.name = name
  }
  class myUtils {
      constructor(options){
          this.options = options
      }
  }
  // good
  function Person(name){
      this.name = name
  }
  class MyUtils {
      constructor(options){
          this.options = options
      }
  }
  ```

  CSS 命名规则：

  ```css
  /* 采用英文命名，用中划线 - 连接 */
  .swiper-wrap{...}
  
  /* less、scss、stylus 采用小驼峰命名 */
  $bgColor: #000;
  ```




## 代码风格约定

代码缩进推荐使用四个空格，但是不强制要求，只要项目中统一就行。

JS 代码统一不加分号。



## HTML 规范

* 语法规定

  在 HTML 属性上，使用双引号，不要使用单引号；属性名全小写，用中划线做分隔符；自动闭合的标签要加上 空格/；例如：

  ```html
  <!DOCTYPE html>
  <html>
      <head>
          <title>Page title</title>
      </head>
      <body>
          <img src="images/companyLogo.png" alt="Company" />
          <h1 class="hello-world">Hello, world!</h1>
      </body>
  </html>
  ```

* 文件引入规则

  css 文件引入统一放到 `head` 里，js 文件引入统一放到 `</body>` 之后，文件的 `type`  不用写，因为 `text/css`  和  `text/javascript`  分别是他们的默认值， `style` 标签要放到 `link `标签之后，但是不推荐写在页面里，写到  css  里更好。例如：

  ```html
  <!DOCTYPE html>
  <html>
      <head>
          <link rel="stylesheet" href="codeGuide.css">
          <style></style>
      </head>
      <body></body>
      <script src="codeGuide.js"></script>
  </html>
  ```

* 尽量少的 DOM

  在编写 HTML 代码时，应尽量减少不必要的 DOM ，尽量遵循HTML标准和语义，但是不应该以浪费实用性作为代价；任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。例如：

  ```html
  <!DOCTYPE html>
  <html>
      <head>
          <style>
              .margin{
                  margin: 100px auto;
              }
          </style>
      </head>
      <body>
          <!-- bad -->
          <div class="h100"></div>
          <div class="content w1260"></div>
          <div class="h100"></div>
          
          <!-- good -->
          <div class="content w1260 margin"></div>
      </body>
  </html>
  ```

  



## CSS, SCSS规范

* 不需要空格
  1. 属性名后
  2. 多个规则的分隔符','前
  3. `!important` '!'后
  4. 属性值中'('后和')'前
  5. 行末不要有多余的空格

* 需要空格
  1. 属性值前
  2. 选择器'>', '+', '~'前后
  3. '{'前
  4. `!important` '!'前
  5. `@else` 前后
  6. 属性值中的','后
  7. 注释'/*'后和'*/'前

```css
/* bad */
.element {
    color :red! important;
    background-color: rgba(0,0,0,.5);
}

/* good */
.element {
    color: red !important;
    background-color: rgba(0, 0, 0, .5);
}

/* bad */
.element ,
.dialog{
    ...
}

/* good */
.element,
.dialog {

}

/* bad */
.element>.dialog{
    ...
}

/* good */
.element > .dialog{
    ...
}

/* bad */
.element{
    ...
}

/* good */
.element {
    ...
}

/* bad */
@if{
    ...
}@else{
    ...
}

/* good */
@if {
    ...
} @else {
    ...
}
```

* 换行

  '{'后和'}'前；每个属性独占一行；多个规则的分隔符','后；

```css
/* bad */
.element
{color: red; background-color: black;}

/* good */
.element {
    color: red;
    background-color: black;
}

/* bad */
.element, .dialog {
    ...
}

/* good */
.element,
.dialog {
    ...
}
```

* 引号

  最外层统一使用双引号；url的内容要用引号；属性选择器中的属性值需要引号。

```css
.element:after {
    content: "";
    background-image: url("logo.png");
}

li[data-type="single"] {
    ...
}
```





## JavaScript 规范

* 最重要的

  1. 本地调试代码和 `debugger` 不要提交到 SVN 或者 GIT 仓库
  2. 只要有 babel 的项目全部使用 ES6/7，变量声明使用 let / const
  3. 同一个作用域内变量声明全部放到顶部，逻辑代码在下面
  4. 语义化命名，减少无用代码、增强可读性

* 关于空格

  1. 二元运算符前后和三元运算符 '?:' 前后要加空格
  2. 代码块 '{' 前要加空格
  3. 下列关键字前：`else`, `while`, `catch`, `finally`要加空格
  4. 下列关键字后：`if`, `else`, `for`, `while`, `do`, `switch`, `case`, `try`, `catch`, `finally`, `with`, `return`, `typeof`要加空格
  5. 单行注释 '//' 后（若单行注释和代码同行，则 '//' 前也需要），多行注释 '*' 后加空格
  6. 对象的属性值前加空格
  7. for循环，分号后留有一个空格，前置条件如果有多个，逗号后留一个空格
  8. 函数的参数之间

  ```javascript
  // bad
  var a = {
      b :1
  }
  
  // good
  var a = {
      b: 1
  }
  
  // bad
  ++ x
  y ++
  z = x?1:2
  
  // good
  ++x
  y++
  z = x ? 1 : 2
  
  // bad
  var a = [ 1, 2 ]
  
  // good
  var a = [1, 2]
  
  // bad
  var a = ( 1+2 )*3
  
  // good
  var a = (1 + 2) * 3
  var doSomething = function(a, b, c){
      // do something
  };
  doSomething(item)
  
  // bad
  for(i=0;i<6;i++){
      x++;
  }
  // good
  for (i = 0; i < 6; i++) {
      x++
  }
  
  // bad
  if(condition){
      // do something
  }else{
      // do something
  }
  // good
  if (condition) {
      // do something
  } else {
      // do something
  }
  ```

  

* 注释

  1. 双斜线后，必须跟一个空格
  2. 缩进与下一行代码保持一致
  3. 可位于一个代码行的末尾，与代码间隔一个空格
  4. 多行注释最少三行, '*' 后跟一个空格
  5. 通用工具函数方法使用文档注释，需完善功能、参数等信息

```javascript
if (condition) {
  // 这里是注释
  allowed();
}

/*
 * 这里是注释
 */
let x = 1

/**
 * @func
 * @desc 一个带参数的函数
 * @param {string} a - 参数a
 * @param {number} b=1 - 参数b默认值为1
 * @param {string} c=1 - 参数c有两种支持的取值</br>1—表示x</br>2—表示xx
 * @param {object} d - 参数d为一个对象
 * @param {string} d.e - 参数d的e属性
 * @param {string} d.f - 参数d的f属性
 * @param {object[]} g - 参数g为一个对象数组
 * @param {string} g.h - 参数g数组中一项的h属性
 * @param {string} g.i - 参数g数组中一项的i属性
 * @param {string} [j] - 参数j是一个可选参数
 */
function foo(a, b, c, d, g, j) {
    // do something
}
```

* 引号

  优先使用单引号，如有多层嵌套最外层统一使用单引号。

```javascript
// bad
let x = "test"

// good
let y = 'foo',
    z = '<div id="test"></div>'
```

* 需要注意的
  1. 优先使用 '===' 和 '!==' 进行判断
  2. 不要在内置对象的原型上添加方法，如Array, Date
  3. 不要在内层作用域的代码里声明了变量，之后却访问到了外层作用域的同名变量
  4. 变量不要先使用后声明
  5. 不要在一句代码中单单使用构造函数，记得将其赋值给某个变量
  6. 不要在同个作用域下声明同名变量
  7. 不要在一些不需要的地方加括号，例：delete(a.b)
  8. 不要使用未声明的变量（全局变量需要加到.jshintrc文件的globals属性里面）
  9. 不要声明了变量却不使用
  10. 不要在应该做比较的地方做赋值
  11. 数组中不要存在空元素
  12. 不要在循环内部声明函数
  13. 不要像这样使用构造函数，例：`new function () { ... }`, `new Object`

```javascript
// bad
if (a == 1) {
    a++
}

// good
if (a === 1) {
    a++
}

// bad
Array.prototype.count = function(value){
    return 4
}

// bad
var x = 1
function test(){
    if (true) {
        var x = 0
    }
    x += 1
}

// bad
function test(){
    console.log(x)

    var x = 1
}

// bad
new Person()

// good
var person = new Person()

// bad
delete(obj.attr)

// good
delete obj.attr

// bad
if (a = 10) {
    a++
}

// bad
var a = [1, , , 2, 3]

// bad
var nums = []
for (var i = 0; i < 10; i++) {
    (function(i) {
        nums[i] = function(j) {
            return i + j
        }
    }(i))
}

// bad
var singleton = new function(){
    var privateVar

    this.publicMethod = function(){
        privateVar = 1
    }

    this.publicMethod2 = function(){
        privateVar = 2
    }
}
```





## VUE 规范

* 需要注意的

  vue 页面模板要 template 标签在最前面，script 标签在中间，style 标签在最后，VSCode 推荐使用 Vue VSCode Snippets 插件快捷生成模板。

  vue 页面模板只留下需要用到的就行，如果只用到了 methods ，那就不要写其他的，尽量使代码简洁。

* 模块化开发

  一个 vue 文件代码行数禁止超过 500 行，要把页面细分为多个组件，页面只是用来组合多个组件展示，以此来实现低耦合、高复用性。例如：一个有 3 个表单、两个弹窗的 vue 页面

  ```javascript
  <template>
      <!-- 建议用省略写法 -> : 代替 v-bind: -->
      <my-form1 :options="options" />
      <my-form2 :options="options" />
      <my-form3 :options="options" />
  
      <my-dialog1 :options="options" />
      <my-dialog2 :options="options" />
  </template>
  <script>
      import myForm1 from '...'
      import myForm2 from '...'
      import myForm3 from '...'
      import myDialog1 from './components/myForm1'
      import myDialog2 from './components/myForm2'
  	export default{
          components: {
              myForm1,
              myForm2,
              myForm3,
              myDialog1,
              myDialog2
          }
      }
  </script>
  ```

* 开发目录

  apis 文件用来放所有的请求、assets 放所有资源、components 放所有的通用组件、views 放页面、router 放路由、store 放 vuex 相关、utils 放所有的工具函数、styles 放公共样式文件，components 和 views 下的组件和页面都要放在文件里，页面或组件的单独组件要放到个文件夹的 components 文件夹。

```
src
│  App.vue
│  main.js
│
├─api
│      api.js
│      axiosConfig.js
│
├─assets
│  ├─font-icon
│  │      iconfont.ttf
│  │
│  └─images
│          ava.jpg
│
├─components
│  ├─adminDrawer
│  │      index.vue
│  │
│  ├─adminMenu
│  │      index.vue
│  │
│  ├─bolgHeader
│  │      index.vue
│  │
│  ├─editor
│  │      index.vue
│  │
│  └─websiteNotice
│          index.vue
│
├─router
│      routerConfig.js
│      routerMap.js
│
├─store
│  │  store.js
│  │
│  └─modules
│          artical.js
│          user.js
│
├─styles
│      common.styl
│
└─views
    ├─404
    │      index.vue
    │
    ├─addArtical
    │      index.vue
    │
    ├─articalDetail
    │      index.vue
    │
    ├─articals
    │  │  index.vue
    │  │
    │  └─components
    │          dataTable.vue
    │          searchRow.vue
    │
    ├─articalTypes
    │  │  index.vue
    │  │
    │  └─components
    │          dataTable.vue
    │
    ├─auth
    │      authBox.vue
    │      login.vue
    │      register.vue
    │
    ├─deletedArtical
    │      index.vue
    │
    └─layout
            index.vue
```

