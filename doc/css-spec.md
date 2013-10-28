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
1. 为了防止文件合并及编码转换时造成问题，建议将样式中文字体名字改成对应的英文名字，几个单词中间有空格组成的必须加引号)，如：

    ```css
    .cn-font{
        // 微软雅黑, 黑体, 宋体
        font-family: 'Microsoft Yahei', 'SimHei', 'SimSun';
    }
    ```


##命名规范
1. 除布局、唯一独立模块外建议少用id，必须保证id唯一性。

2. 一律采用小写中划线方式命名，如 `xxx-yyy`，禁止出现大写字母。

3. 命名除 `.global-` `.fn-` `.ui-` `.J-` 外，可自定义命名。

4. 一般情况下，如果命名比较通用，比如 `current` `active` `selected` `first` `last`，请限定在相应的上下文环境中。比如其父节点ID为#parent 等比较通用的命名，建议写成 `#parent .current{}`，而非 `.current{}`，即使是为了重用，也应该注意。只有在非常明确不会影响到其他组件工作，并且其他人不会写这种命名的情况下，才让它变成全局通用的。

5. 采用通俗易懂的英文单词并按内容/功能命名，严禁出现如xxx1、xxx2等的数字class/id。

6. 尽可能提高代码模块的复用，复用模块、独立模块可按xxx-mod命名（-mod可不写），mod下面再取xxx-hd|head（头部）、xxx-body|content（内容）、xxx-ft|footer（底部）命名.

    例如：
    ```html
    <!-- 推荐 -->
    <div class="global-topbar">
        <div class="global-topbar-body">
            <ul class="global-nav-main">
                <li class="global-nav-item">1</li>
                <li class="global-nav-item">2</li>
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
    ```

7. 常用命名（多记多查英文单词，多问谷歌翻译）：page、wrap、layout、header(head、hd)、footer(foot、ft)、content(cont)、body、menu、nav、main、submain、sidebar(side)、logo、banner、title(tit)、popo(pop)、icon、note、btn、txt、iblock、window(win)、tips等。

8. 作为JS接口的class或者ID，必须是以 `J-` 前缀开头，使用驼峰式命名：`J-feed-list`、`J-page`。除 JS 接口命名外，其他命名一律使用小写字母。



##书写顺序

一般分三行，按顺序：
1. 显示属性， 如：`display` `position` `float`
2. 自身属性， 如：`font` `border` `margin` `padding` `width` `height` `line-height`
3. 文本属性， 如：`color` `background` `vertical-align` `text-align` `text-decoration`

    ```css
    .button {
        /* 显示属性 */
        position: relative;
        display: inline-block;
        
        /* 自身属性 */
        font-size: 22px;
        border: 1px solid #5cb325;
        margin: 10px 0;
        padding: 0 33px;
        width: 100px;
        height: 30px;
        line-height: 30px;

        /* 文本属性 */
        color: #fff;
        background-color: #58ac23;
    }
    ```
