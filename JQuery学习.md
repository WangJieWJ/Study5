# JQuery学习笔记

## 1、选择器

###	基本选择器
		通过id：			$("#idName")
		通过class:			$(".className")
		通过标签的名称：	$("div")
		等……
		
###	层次选择器：
		后代选择器：			$("#menu  #level"):选取menu元素里的所有level(后代)元素
		子代(直接后代)：		$("#menu > #level"):选取menu元素下的child(子)元素,与$("menu level")有区别，$("menu level")选择的是后代元素
		下一个同辈的元素		$(".className + li"):选取class为className的下一个<li/>同辈元素
		后面所有同辈的元素		$("#className ~ li"):选取id为className的之后所有<li/>同辈元素

###	过滤选择器：
		过滤选择器主要是通过特定的过滤规则来筛选出所需的DOM元素，过滤的规则与CSS中的伪类选择器语法相同，即选择器都以一个冒号(:)开头。
		按照不同的过滤规则，过滤选择器可以分为基本过滤器、内容过滤器、可见过滤器、属性过滤器、子元素过滤器和表单对象属性过滤器选择器。
		
####	1、基本过滤器
			:first	 			选取第一个元素  						        $("div:first")选取所有<div>元素中第1个<div>元素
			:last  			  	选取最后一个元素								$("div:last")选取所有<div>元素中最后1个<div>元素
			:not(selector)		去除所有与给定选择器匹配的元素。				$("input:not(.myClass)")选取class不是myClass的<input>元素
			:odd				选取索引是奇数的所有元素，索引从0开始			$("input:odd")选取索引为奇数的<input>元素
			:even				选取索引是偶数的所有元素，索引从0开始			$("input:even")选取索引为偶数的<input>元素
			:eq(index)			选择索引等于index的元素(index从0开始)			$("input:eq(1)")选取索引等于1的<input>元素
			:gt(index)			选取索引大于index的元素(index从0开始)			$("input:gt(1)")选取索引大于1的<input>元素(注：大于1，而不包括1)
			:lt(index)			选取索引小于index的元素(index从0开始)			$("input:lt(1)")选取索引小于1的<input>元素(注：小于1，而不等于1)
			:header				选取所有的标题元素，例如h1,h2,h3等的			$("input:header")选取网页中的所有<h1>、<h2>、<h3>……
			:animated           选取当前正在执行动画的所有元素					$("div:animated")选取正在执行动画的<div>元素
			:focus				选取当前获取焦点的元素							$(":focus")选取当前获取焦点的元素
			
####	2、内容选择器
			:contains(text)		选取含有文本内容为“text”的元素					$("div:contains('我')")选取含有违背"我"的<div>元素
			:empty				选取不包含子元素或者文本的空元素				$("div:empty")选取不包含子元素(包括文本元素)的<div>元素
			:has(selector)		选取含有选择器所匹配的元素的元素				$("div:has(p)")选取含有<p>元素的<div>元素
			:parent				选取含有子元素或者文本的元素					$("div:parent")选取拥有子元素(包括文本元素)的<div>元素
			
####	3、可见性选择器
			:hidden				选取所有不可见的元素							$(":hidden")选取所有不可见的元素，包括<input type="hidden"/>、
																				<input type="hidden">、<input type="hidden">等……，
																				如果只想选取<input>元素，可以使用$("input:hidden").
			:visible			选取所有可见的元素								$(div:visible)选取所有可见的<div>元素
		
####	4、属性过滤选择器
			[attribute]			选取拥有此属性的元素							$("div[id]")选取拥有属性id的元素
			[attribute=value]	选取属性值为value的元素							$("div[title='test']")选取属性title为test的<div>元素
			[attribute!=value]	选取属性值不等于value的元素						$("div[title!='test']")选取属性title不等于test的<div>元素
																					(注意：没有title的<div >也会被选取)
			[attribute^=value]  选取属性值以value开始的元素						$("div[title^='test']")选取属性title以“test”开始的<div>元素 
			[attribute$=value]	选取属性值以value结束的元素						$("div[title$='test']")选取属性title以“test”结尾的<div>元素
			[attribute*=value]	选取属性的值含有value的元素						$("div[title*='test']")选取属性title含有“test”的<div>元素 
			[attribute|=value]  选取属性等于给定字符串或以该字符串为前缀(该字符串后面跟一个字符“-”)的元素
																				$("div[title|='en']")选取属性title等于en或以en为前缀
																					(该字符串后跟一个连字符"-")的元素
			[attribute1][attribute2][attributeN]	使用属性选择器合成一个复合属性选择器，满足多个条件。每个条件一次，缩小一次范围
																				$("div[id][title$='test']")选取拥有属性id，并且属性title以'test'结束的<div>元素
####	5、子元素过滤选择器
			:nth-child(index/even/odd/equation)		选取每个父元素下的第index个子元素或者奇偶元素(index从1算起)			
																				:eq(index)只匹配一个元素，而:nth-child将为每一个父元素匹配子元素，
																					并且:nth-child(index)的index是从1开始的，而eq(index)是从0算起的
			
			:nth-child()选择器是常用的子元素过滤选择器，详细功能如下。
						1、:nth-child(even)能选取每个父元素下的索引值是偶数的元素
						2、:nth-child(odd)能选取每个元素下的索引值是奇数的元素
						3、:nth-child(2)能选取每个父元素下的索引值等于2的元素
						4、:nth-child(3n)能选取每个父元素下的索引值是3的倍数(n从1开始)。
						5、:nth-child(3n+1)能选取每个父元素下的索引值是(3n+1)的元素(n从1开始)。
			
			
			
			:first-child        选取每个父元素的第1个子元素						:first只返回单个元素，而:first-child选择符将为每个父元素匹配第1个子元素。
																					例如$("ul li:first-child");选择每个<ul>中的第1个<li>元素。
			
			:last-child			选取每个父元素的最后一个子元素					同样，:last只返回单个元素，而:last-child选择符将每一个父元素匹配最后一个子元素
																					例如$("ul li:last-child");选择每一个<ul>中最后一个<li>元素
			
			
			:only-child			如果某个元素是他父元素的唯一的子元素，那么将会被匹配，如果父元素中含有其他元素，则不会被匹配。
			
			
			
####	6、表单对象属性过滤选择器
			:enable				选取所有可用的元素					$("#form1:enable")选取id为form1的表单内的所有可用元素。
			:disable			选取所有不可用元素					$("#form2:disable")选取id为form2表单内所有不可用的元素
			:checked			选取所有被选中的元素(单选框、复选框)	$("input:checked")选取所有被选中的<input>元素
			:selected			选取所有被选中的选项元素(下拉列表)		$("input option:selected")选取所有被选中的选项元素
			
			
####  7、表单选择器
			:input				选取所有的<input>、<textarea>、<select>和<button>元素      $(":input")选取所有的<input>、<textarea>、<select>和<button>元素
			:text				选取所有的单行文本框					$(":text")选取所有的单行文本框
			:password			选取所有的密码框						$(":password")选取所有的密码框
			:radio              选取所有的单选框
			:checkbox			选取所有的多选框
			:submit  			选取所有的提交按钮			
			:image				选取所有的图像按钮
			:reset				选取所有的重置按钮
			:button 			选取所有的按钮
			:file				选取所有的上传按钮
			:hidden				选取所有的不可见元素
			
			
## 2、JQuery中的DOM操作
	
###	1、查找节点
#### 1、查找元素节点
			$(ul li:eq(1)).text()   查找元素节点并打印出他的文本内容
	
#### 2、查找属性节点
			$("p").attr("title")	获取属性节点并打印出他的属性内容
			
### 2、创建节点
####	1、创建元素节点
			var $new_li=$("<li></li>");
			
####	2、创建文本节点
			var $new_li=$("<li>香蕉</li>");
			
####	3、创建属性节点
			var $new_li=$("<li title='香蕉'>香蕉</li>");	//可以使用字符串拼接！！！

### 3、插入节点
####	1、append()			向每个匹配的元素内部追加内容		html代码：<p>我想说：</p>
																JQuery代码：$("p").append("<b>你好</b>");
																结果：<p>我想说：<b>你好</b></p>
			
####	2、appendTo()		将所有匹配的元素追加到指定的元素中。
							实际上，使用该方法是颠倒了常规的$(A).append(B)的操作，
							即不是将B追加到A中，而是将A追加到B中
																 HTML代码：<p>我想说：</p>
																 JQuery代码：$("<b>你好</b>").appendTo("p");
																 结果：<p>我想说：<b>你好</b></p>
																 
																 
####	3、prepend()		向每个匹配的元素内部前置内容		HTML代码：											 
																JQuery代码：$("p").prepend("<b>你好</b>");
																结果：<p><b>你好</b>我想说：</p> 
																 
#### 4、prependTo()		将所有匹配的元素前置到指定的元素中，
							实际上，使用该方法是颠倒了常规的$(A).prepend(B)的操作，
							即不是将B前置到A中，而是将A前置到B中
																 HTML代码：	<p>我想说：</p>		
																 JQuery代码：$("<b>你好</b>").prependTo("p");
																 结果：<p><b>你好</b>我想说：</p>
																 
#### 5、after()			在每个匹配的元素之后插入内容		HTML代码：<p>我想说：</p>		
																JQuery代码：$("p").after("<b>你好</b>")
																结果：<p>我想说：</p><b>你好</b>
		

####	6、insertAfter()	将所匹配的元素插入到指定元素后面，
							实际上，使用该方法是颠倒了常规的$(A).after(B)的操作，
							既不是将B插入到A后面，而是将A插入到B后面。
																HTML代码：<p>我想说：</p>
																JQuery代码：$("<b>你好</b>").insertAfter("p");
																结果：<p>我想说：</p><b>你好</b>
																
#### 7、before()			在每个匹配的元素之前插入内容		HTML代码：<p>我想说：</p>
																JQuery代码：$("p").before("<b>你好</b>");
																结果：<b>你好</b><p>我想说：</p>
																 
####	8、insertBefore()   将所匹配的元素插入到指定元素前面，
							实际上，使用该方法是颠倒了常规的$(A).before(B)的操作，
							既不是将B插入到A前面，而是将A插入到B前面。														 
																 HTML代码：<p>我想说：</p>
																JQuery代码：$("<b>你好</b>").insertBefore("p");
															结果：<b>你好</b><p>我想说：</p>
	
### 4、删除节点
		如果文档中某一个元素多余，那么应将其删除。JQuery提供了三种删除节点的方法，即remove()、detach()和empty()
		
#### 1、remove()方法
		所用是从DOM中删除的所有匹配的元素，传入的参数用于根据JQuery表达式来筛选元素
			
			例如：$("ul li:eq(1)").remove();		//获取第2个<li>元素节点，将他从网页中删除
		
		当某个节点用remove()方法删除后，该节点所包含的所有后代节点将同时被删除。
		这个方法返回值是一个指向已被删除的节点的引用，因此可以在以后再使用这些元素。
		下面的JQuery代码说明元素用remove()方法删除后，还是可以继续使用的
		
			var $li=$("ul li:eq(1)").remove();  //获取第2个<li>元素节点后，将他从网页中删除
			$li.appendTo("ul");					//把刚才删除的节点又重新添加到<ul>元素里
		
		可以直接使用appendTo()方法的特性来简化以上代码，JQuery代码如下：
			
			$("ul li:eq(1)").appendTo("ul");
			//appendTo()方法也可以用来移动元素
			//移动元素时首先从文档上删除此元素，然后将该元素插入得到文档中的指定节点
			
		另外remove()方法也可以通过传递参数来选择性删除元素，JQuery代码如下：
			$("ul li").remove("li[title!=菠萝]");
				//将<li>元素中属性title不等于"菠萝"的<li>元素删除
				
#### 2、detach()方法
			detach()和remove()一样，也是从DOM中去掉所有匹配的元素，
			但需要注意的是，这个方法不会把匹配的元素从JQuery对象中删除
			因而可以在将来再使用这些匹配的元素，与remove()方法不同的是，所有绑定的事件、附加的数据等都会保留下来。
			
			通过下面的例子，可以知道他与remove()方法的区别，JQuery代码
				
				$("ul li").click(function(){
					alert($(this).html());
				})
				var $li=$("ul li:eq(1)").detach();  //删除元素
				$li.appendTo("ul");  
				//重新追加此元素，发现他之前绑定的时间还在，如果使用remove()方法删除元素的话，那么他之前绑定的事件就失效。 		
		
#### 3、empty()方法
			严格来讲：empty()方法并不是删除节点，而是清空节点，他能清空元素中的所有后代节点。JQuery代码如下：
			$("ul li:eq(1)").empty();
					//获取第2个<li>元素节点后，清空此元素里的内容，注意是元素里
		
### 5、复制节点
			JQuery代码：
			$("ul  li").click(function(){
				$(this).clone().appendTo("ul");   //复制当前单击的节点，并将他追加到<ul>元素中。
			})
			
		复制节点后，被复制的新元素并不具有任何行为。如果需要新元素也具有复制功能(本例中是单击事件),
		可以使用如下JQuery代码：
			$(this).clone(true).appendTo("body");  //注意参数true
			
		在clone()方法中传递一个参数true，他的含义是复制元素的同时复制元素中所绑定的事件。
		因此该元素的副本也同样具有复制功能(本例指单击事件)

		
### 6、样式操作
####	1、获取样式和设置样式
			HTML代码如下：
				<p class="myClass" title="选择你最喜欢的水果。">你最喜欢的水果是？</p>
			在上面的代码中，class也是<p>元素的属性，因此获取class和设置class都可以使用attr()方法来完成。
			例如使用attr()方法来获取<p>元素的class，JQuery代码如下：
				var p_class=$("p").attr("class");			//获取<p>元素的class
			也可以使用attr()方法来设置<p>元素的class,JQuery代码如下：
				$("p").attr("class","high");				//获取<p>与元素的class为"high"
			运行代码之后，上面的HTML代码将变成如下结构：
				<p class="high" title="选择你最喜欢的水果。">你最喜欢的水果是？</p>
			上面的代码是将原来的class(myClass)替换为新的class(high)。如果此处需要的是"追加效果"，class属性变为"myClass high"，
			即myClass和high两种样式的叠加,那么我们可以使用addClass()方法。
		
#### 2、追加样式
			JQuery提供了专门的addClass("ClassName")方法来追加样式。
		
#### 3、移除样式
			JQuery提供了removeClass("ClassName")方法来删除样式。
			
			JQuery也可以同时删除两个样式的，中间使用空格分隔。removeClass("ClassName1 ClassName2");
		
#### 4、切换样式
			JQuery提供了一个toggleClass()方法来控制样式上的重复切换。如果类名存在则删除它，如果类名不存在则添加他。
			
#### 5、判断是否含有某个样式：
			hasClass()可以用来判断元素中是否含有某个class，如果有，则返回true，否则返回false。

### 7、设置或获取HTML、文本和值
#### 1、html()方法。
			此方法类似于JavaScript中的innerHTML属性，可以用来读取或者设置某个元素的HTML内容。
				<p title="选择你最喜欢的水果。"><strong>你最喜欢的水果是？</strong></p>
			然后用html()方法对<p>元素进行操作。
				var p_html=$("p").html();		//获取<p>元素的HTML代码
				alert(p_html);					//显示<p>元素的HTML代码，结果为 <strong>你最喜欢的水果是？</strong>
		
#### 2、text()方法
			此方法类似于JavaScript中的innerText属性，可以用来读取或者设置某个元素中的文本内容，则对于上面HTML代码进行操作。
				var p_text=$("p").text();		//获取<p>元素的文本内容
				alert(p);						//显示<p>元素的文本内容，结果为  你最喜欢的水果是？
		
####	3、val()方法
			此方法类似于JavaScript中的value属性，可以用来设置和获取元素的值。无论元素是文本框、下拉框还是单选框，
			他都可以返回元素的值，如果元素为多选，则返回一个包含所有选择的值的数组
			
### 8、遍历节点

#### 1、children()方法。
			该方法用于取得匹配元素的子元素集合 (只考虑子元素而不考虑其他后代元素。)
			var $ul=$("ul").children();
			alert($ul.length);
			for(var i=0,len<$ul.length;i<len;i++){
				alert($ul[i].innerHTML);	//循环输出<li>元素的HTML内容。
			}

#### 2、next()方法
			该方法用于取得匹配元素后面紧邻的同辈元素
				var $pl=$("p").next();	//取得紧邻<p>元素后的同辈元素
		
#### 3、prev()方法：
			该方法用于取得匹配元素前面紧邻的同辈元素
				var $ul=$("ul").prev(); //取得紧邻<ul>元素前的同辈元素
		
#### 4、siblings()方法。
			该方法用于取得匹配元素前后所有的同辈元素，即获取匹配元素的兄弟节点。
		
###　3、JQuery中的事件和动画
	
	简写绑定事件：
	
	
	合成事件：
		JQuery有两个合成事件-----hover()方法和toggle()方法，这两个方法属于JQuery自定义的方法。
	
#### 1、hover()方法的语法节结构为：
		hover(enter,leave);
	hover()方法用于模拟光标悬停事件。
	当光标移动到元素上时，会触发指定第1个函数(enter)；
	当光标移出这个元素的时候，会触发指定的第二个函数(leave)。
	
#### 2、toggle()方法
		toggle(fn1,fn2,……,fnN)：
	toggle()方法用于模拟鼠标连续单击事件，第一次单机元素，触发指定的第1个函数(fn1);
	当再次点击同一元素时，则触发指定的第2个函数(fn2);
	如果有更多的函数，则依次触发，知道最后一个。随后的每一次单击都重复对这几个函数的轮番调用。
	




		
### 总结：各类控件中值得获取方式
		
#### 1、<input type="text" id="inputDemo"/>
			获取输入值的方式：$("#inputDemo").val();
			获取完毕之后将输入框清空的方式：$("#inputDemo").val("");
			
		
#### 2、<li title="苹果">苹果</li>
			获取标签中间的值得方式：$("li").text();
		
#### 3、<select id="selectDemo">
			<option value="1">广州</option>
			<option value="2" selected="selected">深圳</option>
			<option value="3">北京</option>
			<option value="4">上海</option>
			<option value="5">西安</option>
		   </select>
			获取选中值得方式:$(#selectDemo:selected).text();
			
#### 4、获取一些标签的属性的方式：
			<a href="" title=""></a>
			想要获取<a>标签的title属性值：$("a").attr("title");
			
			
