# HTML Coding Standards

## Formatting

All HTML documents must use two spaces for indentation and there should be no trailing whitespace. HTML5 syntax must be used and all attributes must use double quotes around attributes.

    <video autoplay="autoplay" poster="poster_image.jpg">
      <source src="foo.ogg" type="video/ogg">
    </video>

HTML5 elements should be used where appropriate reserving `<div>` and `<span>` elements for situations where there is no semantic value (such as wrapping elements to provide styling hooks).

## Doctype and layout

All documents must be using the HTML5 doctype and the `<html>` element should have a "lang" attribute. The `<head>` should also at a minimum include "viewport" and "charset" meta tags.

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Example Site</title>
      </head>
      <body></body>
    </html>

## Forms

Form fields must always include a `<label>` element with a "for" attribute matching the "id" on the input. This helps accessibility by focusing the input when the label is clicked, it also helps screen readers match labels to their respective inputs.

    <label for="field-email">email</label>
    <input type="email" id="field-email" name="email" value="" />

Each `<input>` should have an "id" that is unique to the page. It does not have to match the "name" attribute.

Forms should take advantage of the new HTML5 input types where they make sense to do so, placeholder attributes should also be included where relevant. Including these can provided enhancements in browsers that support them such as tailored inputs and keyboards.

    <div>
      <label for="field-email">Email</label>
      <input type="email" id="field-email" name="email" value="name@example.com">
    </div>
    <div>
      <label for="field-phone">Phone</label>
      <input type="phone" id="field-phone" name="phone_number" value="" placeholder="+44 077 12345 678">
    </div>
    <div>
      <label for="field-url">Homepage</label>
      <input type="url" id="field-url" name="url" value="" placeholder="http://example.com">
    </div>

**Each form component must be named matching the fillable attributes required by the server side**

Example HTML Code from Client Side:

    <div>
      <label for="field-first-name">First Name</label>
      <input id="field-first-name" name="first_name" value="Jane">
    </div>
    <div>
      <label for="field-last-name">Last Name</label>
      <input id="field-last-name" name="last_name" value="Doe">
    </div>

Example Laravel Code from Server Side:

    class User extends Authenticatable implements JWTSubject
    {
         use Notifiable;
         protected $table = 'users';

        /**
         * The attributes that are mass assignable.
         *
         * @var array
         */
        protected $fillable = [
            'last_name',
            'first_name',
            'email',
            'phone_number',
        ];
    }

## Including meta data

Classes should ideally only be used as styling hooks. If you need to include additional data in the HTML document, for example to pass data to JavaScript, then the HTML5 `data-` attributes should be used.

For example:

    <a class="btn" data-format="csv">Download CSV</a>

## Targeting Internet Explorer

Targeting lower versions of Internet Explorer (IE), those below version 9, should be handled by the stylesheets. Small fixes should be provided inline using the `.ie` specific class names. Larger fixes may require a separate stylesheet but try to avoid this if at all possible.

    <!DOCTYPE html>
    <!--[if lt IE 7]> <html lang="en" class="ie ie6"> <![endif]-->
    <!--[if IE 7]>    <html lang="en" class="ie ie7"> <![endif]-->
    <!--[if IE 8]>    <html lang="en" class="ie ie8"> <![endif]-->
    <!--[if gt IE 8]><!--> <html lang="en"> <!--<![endif]-->

These can then be used within the CSS:

    .clear:before,
    .clear:after {
    content: "";
    display: table;
    }

    .clear:after {
    clear: both;
    }

    .ie7 .clear {
    zoom: 1; /_ For IE 6/7 (trigger hasLayout) _/
    }

## i18n

Don’t include line breaks within `<p>` blocks.

Do this:

    <p>Blah foo blah</p>
    <p>New paragraph, blah</p>

And not:

     <p>Blah foo blah
     New paragraph, blah</p>
