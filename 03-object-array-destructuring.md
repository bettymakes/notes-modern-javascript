---
lesson: 03
title: "Object and Array Destructuring in JavaScript. ES6 | ES2015"
course: "Tyler McGinnis - Modern JavaScript"
link: "https://learn.tylermcginnis.com/courses/51206/lectures/3167415"
date: 2018-08-21
---

# Object and Array Destructuring in JavaScript. ES6 | ES2015

## :woman_juggling: Destructuring 101

- `Destructuring` allows us to:
  - Easily get/extract data from an `Object` or an `Array`
  - Assign those extracted values to variables

## :basketball: Object Destructuring

### Basics

- With a JavaScript `Object`, we can:

  - Set a single property, one at a time
    - Through `dot notation`
    ```js
    var user = {};
    user.name = "Poop";
    user.location = "Nature";
    user.points = 50;
    ```
  - Get a single value from a property and create/initialize a new variable, one at a time
    - Through `dot notation`
    ```js
    var name = user.name;
    var location = user.location;
    var points = user.points;
    ```
  - Set multiple properties to an `Object`, at the same time
    - Through `Object literal notation` when initializing the Object
    ```js
    var user = {
      name: "Poop",
      location: "Nature",
      points: 50
    };
    ```
  - Get multiple properties from an `Object` and create/initialize variables, at the same time

    - :fire: ??? Before ES2015 ??? :fire:
    - Through `destructuring`

    ```js
    // var name     = user.name;
    // var location = user.location;
    // var points   = user.points;

    var { name, location, points } = user;
    ```

    - Bonus: We can `destructure` the result of a function invocation:

    ```js
    function getUser() {
      return {
        name: "Poop",
        location: "Nature",
        points: 50
      };
    }

    var { name, location, points } = getUser();
    ```

### Renaming properties

- If the `Object`'s property names are mediocre, we can rename them when destructuring

```js
var user = {
  n: "Poop",
  l: "Nature",
  p: 50
};

var { n: name, l: location, p: points } = user;

console.log(name); // => "Poop"
console.log(location); // => "Nature"
console.log(points); // => 50
```

## :pencil: Array Destructuring

- Array destructuring is useful when the location of the item is its main differentiator (think `Tuples`)

```js
var pokemon = ["Pikachu", "electric", 025];
```

- To extract the values from the array, we'd need to do get them _one at a time_

```js
var name = pokemon[0];
var type = pokemon[1];
var number = pokemon[2];
```

- To extract the values from the array, _at the same time_, we use `destructuring`

```js
var [name, type, number] = pokemon;

var csv = "2000,Honda,Civic,Hot Buy!";
var [year, make, model, description] = csv.split(",");
```

## :wrench: Function Arguments Destructuring

### Objects

- A function's api is typically quite strict; the order of the arguments matter

```js
function fetchRepos(language, minStars, maxStars) {
  // etc.
}

fetchRepos("JavaScript", null, 30);
```

- However, order doesn't matter with destructured function arguments

```js
function fetchRepos({ language, minStars, maxStars }) {
  // etc.
  console.log(language);
  console.log(minStars);
  console.log(maxStars);
}

fetchRepos({
  maxStars: 30,
  language: "JavaScript",
  minStars: null
});
```

- In fact, we can even set `default` vaules for each argument and not have to pass in unnessary values (ie. `minStars: null`)

  ```js
  function fetchRepos({ language = "All", minStars = 0, maxStars = 0 }) {
    // etc.
  }

  fetchRepos({
    maxStars: 30,
    language: "JavaScript"
  });

  // An empty Object literal needs to be passed
  // to invoke the function and accept the default values
  fetchRepos({});
  ```

- To take it one step further, we can assign a default argument value for the entire destructured param

```js
function fetchRepos({ language = "All", minStars = 0, maxStars = 0 } = {}) {
  // etc.
}

// Now we can invoke the functino to accept the default values
// without having to pass an empty Object literal
fetchRepos();
```

### Arrays

- When an argument is expecting an `Array`, we can destructure those values as well. A great use case is with `Promises` since it returns `data` as an Array.

```js
function getUserData(player) {
  return Promise.all([getProfile(player), getRepos(player)]).then(function(
    data
  ) {
    // Simply destructuring the `data` arg
    var [profile, repos] = data;

    return {
      profile: profile,
      repos: repos
    };
  });
}

// OR

function getUserData(player) {
  return Promise.all([getProfile(player), getRepos(player)]).then(function(
    // Destructuring `data` in the fn argument
    [profile, repos]
  ) {
    return {
      profile: profile,
      repos: repos
    };
  });
}
```

---

[:arrow_left: Table of Contents](./README.md)
