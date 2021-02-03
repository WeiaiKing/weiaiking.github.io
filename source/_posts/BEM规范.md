---
title: BEM规范
---
## BEM规范

BEM的命名规矩很容易记：block-name__element-name--modifier-name，也就是模块名 + 元素名 + 修饰器名。

BEM--block，element，modifer  达到一个语义化的css命名方式

```html
<div class="page-btn"> 
  <button type="button" class="page-btn__prev">上一页</button> 
  <button type="button" class="page-btn__next">下一页</button> 
</div> 

```

上面我们用双下划线来明确区分模块名和元素名，当然也可以用单下划线，比如page-btn_prev和page-btn_next。我们只需保留BEM的思想，其命名规范可以任意变通。

* BEM 就三个元素 模块名-元素名_修饰器

### BEM命名好长

其实每个使用BEM的开发团队多多少少会改变其命名规范

```
比如Instagram团队使用的驼峰式:
.blockName-elementName--modifierName { /* ... */ } 
我也可以不使用驼峰,因为识别这模式有__,--,还有用单下划线_
```

> 还是使用原来的BEM规范吧就__--,嵌套多的话可以使用单下划线

### 修饰器

.要使用修饰符,  一个颜色，一个状态,响应式

### 一些命名常用单词-灵活自由组合命名

> header,nav,main,body,footer,wrap,container,box,item,text,left,right,up,down,input,button,img,detail,desc,time,price,data,search,label,sex,gender,girl,boy,name,content,address,phone,number,datetime,next,pre,login,confirm,register,reset,submit,commit,begin,end,start,finish

灵活去嵌套，是类名更加的语义化

```
.header__login
.div__header__next
.div__footer-button__text
```

### 规则

* 模块(card卡片模块)__元素(div)--修饰器(active)
* __ --  两个下划线，两个中划线，BEM就这么简单
* 更多具体https://en.bem.info/methodology/quick-start/#introduction

### 最后

在使用scss的时候呢？我们就可以不用写模块前缀啦！因为可以直接就使用scss嵌套了

只需定义好模块名字就不会产生冲突

