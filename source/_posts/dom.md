---
    title: DOM
---

## dom常用方法及说明

方法 | 说明
----- | -----
getElementById() | 通过ID属性获取元素
getElementByTagName | 通过标签名获取元素集合
getElementByClassName | 通过类名获取元素集合
getElementByName | 通过name属性获取元素集合
querySelector | 通过CSS选择器获取元素
querySelectorAll | 通过CSS选择器获取元素集合
appendChild() | 追加子元素到结尾
removeChild() | 移除子元素
replaceChild() | 替换子元素
insertBefore() | 在...之前插入
creatElement() | 创建元素
creatAttribute() | 创建属性
creatTextNode() | 创建文本节点
getAttribute() | 获取属性
setAttribute() | 设置属性


## dom常用属性

属性 | 说明
---- | ----
innerHTML | 读取/设置HTML内容
parentNode | 获取父节点
childNodes | 获取子节点集合
attributes | 获取属性节点集合 

## 文档中的节点类型

1. 文档申明
2. 元素
3. 文本
4. 属性
5. 注释
6. 文档

## 上下层节点

节点 | 描述
---- | ----
parentNode | 获得父级结点
childNodes | 获得子节点集合
firstChild | 获得第一个子节点
lastChild | 获得最后一个子节点
firstElementChild | 获得第一个子元素
lastElementChild | 获得最后一个子元素
children | 获得所有子元素节点的集合

## 平行节点

节点 | 描述
---- | ----
previousSibling | 获得上一个兄弟节点
nextSibling | 获得下一个兄弟节点
previousElementSibling | 获得上一个兄弟元素
nextElementSibling | 获得下一个兄弟元素

## 节点

* 节点名称：nodeName是String类型的属性，是只读的。
* 节点类型：nodeType是Number类型的属性
* 节点值：nodeValue是String类型的属性

节点 | 节点名称(nodeName) | 节点类型(nodeType) | 节点值(nodeValue)
---- | ---- | ---- | ----
元素节点 | 标签名(全大写) | 1 | undefined 或 null
属性节点 | 属性名 | 2 | 属性值
文本节点 | 始终是#text | 3 | 文本本身
注释节点 | 始终是#comment | 8 | 注释文本本身
文档节点 | 始终是#document | 9 | undefined 或 null
文档申明 | -- | 10 | --