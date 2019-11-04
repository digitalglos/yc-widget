# yc-widget

![widget screenshot](https://github.com/digitalglos/yc-widget/blob/master/YC-widget-screenshot.png)

## Your Circle search widget (with distance)

This widget comes in three 'flavours' depending on how the target content management system (CMS) page is built:

1. Base HTML code you can place directly in your web page if the CMS allows access to the underlying code.  
This is the best option where your CMS will tolerate user injected code but if you use a  rich text editor (RTE) you must test for 'linting' as many RTEs will alter code according to a rule set and this may break the widget.  
(Our CMS RTE only allows basic code so attempts to inject a fully styled widget are frustrated by the 'linter'.)  
    * You can also use this code if you need to ask your web developer to create new or change exisiting templates or&hellip;
    * If you have a server where you can drop custom code and use this in an \<iframe\>  
    However, this use case is outside he scope of this documentation & should you choose to use it you may need to 'top and tail' the code and will need to configure & test the \<iframe\> for suitable size and responsiveness.
2. A version to replace a user defined \<div\> which has an 'id' attribute  
Please check for uniqueness of the 'id' because if you specify a non-unique 'id' the page HTML will be invalid and lead to multiple widgets  
3. A version which replaces a convenient pre-defined \<div\> or other block \<[element]\> with a 'class' attribute

>### Notes  

>* In case 2 and case 3 you must be able to place code (in this case a script) at the bottom of the page; preferrably just before the \</body\> tag.  
Our CMS has this feature specifically to allow for injection of widgets & pop-ups.
>* In case 3. it is important to understand that **the supplied code replaces the _first_ block \<[element]\> having the chosen class** and you will have to carefully inspect the document object model (DOM) to determine which element index to use if you have more than one target \<[element]\> with the same class.  
[Our pages](https://www.gloucestershire.gov.uk/put-your-testing-stuff-here/hidden-articles/iframe-form-with-distance/) have a single sidebar with class="pcg-sidebar" which makes this trivial which is why the supplied code replaces the first element of this class.  
It is possible to tweak the code to replace the nth instance of a class where you don't have a uniquely 'classed' block element.

All widgets are self contained wth all styles inline except for standard furniture such as buttons which may vary in size, shape and 'depth' effects depending on the hosting web site and browser used by visitors.

## Applying the code

- - -

### Case 1

**(Where you have access to the code  or your CMS editor allows injection of code without changing it.)**

Take the code in the file '[your-circle-clean-widget-order-dist-for-innerhtml.html](your-circle-clean-widget-order-dist-for-innerhtml.html)' and paste into a convenient spot on your web page using the HTML code editor.  
**Do not paste into the rich text editor.**

Please check the result carefully -including submitting the search- as many CMS editors 'lint' any code placed manually and remove 'invalid' or 'unsupported' markup; this can break the widget.

If you need to have templates changed or created supply this code to your web developers. They may need to tweak it slightly to fit your needs.

- - -

### Case 2

**(Where your CMS allows simple \<div\> code to be added but removes other parts during 'linting' - usually the \<form\> sections. You must be able to add scripts after the main web page code.)**

Inject a \<div\> on the page with **id="replaceMe"** where you want the widet to appear - eg:

    <div id="replaceMe">If you can see this you have Javascript disabled &amp; the search widget will not work.</div>

The message inside the \<div\> will appear as a warning if Javascript is off.

This places a short piece of code on the page which a script can replace.

Use the code in '[your-circle-form-with-distance-id.js](your-circle-form-with-distance-id.js)' to place a script at the bottom of your page that will replace the \<div\> you injected above with the code from '[your-circle-clean-widget-order-dist-for-innerhtml.html](your-circle-clean-widget-order-dist-for-innerhtml.html)'.  
**Do not paste into the rich text editor.**

Again, please check the result carefully -including submitting the search- as your CMS may break the widget.

- - -

### Case 3

**Where you need to inject the code into an area of the site over which you have no control but which you don't mind replacing with the widget - in our case this was a right hand column.**

Inspect the code on your site carefully & decide which element is suitable. The code in the supplied file replaces the first element in the DOM using the CSS class targeted for replacement.

Use the code in '[your-circle-form-with-distance-class.js](your-circle-form-with-distance-class.js)' to place a script at the bottom of your page that will replace the \<div\> you injected above with the code from '[your-circle-clean-widget-order-dist-for-innerhtml.html](your-circle-clean-widget-order-dist-for-innerhtml.html)'.  
**Do not paste into the rich text editor.**
- - -
Contact [communications@gloucestershire.gov.uk](mailto:communications@gloucestershire.gov.uk) with any queries.

## Tweaking the code

**Where you are comfortable editing HTML and/or Javascript, you may wish to tweak the widget.**

If the widget does not fit your page layout comfortably you may wish to make small changes to adjust its layout to suit. It's perfectly acceptable to do this provided you stick within the guidelines:

* Keep the brand logo and colours
* Within reason you can change the typestyle and font size to fit with your site's typography but the text alongside the logo should be Helvetica/Arial and kept in the same proportion to the size of the logo (Please no fancy fonts)
* Keep the widget inside a solid border but you can switch off rounded corners if that fits better with your page layout
* Be careful modifying the hidden fields - they control initial sort and set the 5 miles initial search range.


