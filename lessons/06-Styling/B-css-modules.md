For scoped CSS, we can use CSS modules. Next.js has support for this built in. We just need to use the `.module.css` extension.

```css
.button {
  padding: 8px 4px;
}
```

Then import that module and apply the styles to whatever element you want. The generated classNames are unique.

```tsx
import styles from "./button.module.css";

const Button = () => {
  return <button className={styles.button}>click me</button>;
};

export default Button;
```
