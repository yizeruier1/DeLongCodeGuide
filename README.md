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
  
  // 构造函数命名首字母必须大写  大驼峰命名
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
  2. 语义化命名，减少无用代码、增强可读性
