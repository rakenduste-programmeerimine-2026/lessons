# Lesson #1: JavaScript Fundamentals: Group Research Topics

Work in pairs. Each group has one topic and prepares a presentation with a short, runnable code example.

## 1. Variables: const, let, and var
- Declaring, assigning, and reassigning variables.
- When to use `const` and when to use `let`.
- Why older code uses `var`.
- Block scope: how `{ }` affects where variables are available.

## 2. Data Types, null, and undefined
- Strings, numbers, booleans, objects, and arrays.
- Checking types with `typeof`.
- The difference between `null` and `undefined`.
- The difference between `"5"` and `5`.
- Two quirks: `typeof null` and `typeof []` both return `"object"`.
- Checking whether a value is an array with `Array.isArray()`.

## 3. Operators and Type Conversion
- Arithmetic operators: `+`, `-`, `*`, `/`, `%`, and `**`.
- Updating values with `+=` and `++`.
- Converting values with `Number()` and `String()`.
- Comparing `"5" + 2` with `Number("5") + 2`.
- What `NaN` means.

## 4. Strings and Template Literals — Solo Topic
- Creating strings with single quotes, double quotes, and backticks.
- Using `.length`, `.trim()`, `.toLowerCase()`, and `.includes()`.
- Inserting values into strings with `${variable}`.
- Example: cleaning up a name and building a greeting.

## 5. Comparisons, Logical Operators, and Decisions
- Comparison operators: `===`, `!==`, `>`, `<`, `>=`, and `<=`.
- Why prefer `===` over `==`.
- Logical operators: `&&`, `||`, and `!`.
- Truthy and falsy values, including `""`, `0`, `null`, and `undefined`.
- Using `if`, `else if`, and `else`.
- Using `condition ? valueA : valueB` for a simple choice.
- Example: checking a user's age and login status to choose a message.

## 6. Numbers and the Math Object
- Using `Math.round()`, `Math.floor()`, and `Math.ceil()`.
- Finding values with `Math.min()` and `Math.max()`.
- Understanding the range of `Math.random()`.
- Example: generating a random whole number from 1 to 6.

## 7. Arrays and Loops
- Creating arrays and accessing items by index.
- Zero-based indexing and `.length`.
- Using `.includes()`, `.push()`, and `.pop()`.
- Which operations change the original array?
- Iterating over an array with `for` and `for...of`.
- Understanding a `for` loop's counter, condition, and update.
- Using `break` and avoiding infinite loops.
- Example: creating a list of names, updating it, and printing each name.

## 8. Objects and Handling Missing Data
- Creating an object with properties and values.
- Reading properties with dot and bracket notation.
- Adding and updating properties.
- Accessing nested objects.
- What happens when a property does not exist?
- Reading nested properties safely with optional chaining: `?.`.
- Providing default values with nullish coalescing: `??`.
- Comparing `value ?? fallback` with `value || fallback`,
  including when the value is `0`, `false`, or `""`.
- Example: displaying a user profile with missing information.

## 9. Functions: Reusable Behavior
- Declaring and calling functions.
- Parameters versus arguments.
- Default parameter values.
- Returning values with `return`.
- The difference between `return` and `console.log()`.
- What a function returns without an explicit `return`.

## 10. Arrow Functions and Callbacks
- Function expressions and arrow function syntax.
- Implicit returns versus explicit `return`.
- Comparing `x => x * 2` with `x => { return x * 2; }`.
- Callbacks: passing a function to another function.
- Example: using a callback with `.forEach()`.

## 11. Array Methods: map, filter, and find
- Transforming items with `.map()`.
- Selecting matching items with `.filter()`.
- Getting the first matching item with `.find()`.
- What each method returns, including when nothing matches.
- Example: transforming and searching a list of products.

## 12. Destructuring and Spread Syntax
- Extracting values with object and array destructuring.
- Copying arrays and objects with `...`.
- Creating a new array with an additional item.
- Creating a new object with an updated property.
- Why a `const` object can still be modified.
- Why spread creates a shallow copy.

## 13. Modules: import and export
- Splitting code into multiple files.
- Named exports and imports.
- Default exports and imports.
- Matching import syntax to the export.
- Example: exporting a helper function and importing it in another file.

## 14. Asynchronous JavaScript: Promises and async/await
- Why some operations finish later.
- What a promise represents.
- Promise states: pending, fulfilled, and rejected.
- Using `async` and `await`.
- Why an `async` function always returns a promise.
- Example: awaiting a provided promise and using its result.

## 15. Fetching Data, JSON, and Error Handling
- Requesting data with `fetch()`.
- Checking `response.ok`.
- Reading JSON with `await response.json()`.
- The difference between JSON and a JavaScript object.
- Handling errors with `try` and `catch`.
- Why an HTTP error such as 404 requires an explicit check.

# Questions Every Group Must Answer

1. **What is it, and what problem does it solve?**
   Explain in your own words.

2. **What does the syntax look like?**
   Explain the important symbols and keywords.

3. **Can you demonstrate every concept listed in your topic with working code?**
   Use short, clear examples and explain what each one does.
   You can use several separate examples instead of one large example.
   Show the output or result and be ready to explain your code.

4. **What will your example output or return, and why?**
   Explain how the code produces the result.

5. **What is one common beginner mistake?**
   Show the mistake and how to fix it.

6. **Where could you use this in an application?**
   For example: user profiles, product lists, forms, or loading data.

7. **Can you give the class one “predict the output” question?**
   Let classmates answer before revealing the result.
