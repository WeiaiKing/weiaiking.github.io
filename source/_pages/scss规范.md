---
title: scss规范
---
## scss规范

css的预处理器，方便更快捷的处理css,解决了css复用，嵌套，也是一个模块

### 记住

* &(嵌套) $(变量) @(引入)

### 1.变量($)

```scss
// 变量可以在css规则块定义之外存在。当变量定义在css规则块内，那么该变量只能在此规则块内使用。
// 变量名可以是中划线也可以是下划线，大多用中划线
$nav-color: #F90;
nav {
  $width: 100px;
  width: $width;
  color: $nav-color;
}

//编译后

nav {
  width: 100px;
  color: #F90;
}

//默认值
$fancybox-width: 400px !default;
.fancybox {
width: $fancybox-width;
}
```

### 2.嵌套(&)

**父选择器的标识符&**

一般情况下，`sass`在解开一个嵌套规则时就会把父选择器（`#content`）通过一个空格连接到子选择器的前边（`article`和`aside`）形成（`#content article`和`#content aside`）。

嵌套的一般情况，会想后代选择器一样使用空格解析嵌套规则，因此伪类，伪元素就不能操作了

```scss
article a {
  color: blue;
  :hover { color: red }
}
//这意味着color: red这条规则将会被应用到选择器article a :hover，

article a {
  color: blue;
  &:hover { color: red }
}
```

**子组合选择器和同层组合选择器：>、+和~**

```scss
//你也可以用同层全体组合选择器~，选择所有跟在article后的同层article元素，不管它们之间隔了多少其他元素：
article ~ article { border-top: 1px dashed #ccc }
//这是同层级选择器

// -----------------------
article {
  ~ article { border-top: 1px dashed #ccc }
  > section { background: #eee }
  dl > {
    dt { color: #333 }
    dd { color: #555 }
  }
  nav + & { margin-top: 0 }
}

//解开
article ~ article { border-top: 1px dashed #ccc }
article > footer { background: #eee }
article dl > dt { color: #333 }
article dl > dd { color: #555 }
nav + article { margin-top: 0 }

```

### 3.导入SASS文件(@)

`css`有一个特别不常用的特性，即`@import`规则，@import`时，浏览器才会去下载其他`css`文件，这导致页面加载起来特别慢。

`sass`也有一个`@import`规则，但不同的是，`sass`的`@import`规则在生成`css`文件时就把相关文件导入进来。

* 嵌套导入

```scss
//有一个名为_blue-theme.scss的局部文件
aside {
  background: blue;
  color: white;
}
//它导入到一个CSS规则内
.blue-theme {@import "blue-theme"}

//生成的结果跟你直接在.blue-theme选择器内写_blue-theme.scss文件的内容完全一样。

.blue-theme {
  aside {
    background: blue;
    color: #fff;
  }
}
```

### 4.混合器@mixin

大段大段的重用样式的代码

**4.1使用@mixin 给重复的代码取个名字**

```scss
@mixin rounded-corners {
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
}
```

**4.2使用@include 调用这个混入**

```scss
notice {
  background-color: green;
  border: 2px solid #00aa00;
  @include rounded-corners;
}
//sass最终生成：

.notice {
  background-color: green;
  border: 2px solid #00aa00;
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
}
```

**4.3混合器中的CSS规则**

```scss
@mixin no-bullets {
  list-style: none;
  li {
    list-style-image: none;
    list-style-type: none;
    margin-left: 0px;
  }
}

ul.plain {
  color: #444;
  @include no-bullets;
}

ul.plain {
  color: #444;
  list-style: none;
}
ul.plain li {
  list-style-image: none;
  list-style-type: none;
  margin-left: 0px;
}
```

**4.4给混合器传参**

```scss
@mixin link-colors($normal, $hover, $visited) {
  color: $normal;
  &:hover { color: $hover; }
  &:visited { color: $visited; }
}

a {
  @include link-colors(blue, red, green);
}

//Sass最终生成的是：

a { color: blue; }
a:hover { color: red; }
a:visited { color: green; }

//默认参数值
@mixin link-colors(
    $normal,
    $hover: $normal,
    $visited: $normal
  )
{
  color: $normal;
  &:hover { color: $hover; }
  &:visited { color: $visited; }
}
// 如果像下边这样调用：@include link-colors(red) $hover和$visited也会被自动赋值为red。
```

### 继承

我们已经了解到混合器主要用于样式展示层的重用，如果你想重用语义化的类呢？这就涉及`sass`的另一个重要的重用特性：选择器继承。这个通过`@extend`语法实现

```scss
//通过选择器继承继承样式
.error {
  border: 1px solid red;
  background-color: #fdd;
}
.seriousError {
  @extend .error;
  border-width: 3px;
}
```

