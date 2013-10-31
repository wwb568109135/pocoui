#HTML 规范

##文档声明

为了更好地向后兼容，统一这样写：
```html
<!DOCTYPE html>
```

##编码
html文件统一使用 `gb2312` 编码，而js和css文件如果是使用 `utf8` 编码，须在标签上加上 `charset="utf-8"`
```html
<!DOCTYPE html>
<head>
<meta charset="gb2312">
<title></title>
<link charset="utf-8" rel="stylesheet" href="//www.poco.cn/css_common/v3/global/topbar.css">
<script charset="utf-8" src="//cb.poco.cn/seajs/2.1.1/sea.js"></script>
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

##基本规范
 - 元素的标签和属性名必须小写，属性值必须加双引号
 - 正确区分自闭合元素和非自闭合元素。非法闭合包括：`<br>..</br>` `<script />` `<iframe />`，非法闭合会导致页面嵌套错误问题
 - 通过给元素设置自定义属性来存放与 JavaScript 交互的数据，属性名格式为 `data-xx` （例如：`data-lazyload-url`）
 - 通过事件冒泡监听的行为，当行为有多个功能时，可以将触发元素赋予 `role` 属性（如：`<a href="javascript:;" role="remove" data-article-id="123">删除</a>` ）

##HTML Tag
用合理HTML标记以及其特有的属性去格式化文档内容


###页面标题 `<title>`

每个页面必须有且仅有一个 title 元素
```html
<title>It's me! 中国图片个人空间  mypoco -- POCO.CN</title>
```

###静态文件引用/脚本/样式代码 `<link>/<script>/<style>`

  - `link` - 用于引入 css 资源时，可省去 `media` （默认为all） 和 `type` （默认为text/css） 属性
  - `style` - `type` 默认为 `text/css`，可以省去
  - `script` - `type` 属性可以省去，不赞成使用`lang`属性，不要使用古老的 `<!– //–>` 这种hack脚本，它用于阻止第一代浏览器（Netscape 1和Mosaic）将脚本显示成文字


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
  - `li` 表示列表项，必须是 `ul/ol` 的子元素


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
  您的浏览器不支持 video 标签。
</video>

<audio src="someaudio.wav">您的浏览器不支持 audio 标签。</audio>
```

###ICON `<i>`
i for Italic，原意是呈现斜体的文本，现在 `<i>` 基本上已经被抛弃，附上 `class` 属性后，就变作 icon 雪碧图或 iconfont 的载体

###地球上出现最多的标签 `<div>/<span>`
从搜索引擎角度看，这2个标签没有任何语义，用法是尽量使用其他来做为页面框架的容器，比如布局、添加额外的视觉效果，而不是段落等的替代品。


###字符实体
HTML 中的预留字符 `小于号（<）和大于号（>）` 必须被替换为字符实体，[字符实体表][5]


###分节元素 `<section>/<article>/<aside>/<nav>`

####section
section是用来对页面上的内容分块处理，表示一段主题的分组，通常带有一个标题（h1-6），应用的典型场景有：文章的章节、标签对话框中的标签页、或者论文中有编号的部分；

***注意：*** section 不是代替 div ，section 不是一个作为容器的元素，当你需要一个元素来作容器的话，请用回`<div>`


W3C上有一句：
> Authors are encouraged to use the article element instead of the section element when it would make sense to syndicate the contents of the element.

当元素内容更加具体而充实的时候，鼓励开发者使用 article 来替换 section


一个简单的苹果分类例子：
```html
<article>
    <header>
        <h1>Apples</h1>
        <p>Tasty, delicious fruit!</p>
    </header>
    <p>The apple is the pomaceous fruit of the apple tree.</p>
  
    <section>
        <h1>Red Delicious</h1>
        <p>These bright red apples are the most common found in many supermarkets.</p>
    </section>
    <section>
        <h1>Granny Smith</h1>
        <p>These juicy, green apples make a great filling for apple pies.</p>
    </section>
</article>
```

扩展阅读：
 - [W3C section Spec][7]
 - [tml5doctor the section element][8]


####article

> The article element represents a complete, or self-contained, composition in a document, page, application, or site and that is, in principle, independently distributable or reusable, e.g. in syndication. This could be a forum post, a magazine or newspaper article, a blog entry, a user-submitted comment, an interactive widget or gadget, or any other independent item of content.

article 可以看作是一个特殊的 section 标签，它是一个独立、完整的内容块，适用的场景：论坛帖子、报刊文章、博文、用户评论、互动的工具和一些任意的独立内容。

例子：
```html
<article>
    <header>
        <h1>The Very First Rule of Life</h1>
        <p><time datetime="2009-10-09">3 days ago</time></p>
        <link href="?comments=0">
    </header>
    <p>If there's a microphone anywhere near you, assume it's hot and sending whatever you're saying to the world. Seriously.</p>
    <p>...</p>
    
    <section>
        <h1>Comments</h1>
        <article id="c1">
            <link href="#c1">
            <footer>
                <p>Posted by: <span><span>George Washington</span></span></p>
                <p><time datetime="2009-10-10">15 minutes ago</time></p>
            </footer>
            
            <p>Yeah! Especially when talking about your lobbyist friends!</p>
        </article>
        <article id="c2">
            <link href="#c2">
            <footer>
                <p>Posted by: <span><span>George Hammond</span></span></p>
                <p><time datetime="2009-10-10">5 minutes ago</time></p>
            </footer>
            <p>Hey, you have the same first name as me.</p>
        </article>
    </section>
</article>
```

#####Section or Article?
引用
> 不要把<article>放在印刷的范畴，比如报纸的文章，而是把它认为是一个独立的个体，像“文章的衣服”来描述，但是它也能包含其它的文章，使这件衣服包容的东西更多。
> — Bruce Lawson


其实重点就是一段内容脱离了整体，还能作为一个完整的、独立的内容而存在，这情况下适合使用 `<article>` ，反之如果内容上下文有关联，使用 `<section>`

他们间最主要的区别是：`<article>` 元素是为信息聚合设计的，而 `<section>` 元素是用来描述文档结构和可调用性。

在 HTML5 设计原理 中，有一条是专门用来解决类似情况的：

最终用户优先(Priority of Constituencies)

> “In case of conflict, consider users over authors over implementors over specifiers over theoretical purity.”

一旦遇到冲突，最终用户优先，其次是作者，其次是实现者，其次标准制定者，最后才是理论。


####aside
用于摆放与页面的主要内容没有相关联东西，例如大量导航和广告链接等

```html
<header>
    <h1>我的博客</h1>
</header>

<aside>
    <nav>
        <h1>友情链接</h1>
        <ul>
            <li><a href="http://www.example.com/">example1</a>
            <li><a href="http://www.example2.com/">example2</a>
        </ul>
    </nav>
</aside>

<article>
内容...
</article>
```


####nav
定义导航链接，链接到其它页面或页面中某个区域

注意一点：不是非所有导向性的链接都使用 nav 元素，例如：页脚的链接组（关于我、版权、联系我们之类），`<footer>` 元素已经足够，`<nav>` 主要目的是用于用户进行导航

适用范围：
 - 主要导航
 - 站內搜索
 - 二级导航
 - 页面内导航

没有必要使用：
 - 分页
 - 文章标签、分类
 - 三级导航
 - 页脚


每当输入 `nav` 三个字母时，问一下自己：“接下来输入的链接，是主要导航吗？”

```html
<nav>
    <ul>
        <li><a href="index.html">Home</a></li>
        <li><a href="/about/">About</a></li>
        <li><a href="/blog/">Blog</a></li>
    </ul>
</nav>
```


###头和尾 `<header>/<hgroup>/<footer>`

####header
通常包含一组介绍性或导航性质的辅助文字，经常用作 `<section>` 的头部，一个 header 通常都包含一个标题（H1-6），但这不是硬性规定，也可以包含一段内容、搜索表单或一个LOGO。

***注意：*** `<header>` 在页面中并非只有一个，不要理解为它只会出现页面的头部，一些页面的内容元素都可以出现 `<header>`

```html
<header>
    <p>Welcome to...</p>
    <h1>Voidwars!</h1>
</header>
```

```html
<article>
    <header>
        <h3>feed title</h3>
        <p><time datetime="2010-03-20">20th March, 2010</time></p>
    <header>
    <p>content....</p>
</article>
<article>
    <header>
        <h3>feed title</h3>
        <p><time datetime="2010-03-20">20th March, 2010</time></p>
    <header>
    <p>content....</p>
</article>
```


####hgroup
代表一组标题，当头部有多层结构时，比如有子头部，副标题，各种标识文字等，使用 hgroup 将 H1-H6 元素组合起来作为部分的头部

对于初接触同学来说，`<header>` 和 `<hgroup>` 应该怎么使用，看看以下例子：


```html
<!-- 假如内容中只有一个标题元素，就不需要使用 `<header>` 或 `<hgroup>` -->
<article>
    <h1>Title goes here</h1>
    <p>Lorem Ipsum dolor set amet</p>
</article>

<!-- 含有主标题、辅助信息、正文内容` -->
<article>
    <header>
        <h1>Title goes here</h1>
        <p><time datetime="2010-03-20">20th March, 2010</time></p>
    </header>
    <p>Lorem Ipsum dolor set amet</p>
</article>

<!-- 含有主标题、副标题、正文内容 -->
<article>
    <hgroup>
        <h1>Title goes here</h1>
        <h2>Subtitle of article</h2>
    </hgroup>
    <p>Lorem Ipsum dolor set amet</p>
</article>

<!-- 含有主标题、副标题、辅助信息、正文内容 -->
<article>
    <header>
        <hgroup>
            <h1>Title goes here</h1>
            <h2>Subtitle of article</h2>
        </hgroup>
        <p><time datetime="2010-03-20">20th March, 2010</time></p>
    </header>                
    <p>Lorem Ipsum dolor set amet</p>
</article>
```

总体来说：
 - 如果你只有一个标题元素，直接用（H1-6），不需要用上 `<hgroup>`
 - 如果你有多个标题，用上 `<hgroup>` 会很适合
 - 如果你带有多个标题，并还有其他辅助性元素时，先将标题放置入 `<hgroup>` 并连同辅助性元素放入 `<header>` 元素内


####footer
定义 section 或 document 的页脚，在通常情况下，该元素会包含创作者的姓名、文档的创作日期以及/或者联系信息。

与 `<header>` 相同，你可以在一个页面中拥有一个以上 `<footer>` ，也可以将 `<footer>` 作为全局页面上


```html
<footer>
    <ul>
        <li>copyright</li>
        <li>sitemap</li>
        <li>contact</li>
        <li>to top</li>
    </ul>
</footer>

<!-- 应用于 Section -->
<section>
    Section content appears here.
    <footer>
    Footer information for section.
    </footer>
</section>

<!-- 应用于 Article -->
<article>
    Article content appears here.
    <footer>
    Footer information for article.
    </footer>
</article>
```

##Why HTML5?

###HTML5设计原理
 1. 避免不必要的复杂性
 2. 支持已有的内容
 3. 解决现实的问题
 4. 求真务实
 5. 平稳退化
 6. 最终用户优先


###老掉牙浏览器 vs HTML5
IE6、IE7、IE8浏览器不支持？用[html5shiv][2]，将它们注入到 DOM 中 `</head>` 前面
```html
<!--[if lt IE 9]>
    <script src="//cb.poco.cn/utility/html5shiv/3.7.0/html5shiv.js"></script>
<![endif]-->
```

###注意事项
 - 不支持HTML5的浏览器必须使用html5shiv去开启
 - 为保持统一，必须将HTML5元素reset
 - 在不熟悉使用哪个HTML5语义的时候，先用HTML4标准去做，然后按照语义进行调整
 - 使用 Chrome 的 [html5outliner][6] 去检查成果



##延伸阅读：
 - [HTML5语义][1]
 - [HTML5设计原理][3]
 - [HTML示例][4]

[1]: http://www.infoq.com/cn/news/2011/09/understanding-html5-semantics
[2]: https://github.com/aFarkas/html5shiv
[3]: http://bogu.me/2012/03/09/3207.html
[4]: http://slides.html5rocks.com/#landing-slide
[5]: http://www.ascii-code.com/html-symbol.php
[6]: https://chrome.google.com/webstore/detail/html5-outliner/afoibpobokebhgfnknfndkgemglggomo
[7]: http://www.w3.org/TR/html5/sections.html#the-section-element
[8]: http://html5doctor.com/the-section-element/
