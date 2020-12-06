### 301 Reading Notes

## Class -01


# Shay Howe’s intro to RWD

- Responsive web design is the practice of building a website suitable to work on every device and screen size, no matter how large or small.

- Responsive web design is centered around user experience.

- The term Responsive web design was coined by Ethan Marcotte and in his book Responsive Web Design.

- With responsive design websites continually and fluidly change based on different factors, such as viewport width, while adaptive websites are built to a group of preset factors.

- flexible layouts, is the practice of building the layout of a website with a flexible grid, capable of dynamically resizing to any width.

- Flexible grids are built using relative length units, most commonly percentages or em units.

- view port with or hight is a flexable unit to use for measurment. 

- Using percents we can use flexible units to make a flexable grid

``` 
section,
aside {
  margin: 1.858736059%; /*  10px ÷ 538px = .018587361 */
}
section {
  float: left;
  width: 63.197026%;    /* 340px ÷ 538px = .63197026 */   
}
aside {
  float: right;
  width: 29.3680297%;  /* 158px ÷ 538px = .293680297 */
}

```

- for even more control within a flexible layout, you can also leverage the min-width, max-width, min-height, and max-height properties.

- Media queries provide the ability to specify different styles for individual browser and device circumstances, the width of the viewport or device orientation for example

- to call media queries 

css

``` 
/* @media Rule */
@media all and (max-width: 1024px) {...}

/* @import Rule */
@import url(styles.css) all and (max-width: 1024px) {...}

```
- Using logical operators in Media Queries

```
@media all and (min-width: 800px) and (max-width: 1024px) {...}
```

- Media features identify what attributes or properties will be targeted within the media query expression.

- Within responsive design the most commonly used features include min-width and max-width. 

```

@media all and (min-width: 320px) and (max-width: 780px) {...}

```

## SMACSS

- SMACSS is a way to examine your design process and as away to fit those rigid frameworks into a flexible thought process.

- It is a document of a consistent approach to site development when using CSS

- At the very core of SMACSS is categorization.

- The 5 categorizations are. Base. Layout. Module. State. Theme

- 

- The orientation media feature determines if a device is in the landscape or portrait orientation. The landscape mode is triggered when the display is wider than taller, and the portrait mode is triggered when the display is taller than wider.



```
@media all and (orientation: landscape) {...}

```

- for all devices under 420px

```
@media all and (max-width: 420px) {
  section, aside {
    float: none;
    width: auto;
  }
}

```

- Mobile First Approuch. One popular technique with using media queries is called mobile first. The mobile first approach includes using styles targeted at smaller viewports as the default styles for a website, then use media queries to add styles as the viewport grows.

```
/* Default styles first then media queries */
@media screen and (min-width: 400px)  {...}
@media screen and (min-width: 600px)  {...}
@media screen and (min-width: 1000px) {...}
@media screen and (min-width: 1400px) {...}
```

- For the best results, and the best looking website, it is recommend that you use the device defaults by applying the device-height and device-width values.

```
<meta name="viewport" content="width=device-width">
```

- and how users can continue to scale a website, use the minimum-scale, maximum-scale, initial-scale, and user-scalable properties.

- Lost over Half of my notes. No save in Github ... gonna start writing my notes in VSCode


## Jquery 

- Jquery is a javascript library
- jquery is accessed through javascript

- With jquery I can do some the things I would do in javascript with smaller amounts of code.

- like 
```
var el = document.getElementById("start");
el.innerHTML = "Go";
```
- would be shortned to this is jquery

```
$("#start").html("Go");
```

- to start using jquery we need to add it to the html head as a script source.

```
    <head>

        <title>Page Title</title>
<script src="https://code.jquery.com/jquery-3.1.1.js"></script>

    </head>
    
 ```
 
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
