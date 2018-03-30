# CSS Refactoring Notes and Issues

### Stats

- 4419 Lines of CSS
- Usability.gov states that 10" is optimal line length for reading on screen. This translates to roughly 98 characters including spaces or around 760px. 
  - Our text lines are roughly 1100px wide, or 162 characters in length.
- ​

1. ***Ask Daniel:** How can we set up SASS and auto-compilation within Umbraco? It would be nice to bundle all our CSS into one file (same for JS).
2. Universal Box Shadow
  There is a box  shadow applied to several class selectors. Might be better and more manageable if we move this into it's own class. 
  Currently:
```css
z-depth-1, .jumbotron, .card, .list-group, .popover, .navbar, .dropdown-menu, .badge, .chip, .pagination .active .page-link, .btn, .pager li a, .cascading-modal.modal-dialog .modal-c-tabs .nav-tabs, .modal-notify.modal-dialog .modal-header { 
  box-shadow: 0px 2px 5px 0px rgba(0,0,0,0.16), 0px 2px 10px 0px rgba(0,0,0,0.12); 
}
```
​	Proposed:

```css
.shadow-sm { 
  box-shadow: 0px 2px 5px 0px rgba(0,0,0,0.16), 0px 2px 10px 0px rgba(0,0,0,0.12); 
}
```
​	**Note: This will need application via a class in the mark-up throughout the site.**



3. Modals
   Modals have been re-written extensively in the `custom.css` file. While not uncommon, much of the code resulted in bloat. Unnecessary changes especially if we want modals to behave with their intended behavior and look. Removing all the modal CSS in the `custom.css` file gives us a good-looking working modal. This change removes the custom animation and leaves the default slide-down-from-top bootstrap animation. We are using bootstrap so it makes sense to leverage what functionality we already have especially if it helps us remove bloat and difficult-to-maintain CSS.
   Proposed:

   ```CSS
   button.close {
       cursor: pointer;
   }
   ```

   **See ModalHTMLAdendum**

   Modals also affect SEO and Google rankings. A Google search for "contact equitrust" brings up the following:
   ![52183008118](C:\Users\JARODR~1\AppData\Local\Temp\1521830081183.png)

   While not exactly terrible, Google cannot find the contact section on the corporate homepage. Moving modal content into actual pages, we can have Google properly index the site and provide better search results for current or potential customers.

   ​

   **Note: Removing all custom modal CSS also removes the slide-in-from-left animation. Is this acceptable?**
   ​

4. Widths and Max-Widths
   Max widths are set to 1200px in our `custom.css` stylesheet. I need to understand where this width came from. Is it a business requirement? Were there analytics that drove this decision? Otherwise, we can alleviate some bloat by leveraging bootstrap and adhering to the predefined breakpoints. 
   For example, we can eliminate the following code:

   ```CSS
   .footer-content {
       margin: 0 auto;
       width: auto;
       max-width: 1200px !important;
   }
   ```

   by using the existing bootstrap class `.container` which automatically sets our width to 1140px.
   There are other instances of the 1200px max-width we can refactor or eliminate altogether and have bootstrap do the work for us @ 1140px.

5. Color
   Most color definitions contain "fallbacks" for older browsers. E.g

   ```CSS
   background-color: rgb(239, 239, 239); /* fallback for other older browsers */
   background-color: rgba(239, 239, 239, 1.0);
   ```

   When no opacity is specified or an opacity of 1 is declared, it is easier to just declare the rgb as the alpha transparency is not needed. Further, rgb(), hsl(), rgba() and hsla() are now widely supported: 
   https://caniuse.com/#feat=css3-colors

6. Classes that are used as hooks by any JavaScript should be prefixed with `js-` to indicate the relationship and dependency to the JavaScript. These classes should not be styled with CSS or have any other function on top of serving as hooks.

7. Naming Conventions:
   A naming convention to be enforced throughout stylesheets:
   The following classes are found in the `custom.css` stylesheet:

   ```css
   .teaser-person-name
   .errorMessage_show
   .TopNavL a
   .H2HamburgerLinkL
   ```

   Following a set naming convention helps maintain consistency and readability.

8. Clarity over brevity. It is important that  classes, modules and components have names that give insight or describe their functionality. For example, `.btn-vk` and `.bg-color-heisenberg` do not tell developers anything about what they do to modify the styles of the elements to which they're attached or when/how to use them. `.btn-primary` tells developers how and when to use that class. Extenders such as `.btn-red` further describe the visual properties of the element to which they're attached. 

9. Cards need to be revisited. What are the requirements for cards, card images, etc.? 

   - rounded images are used for cards (and mobile views of "teasers")
     - Is there are a specific reason for rounded images?
     - Can cards be slightly re-designed?
     - There are no other rounded or round elements in the rest of the corporate site. It would be better to remain visually consistent with the site. The rounded images look out of place.
     - !!! Need to create some samples.

10. ​

11. ​

