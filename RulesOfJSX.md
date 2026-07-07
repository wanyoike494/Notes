JSX (JavaScript XML) is a syntax extension for JavaScript used commonly with React. It looks like HTML, but it comes with a strict set of rules because it ultimately compiles down to standard JavaScript function calls.

Here are the fundamental rules you must follow when writing JSX:

---

## 1. Return a Single Root Element

JSX requires all elements to be wrapped in a **single parent element**. You cannot return multiple top-level elements side-by-side.

* ❌ **Incorrect:**
```jsx
// This will throw a syntax error
return (
  <h1>Hello!</h1>
  <p>Welcome to my site.</p>
);

```


* **Correct:** Wrap them in a `<div>` or a **React Fragment** (`<>...</>`) if you don't want to add extra nodes to the DOM.
```jsx
return (
  <>
    <h1>Hello!</h1>
    <p>Welcome to my site.</p>
  </>
);

```



---

## 2. Close All Tags

Unlike standard HTML where some tags (like `<img>`, `<br>`, or `<input>`) don't need a closing tag, **JSX is strict**. Every single tag must be explicitly closed.

* ❌ **Incorrect:** `<input type="text">` or `<br>`
* **Correct:** Self-closing tags must end with a slash: `<input type="text" />` or `<br />`.

---

## 3. Use `camelCase` for Most Attributes

JSX turns into JavaScript, and attributes become keys in JavaScript objects. Because of this, standard HTML attributes are converted to **camelCase**.

* ❌ **Incorrect:** `<table onclick="activate()">`
* **Correct:** `<table onClick={activate}>`

### Critical Exceptions: `class` and `for`

Because `class` and `for` are reserved keywords in JavaScript, you must use their JSX counterparts:

* Use **`className`** instead of `class`.
* Use **`htmlFor`** instead of `for` (used in labels).

```jsx
// Correct usage
<div className="container">
  <label htmlFor="username">Username</label>
  <input id="username" type="text" />
</div>

```

---

## 4. Embed JavaScript with Curly Braces `{}`

Whenever you want to bring JavaScript logic, variables, or expressions into your markup, you must wrap them in curly braces `{}`.

```jsx
const name = "Joseph";

// Using a variable inside JSX
return <h1>Hello, {name}!</h1>;

```

> 💡 **Note:** Inside curly braces, you can only use **expressions** (things that return a value, like map(), ternary operators, or math). You cannot put entire JavaScript statements like `if` or `for` loops directly inside them.

---

## 5. Inline Styles Must Be Objects

In HTML, styles are passed as strings. In JSX, inline styles must be passed as **JavaScript objects** enclosed in curly braces. This means you will often see double curly braces `{{ }}`—the outer pair for the JSX expression, and the inner pair for the object itself.

* ❌ **Incorrect:** `<div style="color: red; font-size: 16px;">`
* **Correct:** Property names must also be camelCased.
```jsx
<div style={{ color: 'red', fontSize: '16px' }}>

```



---

## Quick Summary Table

| Feature | Standard HTML | JSX |
| --- | --- | --- |
| **Root Elements** | Multiple allowed | Must have **one** wrapper parent |
| **Tag Closing** | Optional for some (`<img>`) | **Mandatory** for all (`<img />`) |
| **Class Attribute** | `class="btn"` | `className="btn"` |
| **Inline Styles** | String: `"color: blue;"` | Object: `{{ color: 'blue' }}` |
| **Naming Convention** | lowercase (`onclick`) | camelCase (`onClick`) |