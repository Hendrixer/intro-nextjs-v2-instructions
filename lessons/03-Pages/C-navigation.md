---
title: "Navigation"
---

Next.js does so much behind the scene when it comes to handling navigation for our pages. From the docs:

_How Navigation Works_
<br>

- A route transition is initiated using <Link> or calling router.push().
- The router updates the URL in the browser’s address bar.
- The router avoids unnecessary work by re-using segments that haven't changed (e.g. shared layouts) from the client-side cache. This is also referred to as partial rendering.
- If the conditions of soft navigation are met, the router fetches the new segment from the cache rather than the server. If not, the router performs a hard navigation and fetches the Server Component payload from the server.
- If created, loading UI is shown from the server while the payload is being fetched.
- The router uses the cached or fresh payload to render the new segments on the client.

## Using the Link component

In place of an anchor tag, we can use the `Link` component from `next/link` to handle click interactions that translate to page naviations. It's easier than ever to use.

```tsx
import Link from "next/link";

export default function Page() {
  return (
    <div>
      <Link href="/blog">Blog</Link>
    </div>
  );
}
```

For dynamic routes, we can just interpolate.

```tsx
import Link from "next/link";

export default function Blog() {
  return (
    <div>
      <Link href={`/blog/${post.title}`}>Post</Link>
    </div>
  );
}
```

## Programatic usage

If you need to navigate between pages programmatically instead of when a user clicks. First, you must understand that this only works in client components, we'll get there later. Next.js provides a hook we can use that creates a router object for that has helpful navigation methods on it.

```tsx
"use client";

import { useRouter } from "next/navigation";

export default function Page() {
  const router = useRouter();

  return (
    <button type="button" onClick={() => router.push("/blog")}>
      Blog
    </button>
  );
}
```
