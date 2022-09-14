## 7 Killer One-Liners in JavaScript

# Shuffle Array

While using algorithms that require _some degree of randomization_, you will often find shuffling arrays quite a necessary skill. The following snippet shuffles an array **in place** with `O(n log n)` complexity.

```javascript
const shuffleArray = (arr) => arr.sort(() => Math.random() - 0.5);

// Testing
const arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
console.log(shuffleArray(arr));
```

# Copy to Clipboard

In web apps, **copy to clipboard** is rapidly rising in popularity due to its _convenience for the user_.

```javascript
const copyToClipboard = (text) =>
  navigator.clipboard?.writeText && navigator.clipboard.writeText(text);

// Testing
copyToClipboard("Hello World!");
```

**NOTE:** The approach works for **93.08%** global users as per [caniuse](https://caniuse.com/?search=Clipboard%20API%3A%20writeText). So the check is necessary that the user's browser supports the **API**. To support all users, you can use an `input` and **copy its contents**.

# Unique Elements

Every language has its own implementation of `Hash List`, in **JavaScript**, it is called `Set`. You can easily get the unique elements from an array using the `Set` **Data Structure**.

```javascript
const getUnique = (arr) => [...new Set(arr)];

// Testing
const arr = [1, 1, 2, 3, 3, 4, 4, 4, 5, 5];
console.log(getUnique(arr));
```

# Detect Dark Mode

With the rising popularity of **dark mode**, it is ideal to switch your app to **dark mode** if the user has it enabled in their device. Luckily, `media queries` can be utilized for making the task a _walk in the park_.

```javascript
const isDarkMode = () =>
  window.matchMedia &&
  window.matchMedia("(prefers-color-scheme: dark)").matches;

// Testing
console.log(isDarkMode());
```

As per [caniuse](https://caniuse.com/?search=%20%20window.matchMedia) the support of `matchMedia` is **97.19%**.

# Scroll To Top

Beginners very often find themselves struggling with scrolling elements into view properly. The easiest way to scroll elements is to use the `scrollIntoView` method. Add `behavior: "smooth"` for a smooth scrolling animation.

```javascript
const scrollToTop = (element) =>
  element.scrollIntoView({ behavior: "smooth", block: "start" });
```

# Scroll To Bottom

Just like the `scrollToTop` method, the `scrollToBottom` method can easily be implemented using the `scrollIntoView` method, only by switching the `block` value to `end`

```javascript
const scrollToBottom = (element) =>
  element.scrollIntoView({ behavior: "smooth", block: "end" });
```

# Generate Random Color

Does your application rely on **random color generation**? Look no further, _the following snippet got you covered_!

```javascript
const generateRandomHexColor = () =>
  `#${Math.floor(Math.random() * 0xffffff).toString(16)}`;
```