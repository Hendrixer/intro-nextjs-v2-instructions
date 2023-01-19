---
title: "Server Components"
---

Finally, we've been talking about server components a lot, so what are they? Server components are a concept created on the React.js level. You can checkout the RFC [here](https://reactjs.org/blog/2020/12/21/data-fetching-with-react-server-components.html).

<br>

Server components are components that never leave the server, so there is never any JavaScript that gets shipped to the client. This means that server components can't use things like hooks and client-side APIs that the browser provides. The results of rendering these components are streamed to the client and cached on a per route segment basis. By default, all components in the app directory in Next.js are server components.

## Server components vs SSR

Traditional SSR is when a component is rendered on the server and the HTML is serialized and sent to the browser, not streamed. Then the client picks up and re-renders the same thing where it then takes over. So you're still shipping JS to the client.

## When to use Server components

You should always just use server components until you have a need for some client side interaction or using a 3rd party lib.
