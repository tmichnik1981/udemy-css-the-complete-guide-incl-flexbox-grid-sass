# CSS the complete guide incl flexbox grid-sass

#### Basics of CSS

##### Theory Selectors

- Elements

```
h1 {
    color: red;
}
```

- Classes

```
.blog-post{
    color: red;
}
```

* Universal

```
*{
    color:red;
}
```

- IDs

```
#main-title{
    color: red;
}
```

- Attributes

```
[disabled]{
    color: red;
}
```

##### Specificity

1. Inline Styles
2. \#ID selectors
3. .class, :pseudo-class and [attribute] selectors
4. <Tag> and ::pseudo-element selectors

##### Inheritance

- Elements inherit styles from their parents (direct or indirect)

##### Combinators

- Applies style to any `<h1>` in element with id = product-overview

```
#product-overview h1 {
}
```

- Combined selectors have higher specificity than single selector

- Types:

  - Adjacent Sibiling - applies to all `<p>` which directly follows `<div>`

  - Elements share the same parent

    ```
    div + p {
    }
    ```


  - Example: changes applies to all `<li>` except the first one

    ```
    li + li {
        background-color: black;
        color: white;
    }
    ```

  - General Sibling applies to all `<p>` which lays next to `<div>` (unnecessary directly)

  - Elements share the same parent

    ~~~
    div ~ p {
        
    }
    ~~~

  - Child - applies to `<p>` which are the direct children of  `<div>`

    ```
    div > p{
        
    }
    ```

  - Descendant

    ```
    div p {
        
    }
    ```


##### Resources and links

- Complete MDN CSS Reference (don't learn this by heart!): <https://developer.mozilla.org/en-US/docs/Web/CSS/Reference>
- Are you a reading guy? Find written CSS docs on MDN: <https://developer.mozilla.org/en-US/docs/Web/CSS>
- Common CSS Properties Reference: <https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Properties_Reference>
- CSS Combinators: <https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors>
- More details on CSS Specifity: <https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity>

#### Diving Deeper into CSS

##### Box model

- content <-> padding <-> border <-> margin 

  ```css
  #product-overview{
      background: #ff1b68;
      padding: 20px;
      border: 5px black solid;
      margin: 20px;
  }
  ```

##### Margin Collapsing

- If 2 elements have margins, only the bigger one is taken into account

##### Shorthand property

```
border: 2px dashed orange

margin: 5px 10px 5px 10px
```

##### Height and Width properties

- Block elements always take 100% of horizontal space 

```
width: 50%;
width: 70px;

height: 100%; //100% of the parent
```

- Box sizing

```
// size of the content is calculated including border and padding
box-sizing: border-box;
// size of the content is calculated without border and padding
box-sizing: content-box

```

- Universal selector sets styles for all elements

```
//overwrites browser defaults and inheritence

* {
    box-sizing: border-box;
}
```

##### Inline vs block elements

- https://academind.com/learn/html/beginner-s-guide/diving-deeper-into-html#block-level-vs-inline-elements

- inline:

  - do not take entire width
  - take up the space they require to fit their content in
  - `margin-top`  and `margin-bottom`  have no effect on the element. `padding-top`  and `padding-bottom`  also have a different effect. They don't push the adjacent content away but they will do so with the element border.
  - setting a `width`  or `height`  on an inline element also has no effect. The width and height is auto to take as much space as required by the content.
  - lay next to each other
  - if you need both block-level and inline behavior, you can set `display: inline-block`  to merge behaviors.
  - example elements are: `<a>` , `<span>` , `<img>` 
  - https://hacks.mozilla.org/2015/03/understanding-inline-box-model/

- block

  - takes full available width
  - we can use padding, margin
  - examples are: `<div>` , `<section>` , `<article>` , `<nav>`  but also `<h1>` , `<h2>`  etc and `<p>`

- `diplay` property modifies default behaviour : 

  - `display: block`

  - `display: none` - element is not visible. Other elements can (and will) take its place instead.

    If you only want to hide an element but you want to keep its place (i.e. other elements don't fill the empty spot), you can use `visibility: hidden;` 

  - `display: inlin-block`

- inline-block - may cause unwanted behavior as placing neighboring elements in two different lines. You can fix this issue either by formating html so that they would lay next to each other (without ENTER) or just decrease (with) space taken by the latter.

##### Pseudo classes & pseudo elements

- pseudo class - defines the style of a special state of an element

  ```css
  .main-nav__item a:hover{
      color: white;
  }
  
  .main-nav__item a:active{
      color: white;
  }
  ```

- pseudo element - defines the style of a specific part of an element

  ```css
  p::first-letter{
      color: red:
      font-size: 20px;
  }
  
  .main-nav__item a::after {
      content: " (Link)";
      color: red;
   
    }
  ```

##### Grouping rules

- Group selectors with a comma **,**

  ```css
  .main-nav__item a:hover,
  .main-nav__item a:active{
      color: white;
  }
  ```


##### Styling `<a>` on a button

```css
.main-nav__item--cta a{
  color: white;
  background: #ff1b68;
  padding: 8px 16px;
  border-radius: 8px;
}

.main-nav__item--cta a:hover,
.main-nav__item--cta a:active{
  color: #ff1b68;
  background: white;
  border: none;
}
```

##### Resources and links

- CSS Box Model: <https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model>
- `box-sizing` : <https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing>
- More on height & width: <https://www.w3schools.com/css/css_dimension.asp>
- The `display`  Property: <https://developer.mozilla.org/en-US/docs/Web/CSS/display>
- Pseudo Classes on the MDN: <https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes>
- Dive deeper into Pseudo Elements: <https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements>
- https://caniuse.com

#### CSS Selectors, Properties & Values

##### CSS classes

- Multiple classes - each class is applied onto an element.

```html
<div class="class1 class2">
```

```
.class1 {}
.class2 {}
```

- Class and element combination.

```html
<a href="#" class="active">
```

```css
a.active {} /*applies to elements <a> with class active*/
```



##### Classes or IDs?

- Classes
  - reusable
  - allow to mark things for styling purposes only
  - Mostly used selector
- ID selectors
  - Only used once per page
  - Also has non CSS meaning

##### !important annotation

- Overwrites specifity and all other selectors
- Do not use it!

```css
div {
    color: red !important;
}
```

##### Selecting the opposite

- Select elements not selected by the selector in the brackets .

```css
a:not(.active) {
    color: blue;
}
```

##### Resources and links

- A discussion on "classes vs IDs": <https://stackoverflow.com/questions/12889362/difference-between-id-and-class-in-css-and-when-to-use-it>
- When is using `!important`  okay? => <https://css-tricks.com/when-using-important-is-the-right-choice/>
- The `:not()`  pseudo class: <https://developer.mozilla.org/en-US/docs/Web/CSS/:not>
- Can I Use: <https://caniuse.com/>





