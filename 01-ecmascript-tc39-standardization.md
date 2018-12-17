---
lesson: 01
title: "ECMAScript, TC39, and the Standardization Process"
course: "Tyler McGinnis - Modern JavaScript"
link: "https://learn.tylermcginnis.com/courses/51206/lectures/3167280"
date: 2018-08-21
---

# ECMAScript, TC39, and the Standardization Process

**:hatching_chick: JavaScript's origin**

- Around 1995, `Netscape Navigator` was the most popular web browser (~80% marketshare)
- Marc Andreessen, the founder of `Netscape` (company behind `Netscape Navigator`), envisioned the web to do more than just share documents:
  - Dynamic platform
  - With client side interactivity
- Netscape’s goal was to build a scripting language simple enough for designers and amateurs to use, Java was too complex
- Brendan Eich was hired at Netscape to embed `Scheme` programming language in Netscape Navigator, he was brought on to build `Mocha` (aka `Javascript`) to complement `Java`
- Naming of JS
  - `Mocha` > `LiveScript` > `JavaScript`
  - Changed to JavaScript to ride the hype of Java
- The intentinos behind JavaScript vs. Java
  - `JavaScript`
    - A scripting language for the browser accessible to both amateurs and designers
  - `Java`
    - The professional tool to build rich web components

**:woman_facepalming: Browser support problems**

- In order for Microsoft's browser, `Internet Explorer`, to stay competitive and support enriched client-side experierences, they created their own language called `JScript`
- `JScript`'s implementation was different than `JavaScript` so you couldn't build a website that would work in both browsers
- `Best viewed with` buttons started to cropping up since not all sites built experiences for both `IE` and `Netscape`:

![Best viewed with IE and Netscape buttons](https://screenshot.click/2018-30-17-9omfz-475o7.jpg)

**:earth_americas: ECMA International**

- ECMA International is an industry association dedicated to the _standarization of information and communication systems_
- In November of 1996, Netscape submitted JavaScript to ECMA to build out a standard specification
- This has many benefits:
  - Gives others ownership & influence over the evolution of the language
  - Consistent implemenetation across browers
- A new specification will have an `Standard` and a `Committee`
  - For JavaScript:
    - `Standard` => ECMA-262
    - `Committee` => TC-39
  - Official name is `ECMAScript`, because `JavaScript` was trademarked by Oracle. To avoid any conflicts, ECMA named it `ECMAScript`

**:rose: What's in a name?**

- `ECMAScript` is used to refer to the `Standard`
- `JavaScript` is used to refer to the language in practice

**:calendar: `TC-39` Release Schedule**

- The _Technical Committee_ consists of various `Members` who typically are companies that are heavily invested in the Web
- Members (aka companies/browser vendors) send `Delegates` who represent those companies
- Delegates are responsible for creating, approving, or denying proposals
- Since 2016, a new version of `ECMAScript` is following an annual release cycle
  - It will include whatever features are ready at that time

---

[:arrow_left: Table of Contents](./README.md)
