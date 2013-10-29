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

###静态文件引用/脚本/样式代码 `<link>/<script>/<style>`

  - `link` - 用于引入 css 资源时，可省去`media`(默认为all) 和 `type`(默认为text/css) 属性
  - `style` - `type` 默认为 `text/css`，可以省去
  - `script` - `type` 属性可以省去，不赞成使用`lang`属性，不要使用古老的`<!– //–>`这种hack脚本，它用于阻止第一代浏览器（Netscape 1和Mosaic）将脚本显示成文字


###段落/标题 `<p>/<h1>/<h2>/<h3>/<h4>/<h5>/<h6>`

引用sofish的一段话：“我们可以用一本书的结构来说明这几个标签，而我们构建一个页面的时候，也应该有这样的一种思想在脑中”
  - 书的名称：H1
  - 书的每个章节标题: H2
  - 章节内的文章标题: H3
  - 章节的段落: P
  - 小标题/副标题: H4/H5/H6


###无序/有序列表 `<ul>/<ol>`

  - `ul` 表示无序列表
  - `ol` 表示有序列表, 可用于排行榜等
  - `li` 表示列表项，必须是`ul/ol`的子元素


###定义列表 `<dl>`
`<dl>` - 关联列表，`<dd>` 是对 `<dt>` 的解释

`<dt>` 和 `<dd>` 的对应关系比较随意：

 - 一个 `<dt>` 对应多个 `<dd>`
 - 多个 `<dt>` 对应一个 `<dd>`
 - 多个 `<dt>` 对应多个 `<dd>`

这些都是合法，可用于名词/单词解释、日程列表、站点目录

摘自w3school例子：
```html
<dl>
  <dt>Coffee</dt>
  <dd>Black hot drink</dd>
  <dt>Milk</dt>
  <dd>White cold drink</dd>
</dl>
```

###表单项 `<form>/<input>/<textarea>/<select>`

 - 添加 `<label>` 来描述该表单项的用途
 - 表单元素的 `name` 不能设定为 `action/enctype/method/novalidate/target/submit` 会导致表单提交混乱

###换行 `<br>`
使用 `<br />` 标签是来输入空行，而不是分隔段落或控制页面留白。

###短语元素 `<em>/<strong>/<code>`

他们都是短语元素

 - `<em>` 原单词为Emphasized text，呈现为被强调的文本
 - `<strong>` 定义重要的文本
 - `<code>` 原单词为Computer code text，定义重要的文本

###格式化片段 `<pre>`
原单词为Preformatted text，定义重要的文本

###图片 `<img>`
图片必须加上alt
```html
<img src="http://image15-c.poco.cn/mypoco/myphoto/20131021/17/521181332013102117065803_640.jpg" alt="卑鄙的我2">
```

###流媒体 `<object>/<embed>/<video>/<audio>`

 - `<video>` - 标签定义视频。
 - `<audio>` - 标签定义声音，比如音乐或其他音频流。
 
```html
<video width="320" height="240" controls="controls">
  <source src="movie.ogg" type="video/ogg">
  <source src="movie.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

<audio src="someaudio.wav">您的浏览器不支持 audio 标签。</audio>
```

###ICON `<i>`
i for Italic，原意是呈现斜体的文本，现在 `<i>` 基本上已经被抛弃，附上 `class` 属性后，就变作 icon 雪碧图的载体

###地球上出现最多的标签 `<div>/<span>`
用法是尽量使用其他来做为页面框架的容器，比如布局、添加额外的视觉效果，而不是段落等的替代品。

###分节元素 `<section>/<article>/<aside>/<nav>`


###老掉牙浏览器 vs HTML5
IE6、IE7、IE8浏览器不支持？用[html5shiv][2]，将它们注入到 DOM 中 `</head>` 前面
```html
<!--[if lt IE 9]>
    <script src="//cb.poco.cn/utility/html5shiv/3.7.0/html5shiv.js"></script>
<![endif]-->
```

延伸阅读：[HTML5语义][1]

[1]: http://www.infoq.com/cn/news/2011/09/understanding-html5-semantics
[2]: https://github.com/aFarkas/html5shiv