## Chapter 3 Element Nodes  

Each element in an HTML document has a unique JS constructor that instatntiatses the element as a node obj in the DOM tree  

Some important properties:  

```
• createElement()  
• tagName
• children
• getAttribute()
• setAttribute()
• hasAttribute()
• removeAttribute() • classList()
• dataset
• attributes

```

### 3.5 Getting a List/Collection of Element Attributes and Values   

see ex3.5  

### 3.6 Getting, Setting, and Removing an Element's Attribute Value  




``` javascript
var atts = document.querySelector('a');
    //remove attributes

atts.removeAttribute('href'); 
atts.removeAttribute('title'); 
atts.removeAttribute('style'); 
atts.removeAttribute('data-foo'); atts.removeAttribute('class'); 
atts.removeAttribute('foo'); //custom attribute atts.removeAttribute('hidden'); //boolean attribute

//set (really re-set) attributes
atts.setAttribute('href','#');
atts.setAttribute('title','title');
atts.setAttribute('style','margin:0;'); atts.setAttribute('data-foo','dataFoo');
atts.setAttribute('class','yes');
atts.setAttribute('foo','boo');
atts.setAttribute('hidden','hidden'); 

/* boolean attribute requires sending the attribute as the value too */

//get attributes
console.log(atts.getAttribute('href')); 
console.log(atts.getAttribute('title')); 
console.log(atts.getAttribute('style')); 
console.log(atts.getAttribute('data-foo')); 
console.log(atts.getAttribute('class')); 
console.log(atts.getAttribute('foo')); 
console.log(atts.getAttribute('hidden'));
```

