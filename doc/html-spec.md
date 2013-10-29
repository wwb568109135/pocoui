#HTML 规范

##文档声明

为了更好地向后兼容，统一这样写：
```html
<!DOCTYPE html>
```

##编码
html文件统一使用`gb2312`编码，js和css文件如果是使用`utf8`编码，须在标签上加上`charset="utf-8"`

```html
<!DOCTYPE html>
<head>
<meta charset="gb2312">
<title></title>
<link charset="utf-8" rel="stylesheet" href="//www.poco.cn/css_common/v3/global/topbar.css">
<script charset="utf-8" href="//cb.poco.cn/seajs/2.1.1/sea.js"></script>
</head>

<body>
</body>
</html>
```

##兼容模式
以IE最高级模式渲染文档

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```


##注释
建议对超过30-50行的页面模块进行注释，以降低开发人员的嵌套成本和后期的维护成本。例如：

```html
<div id="sample">
...
  <div class="sample">
  ...
  </div> <!-- .sample END -->
...
</div> <!-- #sample END -->
```


##HTML Tag
用合理HTML标记以及其特有的属性去格式化文档内容


###页面标题 `<title>`

每个页面必须有且仅有一个 title 元素

```html
<title>It's me! 中国图片个人空间  mypoco -- POCO.CN</title>
```

###段落/标题 `<p>/<h1>/<h2>/<h3>/<h4>/<h5>/<h6>`

引用sofish的一段话：“我们可以用一本书的结构来说明这几个标签，而我们构建一个页面的时候，也应该有这样的一种思想在脑中”
  - 书的名称：H1
  - 书的每个章节标题: H2
  - 章节内的文章标题: H3
  - 章节的段落: P
  - 小标题/副标题: H4/H5/H6


###无序/有序列表 `<ul>/<ol>`

###定义列表 `<dl>`

###表单项 `<form>/<input>/<textarea>/<select>`

###换行 `<br>`

###图片 `<img>`
图片必须加上alt
```html
<img src="http://image15-c.poco.cn/mypoco/myphoto/20131021/17/521181332013102117065803_640.jpg" alt="卑鄙的我2">
```

###流媒体 `<object>/<embed>/<video>/<audio>`


延伸阅读：[HTML5语义][1]

[1]: http://www.infoq.com/cn/news/2011/09/understanding-html5-semantics
