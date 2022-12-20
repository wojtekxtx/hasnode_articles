# Getting value from user input (input field) after clicking button

# Scenario

We have simple form in HTML with:

*   `input` field,
    
*   button that is supposed to display an `alert` with text inputed in `input` field.
    

Simple, right? No, hell not.

# Analysis

## What?

We cannot just:

```javascript
let v = document.getElementById('inputField').value;
alert(v);
```

That would be too simple. Instead, input fields **don't have a value**!!!! Imagine that stupidity?

## Why?

??

# WHAT THE F\*CK HAPPENED WITH JS?

Thats valid question guys. Answer in the comments, please.