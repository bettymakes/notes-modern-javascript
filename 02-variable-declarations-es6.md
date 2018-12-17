---
lesson: 02
title: "var vs let vs const: Variable declarations in ES6 | ES2015"
course: "Tyler McGinnis - Modern JavaScript"
link: "https://learn.tylermcginnis.com/courses/51206/lectures/3167412"
date: 2018-08-21
---

# var vs let vs const: Variable declarations in ES6 | ES2015

## :hatching_chick: Variable, Initialization, and Scope

- `Variable`

  - Variable declarations introduces a new identifier:

  ```js
  var declaration; // => identifier called 'declaration'

  console.log(declaration); // => undefined
  ```

  - Varibles are initialized with the value of `undefined` when they are created

- `Initialization`
  - Initialization is when you first _assign_ a value to a variable
  ```js
  var declaration = "Initializing var with a string value";
  ```
- `Scope`

  - Defines where variables and functions are _accessible_ inside of your program
  - There are two kinds of scope in JavaScript:

    - `Function` scope
      - If the variable statement occurs inside a `Function Declaration`, the variables are defiend with `function-local` scope in that function
    - `Global` scope
      - Otherwise, they are defined with `global scope`, that is, they are created as members of the global object
    - In other words...
      - If a variable is created with the `var` keyword inside of a function, it is accessible within the function and the functions nested inside of it.
      - A variable created without `var` is added as a property on the global object

    ```js
    function discountPrices(prices, discount) {
      var discounted = [];
      for (var i = 0; i < prices.length; i++) {
        var discountedPrice = prices[i] * (1 - discount);
        var finalPrice = Math.round(discountedPrice * 100) / 100;
        discounted.push(finalPrice);
      }

      console.log(i); // => 3
      console.log(discountedPrice); // => 150
      console.log(finalPrice); // => 150

      return discounted;
    }

    discountedPrices([100, 200, 300], 0.5);
    ```

    - Because variables are `function scoped`, we still have access to `i`, `discountedPrice`, and `finalPrice` created within the `for` loop.

- `Hoisting`

  - When the JavaScript interpreter evaluates our code, it moves all of our variable and function declarations to the top of the current scope
  - For instance, if we have the following code ...

  ```js
  // Our code:

  console.log(hoisted); // => undefined
  var hoisted;
  ```

  - It will be interpreted as ...

  ```js
  // Interpretted code:

  var hoisted;
  console.log(hoisted); // => undefined
  ```

  - Given the `discountedPrices` example earlier, the interpretted code would resemble the following:

  ```js
  //Interpretted code

  var discounted;
  var i;
  var discountedPrice;
  var finalPrice;

  function discountPrices(prices, discount) {
    discounted = [];
    for (i = 0; i < prices.length; i++) {
      discountedPrice = prices[i] * (1 - discount);
      finalPrice = Math.round(discountedPrice * 100) / 100;
      discounted.push(finalPrice);
    }

    return discounted;
  }

  discountedPrices([100, 200, 300], 0.5);
  ```

  - Once the variables are initialized, they can then be `referenced`.
  - For instance, JavaScript will find a reference to the `discounted` varaible within this function. If a reference isn't found, it then adds `discounted` as a property to the global scope.

## :memo: `var` vs. `let` vs. `const`

- `var`
  - function scoped
  - Referencing a variable before it's defined will result in the variable being set to `undefined`
- `let`

  - block scoped (ie. `{ }`)

    - This expands beyond functinos and can include `if` and `for` for instance
    - In the example below, changing `var` to `let` would produce `ReferenceErrors` since `i`, `discountedPrice` and `finalPrice` are no longer accessible outside of the `for` block:

    ```js
    function discountPrices(prices, discount) {
      let discounted = [];
      for (let i = 0; i < prices.length; i++) {
        let discountedPrice = prices[i] * (1 - discount);
        let finalPrice = Math.round(discountedPrice * 100) / 100;
        discounted.push(finalPrice);
      }

      console.log(i); // ReferenceError: i is not defined
      console.log(discountedPrice); // ReferenceError: discountedPrice is not defined
      console.log(finalPrice); // ReferenceError: FinalPrice is not defined

      return discounted;
    }

    discountedPrices([100, 200, 300], 0.5);
    ```

  - Referencing a variable before it's defined will result in a `ReferenceError` being thrown

- `const`

  - All the rules for `let` applies to `const`. However, `const` is unique because ...

  - New values _cannot_ be reassigned to `const`

  ```js
  // Reassign a new value

  const powerRangers = 5;
  powerRangers = 10; // TypeError: Assignment to constant variable
  ```

  - But, properties on an object _can_ be modified

  ```js
  // Modify proprties

  const car = {
    brand: "Tesla"
  };
  car.brand = "Honda"; // this is ok!

  car = {}; // TypeError: Assignment to constant variable
  ```

  - Therefore, `const` does not imply immutability since things can be modified

## :woman_shrugging: So which one should we use!?

- TL;DR
  - :white_check_mark: Always use `const` unless the value changes, then use `let`
  - :no_entry_sign: Never use `var` again
- Ask yourself, will this variable's value change?
  - If `no` ...
    - Use `const`
    - This has the benefit of telling your future self and other developers that this variable shouldn't change
  - If `yes` ...
    - Use `let`
    - Common use-case for `let` is in a `for` loop for instance
- Worth noting:
  - The counter-opinion is to not use `const` since it's intent is to signify that the value will not change. However, you can still update properties on an object, so it's counter-intuitive.

---

[:arrow_left: Table of Contents](./README.md)
