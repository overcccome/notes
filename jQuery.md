<h2>一、jQuery选择器

和使用js操作Dom一样，获取文档中的节点对象是很频繁的一个操作，在jQuery中提供了简便的方式供我们查找|定位元素，称为jQuery选择器，选择器可以说是最考验一个人jQuery 功力的地方，通俗的讲,Selector 选择器就是"一个表示特殊语意的字符串”。只要把选择器字符串传入上面的方法中就能够选择不同的Dom 对象并且以jQuery包装集的形式返回。
jQuery 选择器按照功能主要分为"选择”和"过滤”。并且是配合使用的，具体分类如下。基础选择器掌握即可其他用到再查阅。

<h3>1. 基础选择器

| 选择器     | 名称            | 使用                       | 说明                             | 举例                                                  |
| ---------- | --------------- | -------------------------- | -------------------------------- | ----------------------------------------------------- |
| id选择器   | # id            | $("#id属性值")             | 如果有多个同名id，则一第一个为准 | $("#testDiv”) 选择id为testDiv的元素                   |
| 元素选择器 | element         | $("标签名/元素名")         | 选择所有指定标签的元素对象       | $("div”) 选择所有div元素                              |
| 类选择器   | .class          | $(".class属性值")          | 选择class为指定值的元素对象      | $(”.blue"”) 选择所有class=blue的元素                  |
| 组合选择器 | selector1,s2,sN | $("选择器1，选择器2，...") | 选择指定选择器选中的对象         | $("#testDiv,span,.blue”) 同时选中多个选择器匹配的元素 |
| 通用选择器 | *               | $("*")                     | 选择页面中所有的元素对象         | $("*")                                                |

<h3>2. 层次选择器

| 选择器     | 名称                | 使用                      | 说明（1 2 重要 3 4了解）                                     | 举例                                              |
| ---------- | ------------------- | ------------------------- | ------------------------------------------------------------ | ------------------------------------------------- |
| 后代选择器 | ancestor descendant | $("父元素+空格+指定元素") | 选择指定元素的所有后代元素，这个后代可以是第一代也可以是第二代等 | $(“#parent div”)选择id为parent的元素的所有div元素 |
| 子代选择器 | parent > child      | $("父元素>子元素")        | 选择父元素所有的第一代指定元素                               | $(“#parent>div”)选择id为parent的直接div子元素     |
| 相邻选择器 | prev + next         | $("元素+指定元素")        | 选择元素的下一个指定元素（同级），只会查找下一个元素，元素不存在则获取不到（只能找到和它挨着的） | $(“.blue +img”)选择css类为blue的下一个img元素     |
| 同辈选择器 | prev ~ sibling      | $("元素~指定元素")        | 选择的是当前元素下面的所有同级元素                           | $(”.blue~img”)选择css类为blue的之后的img元素      |

<h3>3. 表单选择器

| Froms          | 名称      | 举例                                                         |
| -------------- | --------- | ------------------------------------------------------------ |
| 表单选择器     | :input    | 查找所有的input元素: $(:input"); <br />注意:会匹配所有的input、textarea、select和button元素 |
| 文本框选择器   | :text     | 查找所有文本框: $(":text")                                   |
| 密码框选择器   | :password | 查找所有密码框: $(":password")                               |
| 单选按钮选择器 | :radio    | 查找所有单选按钮: $(“:radio")                                |
| 复选框选择器   | :checkbox | 查找所有复选框:$(":checkbox")                                |
| 提交按钮选择器 | :submit   | 查找所有提交按钮: $(:submit")                                |
| 图像按钮选择器 | :image    | 查找所有图像域:$:image")                                     |
| 重置按钮选择器 | :reset    | 查找所有重置按钮: $(":reset”)                                |
| 按钮选择器     | :button   | 查找所有按钮: $(":button")                                   |
| 文件域选择器   | :file     | 查找所有文件域: $(":file")                                   |

注：表单选择器会选择所有表单元素，元素选择器则只选中input标签，类似于button、textarea之类的非input标签不会选中。

<h2>二、jQuery DOM操作

jQuery也提供了对HTML节点的操作，而且在原生js的基础之上进行了优化，使用起来更加方便。常用的从几个方面来操作，查找元素 (选择器已经实现);创建节点对象；访问和设置节点对象的值，以及属性;添加节点；删除节点；删除、添加、修改、设定节点的CSS样式等。注意: 以下的操作方式只适用于jQuery对象。

<h3>1. 操作元素的属性		

属性的分类：

1. 固有属性：元素本身就有的属性（id、class......）
2. 返回值是布尔值的属性：checked、selected、disabled...
3. 自定义属性：用户自己定义的属性
4. 总结：<u>如果属性的类型是布尔型，使用prop（ ）方法，否则使用attr（ ）方法</u>

<h4>1.1 获取属性

| 方法           | 说明                                                         | 举例                             |
| -------------- | ------------------------------------------------------------ | -------------------------------- |
| attr(“属性名”) | 获取指定的属性值，操作 checkbox 时，<br/>选中返回 checked，没有选中返回 undefined。 | attr("checked")<br/>attr("name") |
| prop(”属性名“) | 获取具有true和false两个属性的属性值                          | prop("checked")                  |

区别：

1. 若果是固有属性，attr( )和prop( )均可获取。

2. 如果是自有属性，attr( )可获取，prop( )不可获取。

3. 如果是返回值为布尔类型的属性，若设置了属性，attr( )返回具体的值，prop( )返回true

   若没有设置过属性atte（ ）返回undefined，prop( )返回false。

<img src="https://longchaohuo.oss-cn-hangzhou.aliyuncs.com/yq_img_for_typora/202301072148575.png" alt="image-20230107214801365" style="zoom: 67%;" />

<h4>1.2 设置属性

| 方法                    | 举例                       |
| ----------------------- | -------------------------- |
| attr(”属性名“,"属性值") | $("#aa").attr("value","1") |
| prop(“属性名”,"属性值") | $("#aa").prop("value","2") |

1. 如果是固有属性，attr( )和prop( )方法均可操作。
2. 如果是自定义属性，attr( )可操作，prop( )不可操作。

![image-20230107215631861](https://longchaohuo.oss-cn-hangzhou.aliyuncs.com/yq_img_for_typora/202301072156953.png)

<h4>1.3 移除属性

| 方法                 | 举例                           |
| -------------------- | ------------------------------ |
| removeAttr(”属性名“) | $("#aa").removeAttr("checked") |

<h3>2. 操作元素的样式

对于元素的样式，也是一种属性，由于样式用得特别多，所以对于样式除了当做属性处理外还可以有专门的方法进行处理。

| 方法                  | 说明                                                         |
| --------------------- | ------------------------------------------------------------ |
| attr("class")         | 获取样式  $("#conBlue").attr("class","green");               |
| attr(“class”,样式名”) | 修改样式         $("#conBlue").attr("class","green");        |
| addClass(“样式名”)    | 添加样式(在原来的样式基础上添加样式，原本的样式会保留，如果出现相同样式，则以样式中后定义的为准)                  $("#conBlue").addClass("pink"); |
| css()                 | 添加具体的样式（添加行内样式）                               |
| removeClass(“class”)  | 移除样式                                                     |

css（ ）增加元素的具体样式，格式:

```
1) css({'样式名’:'样式值’，'样式名2’:'样式值2’})  //设置多个

例: css({"background-color":"red","color":"#fff"});

2)css(“样式名”,”样式值”)   //设置单个

例: css('color'，"white')
```

<img src="https://longchaohuo.oss-cn-hangzhou.aliyuncs.com/yq_img_for_typora/202301072227360.png" alt="image-20230107222730167" style="zoom:67%;" />

<h3>3. 操作元素的内容

对于元素还可以操作其中的内容，例如文本，值，甚至是html。

| 方法              | 说明                                               |
| ----------------- | -------------------------------------------------- |
| html()            | 获取元素的内容，包含html标签（非表单元素）         |
| html(”html,内容”) | 设置元素的内容，包含html标签（非表单元素）         |
| text()            | 获取元素的纯文本内容，不识别html标签（非表单元素） |
| text("text 内容") | 设置元素的纯文本内容，不识别html标签（非表单元素） |
| val()             | 获取元素的值（表单元素）                           |
| val(“值”)         | 设定元素的值（表单元素）                           |

1. html（）和text（）针对非表单元素，val（）针对表单元素

2. 表单元素：（页面中可以操作的就是表单元素）

   文本框text、密码框password、单选框radio、复选框checkbox、隐藏域hidden、文本域textarea、下拉框select

3. 非表单元素：

   div、span、h1-h6、table、tr、td、li、p......

<img src="https://longchaohuo.oss-cn-hangzhou.aliyuncs.com/yq_img_for_typora/202301072245386.png" alt="image-20230107224505254" style="zoom:67%;" />

<h3>4. 创建元素

在jQuery中创建元素很简单，直接使用核心函数即可（前面直接加一个$就行）

```html
$('元素内容');
```

```html
$('<p>this is a paragraph!!!</p>');
```

只有jQuery对象才能使用jquery方法，所以要使用必须把对象变成jquery对象。

<h3>5. 添加元素

| 方法                           | 用法                          | 说明                                                         | 级别                                                  |
| ------------------------------ | ----------------------------- | ------------------------------------------------------------ | ----------------------------------------------------- |
| prepend(content)               | 指定元素.prepend(内容)        | 在元素的开头里面追加内容，被追加的 content 参数，可以是字符、HTML 元素标记、也可以是jQuery对象。 | 父子级别，                               前追加子元素 |
| $(content).prependTo(selector) | $(内容).prependTo（指定元素） | 把内容追加到指定元素内部的最前面                             | 父子级别,     前追加子元素                            |
| append(content)                | 指定元素.append(内容)         | 在元素的最后面追加内容，被追加的 content 参数，可以是字符、HTML 元素标记等 | 父子级别,     后追加子元素                            |
| $(content).appendTo(selector)  | $(内容).appendTo（指定元素）  | 把内容追加到指定元素的结尾                                   | 父子级别,     后追加子元素                            |
| before()                       | $(selector).before(content)   | 在指定元素的前面追加内容                                     | 兄弟级别,   前追加同级元素                            |
| after()                        | $(selector).after(content)    | 在指定元素的后面追加内容                                     | 兄弟级别，后追加同级元素                              |

在添加元素时，如果元素本身不存在（新建的元素），此时会将元素追加到指定位置

如果元素本身存在（已有元素），会将原来元素直接剪切设置到指定位置。

<h3>6. 删除元素

| 方法        | 使用                 | 说明                                         |
| ----------- | -------------------- | -------------------------------------------- |
| remove（ ） | 指定元素.remove（ ） | 删除元素及其对应的子元素，标签和内容一起删除 |
| empty（ ）  | 指定元素.empty（ ）  | 清空所选元素的内容，会保留标签               |

<h3>7. 遍历元素

**each()**
$(selector).each(function(index,element)):遍历元素

参数function 为遍历时的回调函数

index为遍历元素的序列号，从0开始

element是当前的元素，此时是dom元素。（jQuery想要转成dom直接取下标就行，去遍历就相当于一直取指定的下标，所以出来是dom元素）

其中index和element参数不用的话可以省略不写

<img src="https://longchaohuo.oss-cn-hangzhou.aliyuncs.com/yq_img_for_typora/202301081515455.png" alt="image-20230108151531303" style="zoom:67%;" />

<h2>三、jQuery事件

<h3>1. ready加载事件

ready加载事件又称为预加载事件，当页面的dom结构加载完毕后执行（因为js按顺序执行，如果你的标签写在下面代码写在上面，就会获取不到），类似于js中的load事件

ready( )类似于onLoad（ ）事件

ready（）可以写多个，按顺序执行

```
语法：
$(document).ready( function( ){
} )；
等价于
$(function( ){ 
})；
```

<img src="https://longchaohuo.oss-cn-hangzhou.aliyuncs.com/yq_img_for_typora/202301081523979.png" alt="image-20230108152327832" style="zoom:67%;" />

<h3>2. bind（）绑定事件

为被选元素添加一个或多个事件处理程序，并规定事件发生时运行的函数。

<h4>2.1 简单的bind（）事件（绑定单个）

```
$("selector").bind( eventType [，eventData]， handler(eventobject));

$("元素").bind( 事件类型 [，传递的参数]， handler(触发执行函数));
```

```
常用写法：（直接绑定）
$("元素").事件类型(function(){  //事件类型比如click、mouseout等

});
```

* eventType: 是一个字符串类型的事件类型，就是你所需要绑定的事件。

  ​     	这类类型可以包括如下:

  ​					blur, focus, focusin, focusout, load, resize, scroll, unload, click, dblclickmousedown, mouseup, 					mousemove, mouseover, mouseout, mouseentermouseleave,change, select, submit, keydown, 					keypress, keyup, error

  [,leventData]: 传递的参数，格式:{名:值,名2:值2}

  handler(eventObject): 该事件触发执行的函数

* 1. 确定为哪些元素绑定事件               |  获取元素
  2. 绑定什么事件 （事件类型）          | 第一个参数：事件的类型
  3. 相应事件触发的，执行的操作       |第二个参数：函数

<h4>2.2 多个bind（）绑定事件

```
//1. 同时为多个事件绑定同一个函数
	指定元素.bind("事件类型1 事件类型2 ..",function(){
	
	});

//2. 为元素绑定多个事件，并设置对应的不同函数
	指定元素.bind("事件类型",function(){
	
	}).bind("事件类型",function(){
	
	});
	
//3. 为元素绑定多个事件，并设置对应的函数
	指定元素.bind({
	"事件类型":function(){ }；
	"事件类型":function(){ }；
	
//4. 直接绑定 ------------------ **最常用**
	指定元素.事件名(function(){
	
	}).事件名(function(){
	
	}；
```

<img src="https://longchaohuo.oss-cn-hangzhou.aliyuncs.com/yq_img_for_typora/202301081555793.png" alt="image-20230108155556660" style="zoom:67%;" />

<h2>四、jQuery Ajax异步无刷新技术

<h3>1.$.ajax

jquery调用ajax方法:

​		格式:$.ajax({ });

| 参数        | 说明                         |
| ----------- | ---------------------------- |
| type        | 请求方式GET/POST             |
| url         | 请求地址url                  |
| async       | 是否异步，默认是true表示异步 |
| data        | 发送到服务器的数据           |
| dataType    | 预期服务器返回的数据类型     |
| contentType | 设置请求头                   |
| success     | 请求成功时调用此函数         |
| error       | 请求失败时调用此函数         |

<img src="https://longchaohuo.oss-cn-hangzhou.aliyuncs.com/yq_img_for_typora/202301081621504.png" alt="image-20230108162151423" style="zoom:67%;" />



<h3>2.$.get

这是一个简单的GET 请求功能以取代复杂$.ajax。

请求成功时可调用回调函数。如果需要在出错时执行函数，请使用 $.ajax。

```
// 1.请求json文件，忽略返回值
$.get('js/cuisine_area.json');
```

```
// 2.请求json文件，传递参数，忽略返回值
$.get('js/cuisine_area.json',{name:"tom", age:100});
```

```
// 3.请求ison文件,拿到返回值,请求成功后可拿到返回值
$.get('js/cuisine_area.json',function(data){
	console.1og(data) ;
});
```

```
// 4.请求json文件,传递参数,拿到返回值
$.get('js/cuisine_area,json' ,name:"tom"age:100],function(data){
	console.1og(data) ;
});
```

```
语法：
$.get("请求地址","请求参数",function(形参){

})
```

<h3>3.$.post

```
语法：
$.post("请求地址","请求参数",function(形参){

})
```

<h3>4.$.getJSON

表示请求返回的数据类型是JSON格式的ajax请求

```
$.getJsON('js/cuisine_area.json',{name:"tom",age:100},function(data){
	console.1og(data); // 要求返回的数据格式是JSON格式
});
```

```
语法：
$.getJSON("请求地址","请求参数",function(形参){

})
注：getJSON方式要求返回的数据格式满足JSON格式（json字符串）
```

<img src="https://longchaohuo.oss-cn-hangzhou.aliyuncs.com/yq_img_for_typora/202301081640814.png" alt="image-20230108164040741" style="zoom:67%;" />