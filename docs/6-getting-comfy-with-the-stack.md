# Getting Comfy with the Stack

## TypeScript

To get more familiar with TypeScript read this [series of articles](https://www.totaltypescript.com/books/total-typescript-essentials) by Matt Pocock. After reading at least first eight, working with TS will become a piece of cake for you.

## React

I highly recommend to read at least [Quick Start](https://react.dev/learn) and [React with Typescript](https://react.dev/learn/typescript) articles from React official docs to feel yourself more comfortable during the development process.

## Expo

[Expo Tutorial](https://docs.expo.dev/tutorial/overview/) is written pretty good and beginner-friendly, I guess it would be nice from your side to read it too.

After reading, you will feel yourself more comfortable with this technology, so working on the project would be less painful as could have been.

## Styling with Tailwind

For styling we in GatherFlow use mainly [Tailwind](https://v3.tailwindcss.com/) with some utilities like [cva](https://cva.style), etc. If you are not familiar with `tailwind` or `cva`, check [tailwind's](https://v3.tailwindcss.com/) or [cva's](https://cva.style/docs) docs.

### Setting up

If you're using VS Code, for more comfortable usage of tailwind, install [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss). You can also enable autocompletion inside cva just by adding this code to your `settings.json`:

```json
{
  "tailwindCSS.experimental.classRegex": [
    ["cva\\(([^)]*)\\)", "[\"'`]([^\"'`]*).*?[\"'`]"],
    ["cx\\(([^)]*)\\)", "(?:'|\"|`)([^']*)(?:'|\"|`)"]
  ]
}
```

### Styling conventions

We follow tailwind's practices of reusing styles, to find out more about them, you can read [this article in tailwind's docs](https://tailwindcss.com/docs/styling-with-utility-classes#managing-duplication). If you're too busy to read such a large article, here are main of them:

- Use design tokens to prevent some maintaining issues and ensure uniformity across UI elements;
- Use fewer utility classes when possible;
- Keep class ordering (you can actually don't care about this recommendation since we have awesome prettier plugin that automatically sorts classes in the correct order);
- Prevent inconsistencies when overriding and extending styles;
- Avoid using `@apply` directive.

### Writing styles guide

Let's on example of button component find out how do we write styles.

```ts
// ./components/ui/button.tsx

import { cva, type VariantProps } from 'class-variance-authority'

const buttonVariants = cva(
  '...',
  {
    variants: {
      variant: {
        primary: '...',
        outlined: '...',
        ghost: '...',
        danger: '...'
      }
    },
    defaultVariants: {
      variant: 'primary'
    }
  }
)
```

`cva` function accepts such params:

- `base`: your component's base styles;
- `options`: object with such fields:
- - `variant`: your variants schema;
- - `defaultVariants`: default values for previously defined variants.

As next step, let's write interface for button's props:

```ts
type ButtonProps = React.ComponentPropsWithoutRef<typeof Pressable> &
  VariantProps<typeof buttonVariants>;
```

Since `cva` is a type-safe library, we can easily infer component's variants from the schema we have defined before.

Now let's apply styles to our button component:

```tsx
const Button = React.forwardRef<React.ElementRef<typeof Pressable>, ButtonProps>(
  ({ className, variant, size, ...props }, ref) => {
    return (
        <Pressable
          className={cn(
            props.disabled && 'opacity-50',
            buttonVariants({ variant, size, className })
          )}
          ref={ref}
          role='button'
          {...props}
        />
    );
  }
);
```
