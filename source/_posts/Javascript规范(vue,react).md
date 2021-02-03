---
title: Javascript规范
---
## Javascript规范(vue,react)

**优先使用es6语法**

* 变量命名
* 函数命名
* 事件命名
* 逻辑运算符号前后空格
* 记得写分号(eslint一般会规范)
* 常量大写
* 构造函数大驼峰
* 打印规则 console.log(“TODO：事件名称”）
* 全部引用单引号吧，需用’’’’

### 点击事件

on加动词小驼峰命名(onAdd,onEdit,onDelete,onSava)

获取值也可以以**label的属性值**为语义化，这样多个相同的点击类型，也知道是哪个label的。

```
add,remove,create,destroy,select,sava,edit,edit,change,reset,update,
```

### 函数

小驼峰命名，**返回值，目的为命名比较好**
数据请求用fetch+(驼峰式命名)
格式化方法用format+((驼峰式命名)

```
set/get
```

### 变量命名

没办法估计就只能翻译了

尽量以**基础类型组合**，不要担心命名过长

```
index,indez,indey,status,result,sum,
num,arr,obj,str,boolean,
```



## vue规范

* 组件大驼峰命名
* import和组件名一样就好(PascalCase)
* 项目文件小写，用中划线隔开吧
* 自动闭合组件，没有内容的组件应该是闭合的，但原生标签不要这样做

**Prop定义**

```javascript
props:{    
	name:{        
		type:String,Boolean,Array,Number   default:'',false,function(){return []}    
		} }              
```

**路由拆分为多个大模块引入**

router    prodcut.js    user.js    order.js    index.js //引入路由模块     

**Vue实例属性和方法的顺序**

1. name
2. components
3. filters
4. mixins
5. props
6. data
7. computed
8. watch
9. created
10. mounted
11. destroy
12. methods