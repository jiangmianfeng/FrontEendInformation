# 1. HTML5

- HTML5 是 HTML 标准的下一个重要版本，用来替代 HTML 4.01，XHTML 1.0 以及 XHTML 1.1。
- 在 HTML5 平台上，视频、音频、图象、动画，以及同电脑的交互都被标准化
- 新增了很多元素和属性

## 1.1. input新增

| 类型   | 描述         | 说明                                         |
| ------ | ------------ | -------------------------------------------- |
| email  | 邮箱类型     | 判断当前字符串中是否包含`@`符号              |
| search | 搜索类型     |                                              |
| url    | 网址类型     | 判断当前字符串中是否包含`http://`            |
| number | 数字类型     |                                              |
| tel    | 电话号码类型 | 只在移动端浏览器有效                         |
| range  | 范围类型     | 适用于应该包含某个范围内数值的输入字段       |
| color  | 颜色类型     |                                              |
| date   | 日期类型     | 按照 `ISO 8601` 编码的日期（包括年，月，日） |
| month  | 月份类型     | 由 `ISO 8601` 编码的年和月组成的日期         |
| week   | 星期类型     | 由 `ISO 8601` 编码的年和星期数组成的日期     |

## 1.2. 属性新增

- placeholder  内容提示
- required   必填
- autofocus  获得焦点

## 1.3. 视频 

- video 标签

## 1.4. 声频

- audio 标签

# 2 .CSS3

## 2.1. 背景大小

- background-size: contain 长边|cover 短边 

## 2.2. 过渡 transition、转换transform、动画animation

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style type="text/css">


        div.header {
            font-size: 20px;
            font-weight: bold;
            color: aquamarine;
            background-color: gray;
            padding: 20px 0;
            width: 200px;
            height: 200px;
            text-align: center;
            line-height: 200px;
            /*过渡*/
            transition: all 2s ease-in-out;
            animation-name: circle_inner;

        }

        div.header:hover {
            font-size: 50px;
            background-color: chocolate;
            /*转换*/
            /*transform: rotate3d(1, 1, 1, 45deg);*/
            animation: circle_inner 5s;
        }

        @keyframes circle_inner {
            from {
                transform: rotateX(0deg);
            }
            to {
                transform: rotate3d(1, 1, 1, 45deg);
            }
        }
    </style>
</head>
<body>
<div class="parent">
    <div class="header">
        WAHO
    </div>
</div>
</body>
</html>
```

##  2.3. 边框阴影 box-shadow

| 值         | 描述                                     |
| ---------- | ---------------------------------------- |
| *h-shadow* | 必需。水平阴影的位置。允许负值。         |
| *v-shadow* | 必需。垂直阴影的位置。允许负值。         |
| *blur*     | 可选。模糊距离。                         |
| *spread*   | 可选。阴影的尺寸。                       |
| *color*    | 可选。阴影的颜色。请参阅 CSS 颜色值。    |
| inset      | 可选。将外部阴影 (outset) 改为内部阴影。 |



## 2.4. 边框圆角 border-radius

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style type="text/css">


        div.header {
            box-shadow: 5px 10px 10px 6px grey;
            font-size: 20px;
            font-weight: bold;
            color: aquamarine;
            background-color: gray;
            padding: 20px 0;
            width: 200px;
            height: 200px;
            text-align: center;
            line-height: 200px;
            /*过渡*/
            transition: all 2s ease-in-out;
            animation-name: circle_inner;

            border-radius: 5px;

        }

        div.header:hover {
            font-size: 50px;
            background-color: chocolate;
            /*转换*/
            /*transform: rotate3d(1, 1, 1, 45deg);*/
            animation: circle_inner 5s infinite;

        }

        @keyframes circle_inner {
            from {
                transform: rotateX(0deg);
            }
            to {
                transform: rotate3d(1, 1, 1, 45deg);
            }
        }
    </style>
</head>
<body>
<div class="parent">
    <div class="header">
        WAHO
    </div>
</div>
</body>
</html>
```



## 2.5. 多列

# 

| 属性                                                         | 描述                                     |
| ------------------------------------------------------------ | ---------------------------------------- |
| [column-count](http://www.runoob.com/cssref/css3-pr-column-count.html) | 指定元素应该被分割的列数。               |
| [column-fill](http://www.runoob.com/cssref/css3-pr-column-fill.html) | 指定如何填充列                           |
| [column-gap](http://www.runoob.com/cssref/css3-pr-column-gap.html) | 指定列与列之间的间隙                     |
| [column-rule](http://www.runoob.com/cssref/css3-pr-column-rule.html) | 所有 column-rule-* 属性的简写            |
| [column-rule-color](http://www.runoob.com/cssref/css3-pr-column-rule-color.html) | 指定两列间边框的颜色                     |
| [column-rule-style](http://www.runoob.com/cssref/css3-pr-column-rule-style.html) | 指定两列间边框的样式                     |
| [column-rule-width](http://www.runoob.com/cssref/css3-pr-column-rule-width.html) | 指定两列间边框的厚度                     |
| [column-span](http://www.runoob.com/cssref/css3-pr-column-span.html) | 指定元素要跨越多少列                     |
| [column-width](http://www.runoob.com/cssref/css3-pr-column-width.html) | 指定列的宽度                             |
| [columns](http://www.runoob.com/cssref/css3-pr-columns.html) | 设置 column-width 和 column-count 的简写 |

## 