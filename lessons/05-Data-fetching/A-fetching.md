---
title: "Fetching data"
---

## Server components

Pages and Layouts might need data before they render. Tapping into APIs, databases, and other sources. Data is cached and streamed to the client automatically. It is recommended to fetch data in server components so the backend can handle this. There are a few reasons for this:

- They have access to backends DBs
- Keeping your app more secure by not exposing API keys and other secrets to the client
- Reduce the load on the main thread in the browser by having both fetching and rendering happening in the same environment on the server
- ...and many more reason

<br>

### Fetch

React extends the `fetch` function to provide automatic request deduplication. This is on a per request basis. Next.js extends fetch by allowing us to customuze how we cache certain data. We can access fetch globally without any imports and it works mostly the same.

```ts
fetch("https://api.data.com/...");
```

<br>

By default, fetch will cache all results, which is great for static data. But for dynamic data, you can skip the caching.

```ts
fetch("https://api.data.com/...", { cache: "no-store" });
```

### Async components

For server components, we can use `async/await` on the component level to get our data.

```tsx
const getData = async () => {
  const res = await fetch("https://api.cms.com/....");

  return res.json();
};

export default async function HomePage() {
  // wow! No hooks on server components!
  const data = await getData();

  return <div>{data.title}</div>;
}
```

## Getting data without fetch

Getting data without fetch in server components is supported as well. Like when using a DB, the filesystem, or 3rd party SDKs. You just won't get all the granular caching and deduping support. You still will get the default caching for route segments. There's so much more to caching, deduping, and revalidating. I recommend learning more [here](https://beta.nextjs.org/docs/data-fetching/caching).

## Client components

Until we're able to use the new `use()` hook from React, client data fetching is mostly the same as always. It's recommeded to use SWR or ReactQuery.
