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

## 9. Cleafix Technique

One of the most effective ways to contain floats is the clearfix method. The clearfix technique is more preferable and has advantages over other techniques.

In this method, we apply a class to parent element containing floated elements and then we define some sort rules to that class in CSS. It would be better to define a modular class so that we can use the same class again and again wherever we will float the elements in a page. One of the most popular class name that generally developer use for this purpose is 'clearfix' or 'cf'.

```
  <header>..........</header>
  <div class="parent clearfix">
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
  .clearfix:before, .clearfix:after {
    content: "";
    display: table;
  }
  .clearfix:after {
    clear: both;
  }
```

The above code might be a little bit confusing but of course, we will go through the above code in detail. Actually, the clearfix method consists of after and before pseudo elements.

After and before pseudo elements creates dynamic content above and below the class wherever we apply. Here, in this case, the content is empty but if we put anything inside the content(content: "pseudo") we can see the dynamic content will appear on our page. If it feels confusing don't worry just write the code we will cover this topic again in our complex selector chapter.

In the above code, the before and after pseudo element will create a hidden element above and below the clearfix class which we have applied to our parent. We displayed the pseudo elements as a table, just to make it block level element so that it should take full available width above and below the element. We displayed it to a table just to ensure consistency for the older version of internet explorer or else display block will also work fine.

As we made it as a block level elements, it will start from the left end and will go till the right end. This will work as a wall above and below the elements to prevent above and below margin from collapsing and won't let the floating effect go out the box. At the end to the: after pseudo-element, we also applied clear: both. This is to clear floats so that the next upcoming element does not get wrapped around the floated elements.

## 10. Example on float and clearfix.

Let's take an example for more clarity on using floats and clearfix together.

```
  <header class="header">I am the header of the page.</header>
  <section class="parent clearfix">
    <aside class="sidebar">Sidebar of the page.</aside>
    <article class="article">An article on the page.</article>
  </section>
  <footer class="footer">I am the footer of the page.</footer>

  .header, .parent, .sidebar, article, .footer {
    bacground: #bada55;
    padding: 30px;
    margin: 10px;
  }
  .sidebar {
    float: left;
    width: 200px;
  }
  .article {
    float: right;
    width: 800px;
  }
  .clearfix:before, .clearfix:after {
    content: "";
    display: table;
  }
  .clearfix {
    clear: both;
  }
```

This is how we generally work with floats and clearfix. Now suppose we have three columns instead of two columns in a row like a sidebar and an article(as we are having now). Then how should we take the approach?

If we have multi-columns in a row instead of floating one element to the left another to right, we can directly float left to all the elements.

```
  <header class="header">......</header>
  <section class="parent clearfix">
    <div class="column">......</div>
    <div class="column">......</div>
    <div class="column">......</div>
  </section>
  <footer class="footer">.......</footer>

  .header, .parent, .sidebar, col, .footer {
    bacground: #bada55;
    padding: 30px;
    margin: 10px;
  }
  .column {
    float: left;
    width: 300px;
  }
  .clearfix:before, .clearfix:after {
    content: "";
    display: table;
  }
  .clearfix {
    clear: both;
  }
```

## Answer the following questions

1. What are the different ways to position the elements in a page?
2. Which way will you prefer to position the elements in a row and why?
3. What are different values does float property accepts?
4. Float makes the element goes out of the flow, how can we fix the problem to get back into the normal flow?
5. What are the disadvantages if we use clearing method to bring the element back to the normal flow?
6. Explain overflow technique to contain floats as well disadvantages of it.
7. Explain the clearfix method.

## Do the Exercise 1

## 11. Creating reusable and flexible layouts

In the beginning, I mentioned that from here we can start giving our layout a real website kind of structure. To provide real website kind of structures we must know to create reusable layouts. A reusable layout consists of modular classes that can be reused again and again. In a real website, it's not just about creating reusable layouts but also creating a flexible layout. A flexible layout has flexible containers and columns and those flexible containers and columns are made with percentages or flexible units so that they can have flexibility in every size of the screen.

At some point, we will have to make our website responsive and responsive websites consists of flexible layouts which can adapt any screen sizes. We will learn about responsive and adaptive in the responsive web design chapter. But for now, let's see how do we work percentages and then with percentages we will create reusable layouts having flexible containers and columns.

## 12. Working with percentages

Percentages are a relative unit in CSS represented by % unit notation. Percentage unit work in relation to another object in a layout. For example, let's say we have a column of width 50% in our page, now let's see how it works

```
  <section>
    <div class="column">......</div>
  </section>

  section {
    width: 1200px;
  }
  .column {
    width: 50%;
  }
```

Here, we set the width of column 50%, now the column will look for its parent width in which it is nested and then its width will be calculated. Here, the section is having 1200px width so the column width will be 600px but in percentage. If the parent's width decreases or increases accordingly the column's width will also decrease or increase but it will always remain 50% of its parent.

Percentage units are always based on the parent element's size. So whenever we define the things in percentage it will always look for its parent.

## 13. Creating a flexible container

A flexible container does not have a fixed width so instead of applying width we apply max-width. The width property prevents the layout to go narrower. So whenever we decrease the size of the screen the container will be having a fixed width and we will get a horizontal scrollbar which is not good for smaller devices.
But the max-width property will allow the container to become narrower as the screen sizes reduce. This is important for smaller devices like mobile or tablet.

```
  .container {
    max-width: 992px;
    margin: 0 auto;
    padding: 0 30px;
  }
```

This is how we create a flexible container for a website. Here, the container's size can become narrower below than 992 pixels for smaller devices but it won't be greater than 992 pixels. This is good for small screen devices but for the larger screen devices, it won't be great. No worries, we will learn how to tweak the size of the container using media queries in responsive web design chapter.

Generally, a wrapper or a container in a website always remain horizontally center. To keep the container horizontally center we apply margin: 0 auto. So, the 0 value for the margin will provide 0 margins from top and bottom but the auto value will provide auto margin from left and right, and thus the container will always remain horizontally center.

Here, we also padding 0 30px just to provide breathing space from left and right to our content. So, whenever our layout opens in smaller devices the content will not stick to the edges of the screen, it must have some amount of gap from the edges.

## 14. Reusable layouts having a flexible container and columns.

Now that we have seen how to work with percentages and how do we create a container in a page, its time to use them to create a reusable layout. Earlier also we have seen that creating reusable layouts means using the modular classes. A modular class can be used again and again.

For example, let's say we have three columns in a section and each column has the same width with different contents inside it. So, how do we create such columns without repeating the styles again and again?

To create such columns and that can be used again and again we should modular class. Also, our layout should be flexible so we will make use of percentages and flexible container.

```
  <section class="container clearfix">
    <div class="col-1-3">......</div>
    <div class="col-1-3">......</div>
    <div class="col-1-3">......</div>
  </section>
  .container {
    max-width: 992px;
    margin: 0 auto;
    padding: 0 30px;
  }
  .col-1-3 {
    float: left;
    width: 30%;
    margin: 1.5%;
  }
  .clearfix:before, .clearfix:after {
    content: "";
    display: table;
  }
  .clearfix {
    clear: both;
  }
```

Here, `col-1-3` as well container class attribute value is a modular class, this can be used in other sections also depending upon the use cases. Something like this:

```
  <body>
    <section class="container clearfix">
      <div class="col-1-3">......</div>
      <div class="col-1-3">......</div>
      <div class="col-1-3">......</div>
    </section>
    ......
    <section class="container clearfix">
      <div class="col-1-3">......</div>
      <div class="col-1-3">......</div>
      <div class="col-1-3">......</div>
    </section>
  </body>
```

This is the benefit of creating a reusable layout, you can use it as many time as you want. This will help you in saving your time as well as will prevent you from repeating.

## 15. Universal Selector

One important thing to keep in mind while working with the reusable and flexible layout is that you must have every element's box-sizing property as border-box. Because obviously, you will be applying some padding and border in your columns, by default it will expand the size and it may break your layout. To prevent such thing we can use the universal selector which will target each and every element in the document and style it as a border-box.

```
*, *:before, *:after {
	box-sizing: border-box;
}
```

You should be having this style at the top of your stylesheet in every project. This will make every element as a border-box even the pseudo-elements will also have the style as border-box. Now any padding or border will not expand the size of any element in the document.

## 16. Example of using reusable and flexible layout effectively

```
  <body>
    <header>
      <div class="container>........</div>
    </header>
    <main>
      <section>
        <div class="container clearfix">
          <div class="col-1-3">......</div>
          <div class="col-1-3">......</div>
          <div class="col-1-3">......</div>
        </div>
          </section>
      <section>
        <div class="container clearfix">
          <div class="col-1-3">......</div>
          <div class="col-1-3">......</div>
          <div class="col-1-3">......</div>
        </div>
      </section>
    </main>
    <footer>
      <div class="container>........</div>
    </footer>
  </body>

  *, *:before, *:after {
    box-sizing: border-box;
  }
  .clearfix:before, .clearfix:after {
    content: "";
    display: table;
  }
  .clearfix {
    clear: both;
  }
  .container {
    max-width: 992px;
    margin: 0 auto;
    padding: 0 30px;
  }
  .col-1-3 {
    float: left;
    width: 30%;
    margin: 1.5%;
  }
```

Here, in this example, we have a header, main content of the page, as well a footer. You might have seen that I have used the container class in every section even inside the header and footer. This will keep our content aligned from the left as well from right in every section.

You might have also observed that I haven't applied the container class directly in the header or section or footer, instead, I have taken a div inside each section and specify the class attribute value, container. This is just because I want to wrap the real content inside the sections not the parent container like header, section, or footer. Sometimes we may have some background to the parent container(header, section, or footer) and that background is flowing from the left end of the browser to the right end of the browser. In that case, this will help us. If you are not getting what I am trying to say, then you can just experiment with the thing here to make it more clear. Just apply some background to each section including header and footer and then specify the container class to the header, section, and footer element instead of div inside it. You'll see that even the background color is also wrapped inside the container. This is what we don't want.

So, while working with the container always wrap the real content inside the container, not the whole section.

There are a lot more things to learn to create a real website like structure as we move forward we will learn everything in detail. This is just the beginning of creating a real flexible page. We will make use of all these sorts of things to create a full-fledged website.

## Do the exercise2

## Additional Resources

1. https://learn.shayhowe.com/html-css/positioning-content/

2. https://learn.shayhowe.com/html-css/positioning-content/

- https://internetingishard.com/html-and-css/floats/
