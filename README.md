# Accessibility guidelines
A practical guide to an accessible web
This guide is meant to provide team specific information to help you understand the web accessibility standards.

demo: https://vcastrejont.github.io/workshop/hotels.html

## DOCUMENT

### Language
Declaring a language attribute on the HTML element enables a screen reader to read out the text with correct pronunciation.

Specify a language with the lang attribute on the html element, example: `<html lang="en">`

**How to test:** Manually test or using wave testing tool.

## LANDMARKS

Landmarks have a very important role in semantics, html has a wide variety of tags that are specific for every part of a website, we recommend to use them correctly for each case.

Roles are part of the html 5 standard now they help screen reader users to identify the part of a website, many html tags have now an intrinsic role that you can take advantage of but If you use the common `<div>` tags for the layout you need to add a role manually, example:

    <div id="mainContent" role="main">

These are the most common landmarks tags currently available:

### Main

The `<main>` tag specifies the main content of a document. This will help screen readers and other assistive technologies understand where the main content begins. Use only once per document.

**How to test:** Manually test or use a testing tool

### Banner

Banners are a convention used on most web sites to convey branding such as the logo, identity and may also be used as a location for advertising information or include the search form, they are placed typically at the top of the website. You can only have one `role=”banner”` per document, example:

	<header role="banner">...</header>

**How to test:** Manually test or use a testing tool

## Header

The HTML `<header>` element represents introductory content, typically a group of introductory or navigational aids. You can have several `<header>` elements in one document if they don't have the role banner assigned.

### Nav

The `<nav>` tag represents a section of a page whose purpose is to provide navigation links, either within the current document or to other documents.

Notice that not all links of a document should be inside a `<nav>` element. This element is intended only for major block of navigation links. A document may have several `<nav> `elements.

### Footer

Contains information about the document A footer typically contains information about the author of the section, copyright data or links to related documents.

Use `<footer role="contentinfo">` for better compatibility.

**How to test:** Manually test or a testing tool.

### Aside

Asides are frequently presented as sidebars or call-out boxes. They represents a portion of a document whose content is only indirectly related to the document's main content.   They common use of this is for sidebar.

**How to test:** Manually test or a testing tool.

### Page main search

A search landmark contains a collection of items and objects that, as a whole, combine to create search functionality to content on the website

Use `<form role="search">` on any search form in the website.

**How to test:** Manually test

## LINKS
### Underline and Hover

Users with color blindness or low vision may have trouble distinguishing links from regular text when the underline is missing.

If is possible ensure links are recognizable when the user hover the element by adding underlined style.  
**How to test:** Manually test

### Outline

By default browsers have an outline style for focused elements, this important for users that have vision problems or use keyboard to navigate. In case the browser outline is removed should be replaced with another  
**How to test:** Manually test

Learn more about why outline is so important: [http://outlinenone.com](http://outlinenone.com)

## HEADINGS

The headings should be consistent and keep a logical hierarchy level from h1 to h6, a good practice is to have h1 for the most important heading and going down to h6 without skipping any level.

**How to test:** Use wave testing tool

## COLORS

Make sure content is readable and the foreground contrasts sufficiently with the background. Color should not be used as the only means of conveying information, because blind users are not able to see colors, and colorblind or older users may not see colors correctly.

The [WCAG 2.0](http://www.w3.org/TR/WCAG20/) color contrast Level AA success criteria requires contrast ratio of at least 4.5:1 for normal text and 3:1 for large text. Level AAA requires a contrast ratio of at least 7:1 for normal text and 4.5:1 for large text.  

**How to test:** Use wave testing tool

## IMAGES

Images should have an alt property to describe the content of image, example:

	<img src=”mex_food_12.jpg” alt=”Mexican food”>

There is no need to add “Image of mexican food” assistive technology already reads this as image or picture.

Use an empty alt attribute for any image that is only decorative, example:

	<a href=”/home”>Home<img class=”fa-home-icon” alt=””></a>

Note: if the image is the company logo the alt property should be the company name and not “logo”.  

**How to test:** Manually check that the text descriptions provided by ALT attribute is clear and descriptive or use wave testing tool

## KEYBOARD

Many users with disabilities use the keyboard as main way to interact with a website, we must ensure these user can operate the main features of our website.

-   Ensures that the site can be accessed using a keyboard only.

-   Tab order follows a logical pattern.

-   A modal dialog can be closed using <esc> key

-   A good practice is to no set tabindex greater than 0 because this will disrupt the organic tab order

**How to test:** Check manually by tabbing through the page and checking all interactive elements for keyboard accessibility.

## ARIA

The easiest way to get an accessible control is to use a standard HTML control, they are keyboard accessible, scale easily, and are generally understood by screen readers.

Accessible Rich Internet Applications (ARIA )is a specification for making UI controls accessible to screen readers by means of a standard set of DOM attributes.

ARIA is a set of attributes that define ways to make Web content and Web applications more accessible to people with disabilities. ARIA enables accessible navigation landmarks, JavaScript widgets, form hints and error messages, live content updates, and more.  
The ARIA specification is split up into three different types of attributes: roles, states, and properties.

Some of the most used aria tags are:

### Aria-hidden

Applying this attribute to an element effectively removes it and all of its descendants from the accessibility tree.

	<span class="close" aria-hidden="true">X</span>

### Aria-label

Assigns a string that labels an element, use it when <label> is not defined or when it is not visible.  
example:

	<input type="text" name="label" aria-label="Last name">

Placeholder attributes are not a replace for input labels.

### Aria-labelledby

Identifies the element that labels the current element if there is not a label available, example:

	<h2 id="labellastname">Last name</h2> <input type="text" name="label" aria-labelledby="labellastname">

## Aria-checked

Indicates the current "checked" state of checkboxes, radio buttons, and other widgets.

	<span class="custombox" aria-checked="true"></span><input type="checkbox" name="terms" class="hidden">

### Aria-hidden

Note: anything that has a CSS style of visibility: hidden or display: none or uses the HTML5 hidden attribute will be hidden from assistive technology users.

### Role button

We recommend using `<button>` for any interactive controls but in case you want to use other tag for this you will need to add the role necessary and tabindex , example:

	<span role="button" tabindex="0">Save</span>

## TESTING TOOLS

### Wave

Wave is a free tool from WebAIM that will help you check your site for accessibility problems, this tool generates a variety of reports based on the results of an analyzed web page directly on original web page with embedded icons and indicators that reveal the accessibility of that page.


There are 2 ways to use this tool:

-   Use the online version [http://wave.webaim.org/](http://wave.webaim.org/)

-   Install the chrome or firefox extension (recomended) [Extension download](https://chrome.google.com/webstore/detail/wave-evaluation-tool/jbbplnpkjmmeebjpijfedlgcdilocofh)



## Chrome accessibility inspector

This tool allow visualisation of the [accessibility tree](http://www.w3.org/WAI/PF/aria-implementation/#intro_treetypes) view of a web page. Chrome canary adds this new *accessibility* tab to the element section of developer tools.


### Axe

AXe is an automated accessibility open source testing library and a chrome extension. Test results include a list of accessibility issues, severity, descriptions, and snippets of the code that caused the issue.



## SCREEN READERS

### Chromevox

This screen reader uses a relatively simple navigation method based on the exploration of the elements of a web page through various levels of semantic precision. We can navigate a web in a linear way by jumping between blocks, objects, phrases, words or characters of a page.

-   install the extension [Extension download](https://chrome.google.com/webstore/detail/chromevox/kgejglhpjiefppelpmljglcjbhoiplfn?hl=es)

-   How to use the chromevox extension [video link](https://www.youtube.com/watch?v=NyuuK7tB9fM&index=12&list=PL5aqr5w5fRe7QWzXhqxrilIVduWEmLHM2)


### VoiceOver

This is a screen reader integrated on OSX and IOS systems, you can enable this is system preferences > accessibility or you can press Command-F5 to enable VoiceOver.

## FAQ

### Is mobile also important in accessibility?

Yes, a  recent [study of 1782 screen reader users](https://webaim.org/projects/screenreadersurvey7/#mobile) in 2017 showed that 88% used screen readers on their mobile devices.

### Audit tools are enough for test accessibility?

No, although these tools are good to detect most of the problems sometimes they can report false positive issues, in the same way they are not good detecting interaction issues like keyboard events


## Exercise
[Link](exercise/index.html) 
