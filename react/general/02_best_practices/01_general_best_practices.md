# React Best Practices

According to the
[React documentation](<https://legacy.reactjs.org/docs/lists-and-keys.html#:~:text=A%20good%20rule%20of%20thumb,map()%20call%20need%20keys.>)
good rule of thumb is that elements inside the map() call need keys.

### Types vs. Interfaces

### Pass properties rather than an object

According to the principle of least privilege, this is a correct way:

```tsx
<InnerComponent name={object.name} image={object.image} />
```

This restricts InnerComponent from accidentally modifying original object or
accessing properties that aren't intended for it.

Alternatively, properties could be picked from original object and passed as
props:

```tsx
<InnerComponent {...pick(object, "name", "image")} />
```

If there are numerous properties that are tedious to list, there may be single
prop that accepts an object:

```tsx
<InnerComponent object={pick(object, "name", "image")} />
```

P.S.

```tsx
import { pick } from "loadash";

// or
const pick = (o, ...keys) =>
  Object.fromEntries(Object.entries(o).filter(([k]) => keys.includes(k)));
```

See
[this SO thread](https://stackoverflow.com/questions/52621169/react-props-should-i-pass-the-object-or-its-properties-does-it-make-much-diffe)
