    css 的五种基本选择器
    1、元素选择器  h1
    2、类选择器  . class
    3、ID选择器  #myID
    4、属性选择器 只要是属性，
    5、通配符选择器  * 匹配所有元素
    常用属性：
    前景色：  color
    背景色：  background-color
    width  设置宽度
    height 设置高度
    font-family
    font-size
    font-weight :100-900值越大越粗
    text-shadow   color  -1px 水平偏移量 负左,正右 -3px 垂直偏移量  负上，正下

HTML标签
有序标签  ol
<ol>
<li></li>
<li></li>
</ol>

无序标签 ul
<ul>
<li></li>
<li></li>
</ul>
列表样式属性
list-style-type: circle;
list-style-type: none;  去除标签序号

list-style:circle  同上效果

CSS的盒子模型

外边距  margin
边框  border
内边距 padding
内容区

css border: 1px  宽度  dashed 样式（solid）   red  颜色
border 实线边框（solid）、虚线边框（dashed）、点线边框（dotted）、双线边框（double）

line-height  在没有设置div的height属性时，div的高度根据line-height的大小而变化
height = line-height 字居中
height>line-height时 字偏上
height<line-height时 字偏下
超链接：
<a href=''></a>
text-align:center 居中 要设置在包含元素的外层标签，而非元素本身

元素分类
块级元素  独占一行  <h1></h1>
内联元素，行内元素，多个内联元素处在一行中。<a> 不允许使用width and height
行内块级元素  <button>


css display属性
block  设置成块级元素
inline  设置成内联元素
inline-block 设置成行内块级元素

背景图片：
background-image
background-image:url('***')
background-repeat： no-repeat;repeat-x;repeat-y;repeat 默认
background-position: center ; 
background-size: 180px;


CSS 定位
position
:static静态定位
:fixed 固定定位
:relative 相对定位 left:200px  
:absolute 绝对定位

css选择器
伪类选择器：  div:hover
层级选择器：  #myID > #childID 父级标签  子级标签