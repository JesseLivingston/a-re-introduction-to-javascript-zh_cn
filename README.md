<h1>JavaScript “再”入门指南</h1>
<h2 id=".E5.BC.95.E8.A8.80">引言</h2>
<p>为什么会有这一篇“再”入门指南（re-introduction）呢？因为 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript">JavaScript</a> 堪称是<a href="http://javascript.crockford.com/javascript.html">世界上最被人误解的编程语言</a>。虽然 JavaScript 常被视作“玩具语言”，但在它具有迷惑性的简洁外衣下，隐藏着强大的语言特性。既然 JavaScript 已在一大批知名应用中被广泛采用，对于网页和移动开发者来说，深入了解 JavaScript 理所应当成为一项重要的技能。</p>
<p>先从这门语言的历史谈起。1995 年 Netscape 一位名为 Brendan Eich 的员工创造了 JavaScript，随后在 1996 年初，JavaScript 首先被应用于 Netscape 2 浏览器上。最初的 JavaScript 名为 LiveScript，后来因为 Sun Microsystem 的 Java 语言的兴起和广泛使用，Netscape 出于宣传和推广的考虑，将它的名字从最初的 LiveScript 更改为 JavaScript——尽管两者之间并没有什么共同点。这便是之后混淆产生的根源。</p>
<p>几个月后，Microsoft 随着 IE 3 推出了一个与之基本兼容的语言 JScript。Netscape 将 JavaScript 提交至 <a href="http://www.ecma-international.org">Ecma International</a>（一个欧洲标准化组织），<a href="https://developer.mozilla.org/en/JavaScript/Language_Resources">ECMAScript</a> 标准第一版便在 1997 年诞生了，随后在 1999 年以 <a href="http://www.ecma-international.org/publications/standards/Ecma-262.htm">ECMAScript 第三版</a>的形式进行了更新，从那之后这个标准没有发生过大的改动。由于委员会在语言特性的讨论上发生分歧，ECMAScript 第四版尚未推出便被废除，但随后于 2009 年 12 月发布的 ECMAScript 第五版引入了第四版草案加入的许多特性。标准的第六次修订目前处于草案阶段。</p>
<p>JavaScript 能有这样的稳定性（译者注：指语言标准在相当长的时间内没有发生过大的改动）对于开发者是个好消息，因为它给了开发者充足的时间修改已有的代码适应新版本的变化。以下介绍的语言特性基于 ECMAScript 第三版，为了带来不必要的误会，也将使用 JavaScript 这个名称。</p>
<p>与大多数编程语言不同，JavaScript 没有输入或输出的概念。它是一个在宿主环境（host environment）下运行的脚本语言，任何与外界沟通的机制都是由宿主环境提供的。浏览器是最常见的宿主环境，但是其他程序中也包含 JavaScript 解释器，如 Adobe Acrobat、Photoshop、SVG 图像、Yahoo! 的 widget ，以及 <a href="http://nodejs.org">node.js</a> 之类的服务器端环境。JavaScript 的实际应用远不止这些，除此之外还有 NoSQL 数据库（如开源的 <a href="http://couchdb.apache.org">Apache CouchDB</a>）、嵌入式计算机，以及包括 <a href="http://www.gnome.org">GNOME</a> （注：GNU/Linux 上最流行的 GUI 之一）在内的桌面环境等等。</p>
<h2 id=".E6.A6.82.E8.A7.88">概览</h2>
<p>JavaScript 是一种面向对象的动态语言，它包含类型、运算符、核心对象（core objects）和方法。它的语法来源于 Java 和 C，所以这两种语言的许多语法特性同样适用于 JavaScript。需要注意的一个主要区别是 JavaScript 不支持类，类这一概念在 JavaScript 通过对象原型（object prototype）得到延续。另一个主要区别是 JavaScript 中的函数也是对象，JavaScript 允许函数在包含可执行代码的同时，能像其他对象一样被传递。</p>
<p>先从任何编程语言都不可缺少的组成部分——“类型”开始。JavaScript 程序可以修改值（value），这些值都有各自的类型。JavaScript 中的类型包括：</p>
<ul>
 <li><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number">Number</a>（数字）</li>
 <li><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String">String</a>（字符串）</li>
 <li><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Boolean">Boolean</a>（布尔）</li>
 <li><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Symbol">Symbol</a>（符号）</li>
 <li><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function">Function</a>（函数）</li>
 <li><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object">Object</a>（对象）</li>
</ul>
<p>……哦，还有看上去有些奇怪的 Undefined（未定义）类型和 Null （空）类型。此外还有 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array">Array</a> （数组）类型，以及分别用于表示日期和正则表达式的 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date">Date</a>（日期）和 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp">Regular Expression</a>（正则表达式），这三种类型都是特殊的对象。严格意义上说，Function（函数）也是一种特殊的对象。所以准确来说，JavaScript 中的类型应该包括这些：</p>
<ul>
 <li>Number（数字）</li>
 <li>String（字符串）</li>
 <li>Boolean（布尔）</li>
 <li>Symbol（符号）</li>
 <li>Object（对象）
  <ul>
   <li>Function（函数）</li>
   <li>Array（数组）</li>
   <li>Date（日期）</li>
   <li>RegExp（正则表达式）</li>
  </ul>
 </li>
 <li>Null（空）</li>
 <li>Undefined（未定义）</li>
</ul>
<p>还有一种 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Error">Error</a>（错误）类型，这个会在之后的介绍中提到。</p>
<h2 id=".E6.95.B0.E5.AD.97">数字</h2>
<p>根据语言规范，JavaScript 采用“IEEE 754 标准定义的双精度64位格式”（"double-precision 64-bit format IEEE 754 values"）表示数字。据此我们能得到一个有趣的结论，和其他编程语言（如 C 和 Java）不同，JavaScript 不区分整数值和浮点数值，所有数字在 JavaScript 中均用浮点数值表示，所以在进行数字运算的时候要特别注意。看看下面的例子：</p>
<pre class="eval">
0.1 + 0.2 = 0.30000000000000004
</pre>
<p>但具体实现时为了便于进行位操作，整数值通常被视为32位整型变量，在个别实现（如某些浏览器）中也以32位整型变量的形式进行存储。进一步的详细资料可参考 <a href="http://www.hunlock.com/blogs/The_Complete_Javascript_Number_Reference">The Complete JavaScript Number Reference</a>。</p>
<p>JavaScript 支持标准的<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators">算术运算符</a>，包括加法、减法、取模（或取余）等等。还有一个之前没有提及的内置对象 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math">Math</a>（数学），用以处理更多的高级数学函数和常数：</p>
<pre class="brush: js">
Math.sin(3.5);
var d = Math.PI * r * r;
</pre>
<p>你可以使用内置函数 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/parseInt"><code>parseInt()</code></a> 将字符串转换为整型。该函数的第二个参数表示字符串所表示数字的基（进制）：</p>
<pre class="brush: js">
&gt; parseInt("123", 10)
123
&gt; parseInt("010", 10)
10
</pre>
<p>如果调用时没有提供第二个参数（字符串所表示数字的基），2013 年以前的 JavaScript 实现会返回一个意外的结果：</p>
<pre class="brush: js">
&gt; parseInt("010")
8
</pre>
<p>这是因为字符串以数字 0 开头，<code>parseInt</code> 函数会把这样的字符串视作八进制数字。</p>
<p>如果想把一个二进制数字字符串转换成整数值，只要把第二个参数设置为 2 就可以了：</p>
<pre class="brush: js">
&gt; parseInt("11", 2)
3
</pre>
<p>JavaScript 还有一个类似的内置函数 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/parseFloat"><code>parseFloat()</code></a>，用以解析浮点数字符串，跟 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/parseInt"><code>parseInt()</code></a> 不同的地方是 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/parseFloat"><code>parseFloat()</code></a> 只能解析十进制数字。</p>
<p>单元运算符 + 也可以把数字字符串转换成数值：</p>
<pre>
&gt; + "42"
42 
</pre>
<p>如果给定的字符串不存在数值形式，函数会返回一个特殊的值 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/NaN"><code>NaN</code></a>（Not a Number 的缩写）：</p>
<pre class="brush: js">
&gt; parseInt("hello", 10)
NaN
</pre>
<p>如果把 <code>NaN</code> 作为参数进行数学运算，结果也会是 <code>NaN</code>：</p>
<pre class="brush: js">
&gt; NaN + 5
NaN
</pre>
<p>可以使用内置函数 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/isNaN"><code>isNaN()</code></a> 来判断一个变量是否为 <code>NaN</code>：</p>
<pre class="brush: js">
&gt; isNaN(NaN)
true
</pre>
<p>JavaScript 还有两个特殊值：<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Infinity"><code>Infinity</code></a>（正无穷）和 <code>-Infinity</code>（负无穷）：</p>
<pre class="brush: js">
&gt; 1 / 0
Infinity
&gt; -1 / 0
-Infinity
</pre>
<p>可以使用内置函数 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/isFinite"><code>isFinite()</code></a> 来判断一个变量是否为 <code>Infinity</code>, <code>-Infinity</code> 或 <code>NaN</code>：</p>
<pre class="brush: js">
&gt; isFinite(1/0)
false
&gt; isFinite(-Infinity)
false
&gt; isFinite(NaN)
false
</pre>
<div class="note">
 <strong>备注：</strong><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/parseInt"><code>parseInt()</code></a> 和 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/parseFloat"><code>parseFloat()</code></a> 函数会尝试逐个解析字符串中的字符，直到遇上一个无法被解析成数字的字符，然后返回该字符前所有数字字符组成的数字。使用运算符 + 将字符串转换成数字，只要字符串中含有无法被解析成数字的字符，该字符串都将被转换成 <code>NaN</code>。请你用这两种方法解析“10.2abc”这一字符串，比较得到的结果，理解这两种方法的区别。</div>
<h2 id=".E5.AD.97.E7.AC.A6.E4.B8.B2">字符串</h2>
<p>JavaScript 中的字符串是一串字符序列。更准确地说，它们是一串由<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Values,_variables,_and_literals#Unicode.E7.BC.96.E7.A0.81">Unicode 字符</a>构成的字符序列，每一个字符由一个 16 位二进制数表示。这对于那些需要和多语种网页打交道的开发者来说是个好消息。</p>
<p>如果想表示一个单独的字符，只需使用长度为 1 的字符串。</p>
<p>通过访问字符串的 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/length"><code>length</code></a>（长度）属性可以得到它的长度。</p>
<pre class="brush: js">
&gt; "hello".length
5
</pre>
<p>这就是 JavaScript 对象。前面已经提过，字符串实际上也是对象，所以它们也有<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String#Methods">方法</a>：</p>
<pre class="brush: js">
&gt; "hello".charAt(0)
h
&gt; "hello, world".replace("hello", "goodbye")
goodbye, world
&gt; "hello".toUpperCase()
HELLO
</pre>
<h2 id=".E5.85.B6.E4.BB.96.E7.B1.BB.E5.9E.8B">其他类型</h2>
<p>JavaScript 中 <code>null</code> 和 <code>undefined</code> 是不同的，前者表示一个空值（non-value），后者是“undefined（未定义）”类型的对象，表示一个还没有被分配的值。我们之后再具体讨论变量，但有一点可以先简单说明一下，JavaScript 允许声明变量但不对其赋值，一个未被赋值的变量就是 <code>undefined</code> 类型。还有一点需要说明的是，<code>undefined</code> 是一个不允许修改的常量。</p>
<p>JavaScript 包含布尔类型，这个类型的变量有两个可能的值，分别是 <code>true</code> 和 <code>false</code>（两者都是关键字）。根据具体需要，JavaScript 按照如下规则将变量转换成布尔类型：</p>
<ol>
 <li><code>false</code>、<code>0</code>、空字符串(<code>""</code>)、<code>NaN</code>、<code>null</code> 和 <code>undefined</code> 被转换为 <code>false</code></li>
 <li>其他值被转换为 <code>true</code></li>
</ol>
<p>也可以使用 <code>Boolean()</code> 函数进行显式转换：</p>
<pre class="brush: js">
&gt; Boolean("")
false
&gt; Boolean(234)
true
</pre>
<p>不过一般没必要这么做，因为 JavaScript 会在需要一个布尔变量时隐式完成这个转换操作（比如在 <code>if</code> 条件语句中）。通常我们可以把转换成布尔值后分别为 <code>true</code> 和 <code>false</code> 的变量分别称为“真值（true values）”和“假值（false values）”。</p>
<p>JavaScript 支持包括 <code>&amp;&amp;</code>（逻辑与）、<code>||</code> (逻辑或)和<code>!</code>（逻辑非）在内的逻辑运算符。</p>
<h2 id=".E5.8F.98.E9.87.8F">变量</h2>
<p>在 JavaScript 中声明一个新变量的方法是使用关键字 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/var"><code>var</code></a>：</p>
<pre class="brush: js">
var a;
var name = "simon";
</pre>
<p>如果声明了一个变量却没有对其赋值，那么这个变量的类型就是 <code>undefined</code>。</p>
<h2 id=".E8.BF.90.E7.AE.97.E7.AC.A6">运算符</h2>
<p>JavaScript的算术操作符包括 <code>+</code>、<code>-</code>、<code>*</code>、<code>/</code> 和 <code>%</code>（求余）。赋值使用 <code>=</code> 运算符，此外还有一些复合运算符，如 <code>+=</code> 和 <code>-=</code>，它们等价于 <code>x = x
 <i>
  op</i>
 y</code>。</p>
<pre class="brush: js">
x += 5
x = x + 5
</pre>
<p>可以使用 <code>++</code> 和 <code>--</code> 分别实现变量的自增和自减。两者都可以作为前缀或后缀操作符使用。</p>
<p><a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#.E5.8A.A0.E6.B3.95_(.2B)"><code>+</code> 操作符</a>还可以用来连接字符串：</p>
<pre class="brush: js">
&gt; "hello" + " world"
hello world
</pre>
<p>如果你用一个字符串加上一个数字（或其他值），那么操作数都会被首先转换为字符串。如下所示：</p>
<pre class="brush: js">
&gt; "3" + 4 + 5
345
&gt; 3 + 4 + "5"
75
</pre>
<p>这里不难看出一个实用的技巧——通过与空字符串相加，可以将某个变量快速转换成字符串类型。</p>
<p>JavaScript 中的比较操作使用 <code>&lt;</code>、<code>&gt;</code>、<code>&lt;=</code> 和 <code>&gt;=</code>，这些运算符对于数字和字符串都通用。相等的比较稍微复杂一些。由两个“<code>=</code>（等号）”组成的相等运算符有类型自适应的功能，具体例子如下：</p>
<pre class="brush: js">
&gt; "dog" == "dog"
true
&gt; 1 == true
true
</pre>
<p>如果在比较前不需要自动类型转换，应该使用由三个“<code>=</code>（等号）”组成的相等运算符：</p>
<pre class="brush: js">
&gt; 1 === true
false
&gt; true === true
true
</pre>
<p>JavaScript 还支持 <code>!=</code> 和 <code>!==</code> 两种不等运算符，具体区别与两种相等运算符的区别类似。</p>
<p>JavaScript 还提供了 <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators">位操作符（Bitwise operator）</a>。</p>
<h2 id=".E6.8E.A7.E5.88.B6.E7.BB.93.E6.9E.84">控制结构</h2>
<p>JavaScript 的控制结构与其他类 C 语言类似。可以使用 <code>if</code> 和 <code>else</code> 来定义条件语句，还可以将这两者组合使用：</p>
<pre class="brush: js">
var name = "kittens";
if (name == "puppies") {
  name += "!";
} else if (name == "kittens") {
  name += "!!";
} else {
  name = "!" + name;
}
name == "kittens!!"
</pre>
<p>JavaScript 支持 <code>while</code> 循环和 <code>do-while</code> 循环。前者适合常见的基本循环操作，如果需要循环体至少被执行一次则可以使用 <code>do-while</code>：</p>
<pre class="brush: js">
while (true) {
  // 一个无限循环！
}

do {
  var input = get_input();
} while (inputIsNotValid(input))
</pre>
<p>JavaScript 的 <code>for</code> 循环与 C 和 Java 中的相同，使用时可以在一行代码中提供控制信息。</p>
<pre class="brush: js">
for (var i = 0; i &lt; 5; i++) {
  // 将会执行五次
}
</pre>
<p><code>&amp;&amp;</code> 和 <code>||</code> 运算符使用短路逻辑（short-circuit logic），是否会执行第二个语句（操作数）取决于第一个操作数的值。在需要访问某个对象的属性时，使用这个特性可以事先检测该对象是否为空：</p>
<pre class="brush: js">
var name = o &amp;&amp; o.getName();
</pre>
<p>或运算可以用来设置默认值：</p>
<pre class="brush: js">
var name = otherName || "default";
</pre>
<p>类似地，JavaScript 也有一个三元操作符：</p>
<pre class="eval">
var allowed = (age &gt; 18) ? "yes" : "no";
</pre>
<p>在需要多重分支时可以使用 <code>switch</code> 语句：</p>
<pre class="brush: js">
switch(action) {
    case 'draw':
        drawit();
        break;
    case 'eat':
        eatit();
        break;
    default:
        donothing();
}
</pre>
<p>如果你不使用 <code>break</code> 语句，JavaScript 解释器将会执行之后 <code>case</code> 中的代码。除非是为了调试，一般你并不需要这个特性，所以大多数时候不要忘了加上 <code>break。</code></p>
<pre class="brush: js">
switch(a) {
    case 1: // 继续向下
    case 2:
        eatit();
        break;
    default:
        donothing();
}
</pre>
<p><code>default</code> 语句是可选的。<code>switch</code> 和 <code>case</code> 都可以使用需要运算才能得到结果的表达式；在 <code>switch</code> 的表达式和 <code>case</code> 的表达式是使用 <code>===</code> 严格相等运算符进行比较的：</p>
<pre class="eval">
switch(1 + 3):
    case 2 + 2:
        yay();
        break;
    default:
        neverhappens();
}
</pre>
<h2 id=".E5.AF.B9.E8.B1.A1">对象</h2>
<p>JavaScript 中的对象可以简单理解成“名称-值”对，不难联想 JavaScript 中的对象与下面这些概念类似：</p>
<ul>
 <li>Python 中的字典</li>
 <li>Perl 和 Ruby 中的散列（哈希）</li>
 <li>C/C++ 中的散列表</li>
 <li>Java 中的 HashMap</li>
 <li>PHP 中的关联数组</li>
</ul>
<p>这样的数据结构设计合理，能应付各类复杂需求，所以被各类编程语言广泛采用。正因为 JavaScript 中的一切（除了核心类型，core object）都是对象，所有 JavaScript 程序必然与大量的散列表查找操作有着千丝万缕的联系，而散列表擅长的正是高速查找。</p>
<p>“名称”部分是一个 JavaScript 字符串，“值”部分可以是任何 JavaScript 的数据类型——包括对象。这使用户可以根据具体需求，创建出相当复杂的数据结构。</p>
<p>有两种简单方法可以创建一个空对象：</p>
<pre class="brush: js">
var obj = new Object();
</pre>
<p>和：</p>
<pre class="brush: js">
var obj = {};
</pre>
<p>这两种方法在语义上是相同的。第二种更方便的方法叫作“对象字面量（object literal）”法。这种语法在 JSON 格式中被广泛采用，一般我们优先选择第二种方法。</p>
<p>完成创建后，对象属性可以通过如下两种方式进行赋值：</p>
<pre class="brush: js">
obj.name = "Simon"
var name = obj.name;
</pre>
<p>和：</p>
<pre class="brush: js">
obj["name"] = "Simon";
var name = obj["name"];
</pre>
<p>这两种方法在语义上也是相同的。第二种方法的优点在于属性的名称被看作一个字符串，这就意味着它可以在运行时被计算，缺点在于这样的代码有可能无法在后期被解释器优化。它也可以被用来访问某些以<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords">预留关键字</a>作为名称的属性的值：</p>
<pre class="brush: js">
obj.for = "Simon"; // 语法错误，因为 for 是一个预留关键字
obj["for"] = "Simon"; // 工作正常
</pre>
<p>“对象字面量”也可以用来在对象中定义一个对象：</p>
<pre class="brush: js">
var obj = {
    name: "Carrot",
    "for": "Max",
    details: {
        color: "orange",
        size: 12
    }
}
</pre>
<p>对象的属性可以通过链式（chain）表示方法进行访问：</p>
<pre class="brush: js">
&gt; obj.details.color
orange
&gt; obj["details"]["size"]
12
</pre>
<h2 id=".E6.95.B0.E7.BB.84">数组</h2>
<p>JavaScript 中的数组是一种特殊的对象。它的工作原理与普通对象类似（比如数组中的元素可以视作数组的属性，可以像访问对象属性那样通过使用[]进行访问），但数组还有一个特殊的属性——<code>length</code>（长度）属性。这个属性的值通常比数组最大索引大 1。</p>
<p>创建数组的传统方法是：</p>
<pre class="brush: js">
&gt; var a = new Array();
&gt; a[0] = "dog";
&gt; a[1] = "cat";
&gt; a[2] = "hen";
&gt; a.length
3
</pre>
<p>使用数组字面量（array literal）法更加方便：</p>
<pre class="brush: js">
&gt; var a = ["dog", "cat", "hen"];
&gt; a.length
3
</pre>
<div class="warning">
 <p>使用字面量法创建对象或数组时在括号末尾加上逗号在不同浏览器中可能导致不同的结果，所以暂时不推荐这么做。</p>
</div>
<p>注意，<code>Array.length</code>并不总是数组中元素的个数，如下所示：</p>
<pre class="brush: js">
&gt; var a = ["dog", "cat", "hen"];
&gt; a[100] = "fox";
&gt; a.length
101
</pre>
<p>记住：数组的长度是比数组最高索引值大 1 的数。</p>
<p>如果试图访问一个不存在的数组索引，会得到 <code>undefined</code>：</p>
<pre class="brush: js">
&gt; typeof(a[90])
undefined
</pre>
<p>可以通过如下方式遍历一个数组：</p>
<pre class="brush: js">
for (var i = 0; i &lt; a.length; i++) {
    // Do something with a[i]
}
</pre>
<p>这么做效率不太好，因为每循环一次都要计算一次长度。改进的版本是：</p>
<pre class="brush: js">
for (var i = 0, len = a.length; i &lt; len; i++) {
    // Do something with a[i]
}
</pre>
<p>还有一种更好的写法是：</p>
<pre class="brush: js">
for (var i = 0, item; item = a[i++];) {
    // Do something with item
}
</pre>
<p>这里我们使用了两个变量。<code>for</code> 循环中间部分的表达式仍然用来判断是否为真——如果为真，那么循环继续。因为<code>i</code>每次递增 1，这个数组的元素会被逐个传递给 item 变量。当遇到一个假值元素（如<code>undefined</code>）时，循环结束。</p>
<p>注意这个技巧只能在你知道数组中不含假值时才可以使用。如果想要遍历可能包含 0 或空字符串的数组，应该使用<code>i, len</code>的写法。</p>
<p>遍历数组的另一种方法是使用 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...in"><code>for...in</code></a> 循环。注意，如果有人向 <code>Array.prototype</code> 添加了新的属性，使用这样的循环这些属性也同样会被遍历：</p>
<pre class="brush: js">
for (var i in a) {
  // Do something with a[i]
}
</pre>
<p>如果想在数组后追加元素，只需要：</p>
<pre class="brush: js">
a.push(item);</pre>
<p>Array（数组）类自带了许多方法：</p>
<table>
 <thead>
  <tr>
   <th scope="col">方法名称</th>
   <th scope="col">描述</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>a.toString()</code></td>
   <td>返回一个包含数组中所有元素的字符串，每个元素通过逗号分隔。</td>
  </tr>
  <tr>
   <td><code>a.toLocaleString()</code></td>
   <td>根据宿主环境的区域设置，返回一个包含数组中所有元素的字符串，每个元素通过逗号分隔。</td>
  </tr>
  <tr>
   <td><code>a.concat(item1[, item2[, ...[, itemN]]])</code></td>
   <td>返回一个数组，这个数组包含原先 <code>a</code> 和 <code>item1、item2、……、itemN</code> 中的所有元素。</td>
  </tr>
  <tr>
   <td><code>a.join(sep)</code></td>
   <td>返回一个包含数组中所有元素的字符串，每个元素通过指定的 <code>sep</code> 分隔。</td>
  </tr>
  <tr>
   <td><code>a.pop()</code></td>
   <td>删除并返回数组中的最后一个元素。</td>
  </tr>
  <tr>
   <td><code>a.push(item1, ..., itemN)</code></td>
   <td>将 <code>item1、item2、……、itemN</code> 追加至数组 <code>a</code>。</td>
  </tr>
  <tr>
   <td><code>a.reverse()</code></td>
   <td>数组逆序（会更改原数组 <code>a</code>）。</td>
  </tr>
  <tr>
   <td><code>a.shift()</code></td>
   <td>删除并返回数组中第一个元素。</td>
  </tr>
  <tr>
   <td><code>a.slice(start, end)</code></td>
   <td>返回子数组，以 <code>a[start]</code> 开头，以 <code>a[end]</code> 前一个元素结尾。</td>
  </tr>
  <tr>
   <td><code>a.sort([cmpfn])</code></td>
   <td>依据 <code>cmpfn</code> 返回的结果进行排序，如果未指定比较函数则按字符顺序比较（即使元素是数字）。</td>
  </tr>
  <tr>
   <td><code>a.splice(start, delcount[, item1[, ...[, itemN]]])</code></td>
   <td>从 <code>start</code> 开始，删除 <code>delcount</code> 个元素，然后插入所有的 <code>item</code>。</td>
  </tr>
  <tr>
   <td><code>a.unshift([item])</code></td>
   <td>将 <code>item</code> 插入数组头部，返回数组新长度（考虑 <code>undefined</code>）。</td>
  </tr>
 </tbody>
</table>
<h2 id=".E5.87.BD.E6.95.B0">函数</h2>
<p>学习 JavaScript 最重要的就是要理解对象和函数两个部分。最简单的函数就像下面这个这么简单：</p>
<pre class="brush: js">
function add(x, y) {
    var total = x + y;
    return total;
}
</pre>
<p>这个例子包括你需要了解的关于基本函数的所有部分。一个 JavaScript 函数可以包含 0 个或多个已命名的变量。函数体中的表达式数量也没有限制。你可以声明函数自己的局部变量。<code>return</code> 语句在返回一个值并结束函数。如果没有使用 <code>return</code> 语句，或者一个没有值的 <code>return</code> 语句，JavaScript 会返回 <code>undefined</code>。</p>
<p>已命名的参数更像是一个指示而没有其他作用。如果调用函数时没有提供足够的参数，缺少的参数会被 <code>undefined</code> 替代。</p>
<pre class="brush: js">
&gt; add()
NaN // 不能在 undefined 对象上进行加法操作
</pre>
<p>你还可以传入多于函数本身需要参数个数的参数：</p>
<pre class="brush: js">
&gt; add(2, 3, 4)
5 // 将前两个值相加，4被忽略了
</pre>
<p>这看上去有点蠢。函数实际上是访问了函数体中一个名为 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions_and_function_scope/arguments"><code>arguments</code></a> 的内部对象，这个对象就如同一个类似于数组的对象一样，包括了所有被传入的参数。让我们重写一下上面的函数，使它可以接收任意个数的参数：</p>
<pre class="brush: js">
function add() {
    var sum = 0;
    for (var i = 0, j = arguments.length; i &lt; j; i++) {
        sum += arguments[i];
    }
    return sum;
}

&gt; add(2, 3, 4, 5)
14
</pre>
<p>这跟直接写成 <code>2 + 3 + 4 + 5</code> 也没什么区别。接下来创建一个求平均数的函数：</p>
<pre class="brush: js">
function avg() {
    var sum = 0;
    for (var i = 0, j = arguments.length; i &lt; j; i++) {
        sum += arguments[i];
    }
    return sum / arguments.length;
}
&gt; avg(2, 3, 4, 5)
3.5
</pre>
<p>这个很有用，但是却带来了新的问题。<code>avg()</code> 函数处理一个由逗号连接的变量串，但如果想得到一个数组的平均值该怎么办呢？可以这么修改函数：</p>
<pre class="brush: js">
function avgArray(arr) {
    var sum = 0;
    for (var i = 0, j = arr.length; i &lt; j; i++) {
        sum += arr[i];
    }
    return sum / arr.length;
}
&gt; avgArray([2, 3, 4, 5])
3.5
</pre>
<p>但如果能重用我们已经创建的那个函数不是更好吗？幸运的是 JavaScript 允许使用 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/apply"><code>apply()</code></a>来调用一个函数，并传递给它一个包含了参数的数组。</p>
<pre class="brush: js">
&gt; avg.apply(null, [2, 3, 4, 5])
3.5
</pre>
<p>传给 <code>apply()</code> 的第二个参数是一个数组，它将被当作 <code>avg()</code> 的参数使用，至于第一个参数 <code>null</code>，我们将在后面讨论。这也正说明了事实上函数也是一种对象。</p>
<p>JavaScript 允许你创建匿名函数：</p>
<pre class="brush: js">
var avg = function() {
    var sum = 0;
    for (var i = 0, j = arguments.length; i &lt; j; i++) {
        sum += arguments[i];
    }
    return sum / arguments.length;
}
</pre>
<p>这个函数在语义上与 <code>function avg()</code> 相同。你可以在代码中的任何地方定义这个函数，就像写普通的表达式一样。基于这个特性，有人发明出一些有趣的技巧。与 C 中的块级作用域类似，下面这个例子隐藏了局部变量：</p>
<pre class="brush: js">
&gt; var a = 1;
&gt; var b = 2;
&gt; (function() {
    var b = 3;
    a += b;
})();
&gt; a
4
&gt; b
2
</pre>
<p>JavaScript 允许以递归方式调用函数。递归在处理树形结构（比如浏览器 <a href="https://developer.mozilla.org/zh-CN/docs/Web/API/Document_Object_Model">DOM</a>）时非常有用。</p>
<pre class="brush: js">
function countChars(elm) {
    if (elm.nodeType == 3) { // TEXT_NODE
        return elm.nodeValue.length;
    }
    var count = 0;
    for (var i = 0, child; child = elm.childNodes[i]; i++) {
        count += countChars(child);
    }
    return count;
}
</pre>
<p>这里需要说明一个潜在问题——既然匿名函数没有名字，那该怎么递归调用它呢？答案是通过 <code>arguments</code> 对象，就是之前提过那个用来包含一系列参数的对象，它还提供了一个名为 <code>arguments.callee</code> 的属性。这个属性通常指向当前的（调用）函数，因此它可以用来进行递归调用：</p>
<pre class="brush: js">
var charsInBody = (function(elm) {
    if (elm.nodeType == 3) { // TEXT_NODE
        return elm.nodeValue.length;
    }
    var count = 0;
    for (var i = 0, child; child = elm.childNodes[i]; i++) {
        count += arguments.callee(child);
    }
    return count;
})(document.body);
</pre>
<p>由于 <code>arguments.callee</code> 指向当前函数，而且所有的函数都是对象，不难想象可以使用 <code>arguments.callee</code> 保存对这同一个函数的多重调用的一些信息。下面是一个可以记住它被调用了多少次的函数：</p>
<pre class="brush: js">
function counter() {
    if (!arguments.callee.count) {
        arguments.callee.count = 0;
    }
    return arguments.callee.count++;
}

&gt; counter()
0
&gt; counter()
1
&gt; counter()
2
</pre>
<h2 id=".E8.87.AA.E5.AE.9A.E4.B9.89.E5.AF.B9.E8.B1.A1">自定义对象</h2>
<div class="note">
 <strong>备注：</strong>关于 JavaScript 中面向对象编程更详细的信息，请参考 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript">JavaScript 面向对象简介</a>。</div>
<p>在经典的面向对象语言中，对象是指数据和在这些数据上进行的操作的集合。与 C++ 和 Java 不同，JavaScript 是一种基于原型的编程语言，并没有 <code>class</code> 语句，而是把函数用作类。那么让我们来定义一个人名对象，这个对象包括人的姓和名两个域（field）。名字的表示有两种方法：“名 姓（First Last）”或“姓, 名（Last, First）”。使用我们前面讨论过的函数和对象概念，可以像这样完成定义：</p>
<pre class="brush: js">
function makePerson(first, last) {
    return {
        first: first,
        last: last
    }
}
function personFullName(person) {
    return person.first + ' ' + person.last;
}
function personFullNameReversed(person) {
    return person.last + ', ' + person.first
}
&gt; s = makePerson("Simon", "Willison");
&gt; personFullName(s)
Simon Willison
&gt; personFullNameReversed(s)
Willison, Simon
</pre>
<p>上面的写法虽然可以满足要求，但是看起来很麻烦，因为需要在全局名字空间中写很多函数。既然函数本身就是对象，如果需要使一个函数隶属于一个对象，那么不难得到：</p>
<pre class="brush: js">
function makePerson(first, last) {
    return {
        first: first,
        last: last,
        fullName: function() {
            return this.first + ' ' + this.last;
        },
        fullNameReversed: function() {
            return this.last + ', ' + this.first;
        }
    }
}
&gt; s = makePerson("Simon", "Willison")
&gt; s.fullName()
Simon Willison
&gt; s.fullNameReversed()
Willison, Simon
</pre>
<p>上面的代码里有一些我们之前没有见过的东西：关键字 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/this"><code>this</code></a>。当使用在函数中时，<code>this</code> 指代当前的对象，也就是调用了函数的对象。如果在一个对象上使用<a href="https://developer.mozilla.org/en/JavaScript/Reference/Operators/Member_Operators">点或者花括号</a>来访问属性或方法，这个对象就成了 <code>this</code>。如果并没有使用“点”运算符调用某个对象，那么 <code>this</code> 将指向全局对象（global object）。这是一个经常出错的地方。例如：</p>
<pre class="brush: js">
&gt; s = makePerson("Simon", "Willison")
&gt; var fullName = s.fullName;
&gt; fullName()
undefined undefined
</pre>
<p>当我们调用 <code>fullName()</code> 时，<code>this</code> 实际上是指向全局对象的，并没有名为 <code>first</code> 或 <code>last</code> 的全局变量，所以它们两个的返回值都会是 <code>undefined</code>。</p>
<p>下面使用关键字 <code>this</code> 改进已有的 <code>makePerson</code>函数：</p>
<pre class="brush: js">
function Person(first, last) {
    this.first = first;
    this.last = last;
    this.fullName = function() {
        return this.first + ' ' + this.last;
    }
    this.fullNameReversed = function() {
        return this.last + ', ' + this.first;
    }
}
var s = new Person("Simon", "Willison");
</pre>
<p>我们引入了另外一个关键字：<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/new"><code>new</code></a>，它和 <code>this</code> 密切相关。它的作用是创建一个崭新的空对象，然后使用指向那个对象的 <code>this</code> 调用特定的函数。注意，含有 <code>this</code> 的特定函数不会返回任何值，只会修改 <code>this</code> 对象本身。<code>new</code> 关键字将生成的 <code>this</code> 对象返回给调用方，而被 <code>new</code> 调用的函数成为构造函数。习惯的做法是将这些函数的首字母大写，这样用 <code>new</code> 调用他们的时候就容易识别了。</p>
<p>我们的人名对象现在已经相当完善了，但还有一些不太好的地方。每次我们创建一个人名对象的时候，我们都在其中创建了两个新的函数对象——如果这个代码可以共享不是更好吗？</p>
<pre class="brush: js">
function personFullName() {
    return this.first + ' ' + this.last;
}
function personFullNameReversed() {
    return this.last + ', ' + this.first;
}
function Person(first, last) {
    this.first = first;
    this.last = last;
    this.fullName = personFullName;
    this.fullNameReversed = personFullNameReversed;
}
</pre>
<p>这种写法的好处是，我们只需要创建一次方法函数，在构造函数中引用它们。那是否还有更好的方法呢？答案是肯定的。</p>
<pre class="brush: js">
function Person(first, last) {
    this.first = first;
    this.last = last;
}
Person.prototype.fullName = function() {
    return this.first + ' ' + this.last;
}
Person.prototype.fullNameReversed = function() {
    return this.last + ', ' + this.first;
}
</pre>
<p><code>Person.prototype</code> 是一个可以被<code>Person</code>的所有实例共享的对象。它是一个名叫原型链（prototype chain）的查询链的一部分：当你试图访问一个 <code>Person</code> 没有定义的属性时，解释器会首先检查这个 <code>Person.prototype</code> 来判断是否存在这样一个属性。所以，任何分配给 <code>Person.prototype</code> 的东西对通过 <code>this</code> 对象构造的实例都是可用的。</p>
<p>这个特性功能十分强大，JavaScript 允许你在程序中的任何时候修改原型（prototype）中的一些东西，也就是说你可以在运行时给已存在的对象添加额外的方法：</p>
<pre class="brush: js">
&gt; s = new Person("Simon", "Willison");
&gt; s.firstNameCaps();
TypeError on line 1: s.firstNameCaps is not a function
&gt; Person.prototype.firstNameCaps = function() {
    return this.first.toUpperCase()
}
&gt; s.firstNameCaps()
SIMON
</pre>
<p>有趣的是，你还可以给 JavaScript 的内置函数原型（prototype）添加东西。让我们给 <code>String</code> 添加一个方法用来返回逆序的字符串：</p>
<pre class="brush: js">
&gt; var s = "Simon";
&gt; s.reversed()
TypeError on line 1: s.reversed is not a function
&gt; String.prototype.reversed = function() {
    var r = "";
    for (var i = this.length - 1; i &gt;= 0; i--) {
        r += this[i];
    }
    return r;
}
&gt; s.reversed()
nomiS
</pre>
<p>定义新方法也可以在字符串字面量上用（string literal）。</p>
<pre class="brush: js">
&gt; "This can now be reversed".reversed()
desrever eb won nac sihT
</pre>
<p>正如我前面提到的，原型组成链的一部分。那条链的根节点是 <code>Object.prototype</code>，它包括 <code>toString()</code> 方法——将对象转换成字符串时调用的方法。这对于调试我们的 <code>Person</code> 对象很有用：</p>
<pre class="brush: js">
&gt; var s = new Person("Simon", "Willison");
&gt; s
[object Object]
&gt; Person.prototype.toString = function() {
    return '&lt;Person: ' + this.fullName() + '&gt;';
}
&gt; s
&lt;Person: Simon Willison&gt;
</pre>
<p>你是否还记得之前我们说的 <code>avg.apply()</code> 中的第一个参数 <code>null</code>？现在我们可以回头看看这个东西了。<code>apply()</code> 的第一个参数应该是一个被当作 <code>this</code> 来看待的对象。下面是一个 <code>new</code> 方法的简单实现：</p>
<pre class="brush: js">
function trivialNew(constructor) {
    var o = {}; // Create an object
    constructor.apply(o, arguments);
    return o;
}
</pre>
<p>这并不是一个 <code>new</code> 的精确副本，因为它没有创建原型（prototype）链。想举例说明 <code>apply()</code> 有些困难，因为你不会经常用到这个函数，但是适当了解一下还是很有用的。在这一小段代码里，<code>...args</code>（包括省略号）叫作<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/rest_parameters">剩余参数（rest arguments）</a>。如名所示，这个东西包含了剩下的参数。目前这个功能还处于试验阶段，仅在 Firefox 中提供支持，目前仍然建议使用 <code>argument</code>。</p>
<p>因此调用</p>
<pre class="brush: js">
var bill = trivialNew(Person, "William", "Orange");</pre>
<p>可认为和调用如下语句是等效的</p>
<pre class="brush: js">
var bill = new Person("William", "Orange");</pre>
<p><code>apply()</code> 有一个姐妹函数，名叫 <a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/call"><code>call</code></a>，它也可以允许你设置 <code>this</code>，但它带有一个扩展的参数列表而不是一个数组。</p>
<pre class="brush: js">
function lastNameCaps() {
    return this.last.toUpperCase();
}
var s = new Person("Simon", "Willison");
lastNameCaps.call(s);
// Is the same as:
s.lastNameCaps = lastNameCaps;
s.lastNameCaps();
</pre>
<h2 id=".E5.86.85.E9.83.A8.E5.87.BD.E6.95.B0">内部函数</h2>
<p>JavaScript 允许在一个函数内部定义函数，这一点我们在之前的 <code>makePerson()</code> 例子中也见过。关于 JavaScript 中的嵌套函数，一个很重要的细节是它们可以访问父函数作用域中的变量：</p>
<pre class="brush: js">
function betterExampleNeeded() {
    var a = 1;
    function oneMoreThanA() {
        return a + 1;
    }
    return oneMoreThanA();
}
</pre>
<p>如果某个函数依赖于其他的一两个函数，而这一两个函数对你其余的代码没有用处，你可以将它们嵌套在会被调用的那个函数内部，这样做可以减少全局作用域下的函数的数量，这有利于编写易于维护的代码。</p>
<p>这也是一个减少使用全局变量的好方法。当编写复杂代码时，程序员往往试图使用全局变量，将值共享给多个函数，但这样做会使代码很难维护。内部函数可以共享父函数的变量，所以你可以使用这个特性把一些函数捆绑在一起，这样可以有效地防止“污染”你的全局空间——你可以称它为“局部全局（local global）”。虽然这种方法应该谨慎使用，但它确实很有用，应该掌握。</p>
<h2 id=".E9.97.AD.E5.8C.85">闭包</h2>
<p>下面我们将看到的是 JavaScript 中必须提到的功能最强大的结构之一：闭包。但它可能也会带来一些潜在的麻烦。那它究竟是做什么的呢？</p>
<pre class="brush: js">
function makeAdder(a) {
    return function(b) {
        return a + b;
    }
}
x = makeAdder(5);
y = makeAdder(20);
x(6)
?
y(7)
?
</pre>
<p><code>makeAdder</code> 这个名字本身应该能说明函数是用来做什么的：它创建了一个新的 <code>adder</code> 函数，这个函数自身带有一个参数，它被调用的时候这个参数会被加在外层函数传进来的参数上。</p>
<p>这里发生的事情和前面介绍过的内嵌函数十分相似：一个函数被定义在了另外一个函数的内部，内部函数可以访问外部函数的变量。唯一的不同是，外部函数被返回了，那么常识告诉我们局部变量“应该”不再存在。但是它们却仍然存在——否则 <code>adder</code> 函数将不能工作。也就是说，这里存在 <code>makeAdder</code> 的局部变量的两个不同的“副本”——一个是 <code>a</code> 等于5，另一个是 <code>a</code> 等于20。那些函数的运行结果就如下所示：</p>
<pre class="brush: js">
x(6) // 返回 11
y(7) // 返回 27
</pre>
<p>下面来说说到底发生了什么。每当 JavaScript 执行一个函数时，都会创建一个作用域对象（scope object），用来保存在这个函数中创建的局部变量。它和被传入函数的变量一起被初始化。这与那些保存的所有全局变量和函数的全局对象（global object）类似，但仍有一些很重要的区别，第一，每次函数被执行的时候，就会创建一个新的，特定的作用域对象；第二，与全局对象（在浏览器里面是当做 <code>window</code> 对象来访问的）不同的是，你不能从 JavaScript 代码中直接访问作用域对象，也没有可以遍历当前的作用域对象里面属性的方法。</p>
<p>所以当调用 <code>makeAdder</code> 时，解释器创建了一个作用域对象，它带有一个属性：<code>a</code>，这个属性被当作参数传入 <code>makeAdder</code> 函数。然后 <code>makeAdder</code> 返回一个新创建的函数。通常 JavaScript 的垃圾回收器会在这时回收 <code>makeAdder</code> 创建的作用域对象，但是返回的函数却保留一个指向那个作用域对象的引用。结果是这个作用域对象不会被垃圾回收器回收，直到指向 <code>makeAdder</code> 返回的那个函数对象的引用计数为零。</p>
<p>作用域对象组成了一个名为作用域链（scope chain）的链。它类似于原形（prototype）链一样，被 JavaScript 的对象系统使用。</p>
<p>一个闭包就是一个函数和被创建的函数中的作用域对象的组合。</p>
<p>闭包允许你保存状态——所以它们通常可以代替对象来使用。<a href="http://stackoverflow.com/questions/111102/how-do-javascript-closures-work">这里</a>有一些关于闭包的详细介绍。</p>
<h3 id=".E5.86.85.E5.AD.98.E6.B3.84.E9.9C.B2">内存泄露</h3>
<p>使用闭包的一个坏处是，在 IE 浏览器中它会很容易导致内存泄露。JavaScript 是一种具有垃圾回收机制的语言——对象在被创建的时候分配内存，然后当指向这个对象的引用计数为零时，浏览器会回收内存。宿主环境提供的对象都是按照这种方法被处理的。</p>
<p>浏览器主机需要处理大量的对象来描绘一个正在被展现的 HTML 页面——<a href="https://developer.mozilla.org/zh-CN/docs/Web/API/Document_Object_Model">DOM</a> 对象。浏览器负责管理它们的内存分配和回收。</p>
<p>IE 浏览器有自己的一套垃圾回收机制，这套机制与 JavaScript 提供的垃圾回收机制进行交互时，可能会发生内存泄露。</p>
<p>在 IE 中，每当在一个 JavaScript 对象和一个本地对象之间形成循环引用时，就会发生内存泄露。如下所示：</p>
<pre class="brush: js">
function leakMemory() {
    var el = document.getElementById('el');
    var o = { 'el': el };
    el.o = o;
}
</pre>
<p>这段代码的循环引用会导致内存泄露：IE 不会释放被 <code>el</code> 和 <code>o</code> 使用的内存，直到浏览器被彻底关闭并重启后。</p>
<p>这个例子往往无法引起人们的重视：一般只会在长时间运行的应用程序中，或者因为巨大的数据量和循环中导致内存泄露发生时，内存泄露才会引起注意。</p>
<p>不过一般也很少发生如此明显的内存泄露现象——通常泄露的数据结构有多层的引用(references)，这种情况下循环引用不会导致过于严重的后果。</p>
<p>闭包很容易发生无意识的内存泄露。如下所示：</p>
<pre class="brush: js">
function addHandler() {
    var el = document.getElementById('el');
    el.onclick = function() {
        this.style.backgroundColor = 'red';
    }
}
</pre>
<p>这段代码创建了一个元素，当它被点击的时候变红，但同时它也会发生内存泄露。为什么？因为对 <code>el</code> 的引用不小心被放在一个匿名内部函数中。这就在 JavaScript 对象（这个内部函数）和本地对象之间（<code>el</code>）创建了一个循环引用。</p>
<p>这个问题有很多种解决方法，最简单的一种是不要使用 <code>el</code> 变量：</p>
<pre class="brush: js">
function addHandler(){
    document.getElementById('el').onclick = function(){
        this.style.backgroundColor = 'red';
    };
}
</pre>
<p>有趣的是，有一种破坏因为闭包引入循环引用的窍门是添加另外一个闭包：</p>
<pre class="brush: js">
function addHandler() {
    var clickHandler = function() {
        this.style.backgroundColor = 'red';
    };
    (function() {
        var el = document.getElementById('el');
        el.onclick = clickHandler;
    })();
}
</pre>
<p>内部函数被直接执行，并在 <code>clickHandler</code> 创建的闭包中隐藏了它的内容。</p>
<p>另外一种避免闭包的好方法是在 <code>window.onunload</code> 事件发生期间破坏循环引用。很多库都能完成这项工作。注意这样做将使 <a href="https://developer.mozilla.org/en-US/docs/Using_Firefox_1.5_caching"> Firefox 1.5 中的 bfcache</a> 无法工作。所以除非有其他必要的原因，最好不要在 Firefox 中注册一个<code>unload</code> 的监听器。</p>
<div class="note">
 <p><span style="line-height: 1.5;"><strong>备注：</strong>在这篇文档完成后 JavaScript 加入了其他特性。尽管如此，这篇文档还是很有价值的参考文档。</span></p>
</div>
<p>&nbsp;</p>