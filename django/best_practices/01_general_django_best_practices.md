# Django Best Practices

## Models

<!--
- You don't need and should not alter default pk field if you don't want to use it as part of the url. Leave pk as it is, don't change it. Make a new uuid field or slug field or whatever unique identifier you prefer, and use it as part of the url.
- Each model must have a get_pk_related_field_data method which is used to create a representation of an object in a serializer relationship.
-->
