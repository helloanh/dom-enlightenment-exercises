## DOM Enlightenment  
notes and exercises for book with the same name by Cody Lindley  

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

+ logs null for DOCUMENT_TYPE_NODE, DOCUMENT_NODE, DOCUMENT_FRAGMENT_NODE, ELEMENT_NODE with the code below in your browser */  

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

+ browser parses html doc, contructs nodes and tree based on contents of html file  

+ the browser deals with the creation of nodes for initial loading of the html document  

+ however, it is possible to create your own nodes using JS  

** There are two methods to allow us to programmically create Element and Text nodes using JS: **    
		+ createElement()  
		+ createTextNode()  

+ other methods are available like createAttribute() and createComment() but they are not commonly used    

+ createAttribute() meothod is deprecated and shouldn't be used    

### 1.7 






