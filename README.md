# StuntCoders style guide for SCSS

### Folder structure
```
    scss/
    |__base/
    |   |__ _fonts.scss
    |   |__ _variables.scss
    |   |.. ...
    |
    |__components/
    |   |__ _buttons.scss
    |   |__ _forms.scss
    |   |__ _headings.scss
    |   |__ _notifications.scss
    |   |__ _tables.scss
    |   |.. ...
    |
    |__layout/
    |   |__ _base.scss
    |   |__ _footer.scss
    |   |__ _header.scss
    |   |__ _sidebar.scss
    |   |.. ...
    |
    |__templates/
    |   |__ _account.scss
    |   |__ _cart.scss
    |   |__ _checkout.scss
    |   |__ _contact.scss
    |   |__ _homepage.scss
    |   |.. ...
    |
    |__utils/
    |   |__ _helpers.scss
    |   |__ _keyframes.scss
    |   |__ _mixins.scss
    |   |.. ...
    |
    |__vendors/
    |   |__ _foundation.scss
    |   |__ _slick.scss
    |   |.. ...
    |
    |__ styles.scss
```
- **Base** should include global styles settings.
- **Components** should have everything necessary for a certain part of the UI. They should be independent and reusable. Each component should not directly modify or depend on another component.
- **Layout** contains styling for larger layout components. This folder could have stylesheets for all main parts of the site, the grid system, etc.
- **Templates** include template specific styles, or even an entire workflow that could be stated by single name (_Checkout, Account pages..._).
- **Utils** gather all the tools and helpers used across the project.
- **Vendors** contain all SCSS files from external libraries and frameworks.

### Formatting

#### Indentation and spacing
- Be consistent with indentation. On Magento projects make sure that indentation is one tab, while on Rails projects, indentation needs to be 2 spaces.
- Use a single space after a property's name colon
- Use one whitespace between an element and a bracket
- Use one selector per line, one rule per line
```scss
    .button,
    .link {
        color: $white;
        text-decoration: none;
    }
 ```
- Use Line-Break between styles, new element and after closing the bracket
```scss
    .button {
        background-color: $red;

        &:hover {
            background-color: $black;
        }

        &.button-large {
            width: 100%;
        }

        @include breakpoint(320) {
            font-size: 0.8em;
        }
    }

    .link {
        color: $blue;
    }
```
- No space before and after single line comment that wraps styles section
```scss
    // Button - START
    .button {
        background-color: $black;
    }
    // Button - END
```
- Comments that are in the same line as code are perceded by one space
```scss
    .button-move {
        cursor: pointer; // Use as falback
        cursor: grab;
    }
```
- Commas in function arguments should be followed by a single space
```scss
    .button {
        box-shadow: 0 1px 1px 2px rgba($black, 0.2);
        transition: all 2.5s cubic-bezier(1, 0, 0, 1);
    }
```
### Naming
- Use hyphens rather than underscores and camelCase in class names
```scss
    // Bad example
    .button_outline {
        ...
    }

    .buttonOutline {
        ...
    }

    // Good example
    .button-outline {
        ...
    }
```
- Use hyphens rather than underscores and camelCase in variable and mixin names
- Do not use ID selectors
- Use a tag as a root selector only in base declaration partial
- Use meaningful or generic class names
- Use class names that are as short as possible but as long as necessary
```scss
    // Not recommended
    .navigation {}
    .athr {}

    // Recommended
    .nav {}
    .author {}
```
### Nesting and Ordering
- Selectors should be nested in the following way: pseudo-elements, pseudo-selectors, @inlcude blocks, child selectors.
```scss
    .button {
        @include hide-text;
        width: 100px;
        color: $white;
        background-color: $facebook;

        &::before {
            ...
        }

        &::after {
            ...
        }

        &:hover {
            ...
        }

        &:focus {
            ...
        }

        @include breakpoint(480) {
            width: 100%;
        }

        .icon-facebook {
            font-size: 0.9em;
        }
    }
```
- Nesting depth should not be greater than 5
- Selector depth should not be greater than 3
### Style Rules
- Do not use units after 0 values unless they are required
```scss
    // Bad example
    .button {
        box-shadow: 0px 0px 1px $black;
        margin: 0px;
    }

    // Good example
    .button {
        box-shadow: 0 0 1px $black;
        margin: 0;
    }
```
- Always use hex notation for color variables
```scss
    // Bad example
    $black: black;
    $white: rgb(255, 255, 255);
    $red: hsl(0, 100%, 50%);

    // Good example
    $black: #000;
    $white: #fff;
    $red: #f00;
```
- Use color variables as function arguments
```scss
    background-color: rgba($black, 0.2);
    color: lighten($black, 80%);
```
- Always use single quotes
```scss
    &::before {
        content: '';
    }
```
- Never use vendor prefixes

### Comments
- Always use single line comments style
```scss
    .button {
        @inlcude hide-text; // Text for icon button needs to be hidden
    }

    // This
    // is
    // the
    // multiline
    // comment
```
- Use 'temporary style' comment in uppercase with your name alongside
```scss
    .button {
        color: $red !important; // TEMPORARY - John Doe
    }
```
