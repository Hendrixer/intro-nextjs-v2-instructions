---
description: "Getting starting from scratch"
---

## Using create-next-app

The fastest way to get started with Next.js is to use `create-next-app`. It's very simple, just run:

```bash
create-next-app@latest --experimental-app
```

This will install the node_modules you need, and setup a basic app with example code for you to get started. I recommend using this approach when starting a Next.js app.

## Manually

If you can't or prefer not to use create-next-app, its still very simple to get started. You only have to install a few modules:

```bash
npm i next@latest react@latest react-dom@latest eslint-config-next@latest
```

You can then create some scripts in your `package.json`:

```json
"scripts": {
  "dev": "next dev",
  "build": "next build",
  "start": "next start",
  "lint": "next lint"
}
```

And then to enable the latest features, we must tell Next.js using the `next.config.js` file

```js
/** @type {import('next').NextConfig} */
const nextConfig = {
  experimental: {
    appDir: true,
  },
};

module.exports = nextConfig;
```

At this point, you have everything you need to get started, anything else from create-next-app is either optional or not necessary (like the example code it creates).
