# Preview article on Medium?

What `WordPress`, `Medium`, `Hashnode` and many other blogging platforms have in common? They all use one, although highly customized,  editor. That is [TinyMCE](https://github.com/tinymce/tinymce).

# Problem
While writing article on [Medium](https://medium.com) their editor just plain sucks.
There is no easy way of doing so simple task as previewing article.

# Remediation
This is no easy task esecially for standard reader/user. IT pro will know what, and where, to do.

## Thesis
Basically there are two ways of doing it:
* old-fashioned way: using external Markdown editor, like `MarkDown Pad`, write your article and than cpy-paste (`ctrl+c >> ctrl+v`) into Medium's editor,
* more modern way: using `WebDev Tools` as well as [this little browser extension](https://github.com/adam-p/markdown-here)

## How to
Bear in mind: **this is not official guide**. Steps below have been found out by me after many hours of playing with & testing various approaches.

If you decide to `enable` preview mode, you need to:
* inspect [Medium](https://medium.com) with `WebDev Tools`,
* find tab that displays `CSS/SASS` code,
* you will notice code:

```css
.preview-btn,
.prv-btn {
...
display: none;
...
}
```
* change `display: none;` to `display:grid`
* no need to save it, `WebDev Tools` autoapplies changes

**Remember: do not reload page! Upon reloading, yoiur changes will be gone!**