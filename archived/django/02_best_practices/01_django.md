# Django Style Guide and Best Practices

## Testing

See [documentation on Testing](testing-intro).

<!-- ## Semantics -->

<!--
- Not necessarily. Just ensure that you are referring to a class/model/object when you use the code name and are not using it as a noun otherwise it doesn't make sense and you will run into inconsistencies when things don't really fit.
- When referring to a class corresponding to a model, always follow the
  reference with 'object(s)' or model to be clear as the class name is neither natural
  language nor does it, necessarily, refer to the actual corresponding noun.
  Similarly, do not use the natural language name to refer to a class e.g.:

  (Good) A form for `ProductVariant` objects.

  (Bad) A form for a `ProductVariant`.

  (Good) A form for a product variant.

  (Bad) A form for product variant objects. -->

<!-- ## Data Fixtures -->

<!-- Directory structure -->

<!-- ## Workflow -->

<!--
- When modifying models with fields that can't be None, first do with a default value then remove the default it.
-->

<!-- ## Models -->

<!--
- You don't need and should not alter default pk field if you don't want to use it as part of the url. Leave pk as it is, don't change it. Make a new uuid field or slug field or whatever unique identifier you prefer, and use it as part of the url.
- Each model must have a get_pk_related_field_data method which is used to create a representation of an object in a serializer relationship.
- Use get_object_or_404
-->

<!-- ## Validation -->

<!--
- In docstrings act as though everything has been created otherwise you will crack your head trying to figure out how to say this thing has not been created yet.
-->

<!--
- https://legacy.reactjs.org/blog/2016/07/13/mixins-considered-harmful.html
- Definitely want to separate the validation logic for seperation of concerns. OOP. I.e. code reuse and complexity encapsulation. Mixins are ideal for situations where you have a collection of interdependent non-side-effect-free code that you'd like to share between components. The primary disadvantage of a mixin, is that it can make your code harder to read. Imagine you come back to work on the AppTextArea component six months later, and it isn't obvious how and why certain things work or where they are defined... then you remember it uses a mixin, and then you have to dive into the mixin code... In other words it makes for implicit, rather than explicit implementations. Shared Functions. Shared functions are ideal for situations where you can reuse units of side-effect-free code in your application. In my case, I have a date library with a formatBySlash function which takes a Date object and returns something like "5/12/2018". I've added it as a global filter, so I can do things like {{ post.createdAt | formatBySlash }} in my templates. Additionally I can import the function and use it directly in a method or computed property. Use mixins for complex functions, like https://vuex.feathersjs.com/mixins.html#injected-properties. Everything else just use utils. Mixins are a honey trap. You may win some lines of code using them but you will end up loosing time in comprehension/readability as it's more difficult to keep track of what's happening after a few months. Utils all the way. That's also what Vue 3 suggests so you will be prepared getting rid of mixins. Mixins vs Static member is like Black vs White. They do the opposite. Members of a mixin are linked to one specific instance of an object. But static members are common to all objects. If it made sense to implement something like a static function, then it likely means that a mixin is not what you want. It'll just make the object bloated and slower to instantiate.

Shared functions are flexible, easy to test, and make your code more explicit.
- Definitely need some way to group them i.e. a class otherwise you'd need a file for Products one for ProductVariants etc.
-->

<!-- In Django, you can organize validation methods for form cleaning in several
ways, depending on your project's structure and complexity. The best approach
often depends on the specific needs of your application. Here are some common
ways to organize validation methods for form cleaning in Django:

Inline Validation: The simplest way to organize validation methods is by
defining clean methods directly in your form classes. For example:

python Copy code from django import forms

class MyForm(forms.Form): field1 = forms.CharField() field2 = forms.EmailField()

    def clean_field1(self):
        data = self.cleaned_data['field1']
        # Validate data here
        return data

    def clean_field2(self):
        data = self.cleaned_data['field2']
        # Validate data here
        return data

This approach keeps the validation logic closely tied to the form itself, making
it easy to maintain.

Custom Form Validators: You can create custom validation functions outside of
the form class and use them in the form's clean method. This approach promotes
code reusability and separation of concerns.

python Copy code from django import forms

def validate_field1(value): # Validate value here

def validate_field2(value): # Validate value here

class MyForm(forms.Form): field1 = forms.CharField(validators=[validate_field1])
field2 = forms.EmailField(validators=[validate_field2])

    def clean(self):
        cleaned_data = super().clean()
        # Additional form-level validation can be performed here
        return cleaned_data

Custom Validation Classes: If your form has complex validation requirements, you
can create custom validation classes and use them in your form.

python Copy code from django import forms from myapp.validators import
MyValidator

class MyForm(forms.Form): field1 = forms.CharField() field2 = forms.EmailField()

    def clean(self):
        cleaned_data = super().clean()
        my_validator = MyValidator()
        my_validator.validate(cleaned_data)
        # Additional form-level validation can be performed here
        return cleaned_data

In this approach, the MyValidator class encapsulates complex validation logic,
promoting code modularity and testability.

Form Mixins: You can use form mixins to encapsulate reusable validation logic
and mix them into your forms. This approach is useful when you have multiple
forms with similar validation requirements.

python Copy code from django import forms

class MyValidationMixin: def clean_field1(self): data =
self.cleaned_data['field1'] # Validate data here return data

class MyForm(forms.Form, MyValidationMixin): field1 = forms.CharField() field2 =
forms.EmailField() Form mixins are a way to keep validation logic separate and
reusable while maintaining a clean and organized codebase.

Choose the organization method that best fits your project's needs and promotes
code readability, reusability, and maintainability. The choice often depends on
the specific validation requirements and the overall architecture of your Django
application. -->
