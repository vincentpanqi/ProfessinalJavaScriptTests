vaScript高级程序设计》笔记

Tags: StudyNotes

---
# JavaScript简介
## JavaScript名字的由来
布兰登*艾奇为Netscape的Navigator 2开发脚本语言，起名LiveScript，后因跟Sun公司合作开发，临时起名JavaScript,搭了Java的顺风车。

## 完整的JavaScript的实现由以下三个部分组成：
	- 核心（ECMAScript）
		- 文档对象模型（DOM）
			- 浏览器对象模型（BOM）

			## ECMAScript
			它规定了JavaScript的下列组成部分   

			- 语法
			- 类型
			- 语句
			- 关键字
			- 保留字
			- 操作符
			- 对象

			ECMAScript是由欧洲计算机制造协会（ECMA European  Computer Manufactures Association）制定的一种新脚本语言的标准。
			ECMAScript 与WEB浏览器没有依赖关系，WEB浏览器只是ECMAScript常见的**宿主环境**之一，其他的宿主环境还有Node（一种服务端JavaScript平台）和Adobe Flash。
			IE9完整的实现了对ECMA-262的支持，Firefox 4也紧随其后做到了兼容。

			## DOM
			DOM是针对XML但经过扩展用于HTML的应用程序变成接口。
			- DOM标准的出现
			Netscape和微软在开发DHTML方面各抒己见，如果不对他们进行控制，Web开发领域将会出现技术上的两强割据，浏览器之间互不兼容的局面，此时，负责制定Web通信标准的W3C（World Wide Web Consortium,万维网联盟）开始着手规划DOM。

			##BOM
			即可以访问和操作浏览器窗口的浏览器对象模型（Brouser Object Model）。
			但是它作为Javascript的一部分却没有相关的标准，这个问题在HTML5中得到了解决，HTML5发布后，很多关于BOM的困惑将烟消云散。
			从根本上讲，BOM只处理浏览器窗口和框架，但人们习惯把所有针对浏览器的所有JavaScript的扩展都算作BOM的一部分，如下面的一些扩展：
			- 弹出新浏览器窗口的功能
			- 移动、缩放和关闭浏览器窗口的功能
			- 提供浏览器详细信息的navigator对象
			- 提供浏览器所夹在页面详细信息的location对象
			- 提供用户显示器分辨率详细信息的screen对象
			- 对cookies的支持
			-想XMLHttpRequest和IE的ActiveXObject这样的自定义对象
			虽然这方面没有标准，但HTML5的出现会将


			# 在HTML中使用JavaScript
			---
			## <script>元素
			有一下6个属性，但都是可选的：
			- async：表示应该立即下载脚本，但不妨碍页面的其他操作。只对外部脚本有效，即先夹在外部脚本，再夹在内部html
			- charset：大多数浏览器会忽略它的值！
			- defer： 延迟夹在javascript，也是只对外部脚本有效。
			- language:已废弃。
			- src
			- type：如果不写这个属性，其默认仍为“text/javascript”。

			注意：当浏览器遇到字符串“</script>”时，就会认为那是结束标签，因此下面的语法是错误的：

			```
			         <script>
					              function(){
								                   alert("</script>");
												               }
															             </script>

																		 ```

																		 - 解决加载js时浏览器出现的一片空白现象
																		 对于很多JavaScript代码的页面来说，无疑会导致浏览器在呈现页面时出现明显的延迟，为了避免这个问题，现代Web应用程序一般都会把全部的JS引用放在`<body>`元素中页面内容的后面。如：
																		 ```
																		 <body>
																		 	<!--这里放内容-->
																				.....
																					<script src="example1.js"></script>
																						<script src="example2.js"></script>
																						</body>
																						```

																						##异步脚本


																						#变量、作用域和内存管理
																						##基本类型和引用类型的值
																						ECMAScript 变量可能包含两种不同数据类型的值:**基本类型值**和**引用类型值**。
																						基本类型值指的是简单的数据段,而引用类型值指那些可能由多个值构成的对象5种基本数据类型:Undefined、Null、Boolean、Number 和 String。这 5 种基本数据类型是按值访问的,因为可以操作保存在变量中的实际的值。
																						引用类型的值是保存在内存中的对象。与其他语言不同,JavaScript 不允许直接访问内存中的位置,也就是说不能直接操作对象的内存空间。在操作对象时,实际上是在操作对象的引用而不是实际的对象。为此,引用类型的值是按引用访问的 。

																						> 注：字符串是以基本类型存储的。

																						###复制变量值
																						基本类型是复制并创建一个新值
																						引用类型是使用引用

																						###传递参数
																						ECMAScript 中所有函数的参数都是按值传递的。

																						###检测类型
																						typeof 操作符是确定一个变量是字符串、数值、布尔值,还是 undefined 的最佳工具。
																						虽然在检测基本数据类型时 typeof 是非常得力的助手,但在检测引用类型的值时,这个操作符的用处不大。通常,我们并不是想知道某个值是对象,而是想知道它是什么类型的对象。为此,ECMAScript提供了 instanceof 操作符,

																						```
																						alert(person instanceof Object);// 变量 person 是 Object 吗?
																						alert(colors instanceof Array);// 变量 colors 是 Array 吗?
																						alert(pattern instanceof RegExp);// 变量 pattern 是 RegExp 吗?
																						```
																						> 注：所有引用类型的值都是 Object 的实例。

																						## 执行环境和作用域
																						每个执行环境都有一个与之关联的**变量对象**(variable object)
																						,环境中定义的所有变量和函数都保存在这个对象中。*虽然我们编写的代码无法访问这个对象,但解析器在处理数据时会在后台使用它。*    
																						全局执行环境是最外围的一个执行环境

																						### 没有块级作用域
																						```
																						for (var i=0; i < 10; i++){
																						doSomething(i);
																						}
																						alert(i);   //10

																						```
																						### 声明变量的作用域
																						使用 var 声明的变量会自动被添加到最接近的环境中，如果初始化变量时没有使用 var 声明,该变量会自动被添加到全局环境。
																						例如下面的代码会出错：
																						```
																						function add(num1, num2) {
																						var sum = num1 + num2;
																						return sum;
																						}
																						var result = add(10, 20); //30
																						alert(sum);
																						//由于 sum 不是有效的变量,因此会导致错误

																						```
																						而下面的代码可以正确输出：
																						```
																						function add(num1, num2) {
																						sum = num1 + num2;
																						return sum;
																						}
																						var result = add(10, 20); //30
																						alert(sum); //        30
																						```

																						> 不声明就直接使用变量是常见的错误做法，我们建议在初始化变量之前,一定要先声明,这样就可以避免类似问题。

																						###数组
																						JavaScript的数组可以保存任意类型，并且数组的大小可以**自由增删**。
																						例如，扩充数组：
																						```
																						var colors = ["red", "blue", "green"]; // 定义一个字符串数组
																						colors[3] = "brown";   // 新增第四项
																						```
																						减小数组：
																						```
																						var colors = ["red", "blue", "green"];// 创建一个包含 3 个字符串的数组
																						colors.length = 2;
																						alert(colors[2]);   //undefined
																						```

																						> 所有对象（包括数组）有含有toLocaleString(),toString(),valueOf()方法。

																						###函数
																						**函数是对象,函数名是指针**

																						由于函数名仅仅是指向函数的指针,因此函数名与包含对象指针的其他变量没有什么不同。换句话
																						说,一个函数可能会有多个名字,

																						```
																						function sum(num1, num2){
																						return num1 + num2;
																						}
																						alert(sum(10,10));//20
																						var anotherSum = sum;
																						alert(anotherSum(10,10)); //20
																						sum = null;
																						alert(anotherSum(10,10)); //20
																						```

																						####prototype
																						prototype 是保存它们所有实例方法的真正所在

																						使用 new 操作符创建的引用类型的实例,
																						在执行流离开当前作用域之前都一直保存在内存中。而自动创建的基本包装类型的对象,则只存在于一
																						行代码的执行瞬间,然后立即被销毁。这意味着我们不能在运行时为基本类型值添加属性和方法。来看
																						下面的例子:
																						```
																						var s1 = "some text";
																						s1.color = "red";      //不是显视的表明new String("some text");
																						alert(s1.color);  //undefined
																						```

																						# 面向对象的程序设计
																						ECMA-262 把对象定义为:“无序属性的集合,其属性可以包含基本值、对象或者函数。“

																						一旦把属性定义为不可配置的,就不能再把它变回可配置了。

																						不一定非要同时指定 getter 和 setter。只指定 getter 意味着属性是不能写,尝试写入属性会被忽略。在严格模式下,尝试写入只指定了 getter 函数的属性会抛出错误。类似地,只指定 setter 函数的属性也不能读,否则在非严格模式下会返回 undefined,而在严格模式下会抛出错误。


																						厂模式虽然解决了创建多个相似对象的问题,但却没有解决对象识别的问题(即怎样知道一个对象的类型)。
																						ECMAScript 中的构造函数可用来创建特定类型的对象。

																						##原型模式
																						我们创建的每个函数都有一个 prototype(原型)属性,这个属性是一个指针,指向一个对象,而这个对象的用途是包含可以由特定类型的所有实例共享的属性和方法。

																						不必在构造函数中定义对象实例的信息,而是可以将这些信息直接添加到原型对象中

																						##继承
																						构造函数、原型和实例的关系:
																						每个构造函数都有一个原型对象,原型对象都包含一个指向构造函数的指针,而实例都包含一个指向原型对象的内部指针。

																						------------
																						# 函数表达式

																						##必包
																						闭包是指有权访问另一个函数作用域中的变量的函数。创建闭包的常见方式,就是在一个函数内部创建另一个函数。


																						全局环境的变量对象始终存在,而像compare()函数这样的局部环境的变量对象,则只在函数执行的过程中存在。在创建 compare()函数时,会创建一个预先包含全局变量对象的作用域链,这个作用域链被保存在内部的[[Scope]]属性中。
																						当调用 compare()函数时,会为函数创建一个执行环境,然后通过复制函数的[[Scope]]属性中的对象构建起执行环境的作用域链。此后,又有一个活动对象(在此作为变量对象使用)被创建并被推入执行环境作用域链的前端。


																						##私有变量
																						JavaScript 中没有私有成员的概念;所有对象属性都是公有的。不过,倒是有一个私有
																						变量的概念。任何在函数中定义的变量,都可以认为是私有变量,因为不能在函数的外部访问这些变量。私有变量包括函数的参数、局部变量和在函数内部定义的其他函数。

																						必包的特殊性：
																						一般来讲,当函数执行完毕后,局部活动对象就会被销毁,内存中仅保存全局作用域(全局执行环境的变量对象)。但是,闭包的情况又有所不同。


																						---
																						#BOM 
																						##window对象
																						在浏览器中,window 对象有双重角色,
																						它既是通过 JavaScript 访问浏览器窗口的一个接口,又是 ECMAScript 规定的 Global 对象。

																						定义全局变量与在 window 对象上直接定义属性还是有一点差别:全局变量不能通过 delete 操作符删除,而直接在 window 对象上的定义的属性可以。
																						L这是因为使用 var 语句添加的 window 属性有一个名为[[Configurable]]的特性,这个特性的值被因此这样定义的属性不可以通过 delete 操作符删除

																						##location
																						它提供了与当前窗口中加载的文档有关的信息,还提供了一些导航功能。事实上,location 对象是很特别的一个对象,因为它既是 window 对象的属性,也是
																						document 对象的属性;换句话说,window.location 和 document.location 引用的是同一个对象。location 对象的用处不只表现在它保存着当前文档的信息,还表现在它将 URL 解析为独立的片段,让开发人员可以通过不同的属性访问这些片段。

