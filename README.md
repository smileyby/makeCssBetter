编写好的CSS代码
=============

> 编写好的css代码，有助于页面的渲染速度。本质上，引擎需要解析的css规则越少，性能越好。MDN上将css选择符归为四个主要类别如下所示，性能一次降低。

1.	ID规则
2.	Class规则
3.	标签规则
4.	通用规则

#### 避免过度约束

> 一条普遍规则，不要添加不必要的约束

```css

	// 糟糕
	ul#someid{...}
	.menu#otherid{...}
	
	// 好的
	#someid{...}
	#otherid{...}

```

#### 后代选择符最烂

> 不仅性能低下而且代码脆弱，html代码个css1代码严重耦合，html代码结构发生变化，css也修改，这是多么糟糕，特别是在大公司，写html和css的往往不是同一个人

```css
	
	// 烂透了
	html div tr td {....}

```

#### 避免链式（交集）选择符

> 这和过度约束的情况类似，更明智的做法很简单的创建一个新的css类选择符

```css

	// 糟糕
	.menu.left.icon{...}
	
	// 好的
	.menu-left-icon{...}

```

#### 坚持KISS原则（keep it simple）

> 想象我们有如下dom结构

```css

	<ul id="navigator">
		<li><a href="#" class="twitter"></a></li>
		<li><a href="#" class="facebook"></a></li>
		<li><a href="#" class="dribble"></a></li>
	</ul>

```

> 下面是对应的规则

```css

	// 糟糕
	#navigator li a {...}
	
	// 好的
	#navigator {...}
```

#### 使用复合（紧凑）语法

> 尽可能使用复合语法

```css

	// 糟糕
	.someclass {
	 padding-top: 20px;
	 padding-bottom: 20px;
	 padding-left: 10px;
	 padding-right: 10px;
	 background: #000;
	 background-image: url(../imgs/carrot.png);
	 background-position: bottom;
	 background-repeat: repeat-x;
	}
	 
	// 好的
	.someclass {
	 padding: 20px 10px 20px 10px;
	 background: #000 url(../imgs/carrot.png) repeat-x bottom;
	}

```

####　避免不必要的命名空间

```css

	// 糟糕
	.someclass table tr.otherclass td.somerule {..}
	 
	//好的
	.someclass .otherclass td.somerule {..}

```

####　避免不必要的重复

> 尽可能组合重复的规则

```css

	// 糟糕
	.someclass {
	 color: red;
	 background: blue;
	 font-size: 15px;
	}
	 
	.otherclass {
	 color: red;
	 background: blue;
	 font-size: 15px;
	}
	 
	// 好的
	 
	.someclass, .otherclass {
	 color: red;
	 background: blue;
	 font-size: 15px;
	}

```

#### 尽可能精简规则

> 在上面规则的基础上，你可以进一步合并不同的重复的规则

```css

	// 糟糕
	.someclass {
	 color: red;
	 background: blue;
	 height: 150px;
	 width: 150px;
	 font-size: 16px;
	}
	 
	.otherclass {
	 color: red;
	 background: blue;
	 height: 150px;
	 width: 150px;
	 font-size: 8px;
	}
	 
	// 好的
	.someclass, .otherclass {
	 color: red;
	 background: blue;
	 height: 150px;
	 width: 150px;
	}
	 
	.someclass {
	 font-size: 16px;
	}
	 
	.otherclass {
	 font-size: 8px;
	}

```

####避免不明确的命名约定

> 最好使用表示语义的名字。一个好的css类型应描述它是什么而不是它像什么。

#### 避免 !important

> 其实你应该也可以使用其他优质的选择器。

####　遵循一个标准的声明顺序

> 虽然有一些排列属性顺序常见的方式，下面是我遵循的一种流行方式。

```css

	someclass {
	 /* Positioning */
	 /* Display & Box Model */
	 /* Background and typography styles */
	 /* Transitions */
	 /* Other */
	}

```

#### 组织好的代码格式

> 代码的易读性和易维护性成正比。下面是我遵循的格式化方法。

```css

	// 糟糕
	.someclass-a, .someclass-b, .someclass-c, .someclass-d {...}
	
	// 好的
	.someclass-a,
	.someclass-b,
	.someclass-c,
	.someclass-d {
		...
	}
	
	// 好的做法
	.someclass {
		background-image:
	        linear-gradient(#000, #ccc),
	        linear-gradient(#ccc, #ddd);
	    box-shadow:
	        2px 2px 2px #000,
	        1px 4px 1px 1px #ddd inset;
	}

```

> 显然，这里只讲述了少数的规则，如果你想阅读更多的只是，建议阅读MDN上的[编写高效的CSS](https://developer.mozilla.org/en-US/docs/Learn/CSS)和谷歌的[优化浏览器渲染](https://developers.google.com/speed/docs/best-practices/rendering#UseEfficientCSSSelectors)指南。