## DOM Enlightenment  
notes and exercises for the textbook with the same name by Cody Lindley  

### Ch1 - Node Overview    

#### The Document Object Model (DOM)  

+ hierarchy/tree of javascript node objects    
+ the purpose of DOM is to creat a programmatic interface for scripting the live document using javascript    

``` javascript
// use this to read all the node types and their numeric values  
console.log(Node.ELEMENT_NODE);

for (var k in Node){
	console.log(k, ' = ' +Node[k]);
}

/* *** output in chrome ***
ELEMENT_NODE  = 1
VM410:2 ATTRIBUTE_NODE  = 2  
VM410:2 TEXT_NODE  = 3  
VM410:2 CDATA_SECTION_NODE  = 4  
VM410:2 ENTITY_REFERENCE_NODE  = 5  
VM410:2 ENTITY_NODE  = 6
VM410:2 PROCESSING_INSTRUCTION_NODE  = 7  
VM410:2 COMMENT_NODE  = 8
VM410:2 DOCUMENT_NODE  = 9  
VM410:2 DOCUMENT_TYPE_NODE  = 10
VM410:2 DOCUMENT_FRAGMENT_NODE  = 11  
VM410:2 NOTATION_NODE  = 12  
VM410:2 DOCUMENT_POSITION_DISCONNECTED  = 1
VM410:2 DOCUMENT_POSITION_PRECEDING  = 2
VM410:2 DOCUMENT_POSITION_FOLLOWING  = 4
VM410:2 DOCUMENT_POSITION_CONTAINS  = 8
VM410:2 DOCUMENT_POSITION_CONTAINED_BY  = 16
VM410:2 DOCUMENT_POSITION_IMPLEMENTATION_SPECIFIC  = 32
*/

```
+  subnode objects inherit from the node object  
+ ATTRIBUTE_NODE is not actually part of a tree, but rather is listed for historical reasons.  It will be removed in DOM4

```
Object < Node < Element < HTMLElement < (e.g., HTML*Element)   
Object < Node < Attr (this is deprecated in DOM4)  
Object < Node < CharacterData < Text  
Object < Node < Document < HTMLDocument  
Object < Node < DocumentFragment  

```  

### 1.5 Identify Type and Name of a Node  
+ every node has a nodeType and nodeName property that is inherited from Node object.  
+ for ex, **Text** nodes have a nodeType code of 3 and a nodeName value of #text  
+  the numeric value 3 is a numeric code representing the type of underlying object the node represents  

+ it is good to memorize these 5 nodeTypes and nodeNames  
+ (see ex5 html file) 

htmlElement (HTMLBodyElement) 1    
Text 3  
Attr 2  
HTMLDocument 9  
DocumentFragment 11  
DocumentType 10    

### 1.6 Getting a Node's Value  
+ nodeValue property returns *null* for most of the node types, expect Text and Comment  

+ the nodeValue is centered for dealing with texts   

+ logs null for DOCUMENT_TYPE_NODE, DOCUMENT_NODE, DOCUMENT_FRAGMENT_NODE, ELEMENT_NODE with the code below in your browser   

``` javascript
	console.log(document.doctype.nodeValue); 
	console.log(document.nodeValue);
	console.log(document.createDocumentFragment().nodeValue);
	console.log(document.querySelector('a').nodeValue);

	// logs string of text 
	console.log(document.querySelector('a').firstChild.nodeValue);  

/* output

console.log(document.doctype.nodeValue);
conole.log(document.nodeValue);
console.log(document.createDocumentFragment().nodeValue);
console.log(document.querySelector('a').nodeValue);
VM658:2 null
VM658:3 null
VM658:4 null
VM658:5 null
undefined
console.log(document.querySelector('a').firstChild.nodeValue); 
VM659:2 Hi
undefined

*/
```

### 1.7 Using JS Methods to Create Element and Text Nodes  

+  browser parses html doc, contructs nodes and tree based on contents of html file  

+  the browser deals with the creation of nodes for initial loading of the html document  

+  however, it is possible to create your own nodes using JS  

**There are two methods to allow us to programmically create Element and Text nodes using JS:**      
	+  createElement()  
	+  createTextNode()  

+ other methods are available like createAttribute() and createComment() but they are not commonly used    

+ createAttribute() meothod is deprecated and shouldn't be used    

### 1.8 Using JS Strings to Create and Add Element and Text Nodes to the DOM  

+  the innerHTML, outerHTML, textContent, and insertAdjacentHTML() properties and methods are used to create and add nodes to the DOM  

``` javascript

// more practice
	// img tag is placed inside the div container with the id='A'
	document.getElementById('A').innerHTML = '<img src="http://s3.amazonaws.com/digitaltrends-uploads-prod/2015/04/imgur-embed-2.jpg">image</img>';

	// the new div completely replaced the old div container with nested img inside
	document.getElementById('A').outerHTML = '<div id="A" class="new">I just replaced the img tag with this div </div>'

```

+ try using *insertAdjacentHTML()* method for more precision  
+ this method only works with Element nodes, use it to insert nodes before the beginning tag, after the beginning tag, before the end tag, and after the end tag  

for example  

``` javascript

// put this in the html:  <i> id="elm">how</i>

// try out in the console
var elm = document.getElementById('elm');
elm.insertAdjacentHTML('beforebegin', '<span>Hey-</span>');
elm.insertAdjacentHTML('afterbegin', '<span>dude-</span>');
elm.insertAdjacentHTML('beforeend', '<span>-are</span>');
elm.insertAdjacentHTML('afterend', '<span>-you?</span>');
console.log(document.body.innerHTML);
/* logs
<span>Hey-</span><i id="A"><span>dude-</span>how<span>-are</span></i>
<span>-you?</span>
*/


```


### 1.9 Extracting Parts of the DOM Tree as Javascript Strings   

+  the exact same properties (innerHTML, outerHTML, textContent) for adding nodes can be used to extract parts of the DOM  

``` javascript
console.log(document.getElementById('A').innerHTML);
console.log(document.getElementById('A').outerHTML);
console.log(document.getElementById('A').textContent);

``` 

+ the textContent, innerText, and outerText while being read, will return all the text nodes contained within the selected node  

### 1.0 Using appendChild() and insertBefore() to add node Objects to the DOM  

+  appendChild() - append a node or multiple nodes to the end of the child node(s) of the node the method is called on  

+  if there is no child node, the node being appended will be the first child node  

``` javascript
// console log

// create the txt node
var tx = document.createTextNode('testing testing')
undefined

tx
"testing testing"

// create the list element
var li = document.createElement('li');
undefined

// add txt node in li
li.appendChild(tx);
"testing testing"
li
<li>​testing testing​</li>​

// grab the ul tag in the DOM

var ul = document.querySelector('ul')
undefined
ul
<ul>​
	<li>​1​</li>​
	<li>​2​</li>​
	<li>​3​</li>​
</ul>​

// insert the li in the selected ul as the first child
ul.insertBefore(li, ul.firstChild);
<li>​testing testing​</li>​

// view the html document 
console.log(document.body.innerHTML);
VM11591:2 
		<p>Test, I am inside p tag.  
			<strong>this should be bold</strong>
		</p>

		<ul>
			<li>testing testing</li>
			<li>1</li>
			<li>2</li>
			<li>3</li>
		</ul>

undefined
```
### 1.11 removeChild() and replaceChild() to Remove and Replace Nodes  

Removing a node form the DOM requires several steps:  
	1.  select the node you want to remove  
	2.  gain access to its parent element, usu by using **parentNode** property  
	3.  on the parent node, invoke the **removeChild()**, passing it the reference to the node to be removed  

``` 
// html file, in ex10 
<div id="A">Hi</div>
<div id="B">Dude</div>

// console code 

var divA = document.getElementById('A');
undefined

divA
<div id=​"A">​Hi​</div>​

// divA is removed
divA.parentNode.removeChild(divA)
<div id=​"A">​Hi​</div>​


// only grabbing the "Dude" text
var divB = document.getElementById('B').firstChild;
undefined

divB
"Dude"

// note how the div is still there, only the text is removed  
divB.parentNode.removeChild(divB);
"Dude"

console.log(document.body.innerHTML);
VM13778:2 
		<p>Test, I am inside p tag.  </p>

		<ul>
			<li>2</li>
			<li>3</li>
		</ul>

		<!-- for testing ex 11 -->
		
		<div id="B"></div>


		<script>
		//create a blink element node and text node
		// var elementNode = document.createElement('strong');
		// var textNode = document.createTextNode('this should be bold');
		
		// //append these nodes to the DOM
		// document.querySelector('p').appendChild(elementNode); 
		// document.querySelector('strong').appendChild(textNode);

		//log's <p>Hi<strong> Dude</strong></p>
		//console.log(document.body.innerHTML);
		</script>
	

undefined 
```


	





