## Chapter 2 Document Nodes  

HTMLDocument constructor creates a DOCUMENT_NODE (the window.document object)  


you can check by calling 
```
window.document.constructor 
// which return the function HTMLDocument()  

window.document.nodeType 
// which return 9, the numeric key mapping to DOCUMENT_NODE 

```

Many properties are available, even if the inherited properties were not considered. I’ve handpicked a list of noteworthy properties and methods for the context of this chapter:  

	• doctype  
	• documentElement   
	• implementation.*   
	• activeElement  
	• body  
	• head  
	• title  
	• lastModified  
	• referrer  
	• URL  
	• defaultview  
	• compatMode  
	• ownerDocument  
	• hasFocus()  

### 2.3 Getting General HTML Document Info  

+ you can get general info on the document such as title, URL, referrer, lastModified, compatMode    

``` javascript
var d  = document
d.title
d.URL
d.referrer
d.lastModified
d.compatMode
```

