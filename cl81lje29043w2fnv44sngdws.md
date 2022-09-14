## The Complete React Roadmap

Learning **React** can be _confusing at first_, sometimes even _downright scary_! This article aims to put forth a **complete roadmap** to learn **React** so that you have a _clear path moving forward_.

# Prerequisites

There are some _prerequisites_ to learning **React**, without which, you will _find yourself struggling hard_. So it is _highly advisable_ to master the following skills first, before diving into learning **React**

1. **HTML** - You need to be well acquainted with the _basic tags_ and the _attributes_ they accept. No need to be an **HTML** master, _just the basics would do_
2. **CSS** - Unless you want to create _bland websites_ like this
    ![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1663157933402/ChbvAAYnK.png)
    You should definitely spend some time going through the basics (namely `selectors`, `box-model`, `flexbox`, `grid layout`, and `responsive design`) of **CSS** too.
3. **JavaScript** - Since **React** runs on top of **JavaScript**, you do need a _solid foundation_ to ease up the process of learning **React**. As a barebones, you would need `variables`, `conditional statements`, `loops`, `DOM manipulation`, and `event triggering`.
    Learning the **ES6+** features such as the `spread` & `rest operators`, and `arrow functions` would come in handy too.

# Basics

1. **Setting up a React Project**: Before you can start learning **React**, quite evidently you would need to set up a **React Project**, which is a _highly tedious task_. Luckily we have _awesome tools_ like the [`create-react-app`](https://reactjs.org/docs/create-a-new-react-app.html) _to get the job done_

2. **Get Acquainted with JSX**: Typically **React** code is written **JSX** (**JavaScript XML**). You can opt to not use it, using only `React.createElement` calls only, but there is no point in making your _life miserable doing it_

    ![Ain't Nobody got time for that](https://cdn.hashnode.com/res/hashnode/image/upload/v1663157935329/1tKdymMXp.gif)

    You should be familiar with the differences between **JSX** and **HTML**, like every `element` _must contain a closing tag_, the events are in **Camel Case** (`onClick` as opposed to `onclick`), and the ability to use **JS** inside the code directly.

3. **Types of Components**: Although recently, there is a push toward using **Functional Component** for all purposes as they are more _intuitive_ and _easier to code_, you should have a _basic understanding_ of **Class Components** too to ensure when you work on a `legacy code base`, you don't end up looking like this

    ![run away](https://cdn.hashnode.com/res/hashnode/image/upload/v1663157937477/2w-JnaoX1.gif)

4. **Props vs State**: `Props` allows us to _pass data from one component to another_, but if used inappropriately, it can lead to `prop chaining`, a _highly undesired practice_ in **React** projects, which we will _fix later down the **Roadmap**_.

    `State` allows you to _store data_ between the component **re-renders**. Updating the `state` **re-renders** the component and _every child_ accepting the `state` data as a prop.

5. **Lists and Keys**: Often while dealing with a lot of **dynamic data**, you be required to render `lists` of **data**. Make sure you add `key` to allow **React** to _keep track of the elements_ and _optimally re-render them_, instead of _re-rendering them every time something changes_.

6. **Component Life Cycle**: The **Class Components** has **life cycle** methods such as `componentDidMount()` and `componentWillUnmount()`, which can also be emulated by the `useEffect` **Hook** in **Functional Components**. These **life cycle** methods run at _specific time_, making them useful for _certain tasks_, such as an **API call** on `componentDidMount()` or **timer cleanups** during `componentWillUnmount()`

# Intermediate

Let's now dive into the Intermediate **React** topics

![let's do it](https://cdn.hashnode.com/res/hashnode/image/upload/v1663157939648/TNSqUnbwP.gif)

1. **Styling**: Till now your Application would end up looking _pretty basic_. Let's fix it right now. There are _hundreds of choices to style the application_, but unless you are using some library such as **Material UI**, **Chakra UI**, **Semantic UI**, I would highly suggest using **CSS** or **SCSS modules**, which gives you complete power of **CSS** with the addition of keeping the _styling scoped to just one file_. 

    No more to worry about using the same class name twice and accidentally overriding it.

2. **Hooks**: **Hooks** were a _recent addition_ in **React 16.8** and it totally changed the **React Ecosystem**. **Hooks** introduced features from **Class Components** into **Functional Components**, making it possible to use `state`, `lifecycle methods`, `context` and `ref`s in **Functional Components**.

    Often people avoid learning the _difficult concepts_ such as `memo` and `ref`, but that's a bad idea as if you are building anything of **real-world significance**, your application will definitely _rely heavily_ on these. Moreover using `context` allows you to avoid the `prop chaining` issue discussed previously.

    **React** also allows you to create **custom hooks** to cater to your personal need, which you should also look into. If you want to master **Hooks**, you should definitely check out [this article](https://dev.to/ruppysuppy/react-hooks-gotta-hook-em-all-78b)

3. **Portals**: Occasionally you will run into edge cases where, you _styling elements_ such as **modal** to _render on top of elements further down the **DOM** tree_ becomes a nightmare. In such cases, **Portals** are there to help you out, they allow you to render elements outside the default **React Root Element**, making it _far easier to not only style_, but even _group elements together_

4. **Lazy Loading**: **Lazy loading** is a _design pattern_ commonly used in **web design** and **development** to _defer initialization of an object_ until _the point at which it is needed_. It can contribute to **efficiency** in the program's operation _if properly and appropriately used_.

    Luckily implementing **Lazy Loading** in **React** is a walk in the park. All you need is the `Suspense` **Component** and familiarity with the `import()` function.

# Advanced

_Found everything on the list a piece of cake?_

![Easy](https://cdn.hashnode.com/res/hashnode/image/upload/v1663157942617/xc16CvMlN.gif)

Put your knowledge to the test with these _advanced skills_

1. **Webpack & Babel**: None of the **JSX** you write can be _understood by a browser_, so it has to be `transpiled` into regular **JS** for Browser to execute it. The transpilation process is handled by **Babel** and bundling everything into a single file is done by **Webpack**.

    To truly understand _how everything fits in_, you need to build a **React App** from scratch, check out [this article](https://dev.to/ruppysuppy/create-react-app-from-scratch-like-a-pro-de0) to know how to do it.

2. **Testing**: **Testing** is something very few people actually enjoy doing, as it falls under the category of **"dark work"**, where the things you _doesn't make any visible changes_. But for large applications, it is of _crucial importance_ as _a small change might end up breaking the entire application_.

3. **TypeScript**: This is simply _one of the core skills you must possess_. **TypeScript** is a superset of **JavaScript**, which adds the important, _yet optional_, **strict type system** and is the language of choice for any **large scale React application**.

That's all you need to know about **React**

![Phew](https://cdn.hashnode.com/res/hashnode/image/upload/v1663157945411/pncCioW2g.gif)

# Ecosystem

> But what about the React Router, or perhaps something for state management?

Glad you asked! Let's dive into the **React Tools** that are worth diving into. You can check these out as soon as you are done with the basics of **React**

1. **Routing**: Since **React** is a _library_ and not a _framework_, it doesn't ship with its own routing, but **React Router** is a library that's worth looking into.

    If you are using an **SSG** (**Static Site Generation**) or SSR (**Server Side Rendering**) like **Gatsby** or **Next.js**, then you would already have a routing built-in, without requiring any additional libraries

2. **State Management**: **State Management** tools like **Context API** is a nice feature of **React**, but falls short in the case of _large scale applications_. In such cases, using a library like **Redux** or the _innumerable ones_ available on `npm` would be a better idea

3. **Cross-Platform**: If you want to use the same logic as your **Web App** in a **Mobile Application** and **Desktop Application** too, **React Native** and **Electron** (or preferably **Tauri**) would be great tools to look into. 

4. **Styling**: If you don't want to write custom styling for your application, **Material UI**, **Chakra UI**, or **Semantic UI** might be worth a look. It can _drastically reduce the effort required_ as they come with **pre-built components**.

# Wrapping Up

That's the **Complete React Roadmap**. Hope that helps you plan out your journey to become a ground-breaking **React Developer**.

**Happy Developing!**

Did I miss something? Share it in the comments below 👇

Want to see an **Advanced React Project** built from scratch? Check out

{% github https://github.com/ruppysuppy/Crypto-Crowdfund no-readme %}

Research says, **writing down your goals on pen & paper** makes you **21%** to **39%** more likely to achieve them. Check out these notebooks and journals to **make the journey of achieving your dreams easier**: [https://www.amazon.com/Tapajyoti-Bose/e/B09VGDDHRR](https://www.amazon.com/Tapajyoti-Bose/e/B09VGDDHRR)