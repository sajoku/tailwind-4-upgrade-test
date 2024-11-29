**Update:**

This is fixed in Tialwind v4 Beta 3


Before
``` css
@config 'tailwind.config.js';

@tailwind base;
@tailwind components;
@tailwind utilities;
@tailwind screens;



h1 {
  @apply tw-bg-black tw-bg-red-50;
}

div {
  @apply tw-group;
}

span {
  @apply tw-text-base tw-font-semibold tw-text-gray-900 tw-text-left tw-group;
}
```


After

``` css


@import 'tailwindcss' prefix(tw);

@variant dark (&:is(.dark *));

/*
  The default border color has changed to `currentColor` in Tailwind CSS v4,
  so we've added these compatibility styles to make sure everything still
  looks the same as it did with Tailwind CSS v3.

  If we ever want to remove these styles, we need to add an explicit border
  color utility to any element that depends on these defaults.
*/
@layer base {
  *,
  ::after,
  ::before,
  ::backdrop,
  ::file-selector-button {
    border-color: var(--color-gray-200, currentColor);
  }
}

h1 {
  @apply tw:bg-black tw:bg-red-50;
}

div {
  @apply tw-group;
}

span {
  @apply tw:text-base tw:font-semibold tw:text-gray-900 tw:text-left tw-group;
}
```
