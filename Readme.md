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
