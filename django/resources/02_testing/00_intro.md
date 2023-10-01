# Testing

## Types of testing

There are numerous types, levels, and classifications of tests and testing
approaches. From the article
[Django Tutorial Part 10: Testing a Django web application](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Testing),
the most important ones are:

- **Unit tests:** Verify functional behavior of individual components, often to
  class and function level.
- **Regression tests:** Tests that reproduce historic bugs. Each test is
  initially run to verify that the bug has been fixed, and then re-run to ensure
  that it has not been reintroduced following later changes to the code.
- **Integration tests:** Verify how groupings of components work when used
  together. Integration tests are aware of the required interactions between
  components, but not necessarily of the internal operations of each component.
  They may cover simple groupings of components through to the whole website.
