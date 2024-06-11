# Getting Started with E-commerce-23 Next.js Projects

<!-- https://docs.google.com/document/d/1Gwgd1dx6L2El4DegaG07vkc4_XNUX7mWDdxbQHKKhqk/edit -->

## ESLint

[ESLint](https://eslint.org/) is a tool for identifying and reporting on
patterns found in ECMAScript/JavaScript code. It statically analyses your code
to quickly find problems and help you fix them. Refer to the
[official ESLint documentation](https://eslint.org/) for details on its usage.

See [ESLint Github page](https://github.com/eslint/eslint) for installation
details. Note: We will only use ESLint for syntax highlighting and finding
problems in code. We will use [Prettier](https://prettier.io/) for code
formatting because according to
[this Reddit thread](https://www.reddit.com/r/node/comments/w95n80/why_use_prettier_if_eslint_can_format/),
Prettier does a better job.

Installation of ESLint pretty much comes down to running the command:

```bash
npm init @eslint/config
```

ESLint supports adding shared settings into configuration files. Plugins use
settings to specify the information that should be shared across all of its
rules.

We will extend the following configurations:

1. eslint-config-airbnb (See
   [npm page](https://www.npmjs.com/package/eslint-config-airbnb) for
   installation instructions.)
2. eslint-config-airbnb-typescript (See
   [Github page](https://github.com/iamturns/eslint-config-airbnb-typescript)
   for installation instructions.)

```
extends: [
  'airbnb',
  'airbnb-typescript'
]
```
