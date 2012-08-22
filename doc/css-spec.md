#CSS 规范

---

##申明及注释
1. 文件头部必须加上文件申明信息，必须包括文件描述、作者、最后更新(更新人+时间)
```css
/*
* @description: 描述（可写中文）
* @overview: 组件描述
* @author: kidney(104958345@qq.com)
*/
```

##编码
1. 为了防止文件合并及编码转换时造成问题，建议将样式中文字体名字改成对应的英文名字，如：黑体(SimHei) 宋体(SimSun) 微软雅黑 (Microsoft Yahei，几个单词中间有空格组成的必须加引号)


##命名规范
1. 除布局、唯一独立模块外建议少用id，必须保证id唯一性。
2. 一律采用小写中划线方式命名，如 xxx-yyy，禁止出现大写字母。
3. 命名除 .fn- / .ui- / .J- 外，可自定义命名。请慎用 active selected current disabled first last success error。
4. 一般情况下，如果命名比较通用，比如 current，请限定在相应的上下文环境中。比如其父节点ID为#parent 等比较通用的命名，建议写成 #parent .current{}，而非 .current{}，即使是为了重用，也应该注意。只有在非常明确不会影响到其他组件工作，并且其他人不会写这种命名的情况下，才让它变成全局通用的。
5. 采用通俗易懂的英文单词并按内容/功能命名，严禁出现如left、right等方向名词的class/id，严禁出现如xxx1、xxx2等的数字class/id。
6. 尽可能提高代码模块的复用，复用模块、独立模块可按xxx-mod命名（-mod可不写），mod下面再取xxx-hd（头部）、xxx-bd（内容）、xxx-ft（底部）命名.
7. 常用命名（多记多查英文单词，多问谷哥与度娘）：page、wrap、layout、header(head)、footer(foot、ft)、content(cont)、menu、nav、main、submain、sidebar(side)、logo、banner、title(tit)、popo(pop)、icon、note、btn、txt、iblock、window(win)、tips等。
8. 作为JS接口的class或者ID，必须是以 J_ 前缀开头，使用驼峰式命名：J-feedList、J-page。除 JS 接口命名外，其他命名一律使用小写字母。


##书写顺序