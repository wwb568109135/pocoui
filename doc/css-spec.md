#CSS 规范

制定本规范的目的在于使我们的CSS代码更加易于维护和重用，从而提升效率

---

##申明及注释

1. 文件头部必须加上文件申明信息，必须包括文件描述、作者，例子：
    ```css
    /*
    * @todo: 表示该处功能还未实现, 无就不用写
    * @notes: 记录一些需要注意的信息，提醒开发者注意而已, 无就不用写
    * @description: 描述（可写中文）
    * @author: kidney(104958345@qq.com)
    */
    ```

2. 块状或行内元素，都请使用 `/* comment */` 注释，注释文字前后端保持各有**一个空格**
    单行注释例子：
    ```css
    /* logo */
    .global-header{
        width: 994px;
        margin-top: 20px;
    }
    ```
    
    多行注释例子：
    ```css
    /* 弹出框遮罩层
    xxxxxx
    yyyyyyyyy
    */
    .ui-dialog-mask{
        background-color: #000;
        opacity: .25;
        filter: alpha(opacity=25)
    }
    ```


##编码
1. 统一使用utf8编码, 必要时加上`@charset "UTF-8";`
2. 为了防止文件合并及编码转换时造成问题，建议将样式中文字体名字改成对应的英文名字，几个单词中间有空格组成的必须加引号，如：

    ```css
    .body{
        font: 12px/1.5 tahoma, arial, 'Microsoft Yahei', 'SimHei';
    }
    ```
3. 因为 Firefox 的某些版本和 Opera 不支持 SimSun 的写法，宋体改用unicode 表示，如：

    ```css
    body{
        font: 12px/1.5 tahoma, arial, \5b8b\4f53;
    }
    ```


##命名规范
1. 除布局、唯一独立模块外建议少用id，必须保证id唯一性。

2. 一律采用小写中划线方式命名，如 `xxx-yyy`，禁止出现大写字母。

3. 命名除 `.global-` `.fn-` `.ui-` `.J-` 外，可自定义命名。

4. 一般情况下，如果命名比较通用，比如 `hover` `current` `active` `selected` `first` `last` `error` `success`等，请限定在相应的上下文环境中。比如其父节点ID为#parent 等比较通用的命名，建议写成 `#parent .current{}`，而非 `.current{}`，即使是为了重用，也应该注意。只有在非常明确不会影响到其他组件工作，并且其他人不会写这种命名的情况下，才让它变成全局通用的.

5. 采用通俗易懂的英文单词并按内容/功能命名，严禁出现如xxx1、xxx2等的数字class/id

6. 常用命名（多记多查英文单词，多问谷歌翻译）：page、wrap、layout、header(head、hd)、footer(foot、ft)、content(cont)、body、menu、nav、main、submain、sidebar(side)、logo、banner、title(tit)、popo(pop)、icon、note、button(btn)、txt、iblock、window(win)、tips等

7. 对于复用性模块、独立模块可按xxx-mod命名（-mod可不写），mod下面再取xxx-head（头部）、xxx-body|content（内容）、xxx-footer（底部）命名. 而模块的状态，写成这样`.ui-name-hover` `.ui-name-error`

    例如：
    ```html
    <!-- 推荐 -->
    <div class="global-topbar">
        <div class="global-topbar-body">
            <ul class="global-topbar-nav">
                <li class="global-topbar-nav-item">1</li>
                <li class="global-topbar-nav-item">2</li>
            </ul>
        </div>
    </div>
    
    <!-- 不推荐 -->
    <div class="global-topbar">
        <div class="body">
            <ul class="main">
                <li class="item">1</li>
                <li class="item">2</li>
            </ul>
        </div>
    </div>
    
    <!-- 推荐 -->
    <div class="ui-box">
        <h3 class="ui-box-title"></h3>
        <p class="ui-box-conent"></p>
    </div>
    
    <!-- 不推荐 -->
    <div class="ui-box">
        <h3 class="title"></h3>
        <p class="conent"></p>
    </div>
    
    <!-- 推荐 -->
    <div class="ui-box ui-box-hover">
        <h3 class="ui-box-title"></h3>
        <p class="ui-box-conent"></p>
    </div>
    
    <!-- 不推荐 -->
    <div class="ui-box">
        <h3 class="ui-box-title ui-box-hover"></h3>
        <p class="ui-box-conent ui-box-hover"></p>
    </div>
    ```

8. 作为JS接口的class或者ID，必须是以 `J-` 前缀开头，如：`J-feed-list`、`J-page`.



##书写顺序

扩展阅读：[Mozilla suggested css order][1]
[1]: http://www.mozilla.org/css/base/content.css

一般分三行，按顺序：

1. 显示属性， 如：`display` `position` `float` `list-style` `clear`

2. 自身属性， 如：`border` `margin` `padding` `width` `height` `background`

3. 文本属性， 如：`color` `font` `vertical-align` `text-align` `text-decoration`

    例子:

    ```css
    .button {
        /* 显示属性 */
        position: relative;
        display: inline-block;
        
        /* 自身属性 */
        border: 1px solid #5cb325;
        margin: 10px 0;
        padding: 0 33px;
        width: 100px;
        height: 30px;
        line-height: 30px;
        background-color: #58ac23;

        /* 文本属性 */
        font-size: 22px;
        color: #fff;
    }
    ```


##样式预编译
SASS是在Ruby环境下运行（[Ruby+SASS安装教程][2]），SASS在CSS的基础上做了一些扩展，使用SASS你可以使用一些简单的编程思想进来编写CSS，SASS中可以定义变量、混合、嵌套以及函数等功能。

当SASS配搭上[Compass][3]，才显出SASS正真威力，Compass是一个非常成熟的SASS库，可是一个很强大的框架

安装了Ruby环境后，只需一句命令就可以安装compass

```
gem install compass
```

安装完成，运行下面命令，就会输出compass的版本

```
compass -v
```

[compass用法指南][4]

[2]: http://www.w3cplus.com/sassguide/install.html
[3]: http://compass-style.org/
[4]: http://www.ruanyifeng.com/blog/2012/11/compass.html
