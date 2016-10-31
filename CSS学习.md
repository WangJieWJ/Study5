# CSS学习

## 1、CSS语法
CSS规则由两个主要的部分构成：选择器，以及一条或多条声明。
```html
selector{declaration1;declaration2;……;declarationN}
```
选择器通常是您需要改变样式的HTML元素。
每条声明由一个属性和一个值组成。
属性(property)是您希望设置的样式的属性(style attribute).每个属性有一个值。属性和值被冒号分开。
```html
selector{property:value}
```	
下面这行代码的作用是将 h1 元素内的文字颜色定义为红色，同时将字体大小设置为 14 像素。
	在这个例子中，h1 是选择器，color 和 font-size 是属性，red 和 14px 是值。
```html
h1 {color:red; font-size:14px;}
```
## 选择器的分组
	你可以对选择器进行分组，这样，被分组的选择器就可以分享相同的声明。用逗号将需要分组的选择器分开。在下面的例子中，我们对所有的标题元素进行了分组。所有的标题元素都是绿色的。
```css
h1,h2,h3,h4,h5,h6 {
		color: green;
	}
```	
## 继承及其问题
根据CSS，子元素从父元素继承属性。但是他并不是按此方式工作。
```css
body{
		font-family:Verdana,sans-serif;
	}
```
	
## 派生选择器
通过依据元素在其位置的上下文关系来定义样式，你可以使标记更加简洁。
你希望列表中的 strong 元素变为斜体字，而不是通常的粗体字，可以这样定义一个派生选择器：
```css
li strong {
			font-style: italic;
			font-weight: normal;
		}
```		
## id选择器
id 选择器可以为标有特定 id 的 HTML 元素指定特定的样式。
id 选择器以 "#" 来定义。
下面的两个 id 选择器，第一个可以定义元素的颜色为红色，第二个定义元素的颜色为绿色：
```css
#red {color:red;}
#green {color:green;}
```
下面的 HTML 代码中，id 属性为 red 的 p 元素显示为红色，而 id 属性为 green 的 p 元素显示为绿色。
```html
<p id="red">这个段落是红色。</p>
<p id="green">这个段落是绿色。</p>
```

## id 选择器和派生选择器
在现代布局中，id 选择器常常用于建立派生选择器。
```css
#sidebar p {
	font-style: italic;
	text-align: right;
	margin-top: 0.5em;
	}
```
上面的样式只会应用于出现在 id 是 sidebar 的元素内的段落。这个元素很可能是 div 或者是表格单元，尽管它也可能是一个表格或者其他块级元素。它甚至可以是一个内联元素，比如 <em></em> 或者 <span></span>，不过这样的用法是非法的，因为不可以在内联元素 <span> 中嵌入 <p> 
## 一个选择器，多种用法
即使被标注为 sidebar 的元素只能在文档中出现一次，这个 id 选择器作为派生选择器也可以被使用很多次：
```css
#sidebar p {
	font-style: italic;
	text-align: right;
	margin-top: 0.5em;
	}
#sidebar h2 {
	font-size: 1em;
	font-weight: normal;
	font-style: italic;
	margin: 0;
	line-height: 1.5;
	text-align: right;
	}
```
在这里，与页面中的其他 p 元素明显不同的是，sidebar 内的 p 元素得到了特殊的处理，同时，与页面中其他所有 h2 元素明显不同的是，sidebar 中的 h2 元素也得到了不同的特殊处理。
	
## CSS类选择器
在CSS中，类选择器以一个点号显示：
```css
.center {text-align: center}
```
在上面的例子中，所有拥有 center 类的 HTML 元素均为居中。
在下面的 HTML 代码中，h1 和 p 元素都有 center 类。这意味着两者都将遵守 ".center" 选择器中的规则。
```css
<h1 class="center">
	This heading will be center-aligned
</h1>
<p class="center">
	This paragraph will also be center-aligned.
</p>
```
和 id 一样，class 也可被用作派生选择器：	
```css
.fancy td {
	color: #f60;
	background: #666;
	}
```
类名为 fancy 的更大的元素内部的表格单元都会以灰色背景显示橙色文字。（名为 fancy 的更大的元素可能是一个表格或者一个 div	
		
## 元素也可以基于它们的类而被选择：	
```css
td.fancy {
	color: #f60;
	background: #666;
	}
```
在上面的例子中，类名为 fancy 的表格单元将是带有灰色背景的橙色。
```html
<td class="fancy">
```
对带有指定属性的HTML元素设置样式
可以为拥有指定属性的 HTML 元素设置样式，而不仅限于 class 和 id 属性。

## 属性选择器
下面的例子为带有 title 属性的所有元素设置样式：
```css
[title]
{
	color:red;
}
```	
## 属性和值选择器
下面的例子为 title="W3School" 的所有元素设置样式：
```css
[title=W3School]
{
	border:5px solid blue;
}
```		

## 设置表单的样式
属性选择器在为不带有Class或id的表单设置样式时特别有用：
```css
input[type="text"]
{
  width:150px;
  display:block;
  margin-bottom:10px;
  background-color:yellow;
  font-family: Verdana, Arial;
}

input[type="button"]
{
  width:120px;
  margin-left:35px;
  display:block;
  font-family: Verdana, Arial;
}
```
## CSS创建
1、引入外部样式
当样式需要应用于很多页面时，外部样式表将是理想的选择。在使用外部样式表的情况下，你可以通过改变一个文件来改变整个站点的外观。每个页面使用 <link> 标签链接到样式表。<link> 标签在（文档的）头部：
```css
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css" />
</head>
```
浏览器会从文件 mystyle.css 中读到样式声明，并根据它来格式文档。
外部样式表可以在任何文本编辑器中进行编辑。文件不能包含任何的 html 标签。样式表应该以 .css 扩展名进行保存。下面是一个样式表文件的例子：
```css
hr {color: sienna;}
p {margin-left: 20px;}
body {background-image: url("images/back40.gif");}
```

2、内部样式表
当单个文档需要特殊的样式时，就应该使用内部样式表。你可以使用 <style> 标签在文档头部定义内部样式表，就像这样:
```css
  hr {color: sienna;}
  p {margin-left: 20px;}
  body {background-image: url("images/back40.gif");}
```

3、内联样式
由于要将表现和内容混杂在一起，内联样式会损失掉样式表的许多优势。
要使用内联样式，你需要在相关的标签内使用样式（style）属性。Style 属性可以包含任何 CSS 属性。本例展示如何改变段落的颜色和左外边距
```css
<p style="color: sienna; margin-left: 20px">
This is a paragraph
</p>
```

## 多重样式
如果某些属性在不同的样式表中被同样的选择器定义，那么属性值将从更具体的样式表中被继承过来。
例如，外部样式表拥有针对 h3 选择器的三个属性：
```css
h3 {
  color: red;
  text-align: left;
  font-size: 8pt;
  }
```
而内部样式表拥有针对 h3 选择器的两个属性：
```css
h3 {
  text-align: right; 
  font-size: 20pt;
  }
```
假如拥有内部样式表的这个页面同时与外部样式表链接，那么 h3 得到的样式是：
```css
color: red; 
text-align: right; 
font-size: 20pt;
```
即颜色属性将被继承于外部样式表，而文字排列（text-alignment）和字体尺寸（font-size）会被内部样式表中的规则取代。

## CSS背景
1、背景色
可以使用 background-color 属性为元素设置背景色。这个属性接受任何合法的颜色值。
这条规则把元素的背景设置为灰色：
```css
p {background-color: gray;}
```
如果您希望背景色从元素中的文本向外少有延伸，只需增加一些内边距：
```css
p {background-color: gray; padding: 20px;}
```
可以为所有元素设置背景色，这包括 body 一直到 em 和 a 等行内元素。
background-color 不能继承，其默认值是 transparent。transparent 有“透明”之意。也就是说，如果一个元素没有指定背景色，那么背景就是透明的，这样其祖先元素的背景才能可见。

2、背景图像
要把图像放入背景，需要使用 background-image 属性。background-image 属性的默认值是 none，表示背景上没有放置任何图像。
如果需要设置一个背景图像，必须为这个属性设置一个 URL 值：
```css
body {background-image: url(/i/eg_bg_04.gif);}
```
大多数背景都应用到body元素，不过并不仅限于此。
下面例子为一个段落应用了一个背景，而不会对文档的其他部分应用背景：
```css
p {background-image: url(/i/eg_bg_03.gif);}
```
您甚至可以为行内元素设置背景图像，下面的例子为一个链接设置了背景图像：
```css
a{background-image: url(/i/eg_bg_07.gif);}
```
另外还要补充一点，background-image 也不能继承。事实上，所有背景属性都不能继承。

3、背景重复
如果需要在页面上对背景图像进行平铺，可以使用background-repeat属性。
属性值 repeat导致图像在水平垂直方向上都平铺，就像以往背景图像的通常做法一样。repeat-x 和 repeat-y分别导致图像只在水平或垂直方向上重复，no-repeat则不允许图像在任何方向上平铺。
默认地，背景图像将从一个元素的左上角开始。请看下面的例子：
```css
body
  { 
  background-image: url(/i/eg_bg_03.gif);
  /*默认是在水平垂直方向上都平铺，如下语句要求只     在垂直方向上平铺*/
  background-repeat: repeat-y;
  }
```

4、背景定位
可以利用 background-position属性改变图像在背景中的位置。
下面的例子在body元素中将一个背景图像居中放置：
```css
body
  { 
    background-image:url('/i/eg_bg_03.gif');
    background-repeat:no-repeat;
    background-position:center;
  }
```
为 background-position属性提供值有很多方法。首先，可以使用一些关键字：top、bottom、left、right 和 center。通常，这些关键字会成对出现，不过也不总是这样。还可以使用长度值，如 100px 或 5cm，最后也可以使用百分数值。不同类型的值对于背景图像的放置稍有差异。

关键字

图像放置关键字最容易理解，其作用如其名称所表明的。例如，top right使图像放置在元素内边距区的右上角。根据规范，位置关键字可以按任何顺序出现，只要保证不超过两个关键字 -一个对应水平方向，
另一个对应垂直方向。如果只出现一个关键字，则认为另一个关键字是 center。
所以，如果希望每个段落的中部上方出现一个图像，只需声明如下：
```css
p{ 
    background-image:url('bgimg.gif');
    background-repeat:no-repeat;
    background-position:top;
}
```
下面是等价的位置关键字：
单一关键字 | 等价的关键字
---- | ---
center | center center
top |  top center 或 center top
bottom | bottom center 或 center bottom
right | right center 或 center right
left  | left center 或 center left

百分数值

百分数值的表现方式更为复杂。假设你希望用百分数值将图像在其元素中居中，这很容易：
```css
body
  { 
    background-image:url('/i/eg_bg_03.gif');
    background-repeat:no-repeat;
    background-position:50% 50%;
  }
```
这会导致图像适当放置，其中心与其元素的中心对齐。换句话说，百分数值同时应用于元素和图像。也就是说，图像中描述为 50% 50% 的点（中心点）与元素中描述为 50% 50% 的点（中心点）对齐。
如果图像位于 0% 0%，其左上角将放在元素内边距区的左上角。如果图像位置是 100% 100%，会使图像的右下角放在右边距的右下角。

因此，如果你想把一个图像放在水平方向2/3、垂直方向1/3处，可以这样声明：
```css
body
  { 
    background-image:url('/i/eg_bg_03.gif');
    background-repeat:no-repeat;
    background-position:66% 33%;
  }
```
如果只提供一个百分数值，所提供的这个值将用作水平值，垂直值将假设为 50%。这一点与关键字类似。
background-position 的默认值是 0% 0%，在功能上相当于 top left。这就解释了背景图像为什么总是从元素内边距区的左上角开始平铺，除非您设置了不同的位置值。

长度值

长度值解释的是元素内边距区左上角的偏移。偏移点是图像的左上角。
比如，如果设置值为50px 100px，图像的左上角将元素内边距区左上角向右50像素、向下100像素的位置上。
```css
body
  { 
    background-image:url('/i/eg_bg_03.gif');
    background-repeat:no-repeat;
    background-position:50px 100px;
  }
```
注意，这一点与百分数值不同，因为偏移只是从一个左上角到另一个左上角。也就是说，图像的左上角与 background-position 声明中的指定的点对齐。

背景关联

如果文档比较长，那么当文档向下滚动时，背景图像也会随之滚动。当文档滚动到超过图像的位置时，图像也就消失了。
可以通过 background-attachment 属性防止这种滚动。通过这个属性，可以声明图像相对于可视区是固定的（fixed），因此不会受到滚动的影响：
```css
body 
  {
  background-image:url(/i/eg_bg_02.gif);
  background-repeat:no-repeat;
  background-attachment:fixed
  }
```

background-attachment属性的默认值是scroll，也就是说，在默认的情况下，背景会随文档滚动。

CSS背景属性
属性 | 描述
-----|-------
background|简写属性，作用是将背景属性设置在一个声明中
background-attachment|背景图像是否固定或者随着页面的其余部分滚动
background-color|设置元素的背景颜色
background-image|把图像设置为背景
background-position|设置背景图像的起始位置
background-repeat|设置背景图像是否及如何重复

## CSS文本

CSS文本属性可定义文本的外观
通过文本属性，您可以改变文本的颜色、字符间距、对齐文本、装饰文本、对文本进行缩进，等等。

1、缩进文本

把 Web 页面上的段落的第一行缩进，这是一种最常用的文本格式化效果。
CSS 提供了 text-indent 属性，该属性可以方便地实现文本缩进。
通过使用 text-indent 属性，所有元素的第一行都可以缩进一个给定的长度，甚至该长度可以是负值。
这个属性最常见的用途是将段落的首行缩进，下面的规则会使所有段落的首行缩进 5 em：
```css
p{
    text-indent:5em;
}
```
注意：一般来说，可以为所有块级元素应用 text-indent，但无法将该属性应用于行内元素，图像之类的替换元素上也无法应用 text-indent 属性。不过，如果一个块级元素（比如段落）的首行中有一个图像，它会随该行的其余文本移动。

提示：如果想把一个行内元素的第一行“缩进”，可以用左内边距或外边距创造这种效果。

2、水平对齐

text-align 是一个基本的属性，它会影响一个元素中的文本行互相之间的对齐方式。它的前 3 个值相当直接，不过第 4 个和第 5 个则略有些复杂。
值 left、right 和 center 会导致元素中的文本分别左对齐、右对齐和居中。
西方语言都是从左向右读，所有 text-align 的默认值是 left。文本在左边界对齐，右边界呈锯齿状（称为“从左到右”文本）。对于希伯来语和阿拉伯语之类的的语言，text-align 则默认为right，因为这些语言从右向左读。不出所料，center 会使每个文本行在元素中居中。

提示：将块级元素或表元素居中，要通过在这些元素上适当地设置左、右外边距来实现。

text-align:center 与 <CENTER>
您可能会认为 text-align:center 与 <CENTER> 元素的作用一样，但实际上二者大不相同。
<CENTER> 不仅影响文本，还会把整个元素居中。text-align 不会控制元素的对齐，而只影响内部内容。元素本身不会从一段移到另一端，只是其中的文本受影响。

justify
最后一个水平对齐属性是 justify。
在两端对齐文本中，文本行的左右两端都放在父元素的内边界上。然后，调整单词和字母间的间隔，使各行的长度恰好相等。您也许已经注意到了，两端对齐文本在打印领域很常见。

3、字间隔

word-spacing 属性可以改变字（单词）之间的标准间隔。其默认值 normal 与设置值为 0 是一样的。
word-spacing 属性接受一个正长度值或负长度值。如果提供一个正长度值，那么字之间的间隔就会增加。为 word-spacing 设置一个负值，会把它拉近：
```css
p.spread {word-spacing: 30px;}
p.tight {word-spacing: -0.5em;}

<p class="spread">
This is a paragraph. The spaces between words will be increased.
</p>

<p class="tight">
This is a paragraph. The spaces between words will be decreased.
</p>
```

4、字母间隔

letter-spacing属性与word-spacing的区别在于，字母间隔修改的是字符或字母之间的间隔。
与 word-spacing 属性一样，letter-spacing 属性的可取值包括所有长度。默认关键字是 normal（这与 letter-spacing:0相同）。输入的长度值会使字母之间的间隔增加或减少指定的量：
```css
h1 {letter-spacing: -0.5em}
h4 {letter-spacing: 20px}

<h1>This is header 1</h1>
<h4>This is header 4</h4>
```

5、字符转换
text-transform 属性处理文本的大小写。这个属性有4个值：

 - none
 - uppercase
 - lowercase
 - capitalize
 默认值为none对文本不做任何改动，将使用源文档中的原有大小写。顾名思义，uppercase 和 lowercase 将文本转换为全大写和全小写字符。最后，capitalize 只对每个单词的首字母大写。

作为一个属性，text-transform可能无关紧要，不过如果您突然决定把所有h1元素变为大写，这个属性就很有用。不必单独地修改所有 h1 元素的内容，只需使用 text-transform 为你完成这个修改：
```css
h1{
    text-transform:uppercase;
}
```
使用 text-transform有两方面的好处。首先，只需写一个简单的规则来完成这个修改，而无需修改h1元素本身。其次，如果您以后决定将所有大小写再切换为原来的大小写，可以更容易地完成修改。

6、文本装饰
接下来，我们讨论text-decoration属性，这是一个很有意思的属性，他提供了很多非常有趣的行为。
text-decoration有5个值：
 
 - none
 - underline
 - overline
 - linethrough
 - blink
 不出所料，underline会对元素加下划线，就像HTML中的U元素一样。overline的作用恰好相反，会在文本的顶端画一个上划线。值line-through则在文本中间画一个贯穿线，等价于 HTML 中的 S 和 strike 元素。blink 会让文本闪烁，类似于 Netscape 支持的颇招非议的 blink 标记。
 
none 值会关闭原本应用到一个元素上的所有装饰。通常，无装饰的文本是默认外观，但也不总是这样。例如，链接默认地会有下划线。如果您希望去掉超链接的下划线，可以使用以下 CSS 来做到这一点：
```css
a {
    text-decoration: none;
  }
```
还可以在一个规则中结合多种装饰。如果希望所有超链接既有下划线，又有上划线，则规则如下：
```css
a:link a:visited {
text-decoration: underline overline;
    }
```
不过要注意的是，如果两个不同的装饰都与同一元素匹配，胜出规则的值会完全取代另一个值。请考虑以下的规则：
```css
h2.stricken {
    text-decoration: line-through;
    }
h2 {
    text-decoration: underline overline;
    }
```
对于给定的规则，所有 class 为 stricken 的 h2 元素都只有一个贯穿线装饰，而没有下划线和上划线，因为 text-decoration 值会替换而不是累积起来。

7、处理空白字符

white-space属性会影响到用户代理对源文档中的空格、换行和tab字符的处理。

通过使用该属性，可以影响浏览器处理字之间和文本行之间的空白符的方式。从某种程度上讲，默认的XTML处理已经完成空白符处理：他会把所有空白符合并为一个空格。所以给定一下标记，他在web浏览器中显示时，每个字之间只会显示一个空格，同时忽略元素中的换行：

可以用以下声明显式地设置这种默认行为：
```css
p {
    white-space: normal;
  }
```
上面的规则告诉浏览器按照平常的做法去处理：丢掉多余的空白符。如果给定这个值，换行字符(回车)会转换为空格，一行中多个空格的序列也会转换为一个空格。

总结：
下面的表格总结了white-space属性的行为：
值|空白符|换行符|自动换行
--|------|------|-------
pre-line|合并|保留|允许
normal|合并|忽略|允许
nowrap|合并|忽略|不允许
pre|保留|保留|不允许
pre-wrap|保留|保留|允许

CSS文本属性：
属性|描述
----|----
color|设置文本颜色
direction|设置文本方向
line-height|设置行高
letter-spacing|设置字符间距
text-align|对齐元素中的文本
text-decoration|向文本添加修饰
text-indent|缩进元素中文本的首行
text-shadow|设置文本阴影。CSS2包含该属性，但是CSS2.1没保留
text-transform|控制元素中的字母
white-space|设置元素中空白的处理方式
word-spacing|设置字间距。

## CSS链接
我们能够以不同的方法为链接设置样式

1、设置链接的样式
能够设置链接样式的CSS属性有很多种(例如color，font-family，background等等)。
链接的特殊性在于能够根据他们所处的状态来设置他们的样式。
链接的四种状态：

 - a:link -普通的、未被访问过的链接
 - a:visited -用户已访问过的链接
 - a:hover -鼠标指针位于链接的上方
 - a:active -链接被点击的时刻
 实例：
```css
 a:link {
    color:#FF0000;
 }		/* 未被访问的链接 */
a:visited {
    color:#00FF00;
}	/* 已被访问的链接 */
a:hover {
    color:#FF00FF;
}	/* 鼠标指针移动到链接上 */
a:active {
    color:#0000FF;
}	/* 正在被点击的链接 */
```
当为链接的不同状态设置样式时，请按照以下次序规则：
- a:hover必须位于a:link和a:visited之后
- a:active必须位于a:hover 

2、常见的链接样式

文本修饰
text-decoration 属性大多用于去掉链接中的下划线：
实例：
```css
a:link {
    text-decoration:none;
    }
a:visited {
    text-decoration:none;
    }
a:hover {
    text-decoration:underline;    }
a:active {
    text-decoration:underline;    }
```

背景色
background-color属性规定链接的背景色
实例：
```css
a:link {
    background-color:#B2FF99;
    }
a:visited {
    background-color:#FFFF85;
    }
a:hover {
    background-color:#FF704D;
    }
a:active {
    background-color:#FF704D;
    }
```
## CSS列表
CSS列表属性允许你放置、改变列表项标志，或者将图像作为列表项标志。

CSS列表
从某种意义上讲，不是描述性的文本的任何内容都可以认为是列表。人口普查、太阳系、家谱、参观菜单，甚至你的所有朋友都可以表示为一个列表或者是列表的列表。
由于列表如此多样，这使得列表相当重要，所以说，CSS 中列表样式不太丰富确实是一大憾事。

列表类型
要影响列表的样式，最简单(同时支持最充分)的办法就是改变其标志类型。
例如，在一个无序列表中，列表项的标志(marker)是出现在各列表项旁边的圆点。在有序列表中，标志可能是字母、数字或另外某种计数体系中的一个符号。
要修改用于列表项的标志类型，可以使用属性 list-style-type：
```css
ul{
    list-style-type:square;
}
```
上面的声明把无序列表中的列表项标志设置为方块。

列表项图像
有时，常规的标志是不够的。你可能想对各标志使用一个图像，这可以利用 list-style-image 属性做到：
```css
ul li {
    list-style-image : url(xxx.gif)
    }
```
CSS列表属性(list)
属性|描述
----|---
list-style|简写属性。用于把所有用于列表的属性设置于一个声明中。
list-style-image|将图像设置为列表项标志
list-style-position|设置列表中列表项标志的位置
list-style-type|设置列表项标志的类型

## CSS表格
CSS表格属性可以帮助您极大的改善表格的外观。

1、表格的边框
如需在 CSS 中设置表格边框，请使用 border 属性。
下面的例子为 table、th 以及 td 设置了蓝色边框：
```css
table,th,td{
    border:1px solid blue;
}
```
请注意，上例中的表格具有双线条边框。这是由于 table、th 以及 td 元素都有独立的边框。
如果需要把表格显示为单线条边框，请使用 border-collapse 属性。

2、折叠边框
border-collapse属性设置是否将表格边框折叠为单一边框。
```css
table
  {
  border-collapse:collapse;
  }
table,th, td
  {
  border: 1px solid black;
  }
```

3、设置宽度和高度
通过width和height属性定义表格的宽度和高度。
通过下面的例子将表格宽度设置为100%，同时将th元素的高度设置为50px：
```css
table
  {
  width:100%;
  }
th
  {
  height:50px;
  }
```

4、表格文本对齐
text-align和vertical-align属性设置表格中文本的对齐方式。
text-align属性设置水平对齐方式，比如左对齐、右对齐或者居中：
```css
td
  {
  text-align:right;
  }
```
vertical-align属性设置垂直对齐方式，比如顶部对齐、底部对齐或居中对齐：
```css
td{
    height:50px;
    vertical-align:bottom;
}
```

5、设置内边距
如需控制表格中内容与边框的距离，请为 td 和 th 元素设置 padding 属性：
```css
td{
    padding:15px;
}
```
6、表格颜色
下面的例子设置边框的颜色，以及th元素的文本和背景颜色：
```css
table, td, th
  {
  border:1px solid green;
  }
th
  {
  background-color:green;
  color:white;
  }
```
CSS Table属性
属性|描述
----|----
border-collapse|设置是否把表格边框合并为单一的边框。
border-spacing|设置分隔单元格边框的距离
caption-side|设置表格标题的位置
empty-cells|设置是否显示表格中的空单元格
table-layout|设置显示单元、行和列的算法。

## CSS轮廓
轮廓(Outline)是绘制元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。CSS outline属性规定元素轮廓的样式、颜色和宽度。
轮廓(Outline)实例：

CSS边框属性
"CSS"列中的数字指示哪个CSS版本定义了该属性。
属性|描述
----|----
outline|在一个声明中设置所有的轮廓属性
outline-color|设置轮廓的颜色
outline-style|设置轮廓的样式
outline-width|设置轮廓的宽度

总结：
border-style常用的属性值为：

- none 无边框
- dotted 点线
- dashed 虚线
- solid 实线
- double 双线
- groove 立体凹线
- ridge 立体凸线
- inset 立体嵌入线
- outset 立体隆起线

font-style常用的属性值为：

- normal  普通
- italic  斜体
- oblique 斜体

## CSS框模型概述
CSS框模型(Box Model)规定了元素框处理元素的内容、内边距、边框和外边框的方式。
CSS框模型概述
外边距------->边框------>内边距------>宽高------>元素
元素框的最内部分是实际的内容，直接包围内容的是内边距。内边距呈现了元素的背景。内边距的边缘是边框。边框以外是外边距，外边距默认是透明的，因此不会遮挡其后的任何元素。
提示：背景应用于由内容和内边距、边框组成的区域。
内边距、边框和外边距都是可选的，默认值是零。但是，许多元素将由用户代理样式表设置外边距和内边距。可以通过将元素的 margin 和padding设置为零来覆盖这些浏览器样式。这可以分别进行，也可以使用通用选择器对所有元素进行设置：
```css
* {
  margin: 0;
  padding: 0;
}
```
在 CSS 中，width和height指的是内容区域的宽度和高度。增加内边距、边框和外边距不会影响内容区域的尺寸，但是会增加元素框的总尺寸。
假设框的每个边上有 10 个像素的外边距和 5 个像素的内边距。如果希望这个元素框达到 100 个像素，就需要将内容的宽度设置为 70 像素，
```css
#box {
  width: 70px;
  margin: 10px;
  padding: 5px;
}
```
提示：内边距、边框和外边距可以应用于一个元素的所有边，也可以应用于单独的边。
提示：外边距可以是负值，而且在很多情况下都要使用负值的外边距。

## CSS内边距
元素的内边距在边框和内容去之间。控制该区域最简单的属性是padding属性。
CSS padding属性定义元素边框与元素内容之间的空白区域。

CSS padding属性
CSS padding属性定义元素的内边距。padding属性接受长度值或百分比值，但不允许使用负值。
例如，如果您希望所有的h1元素的各边都有10像素的内边距，只需要这样：
```css
h1 {
    padding: 10px;
    }
```
您还可以按照上、右、下、左的顺序分别设置各边的内边距，各边均可以使用不同的单位或百分比值：
```css
h1 {
    padding: 10px 0.25em 2ex 20%;
    }
```
单边内边距属性
也通过使用下面四个单独的属性，分别设置上、右、下、左内边距：

- padding-top
- padding-right
- padding-bottom
- padding-left
您也许已经想到了，下面的规则实现的效果与上面的简写规则是完全相同的：
```css
h1 {
  padding-top: 10px;
  padding-right: 0.25em;
  padding-bottom: 2ex;
  padding-left: 20%;
  }
```
内边距的百分比数值
前面提到过，可以为元素的内边距设置百分数值。百分数值是相对于其父元素的 width 计算的，这一点与外边距一样。所以，如果父元素的 width 改变，它们也会改变。
下面这条规则把段落的内边距设置为父元素 width 的 10%：
```css
p {
    padding: 10%;
 }
```
例如：如果一个段落的父元素是 div 元素，那么它的内边距要根据 div 的 width 计算。
```css
<div style="width: 200px;">
<p>This paragragh is contained within a DIV that has a width of 200 pixels.</p>
</div> 
```
注意：上下内边距与左右内边距一致；即上下内边距的百分数会相对于父元素宽度设置，而不是相对于高度。

CSS内边距属性
属性|描述
----|---
padding|简写属性。作用是在一个声明中设置元素的所有内边距属性。
padding-bottom|设置元素的下内边距
padding-left|设置元素的左内边距
padding-right|设置元素的右内边距
padding-top|设置元素的上内边距

## CSS边框
元素的边框 (border)是围绕元素内容和内边距的一条或多条线。
CSS border 属性允许你规定元素边框的样式、宽度和颜色。

1、CSS边框
在 HTML 中，我们使用表格来创建文本周围的边框，但是通过使用 CSS 边框属性，我们可以创建出效果出色的边框，并且可以应用于任何元素。
元素外边距内就是元素的的边框 (border)。元素的边框就是围绕元素内容和内边据的一条或多条线。
每个边框有 3 个方面：宽度、样式，以及颜色。在下面的篇幅，我们会为您详细讲解这三个方面。

2、边框与背景
CSS规范指出，边框绘制在“元素的背景之上”。这很重要，因为有些边框是“间断的”(例如，点线边框或虚线框)，元素的背景应当出现在边框的可见部分之间。

CSS2 指出背景只延伸到内边距，而不是边框。后来 CSS2.1 进行了更正：元素的背景是内容、内边距和边框区的背景。大多数浏览器都遵循 CSS2.1 定义，不过一些较老的浏览器可能会有不同的表现。

3、边框的样式
样式是边框最重要的一个方面，这不是因为样式控制着边框的显示（当然，样式确实控制着边框的显示），而是因为如果没有样式，将根本没有边框。
CSS 的 border-style 属性定义了 10 个不同的非 inherit 样式，包括 none。
例如，您可以为把一幅图片的边框定义为 outset，使之看上去像是“凸起按钮”：
```css
a:link img{
    border-style:outset;
}
```

定义多种样式
您可以为一个边框定义多个样式，例如：
```css
p.aside {
    border-style: solid dotted dashed double;
    }
```
上面这条规则为类名为aside的段落定义了四种边框样式：实线上边框、点线右边框、虚线下边框和一个双线左边框。
我们又看到了这里的值采用了 top-right-bottom-left 的顺序，讨论用多个值设置不同内边距时也见过这个顺序。

定义单边样式
如果您希望为元素框的某一个边设置边框样式，而不是设置所有4个边的边框样式，可以使用下面的单边边框样式属性：

 - border-top-style
 - border-right-style
 - border-bottom-style
 - border-left-style
 因此这两种方法是等价的：
 ```css
 p {
    border-style: solid solid solid none;
    }
p {
    border-style: solid;
    border-left-style: none;
    }
 ```

4、边框的宽度
你可以通过border-width属性来为边框指定宽度。
为边框指定宽度有两种方法：可以指定长度值，比如 2px 或 0.1em；或者使用3个关键字之一，它们分别是thin、medium（默认值） 和 thick。
注释：CSS 没有定义3个关键字的具体宽度，所以一个用户代理可能把 thin 、medium 和 thick 分别设置为等于5px、3px 和 2px，而另一个用户代理则分别设置为 3px、2px 和 1px。
所以，我们可以这样设置边框的宽度：
```csss
p {
    border-style: solid; 
    border-width: 5px;
    }
```
或者：
```css
p {
    border-style: solid; 
    border-width: thick;
    }
```

定义单边宽度
您可以按照top-right-bottom-left的顺序设置元素的各边边框：
```css
p {
    border-style: solid; 
    border-width: 15px 5px 15px 5px;
    }
```
您也可以通过下列属性分别设置边框各边的宽度：

 - boreder-top-width
 - border-right-width
 - border-bottom-width
 - border-left-width
 因此，下面的规则与上面的例子是等价的：
 
 ```css
 p {
  border-style: solid;
  border-top-width: 15px;
  border-right-width: 5px;
  border-bottom-width: 15px;
  border-left-width: 5px;
  }
 ```
没有边框
在前面的例子中，您已经看到，如果希望显示某种边框，就必须设置边框样式，比如 solid 或 outset。
那么如果把 border-style 设置为 none 会出现什么情况：
```css
p{
    border-style:none;
    border-width:50px;
}
```
尽管边框的宽度是50px，但是边框样式设置为none。在这种情况下，不仅边框的样式没有了，其宽度也会变成0。边框消失了，为什么呢？
这是因为如果边框样式为none，即边框根本不存在，那么边框就不可能有宽度，因此边框宽度自动设置为0，而不论您原先定义的是什么。
记住这一点非常重要。事实上，忘记声明边框样式是一个常犯的错误。根据以下规则，所有h1元素都不会有任何边框，更不用说 20 像素宽了：
```css
h1{
    border-width:20px;
}
```
由于border-style的默认值是none，如果没有声明样式，就相当于border-style：none。因此，如果您希望边框出现，就必须声明一个边框样式。

5、边框的颜色
设置边框颜色非常简单。CSS 使用一个简单的 border-color 属性，它一次可以接受最多 4 个颜色值。
可以使用任何类型的颜色值，例如可以是命名颜色，也可以是十六进制和 RGB 值：
```css
p{
    border-style:solid;
    border-color:blue rgb(25%,35%,45%) #909090 red;
}
```
如果颜色值小于4个，值复制就会起作用。例如下面的规则声明了段落的上下边框是蓝色，左右边框是红色：
```css
p{
    border-style:solid;
    border-style:blue red;
}
```
注释：默认的边框颜色是元素本身的前景色。如果没有为边框声明颜色，它将与元素的文本颜色相同。另一方面，如果元素没有任何文本，假设它是一个表格，其中只包含图像，那么该表的边框颜色就是其父元素的文本颜色（因为 color 可以继承）。这个父元素很可能是 body、div 或另一个 table。

定义单边颜色
还有一些单边边框颜色属性。它们的原理与单边样式和宽度属性相同：
 
 - border-top-color
 - border-right-color
 - border-bottom-color
 - border-left-color
要为 h1 元素指定实线黑色边框，而右边框为实线红色，可以这样指定：
```css
h1{
    border-style:solid;
    border-color:black;
    border-right-color:red;
}
```

透明边框
我们 
我们刚才讲过，如果边框没有样式，就没有宽度。不过有些情况下您可能希望创建一个不可见的边框。
CSS2 引入了边框颜色值 transparent。这个值用于创建有宽度的不可见边框。请看下面的例子：
```html
<a href="#">AAA</a>
<a href="#">BBB</a>
<a href="#">CCC</a>
```
我们为上面的链接定义了如下样式：
```css
a:link, a:visited {
  border-style: solid;
  border-width: 5px;
  border-color: transparent;
  }
a:hover {
  border-color: gray;
  }
```
CSS边框属性
属性|描述
----|----
border|简写属性，用于把针对四个边的属性设置在一个声明
border-style|用于设置元素所有边框的样式，或者单独地为各边设置边框样式。
border-width|简写属性，用于为元素的所有边框设置宽度，或者单独地为各边边框设置宽度。
border-color|简写属性，设置元素的所有边框中课件部分的颜色，或为4各边分别设置颜色。
border-bottom|简写属性，用于把下边框的所有属性设置到一个声明中。
border-bottom-color|设置元素的下边框的颜色。
border-bottom-style|设置元素的下边框的样式。
border-bottom-width|设置元素的下边框的宽度。
border-left	|简写属性，用于把左边框的所有属性设置到一个声明中。
border-left-color |设置元素的左边框的颜色。
border-left-style |设置元素的左边框的样式。
border-left-width |设置元素的左边框的宽度。
border-right |简写属性，用于把右边框的所有属性设置到一个声明中。
border-right-color |设置元素的右边框的颜色。
border-right-style |设置元素的右边框的样式。
border-right-width |设置元素的右边框的宽度。
border-top	|简写属性，用于把上边框的所有属性设置到一个声明中。
border-top-color |设置元素的上边框的颜色。
border-top-style |设置元素的上边框的样式。
border-top-width |设置元素的上边框的宽度。

## CSS外边框
围绕在元素边框的空白区域是外边距。设置外边距会在元素外创建额外的“空白”。
设置外边距的最简单的方法就是使用margin属性，这个属性接受任何长度单位、百分数值甚至负值。

1、CSS margin属性
设置外边距的最简单的方法就是使用 margin 属性。
margin 属性接受任何长度单位，可以是像素、英寸、毫米或 em。
margin 可以设置为auto。更常见的做法是为外边距设置长度值。下面的声明在 h1 元素的各个边上设置了 1/4 英寸宽的空白：
```css
h1 {
    margin : 0.25in;
    }
```
下面的例子为 h1元素的四个边分别定义了不同的外边距，所使用的长度单位是像素 (px)：
```css
h1 {
    margin : 10px 0px 15px 5px;
    }
```
与内边距的设置相同，这些值的顺序是从上外边距 (top) 开始围着元素顺时针旋转的：
margin: top right bottom left
另外，还可以为 margin 设置一个百分比数值：
p {margin : 10%;}
百分数是相对于父元素的 width 计算的。上面这个例子为 p 元素设置的外边距是其父元素的 width 的 10%。
margin 的默认值是0，所以如果没有为margin声明一个值，就不会出现外边距。但是，在实际中，浏览器对许多元素已经提供了预定的样式，外边距也不例外。例如，在支持 CSS 的浏览器中，外边距会在每个段落元素的上面和下面生成“空行”。因此，如果没有为p元素声明外边距，浏览器可能会自己应用一个外边距。当然，只要你特别作了声明，就会覆盖默认样式。
		
2、值复制
有时，我们会输入一些重复的值：
```css
p {
    margin: 0.5em 1em 0.5em 1em;
    }
```
通过值复制，您可以不必重复地键入这对数字。上面的规则与下面的规则是等价的：
```css
p {
    margin: 0.5em 1em;
    }
```
		
3、单边外边距属性
您可以使用单边外边距属性为元素单边上的外边距设置值。假设您希望把 p 元素的左外边距设置为 20px。不必使用 margin（需要键入很多 auto），而是可以采用以下方法：
```css
p{
    margin-left:20px;
    }
```
您可以使用下列任何一个属性来只设置相应上的外边距，而不会直接影响所有其他外边距：

- margin-top
- margin-right
- margin-bottom
- margin-left
一个规则中可以使用多个这种单边属性，例如：
```css
h2 {
  margin-top: 20px;
  margin-right: 30px;
  margin-bottom: 30px;
  margin-left: 20px;
  }
```
当然，对于这种情况，使用margin可能更容易一些：
```css
p{
    maigin:20px 30px 30px 20px;
}
```
不论使用单边属性还是使用margin，得到的结果都一样。一般来说，如果希望为多个边设置外边距，使用 margin 会更容易一些。不过，从文档显示的角度看，实际上使用哪种方法都不重要，所以应该选择对自己来说更容易的一种方法。

CSS外边距属性
属性|描述
----|----
margin|简写属性。在一个声明中设置所有外边距属性
margin-bottom|设置元素的下外边距
margin-left|设置元素的左外边距
margin-right|设置元素的右外边距
margin-top|设置元素的上外边距

## CSS定位(Positioning)
CSS定位(Positioning)属性允许你对元素进行定位

1、CSS定位和浮动
CSS 为定位和浮动提供了一些属性，利用这些属性，可以建立列式布局，将布局的一部分与另一部分重叠，还可以完成多年来通常需要使用多个表格才能完成的任务。
定位的基本思想很简单，它允许你定义元素框相对于其正常位置应该出现的位置，或者相对于父元素、另一个元素甚至浏览器窗口本身的位置。显然，这个功能非常强大，也很让人吃惊。要知道，用户代理对CSS2中定位的支持远胜于对其它方面的支持，对此不应感到奇怪。
另一方面，CSS1 中首次提出了浮动，它以 Netscape 在 Web 发展初期增加的一个功能为基础。浮动不完全是定位，不过，它当然也不是正常流布局。我们会在后面的章节中明确浮动的含义。

2、一切皆为框
div、h1 或 p 元素常常被称为块级元素。这意味着这些元素显示为一块内容，即“块框”。与之相反，span 和 strong 等元素称为“行内元素”，这是因为它们的内容显示在行中，即“行内框”。
您可以使用 display属性改变生成的框的类型。这意味着，通过将 display 属性设置为 block，可以让行内元素（比如 <a> 元素）表现得像块级元素一样。还可以通过把 display 设置为 none，让生成的元素根本没有框。这样的话，该框及其所有内容就不再显示，不占用文档中的空间。
但是在一种情况下，即使没有进行显式定义，也会创建块级元素。这种情况发生在把一些文本添加到一个块级元素（比如 div）的开头。即使没有把这些文本定义为段落，它也会被当作段落对待：
```html
<div>
some text
<p>Some more text.</p>
</div>
```
在这种情况下，这个框称为无名块框，因为它不与专门定义的元素相关联。
块级元素的文本行也会发生类似的情况。假设有一个包含三行文本的段落。每行文本形成一个无名框。无法直接对无名块或行框应用样式，因为没有可以应用样式的地方（注意，行框和行内框是两个概念）。但是，这有助于理解在屏幕上看到的所有东西都形成某种框。

3、CSS定位机制
CSS有三种基本的定位机制：普通流、绝对定位。
除非专门指定，否则所有框都在普通流中定位。也就是说，普通流中的元素的位置由元素在 (X)HTML 中的位置决定。
块级框从上到下一个接一个地排列，框之间的垂直距离是由框的垂直外边距计算出来。
行内框在一行中水平布置。可以使用水平内边距、边框和外边距调整它们的间距。但是，垂直内边距、边框和外边距不影响行内框的高度。由一行形成的水平框称为行框（Line Box），行框的高度总是足以容纳它包含的所有行内框。不过，设置行高可以增加这个框的高度。
		
4、CSS position属性
通过使用 position 属性，我们可以选择 4 种不同类型的定位，这会影响元素框生成的方式。
position 属性值的含义：
static
元素框正常生成。块级元素生成一个矩形框，作为文档流的一部分，行内元素则会创建一个或多个行框，置于其父元素中。
relative
元素框偏移某个距离。元素仍保持其未定位前的形状，它原本所占的空间仍保留。
absolute
元素框从文档流完全删除，并相对于其包含块定位。包含块可能是文档中的另一个元素或者是初始包含块。元素原先在正常文档流中所占的空间会关闭，就好像元素原来不存在一样。元素定位后生成一个块级框，而不论原来它在正常流中生成何种类型的框。
fixed
元素框的表现类似于将 position 设置为 absolute，不过其包含块是视窗本身。
提示：相对定位实际上被看作普通流定位模型的一部分，因为元素的位置相对于它在普通流中的位置。

## CSS相对定位
设置为相对定位的元素框会偏移某个距离。元素仍然保持其未定位前的形状，它原本所占的空间仍保留

相对定位是一个非常容易掌握的概念。如果对一个元素进行相对定位，它将出现在它所在的位置上。然后，可以通过设置垂直或水平位置，让这个元素“相对于”它的起点进行移动。
如果将 top 设置为 20px，那么框将在原位置顶部下面 20 像素的地方。如果 left 设置为 30 像素，那么会在元素左边创建 30 像素的空间，也就是将元素向右移动。

## 绝对定位
设置为绝对定位的元素框从文档流完全删除，并相对于其包含块定位，包含块可能是文档中的另一个元素或者是初始包含块。元素原先在正常文档流中所占的空间会关闭，就好像该元素原来不存在一样。元素定位后生成一个块级框，而不论原来它在正常流中生成何种类型的框。

绝对定位使元素的位置与文档流无关，因此不占据空间。这一点与相对定位不同，相对定位实际上被看作普通流定位模型的一部分，因为元素的位置相对于它在普通流中的位置。
普通流中其它元素的布局就像绝对定位的元素不存在一样：

相对定位是“相对于”元素在文档中的初始位置，而绝对定位是“相对于”最近的已定位祖先元素，如果不存在已定位的祖先元素，那么“相对于”最初的包含块

## CSS浮动
浮动的框可以向左或向右移动，直到他的外边缘碰到包含框或另一个浮动框的边框为止。
由于浮动框不在文档的普通流中，所以文档的普通流中的块框表现得就像浮动框不存在一样。

1、CSS浮动
请看下图，当把框1向右浮动时，它脱离文档流并且向右移动，直到它的右边缘碰到包含框的右边缘：

再请看下图，当框1向左浮动时，它脱离文档流并且向左移动，直到它的左边缘碰到包含框的左边缘。因为它不再处于文档流中，所以它不占据空间，实际上覆盖住了框 2，使框 2 从视图中消失。
如果把所有三个框都向左移动，那么框1向左浮动直到碰到包含框，另外两个框向左浮动直到碰到前一个浮动框。
如下图所示，如果包含框太窄，无法容纳水平排列的三个浮动元素，那么其它浮动块向下移动，直到有足够的空间。如果浮动元素的高度不同，那么当它们向下移动时可能被其它浮动元素“卡住”：

2、CSS float属性
在CSS中，我们通过float属性实现元素的浮动。

3、行框和清理
浮动框旁边的行框被缩短，从而给浮动框留出空间，行框围绕浮动框。
因此，创建浮动框可以使文本围绕图像：

要想阻止行框围绕浮动框，需要对该框应用 clear 属性。clear 属性的值可以是 left、right、both 或 none，它表示框的哪些边不应该挨着浮动框。
为了实现这种效果，在被清理的元素的上外边距上添加足够的空间，使元素的顶边缘垂直下降到浮动框下面：


这是一个有用的工具，它让周围的元素为浮动元素留出空间。
让我们更详细地看看浮动和清理。假设希望让一个图片浮动到文本块的左边，并且希望这幅图片和文本包含在另一个具有背景颜色和边框的元素中。您可能编写下面的代码：
