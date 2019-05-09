![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

<!--1:30 5 minutes -->

# Responsive Design and Media Queries

## Objectives

* **Explain** the purpose of the viewport meta tag in context of responsive design
* **Utilize** media queries to change a web page's layout

#### Non-responsive sites

You'll be hard-pressed to find a major website that doesn't deal with mobile devices somehow. For example, [The SpaceJam website](https://www.spacejam.com/archive/spacejam/movie/jam.htm).

<!-- CFU: Think-pair-share -->

<!--1:50 5 minutes -->

## The Viewport

Everyone's had to use "pinch to zoom" on their phone - the page appears shrunken, and part of the site is hanging off the edge of your screen. That "edge of the screen" is called your `viewport`. Open up the Space Jame site, open your Chrome Developer Tools, and click the phone icon next to that to simulate a phone. Now zoom in. What a horrible way to browse!

When designing sites for mobile, we can ask our web page to match the `viewport` by using the viewport tag:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

When designing a responsive site, you **need** the above meta tag. It's what tells your site to pay attention to the viewport size. However, it means using explicit sizing is now, more or less, off the table. If you want something to be an exact size, you'll need them to be so **conditionally** - big on a desktop screen, smaller on a tablet, and even smaller on a phone. Luckily, there's a tool for that!


<!--2:00 5 minutes -->

## Media Queries

Media queries are simply a way to conditionally apply styles based on the width of your viewport.

We already know that if we do something like this:

```css
p {
  color: red;
}

p.blue_text {
  color: blue;
}
```

By default, all `p` tags will have red text - unless they have the class `blue_text`, in which case, the text will be blue. We can do a similar thing with media queries:

```css
p {
  color: blue;
}

@media (min-width: 600px) {
  p {
    color: red;
  }
}
```

Now, all `p` tags will be red, until the screen size reaches 600px, at which point they will turn blue.

A potentially more useful example would be to list all items inline until a certain screen size, then revert the list items to block, causing them to stack.

```css
li {
  display: block;
  color: blue;
}

@media (min-width: 600px) {
  li {
    display: inline-block;
    color: red;
  }
}
```

## Mobile First

You notice how the above feels slightly backwards? We're declaring media queries that affect the page based on its minimum size. That's because we're using a mobile-first strategy. If you design for large screens first, you put yourself in a position where you must consolidate lots of information into a smaller screen, causing you to either smush or remove sections of content. If, instead, you design your smallest experience first, you can add more design to your larger screen. Like frosting on the cake (or don't - whitespace is nice too)! That way, even if we don't have time to implement everything, everyone gets a good experience.

That's the reason we're using the `min-width` query instead of the `max-width` query. This means the styles aren't applied unless, at minimum, the screen is X pixels wide.

> Note: Looking to apply a hyper-specific media query? You can add more arguments to your query, such as `@media (min-device-width: 768px) and (max-device-width: 1024px)`, which would target only all of the sizes an iPad can be (portrait and landscape).

<!--2:05 30-40 minutes -->

## Independent Practice

Let's create a responsive page for your unit 1 squad!

### Create the mobile view FIRST!
Add the following elements to an HTML page:

1. An `h1` with your squad name
1. Your squad image (go find a good one!) below the `h1` tag
2. Your squad summary:
  1. An `h2` tag containing your squad motto
  2. An unordered list with your squad rules
  3. A unique background color or image for the info section
  4. A unique text color squad info
3. At least one paragraph of additional squad details/trivia.

### Then change it up on Desktop

1. Update the background to be different if you're not on a mobile device.
2. Make the first 2 elements(the squad summary and the image) appear next to each other, in two columns, only for non-mobile viewers. Make sure the squad summary is on the left. 

Here's an example of the mobile view from a previous class:

<!-- Example from WDI1 -->

![mobile page design](https://github.com/den-wdi-1/css-responsive-design-and-flexbox/blob/master/images/mobile_view.png)

And this is the desktop view:
![desktop page design](https://github.com/den-wdi-1/css-responsive-design-and-flexbox/blob/master/images/desktop_view.png) 

### Bonus

Go further! Add in addtional media queries, elements, and style rules.

## Useful Links

[7 Habits of Highly Effective Media Queries](http://bradfrost.com/blog/post/7-habits-of-highly-effective-media-queries/)

[Media Queries for Standard Devices](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/)

[Why You Don't Need Device Specific Breakpoints](https://responsivedesign.is/articles/why-you-dont-need-device-specific-breakpoints)

[Brad Frost - Navigation Patterns for Responsive Design](http://bradfrost.com/blog/web/complex-navigation-patterns-for-responsive-design/)


## Licensing
All content is licensed under a CC­BY­NC­SA 4.0 license.
All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
