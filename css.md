# CSS

### Selectors

**Elements**
```css
img{
    /*All these styles apply to every img*/
}
```

**Classes**
`.class-name{}`

**id**
`#my-element{}`

**rules**
```css
.my-wrapper .my-class{
    /* will apply only to "my-class" elements that are WITHIN "my-wrapper" */
}

.class-one,.class-two{
    /* applies to both classes */
}
```

### Pseudoselectors
```css
.my-class:hover{}
.my-class:focus{}

.my-class:first-child{
    /* only the first child WITHIN my-class */
}

.my-class:nth-child(3){
    /* only the 3rd child */
}

.class-one > .child {
    /* only direct children */
}
.class-one.class-two {
    /* must have BOTH of these classes */
}
```

### Units
- `px`
- `%`: percentage of the elements parent
- `vw`/`vh`: percentage viewheight or viewwidth
- `rem`: ratio of the root font-size

### Some basic css rules
```css
.class{
    color: blue; /* text color */
    background:red; /* background color */
    width: 5rem;
    max-width: 100vw;
    height: 10%;
    margin: 20px; /* outside the element */
    padding: 20px; /* inside the element */
    font-size: 10px;
    font-family: 'Avenir', Helvetica;

}
```

### Position
- `relative`: default for all elements. They will be arranged based on their siblings.
- `absolute`: removes the element from the "flow" of the sibling elements. Instead it becomes positioned based on its cloest parents that has "relative" positioning. You can use `top`, `bottom`, `left`, `right` to move it around precisely. 
- Note: either "relative" or "absolute" positioning gives you the ability to use `z-index`

### Display
- `block`: default
- `inline-block`: stack horizontally
- `none`: to hide
- `flex`: !!!

### Flexbox
```css
.parent{
    display:flex;
    flex-direction:column;
    align-items: center; /* flex-start, flex-end, space-between, space-around space-evenly*/
    justify-content: center;
    flex:1;
    flex-wrap: wrap; /* allows the children to wrap */
}
.child{
    flex: 1; /* the ratio of how much space to take up */
}
```
- `align-items`: aligns opposite the direction axis
- `justify-content`: aligns items on the direction axis

### Response CSS
```css
html { /* MOBILE */
  font-size: 15px;
}
@media (min-width: 400px) {
  html { /* TABLET */
    font-size: 18px;
  }
}
@media (min-width: 768px) {
  html { /* DESKTOP */
    font-size: 21px;
  }
}
```
- you can use `rem` units to scale other elements on your page in relation to that `font-size` on your `<html>` element.

### animations
```css
.my-button{
  transition: all 0.2s; /* a "transition" on your animation */
}
.my-button:hover{
  transform: scacle(1.2,1.2) translate(100px,50px);
}

Using "transform" or "opacity" for animations makes your application WAY more performant and will not slow down the page, even with thousands of animations running. 

**long-runing**
```css
.logo{
  animation: spinny infinite 20s linear;
}
@keyframes spinny {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
```
