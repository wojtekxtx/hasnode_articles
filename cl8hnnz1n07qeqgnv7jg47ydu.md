## 7 neat tricks for JS that you probably did not know

Got tired of learning and want to get some **cool tricks up your sleeve** to earn the right to show off? You have come to the right place. Here are **neat tricks** that can even make your life easier!

# Tricks
## Readable numbers

Ever run into an unreadably **long number** where you had to put your finger on the screen to read it? Luckily, there is an easy solution to that by using `_` within the bounds of the number.

```js
const number = 123_456_789;
```

You can put `_` anywhere within a number to make it easier to read, without hampering the number itself.

## Truncate the end of arrays

Most people use `Array.length` as a **getter function**. A little-known fact is: that it can also be used as a **setter**.

```js
let array = [1, 2, 3, 4, 5];

console.log(array); // [1, 2, 3, 4, 5]
console.log(array.length); // 5

array.length = 3;

console.log(array); // [1, 2, 3]
```

## Short circuit evaulation

![short-circuit](https://cdn.hashnode.com/res/hashnode/image/upload/v1663157783389/_qXKbAeW9.gif)

No, we are NOT talking about those **short circuits**.

The `&&` and `||` operators can be easily used to check for conditions and return values in a single line, which is known as **short circuit evaluation**.

### Use case of `&&`

```js
const showUserData = true;
const data = "not so secret data";

// will display false if showUserData is false
console.log(showUserData && data);
```

### Use case of `||`

```js
const fallbackData =
  "nothing to see folks";
const data = "random data";

// will display `fallbackData` if
// data is false-ish (eg: null, undefined, '', etc)
console.log(data || fallbackData);
```

## Optional chaining

> The optional chaining operator (`?.`) enables you to read the value of a property located deep within a chain of connected objects without having to check that each reference in the chain is valid

It's a simple solution to get a **deeply nested property** without having to check the validity of each reference in the chain.

```js
// usage (will return undefined if any of the items is not defined)
user.data?.name;
user.data?.addressList?.[0];
user.greet?.(time);
```

## Get unique values in an array

Accessing the **unique values** in an array is a pretty common operation. There's a usual way, and there's a smart way of doing it

```js
// USUAL WAY
// O(n^2) time complexity & O(n) space complexity
const uniqueValues = array.filter(
  (value, index, self) =>
    self.indexOf(value) === index
);

// SMART WAY
// complexity: O(n) time & space
const uniqueValues = [
  ...new Set(array),
];
```

## Nullish coalescing

> The nullish coalescing operator (`??`) is a logical operator that returns its right-hand side operand when its left-hand side operand is null or undefined, and otherwise returns its left-hand side operand.

**Nullish coalescing** is extremely useful when you want to return a default value when a variable might contain a **null-ish value**.

```js
const getUserName = (user) => {
  return user?.name ?? "Anonymous";
};
```

## Replace all

The `string.replace` method is typically used to **replace the first occurrence of a substring**, but there is a simple way to turn it into a function that can replace all occurrences by using a **regular expression** with a **global flag**.

```js
const replace_string =
  "Visit replacesoft. replacesoft is a software company";

console.log(
  replace_string.replace(
    /replace/,
    "Micro"
  )
); // "Visit Microsoft. replacesoft is a software company"

console.log(
  replace_string.replace(
    /replace/g,
    "Micro"
  )
); // "Visit Microsoft. Microsoft is a software company"
```