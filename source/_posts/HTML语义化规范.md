---
title: HTML语义化规范
---
## HTML语义化规范

```html
<header>
	<nav></nav>
</header>
<main>
	<article>
  <section>
    <div><span></span></div>
    <p></p>
    <ul>
      <li><a></a></li>
    </ul>
    <img />
    <input />
    <button></button>
   </section>
  <aside></aside>
  </article>
</main>
<footer></footer>
```

优点

- 为了在没有CSS的情况下，页面也能呈现出很好地内容结构、代码结构
- 比<div>标签有更加丰富的含义，方便开发与维护
- 方便搜索引擎能识别页面结构，有利于SEO

注意

* 尽可能少的使用无语义的标签div和span
* 在语义不明显时，既可以使用div或者p时，尽量用p，因为p在默认情况下有上下间距，对兼容特殊终端有利
* 使用表格时，标题要用caption，表头用thead，主体部分用tbody包围，尾部用tfoot包围。表头和一般单元格要区分开，表头用th，单元格用td

* 每个input标签对应的说明文本都需要使用label标签，并且通过为input设置id属性

