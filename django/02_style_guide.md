# Django Style Guide

## Semantics

- When referring to a class corresponding to a model, always follow the
  reference with 'object(s)' to be clear as the class name is neither natural
  language nor does it, necessarily, refer to the actual corresponding noun.
  Similarly, do not use the natural language name to refer to a class e.g.:

  (Good) A form for `ProductVariant` objects.

  (Bad) A form for a `ProductVariant`.

  (Good) A form for a product variant.

  (Bad) A form for product variant objects.
