flask-form-macros
=================

## What?

Flask macros are Jinja2 macros that are called like functions.  These macros create form field boilerplate, and were intended to replace my use of WTForms in my projects.

## Use

First add this template filter into your application:
```
@app.template_filter()
def slugify(string):
    return string.lower().replace(' ', '_')
```

Place `form_field_macros.html` in your Flask templates folder, and import:

```
{% import "form_field_macros.html" as fields %}
``` 

Then call:

```
{{ fields.TextField('My Field') }}
```

This will render a field that looks like this:

```
<div>
    <label>My Field: </label>
    <input type="text"
           id="my_field"
           name="my_field"
           class=""
           size="20"
           
    >
</div>
````

**Horizontal forms** are for Bootstrap-compatible horizontal forms.  You'll of course need to have a properly sourced Bootstrap project for this to work. These macros are only meant to support Bootstrap 2.3.2.

```
{{ fields.TextField('My Field', horizontal=True) }}
```

```
 <div class="control-group">
    <label class="control-label">My Field: </label>
    <div class="controls">
            <input type="text"
                   id="my_field"
                   name="my_field"
                   class=""
                   size="20"
            >
    </div>
</div>
```

## Okay, now what?

Essentially, you pass in either a) the macro arguments as specified in the macro signature, or b) you pass in HTML attributes as booleans or key/value pairs. So, if you want to have an HTML5 "email" field, with a value set, that is required:

```
{{ fields.Field('Email Field', type="email", value="Put a value here", required=True) }}
```

## License

Apache 2.0
