# Positioning Content

## Topics of the day

1. Positioning with inline-block
2. Positioning with floats.
3. Floats may change the display property
4. Clearing and containing the floats.
5. Clearing the floats
6. Containing the floats
7. Placing empty div to contain floats
8. Overflow technique
9. Clearfix Technique
10. Example on float and clearfix
11. Creating reusable and flexible layouts
12. Working with percentages
13. Creating a flexible container
14. Reusable layouts having a flexible container and columns.
15. Universal Selector
16. Example of using reusable and flexible layout effectively

Over the last few chapters, we have been creating boxes and manipulating their size. We have seen all the box model property and learned how to implement them. Till now we have learned to create a single column layout. You might have seen whenever we take any block element, it always takes the whole available horizontal width and comes one after another vertically. Working with HTML & CSS and creating websites is not just about creating boxes and single column layout. We will be getting complex layouts having a number of columns in a row. And obviously, to put our content we will be using block level elements. So this single column layout won't help us to create a full-fledged website. We need to learn about positioning the block level elements and creating columns in a row.
To bring the structure according to the design and represent our content in a more beautiful way CSS provide usability to position the content in any imaginable way. In CSS we can take different approaches to design our layouts and each has its own advantages.

## 1. Positioning with inline-block

We have already seen this method of positioning in the box model chapter. To make the element sit next to each other we can change its display property to inline-block so that it should accept all the box model properties.

```
  <header>..........</header>
  <section>.........</section>
  <aside>.........</aside>
  <footer>............</footer>

  section, aside {
    display: inline-block;
  }
```

In the box model, we have discussed a small space always exist between the inline-block elements and how to get rid of it. So, whenever you'll work inline-block elements never forget to remove the space because it may disturb the flow of the content. Sometimes you may face the problem of alignment issues with inline-block elements if you specify a height and put content inside one of the element. so you'll have to apply the `vertical-align` property to make the alignment of proper. The vertical-align property comes with different values. Most popular are the top, bottom, middle, etc. You can set any value.

```
<header>..........</header>
<section></section>
<aside>sidebar</aside>
<footer>............</footer>

section, aside {
	display: inline-block;
	height: 200px;
	background: green;
	vertical-align: top;
}
```

## 2. Positioning with floats

Another way we can position the elements with the floats. Floats let the element to position side by side. It can make the even block level element to come in one line instead of on top of each other. With the float, we can create all kind of layouts. We can even create our custom grid having a number of rows and columns. A real website always has a multi-column layout. From here we can start giving the real website like structure to our layout.
The float comes with three different values: `left, right, and none`. Left and right value send the element to the left and right of the parent element respectively. If the elements are not wrapped inside the parent then the element will be aligned to the left and right of the window.

```
<header>..........</header>
<section>..........</section>
<aside>..........</aside>
<footer>..........</footer>

header, section, aside, footer {
	background: green;
	padding: 50px;
	margin: 10px;
}
section {
	float: left;
}
aside {
	float: right;
}
```

And the last value none has no effect on the element. This is the default value, if the element has no float property then it will be considered as floated none.
Nowadays we have some other specifications like Flexbox and CSS-Grid which have been introduced recently. These new specifications have almost replaced the floated based layouts. In modern websites, you'll find such specifications has been used to style the layouts. But still, we will cover the floats, because this is the foundation which has been used in the majority of the websites. You may feel the use of floats at some point.

Initially, the float was introduced to wrap the content around images. An image could be floated and all the content will flow around it. Just to provide magazine or newspaper article type structure. Okay what I am trying to say, let's make it clear from the above code.

If you use the above code you'll find that the footer blends into section and aside. Also, the floated element section and aside is taking the space according to the content it wraps not according to their default display property.
If we float any element in a page it goes out of flow and rest of the element starts wrapping around the floated element. The float also changes the display property of the element.
