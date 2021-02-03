---
title: css 规范
---

---
date: 2021-02-03
---

## css 规范

* 使用scss+bem优先
* 选择器-基本选择器，组合选择器，伪类选择器，伪元素

```
并集选择器 .class1,.class2
交集选择器 .class1.active
后代选择器 .class1 .nav
子代选择器 .class1>.header
相邻选择器 .class1+.main 只对.class后的.main有效 .class相邻的.main
```

```
伪类 :hover  要记得一般a标签，button标签，给一些hover的效果
伪类选择器  前提是， 他必须有父元素，最高层是body  父元素下的第几个元素 父元素下面第一个不是他的话，顺序就会被打乱
<div><span></span><p></p><p></p></div>
first-child
last-child
nth-child(表达式n) 
nth-last-child(表达式n)
但下面的几种不受其他元素的影响
父元素下面寻找 第一个所匹配的子元素
first-of-type
last-of-type
nth-of-type(n)
nth-last-of-type(n)
```

```
伪元素(修饰内容)
::before
::after
记得加content
```

* 善用选择器减少类名的增加
* 善用伪类减少元素的添加，类名的增加

