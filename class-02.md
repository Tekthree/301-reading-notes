### 301 Reading Notes

## Class -02


# jQuery

- jQuery lets you select css elements then do something with that element.

- the jQuery object has many methods thatt you can use to work with elements you select.

- in jQuery you have the jQuery object followed by a ```.``` then the method and inside the method youll have the parameters.

```
$('li.hot').addClass('complete');

```

- add jQuery to a page by adding the script source tag and linking to the Javascript libarary.

- jQuery making coding simpler. There is nothing it can do that plan javascript can't, but i does take less code to do it. 

- page 302 has a big list of selectors 

- page 304 has a big list of methods.

- when you select more than one elements a jQuery object is returned, known as a matched set. It is stored like an index array, starting at 0.

- some methods only get infor from the first element of the set. like ```html``` but if you use ``` each()``` then you can grab all

- if you want to update the info in the element, then ```html()``` would update all the elements in the set. 

- jQuery objects only store refrences to elements.

- when storing a variable that is a refrence to jQuery object it is often given a name begining with the $ to differentiate it from other variable.

```
$listItems = $("li");
```

## Looping

- looping in jQuery, if I wanted to add a class to multiple elements in plain javascript I would have to write a for loop. In jQuery there are methods that will do all of that for you.

```
$("li").addClass('seasonal');

```

- the ability to update all the elements in the jQuery selection is known as implicit iteration.

- the process of placing several methods in the same selector is referred to as chaining. 

```
$('li[id!='one']').hide().delay().fadeIn(1400);
```

- if one method in the chain doesn't work, then the rest of the methods won't work either.

- Make sure that the HTML document is fully loaded before working with it 
 
 ```
 $(document).ready(function() {

   // jQuery code goes here
});

```

```$``` is used to access the jQuery then accesses the document object 
    
    
- since the code is used almost everytime that you use jQuery, there is a short hand version.

```
$(function() {

   // jQuery code goes here
});

```

- jQuery is used to select HTML elements and perform actions on them. 

- the basic syntax is : ``` $("selector").action()```

```
$("p").hide()  // hides all <p> elements

$(".demo").hide()  // hides all elements with class="demo"
$("#demo").hide()  // hides the element with id="demo"
```

- you can also select all div elements with a class name of menu

```
$("div.menu") 
```

- ![jQuery selectors](https://api.sololearn.com/DownloadFile?id=3119)


- you can manipulate attributes assigned to HTML elements easily through jQuery

- the ``` attr() ``` method is used for getting the value of an attribute.

```
$(function() {

  var val = $("a").attr("href");

  alert(val);

});
// alerts "www.sololearn.com"
JSTry it Yourself

```

- above will get the value of the href from the a tag


- the attr() method allows you to set a value for an attribute by specifying it as the second parameter

```
$( function() {

  $("a").attr("href", "http://www.jquery.com");
  });
  
 ```
 
 - to remove attributes from an element use the ``` removeAttr() ``` method
 
 ```
 $("table").removeAttr("border");
 ```

 
- you can use ``` val() ``` to set the value or get the value


```
$(function() {
  alert($("#name").val());
 });
 
 ```


- ```text()``` sets or returns the text content of selected elements.
- ```html()``` sets or returns the content of selected elements (including HTML markup).
- ```val()``` sets or returns the value of form fields.
- ```attr()``` sets or returns the value of attributes.
- ```removeAttr()``` removes the specified attribute

- ```append()``` inserts content at the end of the selected elements.
- ```prepend()``` inserts content at the beginning of the selected elements.
- ```after()``` inserts content after the selected elements.
- ```before()``` inserts content before the selected elements.




- adding new elements then text to the element 


# Manipulating CSS

- The ```addClass()``` method adds one or more classes to the sleected elements.

```
$("div").addclass("header");

```

- this will add a class to the html div

- the ```removeClass()``` method removes one or more class names from the selected elements. 

```
$("div").removeClass("red");
```

- the ```toggleClass()``` method togggles between adding/removing classes from the selected elements.

```
$(function(){
  
  $("button").click(function(){

    $("p").toggleClass("red");

  });



});

```

# CSS properties

- like the ```html()``` methods, the css() method can be used to get and set CSS property

``` 
$(function() {
   alert($("p").css("background-color"));

   $("p").css("background-color", "blue");
});

```

- the above code alerts the p elements background color then set the background color to blue

- to set mulitple properties we can use JSON syntax

```
css({"property":"value","property":"value"});

```

``` 
$("p").css({"color":"red", "font-size": "200%"});

```

- use the ```height()``` and ```width()``` to set height and width of an element

```
$("div").width(100);
$("div").height(100);

```

- The width() and height() methods get and set the dimensions without the padding, borders and margins.
- The innerWidth() and innerHeight() methods also include the padding.
- The outerWidth() and outerHeight() methods include the padding and borders.


# Manipulate Dom

- jQuery makes it easy to traverse the DOM and work with HTML elements

- The ```<html>``` element is the parent of ```<body>``` and an ancestor of everything below it.
The ```<body>``` element is the parent of the ```<h1>``` and ```<a>``` elements.
The ```<h1>``` and ```<a>``` elements are child elements of the ```<body>``` element and descendants of ```<html>```.
The ```<h1>``` and ```<a>``` elements are siblings (they share the same parent).

Summary
An ancestor is a parent, grandparent, great-grandparent, and so on.
A descendant is a child, grandchild, great-grandchild, and so on.
Siblings share the same parent.

- the ```parent()``` method returns the direct parent element of the selected element. 

```
var e = $("p").parent();

e.css("border", "2px solid red");

```

- the ```parent()``` method can only traverse up one but the ```parents()``` method gets all ancestors of the selected element.

```
$(function(){
  var e = $("p").parents();
  
  e.css("border", "2px solid red");

});

```

- some of the more used methods for taversals are

![traversal methods](https://api.sololearn.com/DownloadFile?id=3044)

- ``` eq() ``` method can be used to select a specific element from multiple selected elements. The index start at zero so if you want the the third div you would use the number  2

```
$("div").eq(2);
```


# Removing Elements

- remove selected elements from the DOM using the remove() method

```
$("p").eq(1).remove();

```

- use the ```empty()``` method to remove all children from a selected element

```
$("div").empty();

```

## Handling Events

- jQuery provides some effective ways to handle events. 

- When an event occurs on a target element, a handler function is executed.

```
var x = document.getElementById("demo");

x.onclick = function() {
  document.body.innerHTML = Date();

} 

```

- the above is Javascrip but to do the same thing in jQuery would be smaller code. 

```
$("#demo").click(function(){
  $("body").html(Date());
});

```


# Common Events

- Mouse Events:

  click occurs when an element is clicked.
  dblclick occurs when an element is double-clicked.
  mouseenter occurs when the mouse pointer is over (enters) the selected element.
  mouseleave occurs when the mouse pointer leaves the selected element.
  mouseover occurs when the mouse pointer is over the selected element.

- Keyboard Events:

  keydown occurs when a keyboard key is pressed down.
  keyup occurs when a keyboard key is released.

- Form Events:

  submit occurs when a form is submitted.
  change occurs when the value of an element has been changed.
  focus occurs when an element gets focus.
  blur occurs when an element loses focus.

- Document Events:

  ready occurs when the DOM has been loaded.
  resize occurs when the browser window changes size.
  scroll occurs when the user scrolls in the specified element. 

- An example of a keydown event will be as follows. Adding a event to id name then displaying  the value of the name field to the id msg div.

```
$("#name").keydown(function){
  $("#msg").html($("#name").val());
});

```

- another way to handle events in jQuery is by using the ```on()```method. This makes it so you can add multiple events to one event handler.


```
$("p").on("click",Function(){
  alert("clicked");
});

```

- You can remove event handlers using the off method

```
$("div").on*("click", function(){
  alert("Hi there!");
  $("div").off("click");
});

```


- every event handling function can receive an event object, which contains properties and methods related to the event, such as the mouse position, type, which, data, target, preventdefault.

```
$("a").click(function(event){
  alert(event.pageX);
event.preventDefault();
}):

```

## Trigger Events

- you can programmatically trigger events using the ```trigger()```.

```
$("div").trigger("click");
```

- this is an example of making a todo list. We first handle the click event for the button. We select the value for the input field and reassign it to a newly created li element. The we take the input value and check if it is empty... in not then create new li, add a button for removing, append the new li to the list div lastley clear the input. the last bit of code is handling the 

```

$(function()){
  $("#add").on("click,function(){
    var val = $("input).val();

    if(val !== ''){
      var elem = $("<li></li>").text(val);
      $(elem).append("<button class='rem'>X</button>");
      $("#mylist").apppend(elem);
      $("input").val("");

      $(".rem").on("click", function(){
        $(this).parent().remove();
      });
    }
  });
});

```




## Hide/Show

- jQuery has come easy-t0-implement effects to create animations

- the ```hide()``` and ```show()``` methods are used to hide and show the selected elements. or you can use the ```toggle()``` method to toggle between hiding and showing


```
$(function(){
  $("p").click(function(){
    $("div").toggle(1000);
  });
});

```

- the fade in/out using ```fadeToggle(1000)```

- ``` slideUp()``` and ```slideDown()``` are used to create a slideing effect on elements. ```slideToggle()```



```
$("div").animate({

  width: '+=250px',

  height: '+=250px'
}, 1000);


```

- jQuery runs the animate calls one by one

```
$(function() {
    var div = $("div");
    div.animate({opacity: 1});
    div.animate({height: '+=100px', width: '+=100px', top: '+=100px'}, 500);
    div.animate({height: '-=100px', width: '-=100px', left: '+=100px'}, 500);
    div.animate({height: '+=100px', width: '+=100px', top: '-=100px'}, 500);
    div.animate({height: '-=100px', width: '-=100px', left: '-=100px'}, 500);
    div.animate({opacity: 0.5});
}); 

```


- create a dropdown menu that will open upon clicking on the menu

```
$("#item").click(function() {

  $("#submenu").slideToggle(500);
}); 

```

## Paired Programming

- Paired Programming commonly involves two roles. The Driver and the Navigator. The Driver is the programmer who is typing and the only one whose hands are on the keyboard. The Navigator uses their words to guide the Driver but does not type. 

- Paired programming helps you with vocabulary Speaking, idea Reading, and writing code from scratch.

- Pair programming touches on all four skills: developers explain out loud what the code should do, listen to others’ guidance, read code that others have written, and write code themselves.

- when two people focus on the same code base, it is easier to catch mistakes

- Often times, the developers in a pairing have different skill sets. If one programmer is more experienced in a certain skill, they can teach a student who is less familiar with that area.