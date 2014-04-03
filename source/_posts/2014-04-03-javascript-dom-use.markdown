
JavaScript DOM基础操作实例

文档对象模型(Document Object Model)，通常简称为DOM，是网站内容与JavaScript互通的接口。自JavaScript成为最常用的语言时JavaScript和DOM通常被视为独立的实体。DOM接口用于存取、遍历和控制HTML和XML文档。下面我们将简单的介绍一些JavaScript DOM的基本操作实例，包括建立、增加、删除、克隆、访问节点等等。

## getElementById(id)  

这是通过`id`来访问某一元素，最常用的之一，例：

	<html> 
	         <body> 
	         <div id="myid"> 
	         test  
	         </div> 
	         <script language="javascript"> 
	         alert(document.getElementById("myid").innerHTML);  
	         </script> 
	         </body> 
	</html> 

注意点：如果元素的`ID`不是唯一，则会取得第一个该`ID`名称的元素。

## getElementsByName(name)  	

这是通过`name`来取得某一堆元素（作为数组），看 `Element`后面有个小`s`就知道了，`ID`是`HTML`文档中要求唯一的，`name`可以不是唯一，如`checkbox`、`radio`等地方会用到多个`input`用同一个`name`来识别是否为同党。对了，`getElementsByName(name)`仅用于取得`input`、`radio`、 `checkbox`等元素，如

	<input name="myradio" type="radio" />。


## getElementsByTagName(tagname)

看这方法就知道这也是取得某一堆元素（作为数组），是通过`TagName`也就是标签名来取得。你可以遍历这个数组获得每一个单独的元素。当一个`DOM`结构很大时，可以通过它来有效地缩小搜查范围。    

	<html>           
         <head> 
         <script> 
         function test() {  
         testall=document.getElementsByTagName("body");  
         testbody=testall.item(0); //获得所有tagName是body的元素（当然每个页面只有一个）  
         testall=testbody.getElementsByTagName("p");// 获得body子元素种的所有P元素  
         testnode=testall.item(1); // 获得第二个P元素           
         alert(testnode.firstChild.nodeValue); //显示这个元素的文本         }  
         </script> 
         </head> 
         <body> 
         <p>hi</p> 
         <p>hello</p> 
         <script language="javascript"> 
         test();  
         </script> 
         </body> 
	</html> 

## appendChild(node)

向当前的元素（应该叫对象比较恰当）追加节点。  

	<html> 
         <body> 
         <head> 
         </head> 
         <div id="test"></div> 
         <script type="text/javascript"> 
         var newdiv=document.createElement("div")  
         var newtext=document.createTextNode("A new div")           
         newdiv.appendChild(newtext)  
         document.getElementById("test").appendChild(newdiv)  
         </script> 
         </body> 
	</html> 

刚才我在第一个例子中为了显示出内容，用了`innerHTML`，刚才看到文章才得知`innerHTMl`不属于`DOM`。 

## removeChild(childreference)

删除当前节点的子节点，返回被删除的节点。这个被删除的节点可以被插入到别的地方。

	<html> 
         <body> 
         <div id="parent"><div id="child">A child</div></div> 
         <script language="javascript"> 
         var childnode=document.getElementById("child")  
         var removednode=document.getElementById("parent").removeChild(childnode)  
         </script> 
         </body> 
	</html> 


## cloneNode(deepBoolean)

复制并返回当前节点的复制节点，复制节点是一个孤立节点，它复制了原节点的属性，在把这个新节点加入到`document`前，根据需要修改`ID`属性确保其`ID`的唯一。这个方法支持一个布尔参数，当`deepBoolean`设置`true`时，复制当前节点的所有子节点，包括该节点内的文本。

	<html> 
         <body> 
         <p id="mynode">test</p> 
         <script language="javascript"> 
         p=document.getElementById("mynode")   
        ppclone = p.cloneNode(true);  
         p.parentNode.appendChild(pclone);  
         </script> 
         </body> 
	</html> 

## replaceChild(newChild, oldChild)

把当前节点的一个子节点换成另一个节点。

	<html> 
         <body> 
         <div id="mynode2"> 
         <span id="orispan">span</span> 
         </div> 
         <script language="javascript"> 
         var orinode=document.getElementById("orispan");  
         var newnode=document.createElement("p");  
         var text=document.createTextNode("test ppp ");  
         newnode.appendChild(text);  
         document.getElementById("mynode2").replaceChild(newnode, orinode);  
         </script> 
         </body> 
	</html> 

