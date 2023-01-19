## Global

You can create a `css` file and import it anywhere in your app. For global styles, it's recommended to import that file into your root layout(s).

```css
* {
  box-sizing: border-box;
}
```

```tsx
// app/layout.tsx

import "./global.css";

export default function RootLayout() {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}
```

If you have more than one RootLayout, be sure to import the global CSS file in each one of them.

## External

External CSS is pretty much the same as global. After you install it with `npm`, import it in a layout.
