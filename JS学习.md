# JavaScript学习

## 1、Number

JavaScript不区分整数和浮点数，统一用Number表示，以下都是合法的Number类型的数据
	
	123;       //整数
	0.456;     //浮点数
	1.234e3;   //科学计数法表示1.234X1000，等同于1234
	-99;       //负数
	NaN;       //NaN表示Not a Number，当无法计算结果时用NAN表示
	Infinity;  //infinity表示无限大，当数值超过了JavaScript的Number所能表示的最大值时，就表示Ininity


## 2、字符串

字符串是以单引号或双引号括起来的任意文本，比如'abd',"abd"等等


## 3、比较运算符

当我们对Number作比较时，可以使用比较运算符得到一个布尔值：

	2>5;  ///false

实际上，JavaScript允许对任意的数据类型作比较：
	false == 0;   //true
	false === 0;  //false
要特别注意相等运算符 ==。JavaScript再设计时，有两种比较运算符：
第一种是==比较，他会自动转换数据类型再比较，很多时候，会得到非常诡异的结果；
第二种是===比较，他不会自动转换数据类型，如果数据类型不一致，返回false，如果一致，再比较。
由于JavaScript这个设计缺陷，不要使用 == 比较，使用坚持使用 === 比较。
另一个例外是NAN这个特殊的Number与所有其他值都不相等，包括他自己：
	NaN === NaN; //false
唯一能判断NaN的方法是通过isNaN()函数
	isNaN(NaN);  //true
	
## 4、数组
数组是一组按顺序排列的集合，集合的每一个值称为元素。JavaScript的数组可以包括任意数据类型。
	[1,2,3,112,'Hello',"World",null,true];此数组包含的8个元素。数组用[]表示，元素之间用,分隔
另一种创建数组的方法是通过Array()函数实现：
	new Array(1,2,3); //创建了数组[1,2,3]
数组的元素可以通过索引来访问。请注意，索引的起始值为0：
	var arr=[1,2,3.12,'Hello',null,true];
	arr[0]; //返回索引值为0的元素，即为1
	arr[5]; //返回索引值为5的元素，即为true
	arr[6]; //索引超出了范围，返回undefined
	
## 5、对象
JavaScript的对象是一组由键-值组成的无序集合，例如：
	var person={
	name:'王杰',
	age:'20',
	tags:['js','web','mobile'],
	city:'Beijing',
	hasCar:true,
	zipcode:null
	};
	JavaScript对象的键都是字符串类型，值可以是任意数据类型。上述person对象一共定义了6个键值对，
其中每个键又称为对象的属性，例如，person的name属性为'王杰',zipcode属性为null
要获取一个对象的属性，我们用对象变量.属性名的方式：
	person.name;      //'王杰'
	person.zipcode;   //null
	
## 6、变量
变量的概念基本上和初中代数的方程变量是一致的，只是在计算机程序中，变量不仅可以是数字，还可以是任意数据类型
变量在JavaScript中就是用一个变量名表示，变量名是大小写英文、数字、$和_的组合，且不能以数字开头。
变量名也不能是JavaScript的关键字，如if、while等。申明一个变量用var语句，
	var a;  //申明了变量a，此时a的值为undefined
	var $b=1;  //申明了变量$b, 同时给$b赋值，此时$b的值为1
	var s_112='123sdf';  //s_112是一个字符串。
在JavaScript中，使用等号=对变量进行赋值。可以把任意数据类型赋值给变量，同一个变量可以反复赋值，
而且可以是不同类型的变量，但是要注意只能用var申明一次，例如：
	var a=123; //a的值是整数123
	a='ABC';   //a变为字符串
这种变量本身类型不固定的语言称之为动态语言，与之对应的是静态语言。静态语言在定义变量时必须指定变量类型，
如果赋值的时候类型不匹配，就会报错。例如Java是静态语言，

	
各种数据类型的详解：

## 一、字符串：

1、转义字符\
	I'm OK -------------> "I'm  OK"
	I'm "OK"!---------------> "I\'m \"OK\"!"
2、多行字符串
由于多行字符用\n写起来比较费事，所以最新的ES6标准新增了一种多行字符串的表示方法，使用`...`来表示
	`这是一个
	多行
	字符串`;     键盘左上角的反单引号。
3、模板字符串 可以避免使用'+'来拼接字符串
	var name='小明';
	var age=20;
	var gender='男'
	var message=`你好,${name},你今年${age}岁了！是${gender}生`;
	alert(message);
4、操作字符串
	var s='Hello World!';
//获取字符串的长度：    
	s.length;		
//获取字符串某个位置的字符	
	s[0]; //'H'
	s[12]; //'!'
	s[13]; //underfined查出范围的索引不会报错，但一律返回undefined
//把一个字符串全部变为大写
	s.toUpperCase(); ///返回'Hello'
//把一个字符串全部转换为小写
    s.toLowerCase(); //返回'hello'
//indexOf()会搜索指定字符串出现的位置
    var s='hello world';
	s.indexOf('world');	//返回7
	s.indexOf('World');  //没有找到指定的子串，返回-1
//返回指定索引区间的子串
	var s='Hello World';
	s.substring(0,5); //从索引0开始到5(不包括5)，返回'hello'
	s.substring(7);   //从索引7开始到结束，返回'world'

## 二、数组

	var arr=[1,2,3.14,'Hello',null,true];
### 1、获取数组长度
	arr.length; //6
注意：1、直接给Array的length赋一个新的值会导致Array大小的变化：
		var arr=[1,2,3];
		arr.length;  //3
		arr.length=6;
		arr;       //arr变为[1,2,3,undefined,undefined,undefined]
		arr.length=2;
		arr;       //arr变为[1,2]
	  2、如果通过索引赋值时，索引超过了范围，同样会引起Array大小的变化：
		var arr=[1,2,3];
		arr[5]='x';
		arr;	//arr变为[1,2,3,undefined,undefined,'x']
	大多数其他编程语言不允许直接改变数组的大小，越界访问索引会报错。然而，JavaScript的Array却不会有任何错误。在编写代码时，不建议直接修改Array的大小，访问索引时要确保索引不会越界。

### 2、indexOf
	与String类似，Array也可以通过indexOf()来搜索一个指定的元素的位置：
	var arr=[10,20,'30','xys'];
	arr.indexOf(10);  //元素10的索引为0
	arr.indexOf(20);  //元素20的索引为1
	arr.indexOf(30);  //元素30没有找到，返回-1
	arr.indexOf('30'); //元素'30'的索引为2
	注意了，数字30和字符串'30'是不同的元素。

### 3、slince
   slice()就是对应String的subString版本，他截取Array的部分元素，然后返回一个新的Array
		var arr=['A','B','C','D','E','F'];
		arr.slice(0,3);			/// 从索引0开始，到索引3结束，但不包括索引3: ['A', 'B', 'C']
		arr.slice(3);			//从索引3开始到结束: ['D', 'E', 'F', 'G']
		var aCopy=arr.slice();   //如果不给slice()传递任何参数，他就会从头到尾截取所有元素。利用这一点，我们可以很容易复制一个数组。
### 4、push和pop
push()向Array的末尾添加若干元素，pop()则把Array的最后一个元素删除掉：
	var arr = [1, 2];
	arr.push('A', 'B'); // 返回Array新的长度: 4
	arr; // [1, 2, 'A', 'B']
	arr.pop(); // pop()返回'B'
	arr; // [1, 2, 'A']
	arr.pop(); arr.pop(); arr.pop(); // 连续pop 3次
	arr; // []
	arr.pop(); // 空数组继续pop不会报错，而是返回undefined
	arr; // []

### 5、unshift和shift
如果要往Array的头部添加若干元素，使用unshift()方法，shift()方法则把Array的第一个元素删掉：
	var arr = [1, 2];
	arr.unshift('A', 'B'); // 返回Array新的长度: 4
	arr; // ['A', 'B', 1, 2]
	arr.shift(); // 'A'
	arr; // ['B', 1, 2]
	arr.shift(); arr.shift(); arr.shift(); // 连续shift 3次
	arr; // []
	arr.shift(); // 空数组继续shift不会报错，而是返回undefined
	arr; // []

### 6、sort
sort()可以对当前Array进行排序，它会直接修改当前Array的元素位置，直接调用时，按照默认顺序排序：
	var arr = ['B', 'C', 'A'];
	arr.sort();
	arr; // ['A', 'B', 'C']
能否按照我们自己指定的顺序排序呢？完全可以，我们将在后面的函数中讲到。

### 7、reverse
reverse()把整个Array的元素给掉个个，也就是反转：
	var arr = ['one', 'two', 'three'];
	arr.reverse(); 
	arr; // ['three', 'two', 'one']

### 8、splice
splice()方法是修改Array的“万能方法”，它可以从指定的索引开始删除若干元素，然后再从该位置添加若干元素：
	var arr = ['Microsoft', 'Apple', 'Yahoo', 'AOL', 'Excite', 'Oracle'];
	// 从索引2开始删除3个元素,然后再添加两个元素:
	arr.splice(2, 3, 'Google', 'Facebook'); // 返回删除的元素 ['Yahoo', 'AOL', 'Excite']
	arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
	// 只删除,不添加:
	arr.splice(2, 2); // ['Google', 'Facebook']
	arr; // ['Microsoft', 'Apple', 'Oracle']
	// 只添加,不删除:
	arr.splice(2, 0, 'Google', 'Facebook'); // 返回[],因为没有删除任何元素
	arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']

### 9、concat
concat()方法把当前的Array和另一个Array连接起来，并返回一个新的Array：
	var arr = ['A', 'B', 'C'];
	var added = arr.concat([1, 2, 3]);
	added; // ['A', 'B', 'C', 1, 2, 3]
	arr; // ['A', 'B', 'C']
实际上，concat()方法可以接收任意个元素和Array，并且自动把Array拆开，然后全部添加到新的Array里：
	var arr = ['A', 'B', 'C'];
	arr.concat(1, 2, [3, 4]); // ['A', 'B', 'C', 1, 2, 3, 4]


### 10、join
join()方法是一个非常实用的方法，它把当前Array的每个元素都用指定的字符串连接起来，然后返回连接后的字符串：
	var arr = ['A', 'B', 'C', 1, 2, 3];
	arr.join('-'); // 'A-B-C-1-2-3'

### 11、多维数组
如果数组的某个元素又是一个Array，则可以形成多维数组，例如：
var arr = [[1, 2, 3], [400, 500, 600], '-'];


## 三、对象
JavaScript的对象是一种无序的集合数据类型，他由若干键值对组成。
JavaScript的对象用于描述现实世界中的某个对象。例如，为了描述“小明”这个淘气的小朋友，我们可以用若干键值对来描述他：
	var xiaoming={
		name:'小明',
		birth:1990,
		school:'No.1 Middle School',
		height:1.20,
		score:null
	};
JavaScript用一个{...}表示一个对象，键值对以xxx: xxx形式申明，用,隔开。注意，最后一个键值对不需要在末尾加,，如果加了，有的浏览器（如低版本的IE）将报错。
上述对象申明了一个name属性，值是'小明'，birth属性，值是1990，以及其他一些属性。最后，把这个对象赋值给变量xiaoming后，就可以通过变量xiaoming来获取小明的属性了：
	xiaoming.name;  //'小明'
	xiaoming.birth;	//1990
访问属性是通过.操作符完成的，但这要求属性名必须是一个有效的变量名。如果属性名包含特殊字符，就必须用''括起来：
	var xiaohong = {
    name: '小红',
    'middle-school': 'No.1 Middle School'
	};
xiaohong的属性名middle-school不是一个有效的变量，就需要用''括起来。访问这个属性也无法使用.操作符，必须用['xxx']来访问：
	xiaohong['middle-school']; // 'No.1 Middle School'
	xiaohong['name']; // '小红'
	xiaohong.name; // '小红'
也可以用xiaohong['name']来访问xiaohong的name属性，不过xiaohong.name的写法更简洁。我们在编写JavaScript代码的时候，属性名尽量使用标准的变量名，这样就可以直接通过object.prop的形式访问一个属性了。

实际上JavaScript对象的所有属性都是字符串，不过属性对应的值可以是任意数据类型。

如果访问一个不存在的属性会返回什么呢？JavaScript规定，访问不存在的属性不报错，而是返回undefined：
	var xiaoming={
		name:'小明'
	};
	xiaoming.age;  //undefined
由于JavaScript的对象是动态类型，你可以自由地给一个对象添加或删除属性：
	var xiaoming = {
		name: '小明'
	};
	xiaoming.age; // undefined
	xiaoming.age = 18; // 新增一个age属性
	xiaoming.age; // 18
	delete xiaoming.age; // 删除age属性
	xiaoming.age; // undefined
	delete xiaoming['name']; // 删除name属性
	xiaoming.name; // undefined
	delete xiaoming.school; // 删除一个不存在的school属性也不会报错
如果我们要检测xiaoming是否拥有某一属性，可以用in操作符：
	var xiaoming={
		name:'小明',
		birth:1999,
		school:'No.1 Middle School',
		height:1.7,
		weight:65,
		score:null
	};
	'name' in xiaoming; //true
	'grade' in xiaoming; //false
不过要小心，如果in判断一个属性存在，这个属性不一定是xiaoming的，它可能是xiaoming继承得到的：
	'toString' in xiaoming; //true
因为toString定义在object对象中，而所有对象最终都会在原型链上指向object，所以xiaoming也拥有toString属性。

要判断一个属性是否是xiaoming自身拥有的，而不是继承得到的，可以用hasOwnProperty()方法：
	var xiaoming={
		name:'小明'
	};
	xiaoming.hasOwnProperty('name');   //true
	xiaoming.hasOwnProperty('toString'); //false

## 四、条件判断

JavaScript使用if () { ... } else { ... }来进行条件判断。例如，根据年龄显示不同内容，可以用if语句实现如下：
	var age = 20;
	if (age >= 18) { // 如果age >= 18为true，则执行if语句块
		alert('adult');
	} else { // 否则执行else语句块
		alert('teenager');
	}
其中else语句是可选的。如果语句只包含一条语句，那么可以省略{}：
	
多行条件判断
	
## 五、循环

### 1、for(...;...;...){
}
JavaScript的循环有两种，一种是for循环，通过初始条件、结束条件和递增条件来循环执行语句块：
	var x = 1;
	var i;
	for(i=1;i<=10;i++){
		x=x*i;
	}
	
### 2、for ... in
for循环的一个变体是for ... in循环，它可以把一个对象的所有属性依次循环出来：
	var o = {
		name: 'Jack',
		age: 20,
		city: 'Beijing'
	};
	for (var key in o) {
		alert(key);  // 'name', 'age', 'city'
	}
要过滤掉对象继承的属性，用hasOwnProperty()来实现：
	var o = {
		name: 'Jack',
		age: 20,
		city: 'Beijing'
	};
	for (var key in o) {
		if (o.hasOwnProperty(key)) {
			alert(key); // 'name', 'age', 'city'
		}
	}
由于Array也是对象，而它的每个元素的索引被视为对象的属性，因此，for ... in循环可以直接循环出Array的索引：
	var a = ['A', 'B', 'C'];
	for (var i in a) {
		alert(i); // '0', '1', '2'
		alert(a[i]); // 'A', 'B', 'C'
	}
请注意，for ... in对Array的循环得到的是String而不是Number

### 3、while
for循环在已知循环的初始和结束条件时非常有用。而上述忽略了条件的for循环容易让人看不清循环的逻辑，此时用while循环更佳。

while循环只有一个判断条件，条件满足，就不断循环，条件不满足时则退出循环。比如我们要计算100以内所有奇数之和，可以用while循环实现：
	var x=0;
	var n=99;
	while(n>0){
		x=x+n;
		n=n-2;
	}

### 4、do ... while
最后一种循环是do { ... } while()循环，它和while循环的唯一区别在于，不是在每次循环开始的时候判断条件，而是在每次循环完成的时候判断条件：
	var n = 0;
	do {
		n = n + 1;
	} while (n < 100);
	n; // 100
用do { ... } while()循环要小心，循环体会至少执行1次，而for和while循环则可能一次都不执行。
	
	
## 六、Map和Set
JavaScript的默认对象表示方式{}可以视为其他语言中的Map或Dictionary的数据结构，即一组键值对

但是JavaScript的对象有个小问题，就是键必须是字符串。但实际上Number或者其他数据类型作为键也是非常合理的。

为了解决这个问题，最新的ES6规范引入了新的数据类型Map。要测试你的浏览器是否支持ES6规范，请执行以下代码，如果浏览器报ReferenceError错误，那么你需要换一个支持ES6的浏览器：
	
### 1、Map
Map是一组键值对的结构，具有极快的查找速度。
	
举个例子，假设要根据同学的名字查找对应的成绩，如果用Array实现，需要两个Array：

	var names = ['Michael', 'Bob', 'Tracy'];
	var scores = [95, 75, 85];
给定一个名字，要查找对应的成绩，就先要在names中找到对应的位置，再从scores取出对应的成绩，Array越长，耗时越长。

如果用Map实现，只需要一个“名字”-“成绩”的对照表，直接根据名字查找成绩，无论这个表有多大，查找速度都不会变慢。用JavaScript写一个Map如下：

	var m = new Map([['Michael', 95], ['Bob', 75], ['Tracy', 85]]);
	m.get('Michael'); // 95	
	
初始化Map需要一个二维数组，或者直接初始化一个空Map。Map具有以下方法：
	var m = new Map(); // 空Map
	m.set('Adam', 67); // 添加新的key-value
	m.set('Bob', 59);
	m.has('Adam'); // 是否存在key 'Adam': true
	m.get('Adam'); // 67
	m.delete('Adam'); // 删除key 'Adam'
	m.get('Adam'); // undefined
由于一个key只能对应一个value，所以，多次对一个key放入value，后面的值会把前面的值冲掉：
	var m = new Map();
	m.set('Adam', 67);
	m.set('Adam', 88);
	m.get('Adam'); // 88

### 2、Set
Set和Map类似，也是一组key的集合，但不存储value。由于key不能重复，所以，在Set中，没有重复的key。

要创建一个Set，需要提供一个Array作为输入，或者直接创建一个空Set：

	var s1 = new Set(); // 空Set
	var s2 = new Set([1, 2, 3]); // 含1, 2, 3
	
重复元素在Set中自动被过滤：
	var s = new Set([1, 2, 3, 3, '3']);
	s; // Set {1, 2, 3, "3"}
	
注意数字3和字符串'3'是不同的元素。

通过add(key)方法可以添加元素到Set中，可以重复添加，但不会有效果：
	s.add(4)
	s
	{1, 2, 3, 4}
	s.add(4)
	s
	{1, 2, 3, 4}
通过delete(key)方法可以删除元素：
	var s=new Set([1,2,3]);
	s;  //Set{1,2,3}
	s.delete(3);
	s;  //Set{1,2}
对于Set集合使用for of来遍历set集合
	var s=new Set();
	s.add("asdasdasd");
	s.add(12312);
	var str="asdasd";
	s.add(str);
	for(var item of s){
		alert(item);
	};
	
##　七、iterable便利集合
遍历Array可以采用下标循环，遍历Map和Set就无法使用下标。为了统一集合类型，ES6标准引入了新的iterable类型，Array、Map和Set都属于iterable类型。

具有iterable类型的集合可以通过新的for ... of循环来遍历。
	
用for ... of循环遍历集合，用法如下：
	
	var a = ['A', 'B', 'C'];
	var s = new Set(['A', 'B', 'C']);
	var m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
	for (var x of a) { // 遍历Array
		alert(x);
	}
	for (var x of s) { // 遍历Set
		alert(x);
	}
	for (var x of m) { // 遍历Map
		alert(x[0] + '=' + x[1]);
	}
更好的方式是直接使用iterable内置的forEach方法，它接收一个函数，每次迭代就自动回调该函数(for...of)。以Array为例：
	var a = ['A', 'B', 'C'];
	a.forEach(function (element, index, array) {
		// element: 指向当前元素的值
		// index: 指向当前索引
		// array: 指向Array对象本身
		alert(element);
	});

Set与Array类似，但Set没有索引，因此回调函数的前两个参数都是元素本身：
	var s = new Set(['A', 'B', 'C']);
	s.forEach(function (element, sameElement, set) {
		alert(element);
	});
Map的回调函数参数依次为value、key和map本身：
	var m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
	m.forEach(function (value, key, map) {
		alert(value);
	});
如果对某些参数不感兴趣，由于JavaScript的函数调用不要求参数必须一致，因此可以忽略它们。例如，只需要获得Array的element：
var a = ['A', 'B', 'C'];
a.forEach(function (element) {
    alert(element);
});


## 函数：

### 1、定义函数
在JavaScript中，定义函数的方式如下：
	function abs(x) {
		if (x >= 0) {
			return x;
		} else {
			return -x;
		}
	}
上述abs()函数的定义如下：
	function指出这是一个函数定义；
	abs是函数的名称；
	(x)括号内列出函数的参数，多个参数以,分隔；
	{ ... }之间的代码是函数体，可以包含若干语句，甚至可以没有任何语句。

请注意，函数体内部的语句在执行时，一旦执行到return时，函数就执行完毕，并将结果返回。因此，函数内部通过条件判断和循环可以实现非常复杂的逻辑。

如果没有return语句，函数执行完毕后也会返回结果，只是结果为undefined。

由于JavaScript的函数也是一个对象，上述定义的abs()函数实际上是一个函数对象，而函数名abs可以视为指向该函数的变量。

因此，第二种定义函数的方式如下：

	var abs = function (x) {
		if (x >= 0) {
			return x;
		} else {
			return -x;
		}
	};
在这种方式下，function (x) { ... }是一个匿名函数，它没有函数名。但是，这个匿名函数赋值给了变量abs，所以，通过变量abs就可以调用该函数。

上述两种定义完全等价，注意第二种方式按照完整语法需要在函数体末尾加一个;，表示赋值语句结束。


### 2、调用函数

调用函数时，按顺序传入参数即可：

abs(10); // 返回10
abs(-9); // 返回9
由于JavaScript允许传入任意个参数而不影响调用，因此传入的参数比定义的参数多也没有问题，虽然函数内部并不需要这些参数：

abs(10, 'blablabla'); // 返回10
abs(-9, 'haha', 'hehe', null); // 返回9
传入的参数比定义的少也没有问题：

abs(); // 返回NaN

此时abs(x)函数的参数x将收到undefined，计算结果为NaN。

要避免收到undefined，可以对参数进行检查：
	function abs(x) {
		if (typeof x !== 'number') {
			throw 'Not a number';
		}
		if (x >= 0) {
			return x;
		} else {
			return -x;
		}
	}

### 3、arguments
JavaScript还有一个免费赠送的关键字arguments，它只在函数内部起作用，并且永远指向当前函数的调用者传入的所有参数。arguments类似Array但它不是一个Array：
	function foo(x) {
		alert(x); // 10
		for (var i=0; i<arguments.length; i++) {
			alert(arguments[i]); // 10, 20, 30
		}
	}
	foo(10, 20, 30);
利用arguments，你可以获得调用者传入的所有参数。也就是说，即使函数不定义任何参数，还是可以拿到参数的值：

### 4、变量作用域

在JavaScript中，用var申明的变量实际上是有作用域的。

如果一个变量在函数体内部申明，则该变量的作用域为整个函数体，在函数体外不可引用该变量：
	'use strict';
	function foo() {
		var x = 1;
		x = x + 1;
	}
	x = x + 2; // ReferenceError! 无法在函数体外引用变量x

如果两个不同的函数各自申明了同一个变量，那么该变量只在各自的函数体内起作用。换句话说，不同函数内部的同名变量互相独立，互不影响：

由于JavaScript的函数可以嵌套，此时，内部函数可以访问外部函数定义的变量，反过来则不行

	'use strict';

	function foo() {
		var x = 1;
		function bar() {
			var y = x + 1; // bar可以访问foo的变量x!
		}
		var z = y + 1; // ReferenceError! foo不可以访问bar的变量y!
	}

### 全局作用域：

不在任何函数内定义的变量就具有全局作用域。实际上，JavaScript默认有一个全局对象window，
全局作用域的变量实际上被绑定到Window的一个属性：
	'use strict';

	var course = 'Learn JavaScript';
	alert(course); // 'Learn JavaScript'
	alert(window.course); // 'Learn JavaScript'
因此，直接访问全局变量course和访问window.course是完全一样的。
	'use strict';

	function foo() {
		alert('foo');
	}
	
	foo(); // 直接调用foo()
	window.foo(); // 通过window.foo()调用

这说明JavaScript实际上只有一个全局作用域。任何变量（函数也视为变量），如果没有在当前函数作用域中找到，就会继续往上查找，
最后如果在全局作用域中也没有找到，则报ReferenceError错误。

方法：

在一个对象中绑定函数，称为这个对象的方法。
在JavaScript中，对象的定义是这样的
	var xiaoming={
		name:'小明',
		birth:1995
	};
但是，如果我们给xiaoming绑定一个函数，就可以做更多的事情。比如，写个age()方法，返回xiaoming的年龄：
	var xiaoming = {
		name: '小明',
		birth: 1990,
		age: function () {
			var y = new Date().getFullYear();
			return y - this.birth;
		}
	};

	xiaoming.age; // function xiaoming.age()
	xiaoming.age(); // 今年调用是25,明年调用就变成26了
绑定到对象上的函数称为方法，和普通函数也没啥区别.
在一个方法内部，this是一个特殊变量，它始终指向当前对象，也就是xiaoming这个变量。所以，this.birth可以拿到xiaoming的birth属性。

### 高阶函数：

高阶函数英文叫Higher-order function。那么什么是高阶函数？
JavaScript的函数其实都指向某个变量。既然变量可以指向函数，函数的参数能接收变量，
那么一个函数就可以接收另一个函数作为参数，这种函数就称之为高阶函数。
	function add(x, y, f) {
		return f(x) + f(y);
	}

1、map
比如我们有一个函数f(x)=x2，要把这个函数作用在一个数组[1, 2, 3, 4, 5, 6, 7, 8, 9]上，
就可以用map实现如下：[1,4,9,25,36,49,64,81];

由于map()方法定义在JavaScript的Array中，我们调用Array的map()方法，传入我们自己的函数，就得到了一个新的Array作为结果：

	function pow(x) {
		return x * x;
	}

	var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
	arr.map(pow); // [1, 4, 9, 16, 25, 36, 49, 64, 81]

map()传入的参数是pow，即函数对象本身。
所以，map()作为高阶函数，事实上它把运算规则抽象了，因此，我们不但可以计算简单的f(x)=x2，还可以计算任意复杂的函数，比如，把Array的所有数字转为字符串：

	var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
	arr.map(String); // ['1', '2', '3', '4', '5', '6', '7', '8', '9']
只需要一行代码。

2、reduce
再看reduce的用法。Array的reduce()把一个函数作用在这个Array的[x1, x2, x3...]上，这个函数必须接收两个参数，
reduce()把结果继续和序列的下一个元素做累积计算，其效果就是：
	[x1, x2, x3, x4].reduce(f) = f(f(f(x1, x2), x3), x4)
比方说对一个Array求和，就可以用reduce实现：
	var arr = [1, 3, 5, 7, 9];
	var sum=arr.reduce(function (x, y) {
		return x + y;
	}); // 25
	alert(sum);  //输出求和数据
	

将一个字符串转换为数字：
	'use strict'
	var s='12';
	alert(typeof s);	//string
	var d=+s;
	alert(typeof d);	//number
	
3、filter
filter也是一个常用的操作，它用于把Array的某些元素过滤掉，然后返回剩下的元素。

和map()类似，Array的filter()也接收一个函数。和map()不同的是，filter()把传入的函数依次作用于每个元素，
然后根据返回值是true还是false决定保留还是丢弃该元素。

例如，在一个Array中，删掉偶数，只保留奇数，可以这么写：
	var arr = [1, 2, 4, 5, 6, 9, 10, 15];
	var r = arr.filter(function (x) {
		return x % 2 !== 0;
	});
	r; // [1, 5, 9, 15]


把一个Array中的空字符串删掉，可以这么写：

4、sort 排序算法
排序算法

排序也是在程序中经常用到的算法。无论使用冒泡排序还是快速排序，排序的核心是比较两个元素的大小。
如果是数字，我们可以直接比较，但如果是字符串或者两个对象呢？直接比较数学上的大小是没有意义的，
因此，比较的过程必须通过函数抽象出来。通常规定，对于两个元素x和y，如果认为x < y，则返回-1，
如果认为x == y，则返回0，如果认为x > y，则返回1，这样，排序算法就不用关心具体的比较过程，而是根据比较结果直接排序。

sort()方法也是一个高阶函数，它还可以接收一个比较函数来实现自定义的排序。
要按数字大小排序，我们可以这么写：
	var arr = [10, 20, 1, 2];
	arr.sort(function (x, y) {
		if (x < y) {
			return -1;
		}
		if (x > y) {
			return 1;
		}
		return 0;
	}); // [1, 2, 10, 20]
如果要倒序排序，我们可以把大的数放前面：
	var arr = [10, 20, 1, 2];
	arr.sort(function (x, y) {
		if (x < y) {
			return 1;
		}
		if (x > y) {
			return -1;
		}
		return 0;
	}); // [20, 10, 2, 1]

默认情况下，对字符串排序，是按照ASCII的大小比较的，现在，我们提出排序应该忽略大小写，
按照字母序排序。要实现这个算法，不必对现有代码大加改动，只要我们能定义出忽略大小写的比较算法就可以：
	var arr = ['Google', 'apple', 'Microsoft'];
	arr.sort(function (s1, s2) {
		x1 = s1.toUpperCase();
		x2 = s2.toUpperCase();
		if (x1 < x2) {
			return -1;
		}
		if (x1 > x2) {
			return 1;
		}
		return 0;
	}); // ['apple', 'Google', 'Microsoft']
	
忽略大小写来比较两个字符串，实际上就是先把字符串都变成大写（或者都变成小写），再比较。
从上述例子可以看出，高阶函数的抽象能力是非常强大的，而且，核心代码可以保持得非常简洁。
最后友情提示，sort()方法会直接对Array进行修改，它返回的结果仍是当前Array：

## 闭包

### 1、函数作为返回值
高阶函数除了可以接受函数作为参数外，还可以把函数作为结果值返回。

我们来实现一个对Array的求和。通常情况下，求和的函数是这样定义的：

	function sum(arr) {
		return arr.reduce(function (x, y) {
			return x + y;
		});
	}

	sum([1, 2, 3, 4, 5]); // 15

但是，如果不需要立刻求和，而是在后面的代码中，根据需要再计算怎么办？可以不返回求和的结果，而是返回求和的函数！
	function lazy_sum(arr) {
		var sum = function () {
			return arr.reduce(function (x, y) {
				return x + y;
			});
		}
		return sum;
	}
当我们调用lazy_sum()时，返回的并不是求和结果，而是求和函数：
	var f = lazy_sum([1, 2, 3, 4, 5]); // function sum()
调用函数f时，才真正计算求和的结果：
	f(); // 15
在这个例子中，我们在函数lazy_sum中又定义了函数sum，并且，内部函数sum可以引用外部函数lazy_sum的参数和局部变量，当lazy_sum返回函数sum时，相关参数和变量都保存在返回的函数中，这种称为“闭包（Closure）”的程序结构拥有极大的威力。

请再注意一点，当我们调用lazy_sum()时，每次调用都会返回一个新的函数，即使传入相同的参数：

var f1 = lazy_sum([1, 2, 3, 4, 5]);
var f2 = lazy_sum([1, 2, 3, 4, 5]);
f1 === f2; // false


箭头函数：

generator

标准对象
在JavaScript的世界里，一切都是对象。

但是某些对象还是和其他对象不太一样。为了区分对象的类型，我们用typeof操作符来获取对象的数据类型
他总是返回一个字符串。
	typeof 123; // 'number'
	typeof NaN; // 'number'
	typeof 'str'; // 'string'
	typeof true; // 'boolean'
	typeof undefined; // 'undefined'
	typeof Math.abs; // 'function'
	typeof null; // 'object'
	typeof []; // 'object'
	typeof {}; // 'object'
可见，number、string、boolean、function和undefined有别于其他类型。特别注意null的类型是object，
Array的类型也是object，如果我们用typeof将无法区分出null、Array和通常意义上的object——{}。


### 有几条规则需要遵守：
1、不要使用new Number()、new Boolean()、new String()创建包装对象。
2、用parseInt()或parseFloat()来转换任意类型到number；
3、用String()来转换任意类型到string，或者直接调用某个对象的toString()方法；
4、通常不必把任意类型的转换为boolean再判断，因为可以直接写if(myVar){...};
5、typeof操作符可以判断出number、boolean、string、function和undefined;
6、判断Array要使用Array.isArray(arr);
7、判断null请使用myVar === null
8、判断某个全局变量是否存在用typeof window.myVar === 'underfined';
9、函数内部判断某个变量是否存在用typeof myVar ==='underfined';


### Date:
在JavaScript中，Date对象用来表示日期和时间。
要获取系统当前时间，用：
	var now = new Date();
	now; // Wed Jun 24 2015 19:49:22 GMT+0800 (CST)
	now.getFullYear(); // 2015, 年份
	now.getMonth(); // 5, 月份，注意月份范围是0~11，5表示六月
	now.getDate(); // 24, 表示24号
	now.getDay(); // 3, 表示星期三
	now.getHours(); // 19, 24小时制
	now.getMinutes(); // 49, 分钟
	now.getSeconds(); // 22, 秒
	now.getMilliseconds(); // 875, 毫秒数
	now.getTime(); // 1435146562875, 以number形式表示的时间戳
	
注意，当前时间是浏览器从本机操作系统获取的时间，所以不一定准确，因为用户可以把当前时间设定为任何值。

如果要创建一个指定日期和时间的Date对象，可以用：
	var d = new Date(2015, 5, 19, 20, 15, 30, 123);
	d; // Fri Jun 19 2015 20:15:30 GMT+0800 (CST)
你可能观察到了一个非常非常坑爹的地方，就是JavaScript的月份范围用整数表示是0~11，
0表示一月，1表示二月……，所以要表示6月，我们传入的是5！这绝对是JavaScript的设计者当时脑抽了一下，
但是现在要修复已经不可能了。


### 时区：
Date对象表示的时间总是按浏览器所在时区显示的，不过我们既可以显示本地时间，
也可以显示调整后的UTC时间：
	var d = new Date(1435146562875);
	d.toLocaleString(); // '2015/6/24 下午7:49:22'，本地时间（北京时区+8:00），显示的字符串与操作系统设定的格式有关
	d.toUTCString(); // 'Wed, 24 Jun 2015 11:49:22 GMT'，UTC时间，与本地时间相差8小时
时间戳是一个自增的整数，它表示从1970年1月1日零时整的GMT时区开始的那一刻，到现在的毫秒数。假设浏览器所在电脑的时间是准确的，那么世界上无论哪个时区的电脑，它们此刻产生的时间戳数字都是一样的，所以，时间戳可以精确地表示一个时刻，并且与时区无关。
所以，我们只需要传递时间戳，或者把时间戳从数据库里读出来，再让JavaScript自动转换为当地时间就可以了。
要获取当前时间戳，可以用：


### RegExp：
字符串是编程时涉及到的最多的一种数据结构，对字符串进行操作的需求几乎无处不在。比如判断一个字符串是否是合法的Email地址，
虽然可以编程提取@前后的子串，在分别判断是否是单词和域名，但这样做不但麻烦，而且代码难以复用。

正则表达式是一种用来匹配字符串的强有力的武器。他的设计思想是用一种描述性的语言来给字符串定义一个规则。
凡是符合规则的字符串，我们就认为他“匹配”了，否则，该字符串就是不合法的。

所以我们判断一个字符串是否是合法的Email的方法是：
	1、创建一个匹配Email的正则表达式；
	2、用该正则表达式去匹配用户的输入来判断是否合法。
因为正则表达式也是用字符串表示的，所以，我们要首先了解如何用字符串来描述字符。
在正则表达式中，如何直接给出字符，就是精确匹配。
 用\d可以匹配一个数字，\w可以匹配一个字符或数字，所以：
     '00\d' 可以匹配 '007'，但是无法匹配'00A';
	 '\d\d\d'可以匹配'010';
	 '\w\w'可以匹配'js'
 .可以匹配'jsp'、'jss'、'js!'等等。
	 'js.'可以匹配'jsp'、'jss'、'js!'等等。
 要匹配边长的字符，在正则表达式中，可以用*表示任意个（包括0个），用+表示至少一个字符，
用?表示0个或1个字符，用{n}表示n个字符，用{n,m}表示n-m个字符：
来看一个复杂的例子：
	  \d{3}\s+\d{3,8}。

我们来从左到右解读一下：
\d{3}表示匹配3个数字，例如'010'；
\s可以匹配一个空格（也包括Tab等空白符），所以\s+表示至少有一个空格，例如匹配' '，'\t\t'等；
\d{3,8}表示3-8个数字，例如'1234567'。
综合起来，上面的正则表达式可以匹配以任意个空格隔开的带区号的电话号码。
如果要匹配'010-12345'这样的号码呢？由于'-'是特殊字符，在正则表达式中，要用'\'转义，所以，上面的正则是
       \d{3}\-\d{3,8}。


### 进阶：：
要做更精确地匹配，可以用[]表示范围，比如：
		[0-9a-zA-Z\_]	可以匹配一个数字、字母或者下划线；
		[0-9a-zA-Z\_]+	可以匹配至少由一个数字、字母或者下划线组成的字符串，比如'a100'，'0_Z'，'js2015'等等；
		[a-zA-Z\_\$][0-9a-zA-Z\_\$]*	可以匹配由字母或下划线、$开头，后接任意个由一个数字、字母或者下划线、$组成的字符串，
		                                 也就是JavaScript允许的变量名；
		[a-zA-Z\_\$][0-9a-zA-Z\_\$]{0, 19}		更精确地限制了变量的长度是1-20个字符（前面1个字符+后面最多19个字符）。	
		A|B		可以匹配A或B，所以(J|j)ava(S|s)cript可以匹配'JavaScript'、'Javascript'、'javaScript'或者'javascript'
		^表示行的开头，^\d表示必须以数字开头。
		$表示行的结束，\d$表示必须以数字结束。
		
### JavaScript有两种方式创建一个正则表达式：

第一种方式是直接通过/正则表达式/写出来，
第二种方式是通过new RegExp('正则表达式')创建一个RegExp对象。
		var re1 = /ABC\-001/;
		var re2 = new RegExp('ABC\\-001');

		re1; // /ABC\-001/
		re2; // /ABC\-001/
		注意，如果使用第二种写法，因为字符串的转义问题，字符串的两个\\实际上是一个\
		var re = /^\d{3}\-\d{3,8}$/;
		re.test('010-12345'); // true
		re.test('010-1234x'); // false
		re.test('010 12345'); // false
		
RegExp对象的test()方法用于测试给定的字符串是否符合条件。

	
### 切分字符串
用正则表达式切分字符串比用固定的字符更灵活，请看正常的切分代码：
		'a b   c'.split(' '); // ['a', 'b', '', '', 'c']
嗯，无法识别连续的空格，用正则表达式试试：
		'a b   c'.split(/\s+/); // ['a', 'b', 'c']
无论多少个空格都可以正常分割。加入,试试：
		'a,b, c  d'.split(/[\s\,]+/); // ['a', 'b', 'c', 'd']
再加入;试试：
		'a,b;; c  d'.split(/[\s\,\;]+/); // ['a', 'b', 'c', 'd']
		
	
### 分组：
除了简单地判断是否匹配之外，正则表达式还有提取子串的强大功能。用()表示的就是要提取的分组（Group）。比如：

^(\d{3})-(\d{3,8})$分别定义了两个组，可以直接从匹配的字符串中提取出区号和本地号码：
		var re = /^(\d{3})-(\d{3,8})$/;
		re.exec('010-12345'); // ['010-12345', '010', '12345']
		re.exec('010 12345'); // null
如果正则表达式中定义了组，就可以在RegExp对象上用exec()方法提取出子串来。

exec()方法在匹配成功后，会返回一个Array，第一个元素是正则表达式匹配到的整个字符串，后面的字符串表示匹配成功的子串。

exec()方法在匹配失败时返回null。

提取子串非常有用。来看一个更凶残的例子：
		var re = /^(0[0-9]|1[0-9]|2[0-3]|[0-9])
					\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])
					\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])$/;
		re.exec('19:05:30'); // ['19:05:30', '19', '05', '30']


### 贪婪匹配
需要特别指出的是，正则匹配默认是贪婪匹配，也就是匹配尽可能多的字符。举例如下，匹配出数字后面的0：
		var re = /^(\d+)(0*)$/;
		re.exec('102300'); // ['102300', '102300', '']
由于\d+采用贪婪匹配，直接把后面的0全部匹配了，结果0*只能匹配空字符串了。
必须让\d+采用非贪婪匹配（也就是尽可能少匹配），才能把后面的0匹配出来，加个?就可以让\d+采用非贪婪匹配：
		var re = /^(\d+?)(0*)$/;
		re.exec('102300'); // ['102300', '1023', '00']


### 全局搜索
JavaScript的正则表达式还有几个特殊的标志，最常用的是g，表示全局匹配：
		var r1 = /test/g;
		// 等价于:
		var r2 = new RegExp('test', 'g');
全局匹配可以多次执行exec()方法来搜索一个匹配的字符串。当我们指定g标志后，每次运行exec()，正则表达式本身会更新lastIndex属性，表示上次匹配到的最后索引：
		var s = 'JavaScript, VBScript, JScript and ECMAScript';
		var re=/[a-zA-Z]+Script/g;

		// 使用全局匹配:
		re.exec(s); // ['JavaScript']
		re.lastIndex; // 10

		re.exec(s); // ['VBScript']
		re.lastIndex; // 20

		e.exec(s); // ['JScript']
		re.lastIndex; // 29

		re.exec(s); // ['ECMAScript']
		re.lastIndex; // 44

		re.exec(s); // null，直到结束仍没有匹配到
	
	
### JSON
		
JSON是JavaScript Object Notation的缩写，它是一种数据交换格式。

在JSON出现之前，大家一直用XML来传递数据。因为XML是一种纯文本格式，所以它适合在网络上交换数据。XML本身不算复杂，
但是，加上DTD、XSD、XPath、XSLT等一大堆复杂的规范以后，任何正常的软件开发人员碰到XML都会感觉头大了，最后大家发现，
即使你努力钻研几个月，也未必搞得清楚XML的规范。

终于，在2002年的一天，道格拉斯·克罗克福特（Douglas Crockford）同学为了拯救深陷水深火热同时又被某几个巨型软件企业长期愚弄的软件工程师，发明了JSON这种超轻量级的数据交换格式。

道格拉斯同学长期担任雅虎的高级架构师，自然钟情于JavaScript。他设计的JSON实际上是JavaScript的一个子集。
在JSON中，一共就这么几种数据类型：

	number：和JavaScript的number完全一致；
	boolean：就是JavaScript的true或false；
	string：就是JavaScript的string；
	null：就是JavaScript的null；
	array：就是JavaScript的Array表示方式——[]；
	object：就是JavaScript的{ ... }表示方式。
以及上面的任意组合。

并且，JSON还定死了字符集必须是UTF-8，表示多语言就没有问题了。
为了统一解析，JSON的字符串规定必须用双引号""，Object的键也必须用双引号""。
由于JSON非常简单，很快就风靡Web世界，并且成为ECMA标准。几乎所有编程语言都有解析JSON的库，
而在JavaScript中，我们可以直接使用JSON，因为JavaScript内置了JSON的解析。

把任何JavaScript对象变成JSON，就是把这个对象序列化成一个JSON格式的字符串，这样才能够通过网络传递给其他计算机。

如果我们收到一个JSON格式的字符串，只需要把它反序列化成一个JavaScript对象，就可以在JavaScript中直接使用这个对象了。
		
		
		
		
### 面向对象编程
JavaScript的所有数据都可以看成对象，	
		那是不是我们已经在使用面向对象编程了呢？
当然不是。如果我们只使用Number、Array、string以及基本的{...}定义的对象，还无法发挥出面向对象编程的威力。
JavaScript的面向对象编程和大多数其他语言如Java、C#的面向对象编程都不太一样。如果你熟悉Java或C#，
很好，你一定明白面向对象的两个基本概念：
	类：类是对象的类型模板，例如，定义Student类来表示学生，类本身是一种类型，Student表示学生类型，但不表示任何具体的某个学生；	实例：实例是根据类创建的对象，例如，根据Student类可以创建出xiaoming、xiaohong、xiaojun等多个实例，
		每个实例表示一个具体的学生，他们全都属于Student类型。
所以，类和实例是大多数面向对象编程语言的基本概念。
不过，在JavaScript中，这个概念需要改一改。JavaScript不区分类和实例的概念，而是通过原型（prototype）来实现面向对象编程。
原型是指当我们想要创建xiaoming这个具体的学生时，我们并没有一个Student类型可用。那怎么办？恰好有这么一个现成的对象：
	var robot = {
		name: 'Robot',
		height: 1.6,
		run: function () {
			console.log(this.name + ' is running...');
		}
	};
我们看这个robot对象有名字，有身高，还会跑，有点像小明，干脆就根据它来“创建”小明得了！
于是我们把它改名为Student，然后创建出xiaoming：
		var Student = {
			name: 'Robot',
			height: 1.2,
			run: function () {
				console.log(this.name + ' is running...');
			}
		};
		var xiaoming = {
			name: '小明'
		};
		xiaoming.__proto__ = Student;
注意最后一行代码把xiaoming的原型指向了对象Student，看上去xiaoming仿佛是从Student继承下来的：

xiaoming.name; // '小明'
xiaoming.run(); // 小明 is running...
xiaoming有自己的name属性，但并没有定义run()方法。不过，由于小明是从Student继承而来，只要Student有run()方法，xiaoming也可以调用：
avaScript的原型链和Java的Class区别就在，它没有“Class”的概念，所有对象都是实例，所谓继承关系不过是把一个对象的原型指向另一个对象而已。
如果你把xiaoming的原型指向其他对象：
		
	var Bird = {
		fly: function () {
			console.log(this.name + ' is flying...');
		}
	};
	xiaoming.__proto__ = Bird;

现在xiaoming已经无法run()了，他已经变成了一只鸟：

	xiaoming.fly(); // 小明 is flying...


	
	
	

			
			
			




