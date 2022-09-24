## 7 Tips for Clean React TypeScript Code you Must Know

**Clean code** isn't code that just works. It refers to **neatly organized code** which is **easy to read**, **simple to understand** and **a piece of cake to maintain**.

Let's take a look at some of the best practices for **clean code** in **React**.

# Provide explicit types for all values

Quite often while using **TypeScript** a lot of people skip out on providing **explicit types** for values, thus missing out on the true benefit **TypeScript** has to offer. Often these can be seen in **code-base**:

**Bad Example 01:**

```tsx
const Component = ({ children }: any) => {
  // ...
};
```

**Bad Example 02:**

```tsx
const Component = ({ children }: object) => {
  // ...
};
```

Instead using a properly defined `interface` would make your life so much easier, with the editor providing you **accurate suggestions**.

**Good Example:**

```tsx
import { ReactNode } from "react";

interface ComponentProps {
  children: ReactNode;
}

const Component = ({ children }: ComponentProps) => {
  // ...
};
```

# Take the previous state into account while updating the state

It is always advisable to **set state as a function of the previous state** if the **new state** relies on the **previous state**. **React state updates can be batched**, and not writing your updates this way can lead to unexpected results.

**Bad Example:**

```tsx
import React, { useState } from "react";

export const App = () => {
  const [isDisabled, setIsDisabled] = useState(false);

  const toggleButton = () => {
    setIsDisabled(!isDisabled);
  };

  // here toggling twice will yeild the same result
  // as toggling once
  const toggleButtonTwice = () => {
    toggleButton();
    toggleButton();
  };

  return (
    <div>
      <button disabled={isDisabled}>
        I'm {isDisabled ? "disabled" : "enabled"}
      </button>
      <button onClick={toggleButton}>
        Toggle button state
      </button>
      <button onClick={toggleButtonTwice}>
        Toggle button state 2 times
      </button>
    </div>
  );
};
```

**Good example:**

```tsx
import React, { useState } from "react";

export const App = () => {
  const [isDisabled, setIsDisabled] = useState(false);

  const toggleButton = () => {
    setIsDisabled((isDisabled) => !isDisabled);
  };

  const toggleButtonTwice = () => {
    toggleButton();
    toggleButton();
  };

  return (
    <div>
      <button disabled={isDisabled}>
        I'm {isDisabled ? "disabled" : "enabled"}
      </button>
      <button onClick={toggleButton}>
        Toggle button state
      </button>
      <button onClick={toggleButtonTwice}>
        Toggle button state 2 times
      </button>
    </div>
  );
};
```

# Keep your files lean & clean

Keeping your files **atomic and lean** makes **debugging**, **maintaining**, and even **finding the files** a walk in the park!

**Bad Example:**

```tsx
// src/App.tsx
export default function App() {
  const posts = [
    {
      id: 1,
      title: "How to write clean react code",
    },
    {
      id: 2,
      title: "Eat, sleep, code, repeat",
    },
  ];

  return (
    <main>
      <nav>
        <h1>App</h1>
      </nav>
      <ul>
        {posts.map((post) => (
          <li key={post.id}>
            {post.title}
          </li>
        ))}
      </ul>
    </main>
  );
}
```

**Good Example:**

```tsx
// src/App.tsx
export default function App() {
  return (
    <main>
      <Navigation title="App" />
      <Posts />
    </main>
  );
}

// src/components/Navigation.tsx
interface NavigationProps {
  title: string;
}

export default function Navigation({ title }: NavigationProps) {
  return (
    <nav>
      <h1>{title}</h1>
    </nav>
  );
}

// src/components/Posts.tsx
export default function Posts() {
  const posts = [
    {
      id: 1,
      title: "How to write clean react code",
    },
    {
      id: 2,
      title: "Eat, sleep, code, repeat",
    },
  ];

  return (
    <ul>
      {posts.map((post) => (
        <Post key={post.id} title={post.title} />
      ))}
    </ul>
  );
}

// src/components/Post.tsx
interface PostProps {
  title: string;
}

export default function Post({ title }: PostProps) {
  return <li>{title}</li>;
}
```

# Use Enums or Constant Objects for values with multiple states

The process of managing variables that can take multiple **states** can be eased a lot by using `Enums` or `Constant Objects`.

**Bad Example:**

```tsx
import React, { useState } from "react";

export const App = () => {
  const [status, setStatus] = useState("Pending");

  return (
    <div>
      <p>{status}</p>
      <button onClick={() => setStatus("Pending")}>
        Pending
      </button>
      <button onClick={() => setStatus("Success")}>
        Success
      </button>
      <button onClick={() => setStatus("Error")}>
        Error
      </button>
    </div>
  );
};
```

**Good Example:**

```tsx
import React, { useState } from "react";

enum Status {
  Pending = "Pending",
  Success = "Success",
  Error = "Error",
}
// OR
// const Status = {
//   Pending: "Pending",
//   Success: "Success",
//   Error: "Error",
// } as const;

export const App = () => {
  const [status, setStatus] = useState(Status.Pending);

  return (
    <div>
      <p>{status}</p>
      <button onClick={() => setStatus(Status.Pending)}>
        Pending
      </button>
      <button onClick={() => setStatus(Status.Success)}>
        Success
      </button>
      <button onClick={() => setStatus(Status.Error)}>
        Error
      </button>
    </div>
  );
};
```

# Use TS-free TSX as much as possible

## How can **TSX** be **TS-free**?

Relax, we are talking only about the **Markup** part NOT the entire **component**. Keeping it **function-free** makes the component easier to understand.

**Bad Example:**

```tsx
const App = () => {
  return (
    <div>
      <button
        onClick={() => {
          // ...
        }}
      >
        Toggle Dark Mode
      </button>
    </div>
  );
};
```

**Good Example:**

```tsx
const App = () => {
  const handleDarkModeToggle = () => {
    // ...
  };

  return (
    <div>
      <button onClick={handleDarkModeToggle}>
        Toggle Dark Mode
      </button>
    </div>
  );
};
```
# Conditionally Rendering Elements (CREs)

**Bad Example:**

```tsx
const App = () => {
  const [isTextShown, setIsTextShown] = useState(false);

  const handleToggleText = () => {
    setIsTextShown((isTextShown) => !isTextShown);
  };

  return (
    <div>
      {isTextShown ? <p>Now You See Me</p> : null}

      {isTextShown && <p>`isTextShown` is true</p>}
      {!isTextShown && <p>`isTextShown` is false</p>}

      <button onClick={handleToggleText}>Toggle</button>
    </div>
  );
};
```

**Good Example:**

```tsx
const App = () => {
  const [isTextShown, setIsTextShown] = useState(false);

  const handleToggleText = () => {
    setIsTextShown((isTextShown) => !isTextShown);
  };

  return (
    <div>
      {isTextShown && <p>Now You See Me</p>}

      {isTextShown ? (
        <p>`isTextShown` is true</p>
      ) : (
        <p>`isTextShown` is false</p>
      )}

      <button onClick={handleToggleText}>Toggle</button>
    </div>
  );
};
```

# Use JSX shorthands
## Boolean Props

**Bad Example:**

```tsx
interface TextFieldProps {
  fullWidth: boolean;
}

const TextField = ({ fullWidth }: TextFieldProps) => {
  // ...
};

const App = () => {
  return <TextField fullWidth={true} />;
};
```

**Good Example:**

```tsx
interface TextFieldProps {
  fullWidth: boolean;
}

const TextField = ({ fullWidth }: TextFieldProps) => {
  // ...
};

const App = () => {
  return <TextField fullWidth />;
};
```

## String Props
**Bad example:**

```tsx
interface AvatarProps {
  username: string;
}

const Avatar = ({ username }: AvatarProps) => {
  // ...
};

const Profile = () => {
  return <Avatar username={"John Wick"} />;
};
```

**Good example:**

```tsx
interface AvatarProps {
  username: string;
}

const Avatar = ({ username }: AvatarProps) => {
  // ...
};

const Profile = () => {
  return <Avatar username="John Wick" />;
};
```

## Undefined Props

**Bad Example:**

```tsx
interface AvatarProps {
  username?: string;
}

const Avatar = ({ username }: AvatarProps) => {
  // ...
};

const Profile = () => {
  return <Avatar username={undefined} />;
};
```

**Good Example:**

```tsx
interface AvatarProps {
  username?: string;
  // OR `username: string | undefined`
}

const Avatar = ({ username }: AvatarProps) => {
  // ...
};

const Profile = () => {
  return <Avatar />;
};
```

Now you too know how to write clean **TSX**!