# CSS

# 1. CSS介绍

## 1.1. 什么是CSS

- CSS全称为 Cascading Style Sheets : 层叠样式表
- CSS是负责网页外观，它是将网页内容与外观分离一门语言。

## 1.2. 发展历史

- 1989随着HTML的诞生，样式就以各种各样的方式出现。最初的HTML只有很少的属性来展示样式。

- 随着HTML快速，需要越来越多的样式 

- 1994年，哈坤提出CSS，伯特正在开发一款浏览，使用哈坤提出CSS

- 1994年，哈坤出席各种会议，展示CSS建设。在芝加哥的会议上，W3C对CSS产生深厚的兴趣，加入在一起，

  1996诞生了第一个正式版本。

- 1998年css2.0
- 2001年css3.0~至今，仍然在完善中 

# 2.  如何使用，2个三，三种范围和三种选择器

## 2.1.  三种范围

- 行内： style属性实现
- 页面:   style标签实现
- 站点 :   css文件实现
  - 在页面上使用需要加载css文件
  - link 链接
  - @import 导入

## 2.2.  三种选择器

- html选择器

  html标签{

  	样式名:样式值;
	
  	样式名:样式值;

  }

  不需要手动调用 ，会自动匹配到对应的标签

- class选择器：一类样式 【推荐】

  .class选择器名{

  	样式名:样式值;
	
  	样式名:样式值;

  }

  需要手动调用 ，通class="class选择器名"的方式进行调用

- id选择器: 一个样式 

  #id选择器名{

  	样式名:样式值;
	
  	样式名:样式值;

  }

  需要手动调用 ，通id="id选择器名"的方式进行调用

## 2.3. 示例，css中注释为`/*内容*/`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>样式</title>
    <!--页面样式-->
    <style>
        /*html选择器*/
        p{
         background-color: bisque;
        }
        /*class选择器*/
        .myclass{
            font-family: "Wingdings 2";
            font-size: 36px;
        }

        /*id选择器*/
        #myid{
            font-family: 华文彩云;
            font-size: 45px;
        }

    </style>
</head>
<body>

<!--行内样式-->
<p style="color: lightgreen; font-size: 36px;font-weight: bold;">第一段的内容</p>
<p id="myid">第二段的内容</p>
<p class="myclass">第三段的内容ABCabc</p>



</body>
</html>
```

css/main.css

```css
/*html选择器*/
p{
    background-color: bisque;
}
/*class选择器*/
.myclass{
    font-family: "Wingdings 2";
    font-size: 36px;
}

/*id选择器*/
#myid{
    font-family: 华文彩云;
    font-size: 45px;
}
```

other.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>样式</title>
    <!--引入全局样式-->
    <!--link引入 【推荐】-->
    <!--<link rel="stylesheet" href="css/main.css">-->
    <!--@import引入-->
    <style>
        @import "css/main.css";
    </style>

</head>
<body>

<!--行内样式-->
<p style="color: lightgreen; font-size: 36px;font-weight: bold;">第一段的内容</p>
<p id="myid">第二段的内容</p>
<p class="myclass">第三段的内容ABCabc</p>

</body>
</html>
```

# 3. 复合选择器

## 3.1. 后代选择器：空格

## 3.2. 直接子代选择器 : >

## 3.3. 兄弟选择器: +

## 3.4. 交集选择器: 紧靠在一起

## 3.5. 并集选择器: ,

## 3.6. 通配符选择器: *

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>复合选择器</title>
    <style>
        /*后代 */
       div p{
            background-color: lightgreen;
        }
        /*直接子代 >*/
        span>p{
            font-size: 36px;
        }
        /*下一兄弟 + */
        #i3 + li{
            color: pink;
        }
        /*下所有兄弟 + */
        #i3 ~ li{
            color: green;
        }
        /*交集*/
        li#i3{
            color: aqua;
        }
        /*并集*/
        #i3,.i5{
            font-size: 24px;
        }
        /*通配*/
        *{
            background: beige;
        }
    </style>
</head>
<body>
    <h2>复合选择器</h2>
    <ul>
        <li>001</li>
        <li>002</li>
        <li id="i3">003</li>
        <li>004</li>
        <li class="i5">005</li>
        <ul>
            <li>1</li>
            <li>2</li>
            <li>3</li>
        </ul>
    </ul>
    <div>
        <span>
            <p>我是一个p</p>
        </span>
    </div>
</body>
</html>
```

# 4. CSS3选择器

## 4.1. 属性选择器 ： [属性名]

```css
[name] {color : red; }
```

| 选择符         | 版本 | 描述                                                         |
| -------------- | ---- | ------------------------------------------------------------ |
| E[att]         | CSS2 | 选择具有att属性的E元素。                                     |
| E[att="val"]   | CSS2 | 选择具有att属性且属性值等于val的E元素。                      |
| E[att~="val"]  | CSS2 | 选择具有att属性且属性值为一用空格分隔的字词列表，其中一个等于val的E元素。 |
| E[att^="val"]  | CSS3 | 选择具有att属性且属性值为以val开头的字符串的E元素。          |
| E[att$="val"]  | CSS3 | 选择具有att属性且属性值为以val结尾的字符串的E元素。          |
| E[att*="val"]  | CSS3 | 选择具有att属性且属性值为包含val的字符串的E元素。            |
| E[att\|="val"] | CSS2 | 选择具有att属性且属性值为以val开头并用连接符"-"分隔的字符串的E元素，且，如果属性值仅为val，也将被选择。 |

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>属性选择器</title>
    <style>
        /*属性名*/
        /*属性名  =属性值*/
        /*属性名 ^=属性值   开头*/
        /*属性名 $=属性值  结尾*/
        /*属性名 *=属性值  包含*/
        /*属性名 ~=属性值  独立单词*/
        /*属性名 |=属性值  开始单词->*/

        a[href]{
            /*color: red;*/
        }
        a[href="game.html"]{
            /*color: pink;*/
        }
        a[class^="download"]{
            /*color:skyblue;*/
        }
        a[class$="movie"]{
            /*color:lightgreen;*/
        }
        a[class*="download"]{
            /*color: gray;*/
        }

        a[class~="download"]{
            /*color: blueviolet;*/
        }
        a[class|="movie"]{
          color: chocolate;
        }
    </style>
</head>
<body>
<div id="d1">
    <a href="music.html" class="download download-music">下载音乐</a> <br>
    <a href="game.html" class="download download-game">下载游戏</a> <br>
    <a href="movie.html" class="movie-mars download download-movie">下载电影</a> <br>
    <a href="book.html" class="load download  download-book">下载书箱</a> <br>
</div>
</body>
</html>
```

## 4.2. 伪类选择器  :  冒号

| 选择符                  | 版本   | 描述                                                         |
| ----------------------- | ------ | ------------------------------------------------------------ |
| [E:link]                | CSS1   | 设置超链接a在未被访问前的样式。                              |
| [E:visited]             | CSS1   | 设置超链接a在其链接地址已被访问过时的样式。                  |
| [E:hover]               | CSS1/2 | 设置元素在其鼠标悬停时的样式。                               |
| [E:active]              | CSS1/2 | 设置元素在被用户激活（在鼠标点击与释放之间发生的事件）时的样式。 |
| [E:focus]               | CSS1/2 | 设置元素在成为输入焦点（该元素的onfocus事件发生）时的样式。  |
| [E:lang(fr)]            | CSS2   | 匹配使用特殊语言的E元素。                                    |
| [E:not(s)]              | CSS3   | 匹配不含有s选择符的元素E。                                   |
| [E:root]                | CSS3   | 匹配E元素在文档的根元素。                                    |
| [E:first-child]         | CSS2   | 匹配父元素的第一个子元素E。                                  |
| [E:last-child]          | CSS3   | 匹配父元素的最后一个子元素E。                                |
| [E:only-child]          | CSS3   | 匹配父元素仅有的一个子元素E。                                |
| [E:nth-child(n)]        | CSS3   | 匹配父元素的第n个子元素E。                                   |
| [E:nth-last-child(n)]   | CSS3   | 匹配父元素的倒数第n个子元素E。                               |
| [E:first-of-type]       | CSS3   | 匹配同类型中的第一个同级兄弟元素E。                          |
| [E:last-of-type]        | CSS3   | 匹配同类型中的最后一个同级兄弟元素E。                        |
| [E:only-of-type]        | CSS3   | 匹配同类型中的唯一的一个同级兄弟元素E。                      |
| [E:nth-of-type(n)]      | CSS3   | 匹配同类型中的第n个同级兄弟元素E。                           |
| [E:nth-last-of-type(n)] | CSS3   | 匹配同类型中的倒数第n个同级兄弟元素E。                       |
| [E:empty]               | CSS3   | 匹配没有任何子元素（包括text节点）的元素E。                  |
| [E:checked]             | CSS3   | 匹配用户界面上处于选中状态的元素E。(用于input type为radio与checkbox时) |
| [E:enabled]             | CSS3   | 匹配用户界面上处于可用状态的元素E。                          |
| [E:disabled]            | CSS3   | 匹配用户界面上处于禁用状态的元素E。                          |
| [E:target]              | CSS3   | 匹配相关URL指向的E元素。                                     |
| [@page:first])          | CSS2   | 设置页面容器第一页使用的样式。仅用于[@page](mk:@MSITStore:F:/%E5%89%8D%E7%AB%AF/CSS_V4.2.2.chm::/rules/@page.htm)规则 |
| [@page:left])           | CSS2   | 设置页面容器位于装订线左边的所有页面使用的样式。仅用于[@page](mk:@MSITStore:F:/%E5%89%8D%E7%AB%AF/CSS_V4.2.2.chm::/rules/@page.htm)规则 |
| [@page:right])          | CSS2   | 设置页面容器位于装订线右边的所有页面使用的样式。仅用于[@page](mk:@MSITStore:F:/%E5%89%8D%E7%AB%AF/CSS_V4.2.2.chm::/rules/@page.htm)规则 |

```html
<head>
    <title>css3伪类样式</title>
    <meta charset="utf-8">
    <style type="text/css">
    /* 父类下第一个子元素且标签名为li的元素 */

    li:first-child {
        color: red;
    }
    /* 父类下最后一个子元素且标签名为li的元素 */

    li:last-child {
        color: blue;
    }
    /* 第二个li的元素 */

    li:nth-of-type(2) {
        color: green;
    }
    /* 倒数第三个li的元素 */

    li:nth-last-of-type(3) {
        color: green;
    }
    /* 父类下第三个子元素且标签名为li的元素 */

    li:nth-child(3) {
        color: pink;
    }
    /* 父类下倒数第二个子元素且标签名为li的元素 */

    li:nth-last-child(2) {
        color: pink;
    }
    /* 找第一个li */

    li:first-of-type {
        font-size: 20px;
    }
    /* 找最后一个li */

    li:last-of-type {
        font-size: 20px;
    }
    /* 找父类下只有一个子元素且标签名为span的元素 */

    span:only-child {
        color: yellow;
    }
    </style>
</head>

<body>
    <ul>
        <li>好好学习，天天向上，迎娶白富美1。</li>
        <li>好好学习，天天向上，迎娶白富美2。</li>
        <li>好好学习，天天向上，迎娶白富美3。</li>
        <li>好好学习，天天向上，迎娶白富美4。</li>
        <li>好好学习，天天向上，迎娶白富美5。</li>
        <li>好好学习，天天向上，迎娶白富美6。</li>
        <li>好好学习，天天向上，迎娶白富美7。</li>
        <li>好好学习，天天向上，迎娶白富美8。</li>
    </ul>
    <div>
        <span>我是独子，我是中心...</span>
    </div>
</body>
```

```	html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>伪类选择器</title>
    <style>
        /*由爱 love 到恨 hate*/
        /*未访问*/
        a:link{
            color:red;
        }
        /*已经访问的*/
        a:visited{
            color:pink;
        }

        /*悬停*/
        a:hover{
            color:green;
        }
        /*正在访问*/
        a:active{
            color:blue;
        }

        /*第一儿子，而且是li*/
        li:first-child{
             color: red;
         }
        /*第一类型，而且是li*/
        li:first-of-type{
            color: blue;
        }

        /*最后一个儿子，而且是li*/
        li:last-child{
            color: green;
        }

        /*最后一个类型，而且是li*/
        li:last-of-type{
            color: skyblue;
        }

        /*第2个儿子，而且是li*/
        li:nth-child(2){
            font-size: 24px;
        }
        /*第3个类型，而且是li*/
        li:nth-of-type(3){
            font-size: 26px;
        }

        /*倒数第2个儿子，而且是li*/
        li:nth-last-child(2){
            color: aqua;
        }
        /*倒数第3个类型，而且是li*/
        ul li:nth-last-of-type(3){
            color: aquamarine;
        }
        /*只有一儿子，而且是span*/
        div>span:only-child{
            font-size: 55px;
        }



    </style>
</head>
<body>
<a href="#">未访问</a>
<a href="#">正在访问</a>
<a href="#">已经访问</a>
<a href="#">悬停</a>
<hr>
<ul>
    <!--<div>aaa</div>-->
    <li>好好学习，天天向上，迎娶白富美1</li>
    <li>好好学习，天天向上，迎娶白富美2</li>
    <li>好好学习，天天向上，迎娶白富美3</li>
    <li>好好学习，天天向上，迎娶白富美4</li>
    <li>好好学习，天天向上，迎娶白富美5</li>
    <li>好好学习，天天向上，迎娶白富美6</li>
    <li>好好学习，天天向上，迎娶白富美7</li>
    <li>好好学习，天天向上，迎娶白富美8</li>
</ul>
<div>
    <span>我是一个孤家寡人</span>
</div>
</body>
</html>
```

# 5. 样式的优先级

## 5.1. 范围的优先级:行内>页面>全局

## 5.2. 选择器的优先级:

### 5.2.1. 先看!important最强优先级

- 程序规定的最强优先级

```html
<style>
    img{width:100px !important}
    img{width:50px }
</style>
```

### 5.2.2. 优先级

-  !important 最强者

- 内联样式优先级为1000

- id选择器优先级为100

- class选择器优先级为10

- html标签选择器优先级为1

- 通配符选择器优先级为0

- 继承的样式没有优先级

- 口诀

  ```html
  先看是否选中，
  如果都不选中，看最近元素样式
  如果一个选中，一个不先中，直接看选中样式
  如果两个都选中，要比权重，权重大的优先级高，但如果权重一样，则写在后面的相同权重的样式会把前面的覆盖掉
  ```

### 5.2.3. 经典题

- 第一题

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>经典题1</title>
    <style type="text/css">
        #box1 .spec2 p{ /*100 10 1*/
            color: red;
        }

        div div #box3 p{ /*100 0 3*/
            color: green;
        }

        div.spec1 div.spec2 div.spec3 p{ /*0 30 4*/
            color: blue;
        }
    </style>
</head>
<body>
    <div id="box1" class="spec1">
        <div id="box2" class="spec2">
            <div id="box3" class="spec3">
                <p>这里是一个p</p>
            </div>
        </div>
    </div>
</body>
</html>
```

- 第二题

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>第二题</title>
    <style type="text/css">
        
        div p{
            color: red;
        }
        #box{
            color: blue;
        }

    </style>
</head>
<body>
<div id="box">
    <p id="para" class="spec">
        <span>文字</span>
    </p>
</div>
</body>
</html>
```

- 第三题

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>第三题</title>
    <style type="text/css">
        span{
            color: red;
        }
        .nav{
            color: blue;
        }
        .nav ul li{
            color: green;
        }
    </style>
</head>
<body>
<div class="nav">
    <ul>
        <li><span>001</span></li>
        <li><span>002</span></li>
        <li><span>003</span></li>
        <li><span>004</span></li>
    </ul>
</div>

</body>
</html>
```

- 第四题 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>第四题</title>
    <style type="text/css">

        /*200 0 1 */
        #box1 #box3 p{
            color: green;
        }

        /*100 10 2        200 0 1  */
        #box1 div.spec2 p,#box1 #box2 p{
            color: blue;
        }


    </style>
</head>
<body>
<div id="box1" class="spec1">
    <div id="box2" class="spec2">
        <div id="box3" class="spec3">
            <p>这里是一个p</p>
        </div>
    </div>
</div>
</body>
</html>
```

- 第五题 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>第五题</title>
    <style type="text/css">
        /*0 10 0*/
        .content{
            color: blue;
        }
        /*0 0 12*/
        div>div>div>div>div>div>div>div>div>div>div>p{
            color: skyblue;
        }
    </style>
</head>
<body>
<div>
    <div>
        <div>
            <div>
                <div>
                    <div>
                        <div>
                            <div>
                                <div>
                                    <div>
                                        <div>
                                            <p class="content">我是一个p</p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</body>
</html>
```

# 6. 样式是可以继承

-  子标签可以继承父部分标签的样式 
- 子标签的样式不会影响父标签的样式

- color，text-开头,line开头和font-开头的样式是可以继承

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>继承</title>
    <style type="text/css">
        div{
            border: 1px solid red;
            width: 200px;
            height: 200px;

            color: pink;
            text-indent:2em;
            font-family: 华文彩云;
            line-height: 30px;
        }
    </style>
</head>
<body>
    <div>
        <p>
            我是一个p我是一个p我是一个p
        </p>
    </div>
</body>
</html>
```

# 7. 块级标签和内联标签

- 块级标签：独占一行 。比如`<h1><p><ul><table><div>`
- 内联标签：同一行内显示，当一行放不下时，换行接着显示。比如:`<a><img><td><span>`
- 示例

```html
    <h2>块级标签</h2>
    <div>第一个div</div>
    <div>第二个div</div>

    <p>001</p>
    <p>002</p>

    <ul>
        <li>0</li>
    </ul>
    <ul>
        <li>0</li>
    </ul>

    <table border="1px" width="100px">
        <tr>
            <td>&nbsp;</td>
        </tr>
    </table>
    <table border="1px" width="100px">
        <tr>
            <td>&nbsp;</td>
        </tr>
    </table>

    <hr>
    <h2>内联样式</h2>
    <a href="#">001</a><a href="#">002</a>
    <span>003</span><span>003</span>
    <img src="img/1.jpg" width="50px" alt="">
    <img src="img/1.jpg" width="50px" alt="">
```

# 8. 字体样式 font-

- 字体样式  font-style
- 字体粗细  font-weight
- 字体大小  font-size
- 字体          font-family
- 复合样式   font：style weight size family

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>字体样式</title>
    <style type="text/css">
           .content{
/*
               font-style: italic;
               font-weight: bold;
               font-size: 24px;
               font-family: 微软雅黑;
*/
               /*简写*/
               font: italic 900 26px 微软雅黑;

           }
    </style>
</head>
<body>
    <div class="content">
        好好学习，天天向上
    </div>
</body>
</html>
```



# 9. 文本样式 text-

- 首先缩进 text-indent:xem
- 水平对齐 text-align: left|center|right
- 垂直对齐: vertical-align: top|middle|bottom 此样式只能用于内联标签，如果块级标签想实现垂直居中，设置行高等于容器高即可。
- 文本线条 text-decoration: underline|line_through|none

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>文本样式</title>
    <style type="text/css">
        p:first-of-type{
            text-indent: 2em;
            text-align: center;
            border: 1px solid red;
        }
        p:last-of-type{
            text-align: right;
            text-decoration: line-through;
            /*border:1px solid blue;*/
        }
        div{
            height: 300px;
            width: 300px;
            border:  1px solid gray;
            text-align: center;
            vertical-align: middle; /*它只适用于内联标签*/
            line-height: 300px; /*如果块级元素的内容要居中，设置行高等于高度*/
        }

    </style>
</head>
<body>
<p>这里是第1个p</p>
<p>这里是第2个p</p>
<div>
    这里是div的内容
</div>
</body>
</html>
```

# 10. 边框样式 border -

- 边框宽度 border-width
- 边框样式 border-style
- 边框颜色 border-color
- 复合样式 border:width style color
- 示例

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>边框样式</title>
    <style type="text/css">
        .content {
           /* border-width: 5px;
            border-style: double;
            border-color: red;*/

            /** 复合样式*/
            /*border:  1px dashed  red;*/

            border-top: 1px solid red;
            border-right:2px dashed green;
            border-bottom: 3px double blue;
            border-left: 4px dotted pink;
        }

    </style>
</head>
<body>
<div class="content">
    我是一个div
</div>
</body>
</html>
```

# 11. 链接样式

a:link{ }

a:visited{ }

a:hover{ }

a:active{ }

# 12 . 背景色、背景图片、列表样式

- 背景色   background-color:red

- 背景图片 background-image:url()

  - 背景图片：background-img:url('path')
  - 背景重复：background-repeat:repeat|no-repeat|repeat-x|repeat-y
  - 背景偏移：background-position:x轴 y轴，如果是正数,x往右,y往下
  - 复合样式：background: color img repeat position

  - 背景大小 : background-size:auto|cover|contain  ,cover：以短边为基础。contain:以长边为基础

- 图片精灵

  - 用一张大图覆盖常用小图，通过图片的偏移实现内容布局。给人感觉同一张图片能看到不同的图案，像个精灵
  - 优点
    - 减少了对服务器请求
    - 只命名一个图片名即可

- 示例

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>背景样式</title>
    <style type="text/css">
        .d1, .d2 {
            width: 300px;
            height: 300px;
            border: 1px solid gray;
        }

        .d1 {
            /*背景色*/
            background-color: lightgreen;
        }

        .d2 {
            /* background-image: url("img/erhuan.png") ;
             background-repeat: no-repeat;
             background-position: -20px -20px;*/
            background: aqua url("img/erhuan.png") no-repeat 10px 10px;
            /*background-size: cover;*/

        }
    </style>
</head>
<body>
<div class="d1">
    我是第一个盒子
</div>

<div class="d2">
    我是第二个盒子
</div>
</body>
</html>
```



- 图片精灵

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>图片精灵</title>
      <style>
          ul{
              list-style: none;
          }
          ul>li{
              height: 40px;
              line-height: 40px;
  
          }
          ul>li>i{
              padding: 21px;
          }
          ul>li:first-of-type>i{
              background: url("img/04.png") no-repeat 0px 11px;
          }
          ul>li:nth-of-type(2)>i{
               background: url("img/04.png") no-repeat -40px 11px;
           }
          ul>li:nth-of-type(3)>i{
              background: url("img/04.png") no-repeat -80px 11px;
          }
          ul>li:nth-of-type(4)>i{
              background: url("img/04.png") no-repeat -120px 11px;
          }
  
      </style>
  </head>
  <body>
  <ul>
      <li><i></i>0001</li>
      <li><i></i>0002</li>
      <li><i></i>0003</li>
      <li><i></i>0004</li>
  
  </ul>
  </body>
  </html>
  ```

# 13. 盒子模型

- 盒子模型，也可以看框模型

  ![](img/border.png)

- 组成部分
  - margin : 外边距
  - border：边框 
  - padding ： 内边距
  - width ： 宽度
  - height ： 高度

- 示例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>盒子模型</title>
      <style type="text/css">
          #outer{
              border: 1px solid black;
          }
  
          #inner{
              width: 300px;
              height: 50px;
              border: 5px solid blue;
  
              margin:20px; /*上下左右全是20*/
              margin:10px 20px 30px 40px;/*上右下左*/
              margin:10px 20px;
              margin:10px 20px 30px;
  
              padding: 10px;
              padding: 10px 20px;
              padding: 10px 20px 30px;
              padding: 10px 20px 30px 40px;
          }
      </style>
  </head>
  <body>
  
  <div id="outer">
      <div id="inner">这是最里边的div</div>
  </div>
  </body>
  </html>
  ```

# 14. 显示与隐藏

- css中有两个属性可以实现显示与隐藏
  - display : none|block|in-line
  - visibility : visible|hidden

- 两者隐藏的区别 
  - display ：none不显示，不占空间
  - visibility:hidden隐藏，占空间

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>显示与隐藏</title>
    <style type="text/css">
        span{
           /*display: none;*/
            visibility: hidden;
        }
    </style>
</head>
<body>

<table border="1" width="60%">
    <tr>
        <td>
            <span>这里第一行第一列</span>
        </td>
        <td></td>
    </tr>

</table>
</body>
</html>
```

# 15. overflow属性

- visible:默认，超过可见
- hidden：超过不可见
- scroll：始终显示滚动条
- auto：超过需要就显示滚动条，否则不显示

- 示例

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>overflow</title>
    <style type="text/css">
        div{
            width: 100px;
            height: 100px;
            border: 1px solid black;

            overflow: visible;
            overflow: hidden;
            overflow: scroll;
            overflow: auto;
        }
    </style>
</head>
<body>

    <div class="content">
        这里div的内容 <br>
        好好学习 <br>
        我爱学习 <br>
        学习使我快乐 <br>
        书中自有颜如玉 <br>
        这里div的内容 <br>
        好好学习 <br>
        我爱学习 <br>
        学习使我快乐 <br>
        书中自有颜如玉 <br>
    </div>
</body>
</html>
```

# 16. 浮动

- float: 设置浮动
  - left：脱标，不占空间
  - right：脱标，，不占空间
  - none：标准
- clear:清除浮动
  - 后面的元素与脱标的元素重叠，设置clear会让脱标的元素重新占位置

## 16.1. 标准文档流

- 将html窗体自上而下分成一行一行，并在每行中按从左至右的顺序排放元素，即为文档流。
- 块级元素
  - 宽度，独占一行
  - 高度，根据内容适应 
  - 设置宽度和高度，但宽度很小，也会独占一行
- 内联元素
  - 一行中从左至右，一行显示不下则换行显示
  - 不能设置高度和宽度
  - 但可以设置vertial-algin:top|middle|bottom

## 16.2.  overflow录用

- 在标准文件流的容器，设置overflow：hidden，
  - 如果标准文档流超过则不显示
  - 如果脱标文档浪超过则占空间再显示

## 16.3. 示例

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>浮动</title>
    <style>
        div{
            border: 1px solid black;
            overflow:hidden;
        }
        div#left,div#right{
            height: 300px;
            width: 49%;
        }
        div#left{
            float: left;
        }
        div#right{
            float: right;
        }

        div#bottom{
            /*clear: left;*/
        }
    </style>
</head>
<body>

<div id="container">
    <div id="top">top</div>
    <div id="left">left</div>
    <div id="right">right</div>
    <div id="bottom">bottom</div>
</div>
</body>
</html>
```

# 17. 定位 position

定位有四种

- static定位，默认
- absolute绝对定位。【脱标】相当于非static定位容器而言,如果没有则相对（页面）定位

- fixed 固定定位 。【脱标】
- relative相对定位。 【脱标】，相对于自己

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>定位</title>
    <style type="text/css">
        div{
            border: 1px solid gray;
            margin: 20px;
        }

        #d1{
            position: static;
        }

        #d2{
            position: absolute;
            bottom: 0;
            right: 0;
        }
        #d3{
            position: fixed;
            right: 0px;
        }

        #d4{
            position: relative;
            top: 20px;
            left: 10px;
        }
    </style>
</head>
<body style="height: 1000px;">
    <div class="container">
        <div id="d1">static定位</div>
        <div id="d2">absolute定位</div>
        <div id="d3">fixed定位</div>
        <div id="d4">relative定位</div>
    </div>
</body>
</html>
```

## 17.1. absolute其它不是相对于浏览器而言，而是相对父容器但非static定位而言。都没有才相对浏览器而言。

我们口诀：子绝父相

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>定位小练习</title>
    <style type="text/css">
        #container{
            border: 1px solid red;
            overflow: hidden;
        }
        #top{
            position: relative;
        }
        #left,#right{
            width: 45%;
            height: 300px;
            float: left;
        }
        #bottom{
            clear: left;
        }
        #right{
            border: 1px solid red;
            position: relative;
        }

        #right>#inner{
            border: 1px solid red;
            position: absolute; /*子绝父相*/
            right: 5px;
            bottom: 5px;
        }
    </style>
</head>
<body>

<div id="container">
    <div id="top">top</div>
    <div id="left">left</div>
    <div id="right">right
        <div id="inner">inner</div>
    </div>
    <!--<div id="bottom">bottom</div>-->
</div>
</body>
</html>
```



 





