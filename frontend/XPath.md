# XPath Cheatsheet

XPath is a query language used to navigate XML and HTML documents.

### XPath Syntax

- Select node by tag name: `//tagname`
- Select node by attribute value: `//tagname[@attribute='value']`
- Select node by attribute existence: `//tagname[@attribute]`
- Select node by attribute value starts with: `//tagname[starts-with(@attribute, 'value')]`
- Select node by attribute value contains: `//tagname[contains(@attribute, 'value')]`
- Select node by index: `(//tagname)[index]`
- Select node by position: `(//tagname)[position()]`
- Select multiple conditions: `//tagname[@attr1='value' and @attr2='value']`
- Select node by text content: `//tagname[text()='value']`

### XPath Axes

- Ancestor: `ancestor::tagname`
- Parent: `parent::tagname`
- Child: `child::tagname`
- Following-sibling: `following-sibling::tagname`
- Preceding-sibling: `preceding-sibling::tagname`
- Following: `following::tagname`
- Preceding: `preceding::tagname`
- Descendant: `descendant::tagname`

### XPath Functions

- `text()`: Selects the text content of a node.
- `last()`: Selects the last occurrence of a node.
- `position()`: Selects the position of a node.
- `count()`: Counts the number of occurrences of a node.
- `concat()`: Concatenates multiple strings.
- `contains()`: Checks if a string contains a substring.
- `starts-with()`: Checks if a string starts with a specified prefix.
- `ends-with()`: Checks if a string ends with a specified suffix.
- `substring()`: Returns a substring of a string.
- `substring-before()`: Returns the part of a string before a specified substring.
- `substring-after()`: Returns the part of a string after a specified substring.
- `normalize-space()`: Removes leading and trailing whitespace from a string.
- `translate()`: Translates a string by replacing the characters with the same index in the second and third arguments.
- `string()`: Converts a value to a string.
- `name()`: Returns the name of a node.
- `local-name()`: Returns the local name of a node.
- `namespace-uri()`: Returns the namespace URI of a node.
- `number()`: Converts a value to a number.

### XPath Operators

- `|`: Union operator.
- `+`: Addition operator.
- `-`: Subtraction operator.
- `*`: Multiplication operator.
- `div`: Division operator.
- `mod`: Modulus operator.
- `=`: Equal operator.
- `!=`: Not equal operator.
- `<`: Less than operator.
- `>`: Greater than operator.
- `<=`: Less than or equal operator.
- `>=`: Greater than or equal operator.
- `and`: Logical and operator.
- `or`: Logical or operator.
- `not`: Logical not operator.
- `union`: Union operator.
- `|`: Union operator.

### XPath Examples

- Select all nodes: `//*`
- Select all nodes with a specific tag name: `//tagname`
- Select all nodes with a specific attribute: `//*[@attribute]`
- Select all nodes with a specific attribute value: `//*[@attribute='value']`
- Select all nodes with a specific attribute value and tag name: `//tagname[@attribute='value']`
- Select all nodes with a specific attribute value and tag name: `//*[@attribute='value' and tagname]`