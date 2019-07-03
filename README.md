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

## 3. Floats may change the display property

When we float any element then it is removed from the normal flow of the page which also alters the default display property of the element. Means a block level will start taking the space according to the content it wraps despite their default display property of taking available width. To fix this behavior we will have to apply some fixed width according to the need.

```
  section {
    float: left;
    width: 600px;
  }
  aside {
    float: right;
    width: 300px;
  }
```

When an inline-level element like span is floated it should start accepting the box model properties like width and height.

```
  span {
    float: left;
    width: 300px;
    height: 300px;
  }
```

## 4. Clearing and Containing the floats

We have seen how the floats affect the normal flow of elements on a page. We saw how the rest of the elements bleed into the floated elements and how the default display behavior of an element changes using floats.

Actually, this is what for the float was introduced, to float images and the rest of the content will automatically wrap around it. But as time passes developer started using floats in a more complex way. They start making their own flexible and reusable grid with floats, with which we could create multi-column layouts.

So, to make the use of floats in a more effective way we need to win over the disadvantage of floats. Sometimes we may find the proper styles are not rendering. We need to remove the unwanted behavior of floats. So to bring the elements into a normal flow on a page we will have to clear or contain, those floating effects.

## 5. Clearing the floats

To clear float in CSS we clear property which accepts different values like left, right,and both. The left value will clear the left floats and right will clear right floats. Both will clear both the right and left floats and it is safer to apply.

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
  footer {
    clear: both;
  }
```

The important point is to note here that we will clear floats from the next element to the floated elements. We will not apply the clear property to the floated element or to the previous of the floated element. The float needs to be cleared from the next element. Here we are clearing from the footer because it is next to the floated element and it getting disturbed bleeding into the floated elements section and aside.

## 6. Containing the floats

However, clearing floats won't return each and everything back to normal. Yet clearing floats also there would be problems. One of the most popular problems you may encounter with a parent containing floated elements. For example, let's wrap the floated element from above, inside a parent div.

```
  <header>..........</header>
  <div>
    <section>..........</section>
    <aside>..........</aside>
  </div>
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
  footer {
    clear: both;
  }
```

Now if you inspect the parent div inside your browser you'll find 0 height of the div. By default, the parent div should have some height as there are few elements inside it. Parent div still haven't gained back its styles. So to gain back each and everything to the normal flow even the parent's styles, we contain the floats instead of clearing.

To contain floats there are different approaches. The most popular are: placing an empty div with clear: both styles, overflow technique, Clearfix technique, etc. Let's check out one by one.

## 7. Placing an empty div.

In this case, we place an empty div before the closing tag of the parent element and set its style to clear: both.

```
  <header>..........</header>
  <div>
    <section>..........</section>
    <aside>..........</aside>
    <div class="clear"></div>
  </div>
  <footer>..........</footer>

  section {
    float: left;
  }
  aside {
    float: right;
  }
  .clear {
    clear: both;
  }
```

Containing floats in this way is not efficient, it is not even semantically correct. Obviously, on a page, we will be having a numerous number of floats at numerous places so we will have to place that number times empty div, which is contextually not correct.

## 8. Overflow technique

In this technique, we use CSS overflow property to the parent containing floated elements and set the value auto. Overflow property comes with a few different values, most popular are auto, hidden, scroll, etc.

```
  <header>..........</header>
  <div class="parent">
    <section>..........</section>
    <aside>..........</aside>
    <div class="clear"></div>
  </div>
  <footer>..........</footer>

  .parent {
    overflow: auto;
  }
  section {
    float: left;
  }
  aside {
    float: right;
  }
```

Now the parent will gain back its height and all the styles applied to it.
The overflow method comes with few problems also. This to be worked in internet explorer we will have to specify some fix height or width. But generally, we don't fix the height, so that the element could flow or take the height according to the content.

Also, if add overflow auto it may add a scrollbar to the element for the internet explorer, which is we don't want. So we will have to say overflow hidden instead of auto. But the problem with hidden is that few styles like box-shadow will not be visible. It's just that different browsers treat overflow property differently.
