# 1. Initial Thoughts (existing wireframes)

### A Shared Naming Convention

Use a naming convention everyone can use to more effectively communicate. E.g. Top nav can become "utility nav" or "site nav" depending on the context. It may be that at some point we can have two navigation components in the header of the portal. Distinguishing between a utility nav, site nav, footer nav, left sidebar nav, etc. can be helpful in mitigating any confusion or the need for further clarification.

Examples seen on Wireframe 1.2: 

- "menu bar on the top" vs. " top navigation bar" vs. " the second navigation bar "

**Utility Navigation** - Navigation that provides access to sections or functionality not crucial to performing tasks on the App.

- (This can be applied to the top-most navigation component on this wireframe - 1.2)

**Main Navigation** - Navigation that provides access to main application functionality or tasks.

- (This can be applied to the secondary navigation on this wireframe - 1.2)

**Secondary Navigation** - Navigation usually attached to or with direct connection to Main Navigation.

- (This can be applied to drop-down navigation. It can be tempting or seem to make more sense calling this the drop-down navigation, however, it may not have that same function in smaller viewports or further iterations of the application. Naming it by it's hierarchical positioning or functionality may make more sense long-term. - 1.2)



### Some thoughts on Drop-down Navigation:

*A more appropriate use of drop-down navigation is when your functionality resembles one of a desktop application. Imitate the metaphor.* - ui-patterns.com

For a more consistent experience, wireframe the navigation and it's functionality for mobile screens. This will help us carry over that experience to the desktop decreasing confusion as to how the navigation behaves. E.g. if the navigation slides in from the left or right, can the navigation exist as a vertical navigation in a sidebar? Would this help users better orient themselves when using the app in mobile after using the app in desktop view?



# 2. UX Strategy

Goals:

1. Personas
   - Who are we designing for?
   - See Personas.md document
2. Wireframes
   - Work with existing wireframes
   - Update wireframes as necessary
   - Create new wireframes
   - See DesignProcess.md document, #2




# CSS/Components Strategy

Goals:

1. Create a consistent UI between Corporate Site and New Apps (Agent Sites)
2. Critique / Modify / Extend Existing wireframes for Agent Apps/Sites
3. Identify reusable components in Corporate Site for inclusion in Agent sites



Tasks:

1. Clean CSS
2. Refactor existing CSS
   1. Identify 
      - UI inventory
      - Identify components / abstractions
      - Repetition of code (DRY principles)
      - Bootstrap undos
      - Bootstrap redos
      - Find / Eliminate utility replacements
   2. Isolate
      - Create a codepen for re-writing / testing components outside of existing code base, eliminating dependencies on smelly code.
   3. Implement
      - Componentize CSS 
      - Introduce / integrate new CSS to code base

   ​