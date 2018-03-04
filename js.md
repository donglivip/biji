###Welcome to use MarkDown
1.0
	typeof()
		返回对象的数据类型
			number string function Object undefinde boolean
		注意:
			typeof()对数组,对象,返回的都是Object,所以如果要详细分析需要引用instanceof
			例:
				arr = [1,2,3];
				if(arr instanceof Array){
				    document.write("arr 是一个数组");
				} else {
				    document.write("arr 不是一个数组");
				}
2.0
	强制类型转换
		2.1
			String(x)
				转化成字符串对象
		2.2
			x.toString()
				效果同上
		2.3
			Number('1203')
			parseInt('123')返回整数
			parsefloat('120.3')返回浮点数
3.0
	字符串操作
		1.subString()
			subString(2):从第二位截取到最后一位
			subString(2，4)从第二位截取到第四位，不包含4
		2.split（）
			使用指定字符串把他分割并存到数组中
		3.join（）
			将数组用制定字符串连接形成字符串
		4.indexof（）
			返回字符串中第一个匹配的字符的下标
		5.substr（1,5）
			从第一位截取五个字符
		6.chatAt()
			返回指定位置的字符
		7.slice（）
			从数组中输出指定索引的
		9.replace('a','b')
			替换
		10.splice
			arrayObject.splice(index,howmany,item1,.....,itemX)
			index	必需。整数，规定添加/删除项目的位置，使用负数可从数组结尾处规定位置。
			howmany	必需。要删除的项目数量。如果设置为 0，则不会删除项目。
			item1, ..., itemX	可选。向数组添加的新项目。	
4.0
	函数
		参数:
			形参:test('x')	
			实参:test('123')	
5.0
	js预加载(),页面onload是不加载函数,需要时再引入	
		appendJS (url, part, callback) {
	        var element = document.createElement('script')
	        element.setAttribute('type', 'text/javascript')
	        element.setAttribute('src', url)
	        if (part) {
	            document[part].appendChild(element)
	        }
	        if (callback && typeof (callback) === 'function') {
	            element.onload = element.onreadystatechange = callback
	        }
	        return element
	   }
6.0
	递归函数
		所谓递归函数就是再函数自身调用函数自身(但是一定要谨慎使用,否则会引起死循环)
			function fact(num){ 
				if (num<=1){ 
					return 1; 
				}else{ 
					return num*fact(num-1); 
				} 
			} 
7.0
	7.1
		立即执行函数基本表达式
			(function () {  
			    alert('watch out!');  
			}());	
	7.2
		立即执行函数传参
			(function(who, when) {  
			    console.log("I met " + who + " on " + when);  
			} ("Joe Black", new Date()));
	7.3
		立即执行函数的返回值
			var result = (function () {  
			    return 2 + 2;  
			}());  
		另外的写法
			var result = function () {  
			    return 2 + 2;  
			}();  		
			var result = (function () {  
			    return 2 + 2;  
			})();
	7.4
		立即执行函数也可以作为一个对象的属性之
			var o = {  
			    message: (function() {  
			        var who = "me",  
			        what = "call";  
			        return what + " " + who;  
			    } ()),  
			    getMsg: function() {  
			        return this.message;  
			    }  
			};  
			// usage  
			o.getMsg(); // "call me"  
			o.message; // "call me" 
8.0
	闭包函数
		8.1
			js的链式作用域
				子对象会一级一级地向上寻找所有父对象的变量
		8.2
			闭包的定义(什么叫闭包)
				闭包就是能够读取其他函数内部变量的函数。 
				当内部函数 在定义它的作用域 的外部 被引用时,就创建了该内部函数的闭包 ,如果内部函数引用了位于外部函数的变量,当外部函数调用完毕后,这些变量在内存不会被 释放,因为闭包需要它们.
		9.3
			闭包的用途
				一个是前面提到的可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中。
		9.4
			注意事项
				1）由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除。
				2）闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），这时一定要小心，不要随便改变父函数内部变量的值。
9.0
	js封装类
		比如需要创建一个对象某某某
			var oPerson = new Object;  
			oPerson.name = "zs";  
			oPerson.sex = 'boy';  
			oPerson.birthday = '2001-02-03';  
			oPerson.sayHi = function()  
			{  
			   alert("Hi ! I am "+this.name);  
			} 
		但是当我们需要创建多个对象时怎么办呢,当然不可能New 多个 Object,这时候就要用到封装类了
			functon createPerson(name,sex,birthday){  
			  var oPerson = new Object;  
			  oPerson.name =name;  
			  oPerson.sex = sex;  
			  oPerson.birthday = birthday;  
			   
			 oPerson.sayHi = function()  
			 {  
			    alert("Hi ! I am "+this.name);  
			 }  
			  return oPerson;  
			}  
			  
			//那么我们多创建几个人的话，就可以  
			var person1 = new createPerson('zs','boy','2001-02-03');  
			var person2 = new createPerson('ls','boy','2001-02-04');  
			person1.sayHi();  
			person2.sayHi();
		但是我们每次创建一个新的对象,都会新建一个sayHi函数,但是这些函数的功能都是一样的,这就造成了浪费,我们可以使用prototype
			functon CreatePerson(name,sex,birthday,fn) {  
			  this.name =name;  
			  this.sex = sex;  
			  this.birthday = birthday;  
			}  
			CreatePerson.prototype.sayHi = function ()  
			{  
			  alert("Hi ! I am "+this.name);  
			}  
			  
			var person1 = new CreatePerson('zs','boy','2001-02-03');  
			var person2 = new CreatePerson('ls','boy','2001-02-04');  
			person1.sayHi(); //outputs "Hi ! I am zs"  
			person2.sayHi(); //outputs "Hi ! I am ls"  
			  
			一般情况下，一个对象或者类不只一个方法，需要多个方法配合使用，那么  
			CreatePerson.prototype={  
			  sayHi:function()  
			  {  
			    alert("Hi ! I am "+this.name);  
			  },  
			  walk:function()  
			  {  
			    alert("walk,walk");  
			  },  
			  ……  
			}  
		9.2
			什么事prototype	
				prototype 属性使您有能力向对象添加属性和方法
				语法:
					object.prototype.name=value
10.0
	js原型,原型链,原型继承
		10.3
			函数的变量和内部函数		
				私有变量(即在函数内部定义的变量,再函数外部无法访问)
					function Xzavier(){
					    var name = "xzavier"; //私有变量
					    var sports = function() {console.log('basketball')}; //私有函数 
					}
					var x = new Xzavier();
					x.name;  //undefined
				如果想要进行访问,则需要暴露一个接口
					function Xzavier(){
					    var name = "xzavier"; //私有变量
					    var sports = function() {console.log('basketball')}; //私有函数
					    return{
					        name: name,
					        sports: sports
					    }
					}
					var x = new Xzavier();
					x.name;  //"xzavier"
			10.3.1
				静态变量
					用点操作符定义的静态变量和内部函数就是实例不能访问到的变量和内部函数。只能通过自身去访问。

						function Xzavier(){
						    Xzavier.name = "xzavier"; //静态变量
						    Xzavier.sports = function() {console.log('basketball')}; //静态函数 
						}
						Xzavier.name; //"xzavier"
						var x = new Xzavier();
						x.name;  //undefined
				实例变量
					通过this定义给实例使用的属性和方法。

						function Xzavier(){
						    this.name = "xzavier"; //实例变量
						    this.sports = function() {console.log('basketball');}; //实例函数 
						}
						Xzavier.name; //undefined
						var x = new Xzavier();
						x.name;  //"xzavier
			10.4
				原型链继承
					function Xzavier() {
					    this.name = 'xzavier';
					    this.sex = 'boy';
					    this.job = "jser";
					}
					
					function X() {};
					
					X.prototype = new Xzavier();
					这种方式虽然让X.prototype继承了Xzavier.prototype,但是X没有constructor属性
						10.4.1
							constructor 属性返回对创建此对象的数组函数的引用。
							原型对象prototype中都有个预定义的constructor属性，用来引用它的函数对象。
							<script type="text/javascript">

								var test=new Array();
								
								if (test.constructor==Array)
								{
								document.write("This is an Array");
								}
								if (test.constructor==Boolean)
								{
								document.write("This is a Boolean");
								}
								if (test.constructor==Date)
								{
								document.write("This is a Date");
								}
								if (test.constructor==String)
								{
								document.write("This is a String");
								}
							
							</script>
					function Xzavier() {
					    this.name = 'xzavier';
					    this.sex = 'boy';
					    this.job = "jser";
					}
					
					function X(){}
					X.prototype = new Xzavier();
					var x = new X()
					x.name  // "xzavier"
					
					需要var x = new X()
			拓展:
				普通对象和函数对象
					函数对象：

						function f1(){};
						var f2 = function(){};
						var f3 = new Function('str','console.log(str)');
					普通对象：

						var o3 = new f1();
						var o1 = {};
						var o2 =new Object();
						
				只有函数对象才有原型
11.0
	call/applay/prototype
		11.1
			作用(用来干么的)
				js中实现继承的方法
		11.2
			原型链实现继承(原始方法,基本不用)
				function Person(name,age){  
			        this.name=name;  
			        this.age=age;  
			    }  
			    Person.prototype.sayHello=function(){  
			        alert("使用原型得到Name："+this.name);  
			    }  
			    var per=new Person("马小倩",21);  
			    per.sayHello(); //输出：使用原型得到Name:马小倩  
		11.3
			call , apply实现继承(缺点,不能继承原型,只是用人家的方法,每次构造一个函数实际上走了两个方法)
			区别,apply的第二个参数只能是数组,而call可以是任意值
			 function Father (name,age,sex){
			 	this.name=name;
			 	this.age=age;
			 	this.sex=sex
			 } 
			 
			 function Childern(name,age,sex,grade){
			 	Father.call(this,name,age,sex)
			 	this.grade=grade
			 }
			 
			 var Childern=new Childern()
		11.4
			共享原型
				Father.prototype.name='Dong'
				function Father(){
					
				}

				function Son(){
					
				}

				Son.prototype=Father.prototype
				
				var Son=new Son
			缺点:
				Son.prototype.sex='man'
				档son的原型改变时,Father也会跟着改变
		11.5
			圣杯模式
				Father.prototype.name='Dong'
				function Father(){
					
				}

				function Son(){
					
				}
				function F(){//中间值
				}
				
				F.prototype=Father.prototype
				
				Son.prototype=new F()
				var Son=new Son
