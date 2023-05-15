# CSS Cheat Sheet

### 1. Selectors

- **Element Selector** selects elements based on their HTML tag name:
  ```css
  p {
    /* CSS rules */
  }
  ```

- **Class Selector** selects elements based on their class attribute:
  ```css
  .my-class {
    /* CSS rules */
  }
  ```

- **ID Selector** selects a single element based on its ID attribute:
  ```css
  #my-id {
    /* CSS rules */
  }
  ```

- **Descendant Selector** selects elements that are descendants of another element:
  ```css
  .parent-element .child-element {
    /* CSS rules */
  }
  ```

- **Adjacent Sibling Selector** selects an element that is directly after another element:
  ```css
  .element + .sibling-element {
    /* CSS rules */
  }
  ```

- **Pseudo-class Selector** selects elements based on a certain state or condition:
  ```css
  a:hover {
    /* CSS rules */
  }
  ```

### 2. Box Model

- **Width and Height** sets the width and height of an element:
  ```css
  .my-element {
    width: 200px;
    height: 100px;
  }
  ```

- **Margin** sets the space around an element:
  ```css
  .my-element {
    margin: 10px;
  }
  ```

- **Padding** sets the space between the content and the border of an element:
  ```css
  .my-element {
    padding: 10px;
  }
  ```

- **Border** sets the border of an element:
  ```css
  .my-element {
    border: 1px solid #000;
  }
  ```

- **Box-sizing** specifies whether an element's width and height include padding and border or not:
  ```css
  .my-element {
    box-sizing: border-box;
  }
  ```

### 3. Typography

- **Font Family** sets the font family for text:
  ```css
  body {
    font-family: Arial, sans-serif;
  }
  ```

- **Font Size** sets the size of the font:
  ```css
  h1 {
    font-size: 24px;
  }
  ```

- **Font Weight** sets the thickness of the font:
  ```css
  strong {
    font-weight: bold;
  }
  ```

- **Text Alignment** aligns the text within an element:
  ```css
  .my-element {
    text-align: center;
  }
  ```

- **Text Decoration** adds decorations to text (e.g., underline, line-through):
  ```css
  a {
    text-decoration: none;
  }
  ```

### 4. Layout

- **Display** specifies the display behavior of an element:
  ```css
  .my-element {
    display: block;
  }
  ```

- **Position** specifies the positioning method for an element:
  ```css
  .my-element {
    position: relative;
  }
  ```

- **Flexbox** provides a flexible way to distribute space among elements in a container:
  ```css
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  ```

- **Grid** creates a grid-based layout system:
  ```css
  .container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 10px;
 