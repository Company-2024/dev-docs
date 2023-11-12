# Django REST Framework Style Guide and Best Practices

## Naming Conventions

### Serializers

When you use `WriteableNestedModelSerializer` from
[DRF Writeable Nested](https://github.com/beda-software/drf-writable-nested),
the serializer and the serializers nested into it should also contain 'Nested'
in their names to show that these are not ordinary `ModelSerializer`s e.g.
`OptionTypeDetailNestedAdminSerializer` and
`OptionValueDetailNestedAdminSerializer`. This is necessary because some fields
might need to be excluded which wouldn't ordinarily be excluded if the
serializers were not dependent on each other.

## Testing

See [documentation on Testing](testing-intro).

<!--
- Giving more than just number in related fields: https://github.com/encode/django-rest-framework/issues/5141, https://stackoverflow.com/questions/50973569/django-rest-framework-relatedfield-cant-return-a-dict-object
- Results in problems on browsable API.
- For ProductDetailAdminSerializer: Why did we not use WritableNested again? When you override create and update to allow adding m2m fields using set, you have to completely define the create and update and can’t use drf-writable-nested.
-->

<!-- ## Validation

https://stackoverflow.com/questions/28885018/passing-class-name-as-argument-to-function#:~:text=yes%20of%20coarse%20you%20can,functions%20or%20even%20modules%20...&text=def%20foo()%3A%20pass%20here,'main. -->
