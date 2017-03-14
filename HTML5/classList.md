# 使用HTML5里的classList操作CSS类

在JavaScript和JavaScript工具库里征战多年，我经常有这样的遐想：什么时候现代浏览器里能提供一些辅助方法和类库，替代那些JavaScript工具库，比如jQuery，让我们用浏览器原生的方法替代它们。我知道浏览器必定会向这个方向改进，但这个进化过程不会很迅速，而且各种浏览器需要共同做这样的革新，火狐浏览器、谷歌浏览器、特别是IE，只有当这些主流浏览器都具备了这样的功能，我们的愿望才算真正的实现。好消息是，其中有一个这样的功能已经被加入到了HTML5 API里：`classList`。

在HTML5 API里，页面DOM里的每个节点上都有一个classList对象，程序员可以使用里面的方法新增、删除、修改节点上的CSS类。使用classList，程序员还可以用它来判断某个节点是否被赋予了某个CSS类。

## Element.classList

这个classList对象里有很多有用的方法：
```javascript
{
	length: {number}, /* # of class on this element */
	add: function() { [native code] },
	contains: function() { [native code] },
	item: function() { [native code] }, /* by index */
	remove: function() { [native code] },
	toggle: function() { [native code] }
}
```
正如你上面看到的，Element.classList类很小，但里面的每个方法都很有用。

### 新增CSS类

使用add方法，你可以往页面元素是新增一个或多个css类：
```javascript
myDiv.classList.add('myCssClass');
```
### 删除一个CSS类

使用remove方法，你可以删除单个CSS类：
```javascript
myDiv.classList.remove('myCssClass');
```
你可以在这个方法里一次传入多个类名，用空格分开，但执行的结果很有可能不是你预期的。

### 反转CSS类的有无
```javascript
myDiv.classList.toggle('myCssClass'); //现在是增加
myDiv.classList.toggle('myCssClass'); //现在是删除
```
这个方法的作用就是，当myDiv元素上没有这个CSS类时，它就新增这个CSS类；如果myDiv元素已经有了这个CSS类，它就是删除它。就是反转操作。

### 检查是否含有某个CSS类
```javascript
myDiv.classList.contains('myCssClass'); //returns true or false
```
目前所有的现代浏览器(火狐浏览器，谷歌浏览器等)都支持这个classList类，所以，相信新型的javaScript类库里都会使用classList类来操作页面CSS类，而不需像以前一样去分析元素节点的class属性！
