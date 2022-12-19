---
title: "Client Components"
---

Client components are the standard React components that you've come to love and know. Full access to browser APIs, hooks, state, interactivity.

## How to use

We simply need to tell React that a component be a client component. Just add the `'use client'` directive at the top of any component you want to be a client component.

```tsx
"use client";

// regular component
const ContactForm = () => {
  const [state, setState] = useState({email: ''});
  const handleChange = () => {
    //....
  }
  const handleSubmit = () => {
    //....
  }

  return (
    <form onSubmit={...}>
      <input value={state.email} onChange={handleChange}/>
    </form>
  )
};
```

## When to use

If your components need hooks like useState and useEffect, then you need it to be a client component.

<br>

Also, 3rd party components that have yet to add the `"use client"` directive,. You will have to wrap them in your own client components.

## When to use client vs server components.

Basically alway use server components for all of your components unless it falls in 1 or more of these:

- It needs interactivity and event listeners (onClick(), onChange(), etc)
- It uses State and Lifecycle Effects (useState(), useReducer(), useEffect(), etc)
- It uses browser-only APIs
- It needs custom hooks that depend on state, effects, or browser-only APIs
- Use React Class components
