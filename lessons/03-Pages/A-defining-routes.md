---
title: "Defining routes"
description: ""
---

## File based routing

Next.js uses file based routing. This means, instead of configuring a router yourself like you would with react-router or express for an API, you instead follow a set of folder and file name conventions and Next.js will configure the router for you. It's really magical.

<br>

## App directory

Next.js 13 introduces the `app` directory that expects you to follow file based routing. Previously, there was the `pages` directory (still works with v13). They both can handle file based routing but very differently. We'll mostly focus on the app directory and talk about the differences.
<br>

All pages must go in the app directory. To create some routes, we have to create a folder with the path of the rotute, and then a `page.{tsx, jsx, js}`. So for the index route, we don't need a folder, becuase the URL for the index page doesn't have a path, we can just create the page file.

```jsx
export default function IndexPage() {
  return <div>home</div>;
}
```

For a route that has a named path, we can create a folder. So for the contact page, we can create a folder called `contact`. Then in that folder, we can create the page.js file for the route. So you should have this
`./app/contact/contact.js` which will create a route for `/contact`.

## Dynamic routes

If your rpute path has a dynamic segment, we can define that as well. So for our blog, the url would look like this `/blog/:title`. And our file structure will look similar: `./app/blog/[title]/page.js`. We can then access the route param inside our page component.

## Grouping

You can group pages together without affecting the URL structure. You might want this to:

- not spam the url with extra segments
- opt into and out of certain layouts
- create multiple root layouts (one for the marketing pages, one for the dashboard, etc)

You can do this with the `()` syntax in the file structure like so:

```
- app
  - (marketing)
    - layout.tsx
    - blog
      - [title]
        - page.tsx
  - (dashboard)
    - layout.tsx
    - home
      - page.tsx
```

Above, we created two groups, `marketing` and `dashboard`. Each group has their own root layout, so we don't need a single root layout here. Also, the URL structure is not affected. The path for the dashboard home is `/home` and not `/dashboard/home`. And the route for a blog post would be `/blog/learn-to-code` and not `/marketing/blog/learn-to-code`. The group folders are ignored by the router. This means you have to aware of potential route conclicts. If the marketing group had a `home` folder with a page, if would have a conflicting route with the dashboard home page.

## Routes for our app

- `/` - home
- `/blog` - blog home
- `/blog/:title` - blog post
- `/contact` - contact page
