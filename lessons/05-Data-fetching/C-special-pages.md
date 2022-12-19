## Special Pages

When fetching data with server components, we can use special pages provided by Next.js to handling loading and error states

<br>

Adding a `loading.tsx` in the same directory as a server component page in the app directory that is fetching data will render that loading component while the data is being fetched. It is equivalent to using a Suspense boundry, which you can still do if you prefer or your server component isn't a page in the app directory.

```tsx
export default function Loading() {
  return <div>...loading</div>;
}
```

<br>

Then same is true for `error.tsx`. If your server component errors our whiile rendering, the error page component will show instead. This is the same as wrapping a component in an Error Boundry.

```tsx
export default function Error() {
  return <div>...error</div>;
}
```
