---
title: "Layouts and Pages"
---

## Head component

Our app needs a `head` component in the app directory. This will hold the meta and title tags for our application.

```tsx
// ./app/head.tsx
export default function Head() {
  return (
    <>
      <title></title>
      <meta name="viewport" content="width=device-width, initial-scale=1" />
    </>
  );
}
```

## Layouts

Layouts are components that wrap our pages. We can use them when we want to keep certain UI elements on page across routes. Things like a navigation bar, footer, layout, etc. We need to create a root layout. You must have a root layout when using the app directory.

```tsx
// ./app/layout.tsx
export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <head />
      <body>{children}</body>
    </html>
  );
}
```

### Nested Layouts

It's required to have a root layout, but we can also have multiple nested layouts that render inside each other. You simply have to create a `layout` file in the route folder. By default, the layouts will nest.
