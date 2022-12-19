## Static params

If you have a dynamic route segment where the params are static, like a blog post, we can use `generateStaticParams()`. So for a blog post at `/app/blog/[title]/page.tsx`:

```tsx
export default async function Page({ params }) {
  const { slug } = params;
  // use this slug to fetch post data
  const post = await getPost(slug);

  return <div>{post.title}</div>;
}

export async function generateStaticParams() {
  const posts = await getPosts();

  return posts.map((post) => ({
    slug: post.slug,
  }));
}
```
