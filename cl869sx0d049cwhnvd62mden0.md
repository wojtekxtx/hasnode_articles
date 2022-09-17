## Full width of article..........

Im fucking furious.............. directing this post at original creator of this blogging masp.

# Dev station

To start, let me tell you what I work on.
* MacBook Pro ( 2020 version ) + external monitor ( Benq GW* 27 inches; with HDMI support )
* Visual Studio Code Insiders + tons of addons,
* Safari as a daily driver.

## Why Mac?
Once upon a time, I worked on Windows. It was plain nightmare. So I switched. Never looked back :) Current Mac is my 2nd one.

But thats not the main reason Im writing this........

# Main problem: CSS

HashNode offers customization of blog(s) by the means of addingf our own CSS styles. Nice little functionality it is.

Or so I thought...........

## Classes

As everywhere else, also on HashNode, selectors are organized in classes ( starting with `.` ). Standard in `CSS`. Nothing to worry about, nothing complicated.

But, here is where fun part begins.........

## Some logic anyone?

Went [to my blog](https://furiousdev.hashnode.dev/). In the browser ( Safari ): `Settings > Advanced` and ticked `Show Develop menu in menu bar`.
On my blog, I clicked PPM on element I wanted to get CSS class name of > `Inspect`, WebInspector opened, and.............

**One huge WTF.................**

Names like `.css-1jqt27n`; generally `css` name + some randomly generated what? string? No its not......... God knows what it is.

Generally Im not huge fan of Google, but this time I thanked God it existed.........

Of course, apart from some crazy names, there are ones that:
* starts with `blog` keyword,
* really works,

But at the same time:
* there are rather limited possibilities of what you can do with them ( there are for basic things only ),
* many of names starting with `blog` keyword have their "duplicates" with `css` keyword, and this counterpart doing not what you think should be doing,

## Actions you cannot do
As an example you cannot set blogpost to be full width of your device ( monitor ). **There is absolutely no way of doing this.** Just look how ugly my blog looks ( so much wasted space ).


![Zrzut ekranu 2022-09-17 o 20.53.40.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663440846412/FkhfnlVSd.png align="left")

![Zrzut ekranu 2022-09-17 o 20.52.37.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1663440875078/998e5sXro.png align="left")
