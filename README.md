# 前端代码规范




## 命名规则

* 项目名称命名

  全部采用大驼峰命名，例如：MyProjectName。

* 目录命名

  全部采用小驼峰，例如：basicUtils、commonTools，有复数结构时，一定要采用复数结构，例如：images、utils。

* 单文件命名

  同目录命名一样，单文件包括 css、js、html、styl、less、sass、scss、vue、jsx、ts 等文件。

* 变量命名

  变量命名采用小驼峰命名，一定要简明扼要，一律用英文命名，不要用汉语拼音，例如：

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

  css 文件引入统一放到`head`里，js 文件引入统一放到`</body>`之后，文件的`type` 不用写，因为`text/css` 和 `text/javascript` 分别是他们的默认值，`style`标签要放到`link`标签之后，但是不推荐写在页面里，写到 css 里更好。例如：

  ```html
  <!DOCTYPE html>
  <html>
      <head>
          <link rel="stylesheet" href="codeGuide.css">
          <style>
          	...
          </style>
      </head>
      <body>
      	...
      </body>
      <script src="codeGuide.js"></script>
  </html>
  ```

  

