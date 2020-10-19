---
layout: post
title: "Adding a reset button with AJAX to a form in Drupal 8"
date: 2020-04-28
---
Reset button in form can be added directly in `buildForm` method of Form class or using a `hook_form_alter`. 
```
$form['reset'] = [
      '#type' => 'button',
      '#value' => $this->t('Reset'),
      '#attributes' => [
        'onclick' => 'return false;',
      ],
      '#attached' => [
        'library' => ['module_name/library_name'],
      ],
    ];
```
here giving the `onclick` event to return `false`, the button will not load the page whenever clicked and by binding it to a JS function from the library attached, a function with `AJAX` submit can be invoked on it.

To define one or more (asset) libraries, add a `*.libraries.yml` file to the root of your module folder. following the convention `module_name.libraries.yml`. The file may look like
```
library_name:
  js:
    js/js_file_name.js: {}
  dependencies:
    - core/jquery
 ```
If we need `jQuery` to work for us, it should be included in the dependency, as the core by default does not include the `jQuery`.Since Drupal uses `jQuery.noConflict()` and only loads JavaScript files when required, to use `jQuery` and the `$` shortcode for `jQuery` we must include `jQuery` and `Drupal` as dependencies in the library definition in our `module_name.libraries.yml` and add a wrapper around your function.

```
(function ($, Drupal) {
  Drupal.behaviors.myModuleBehavior = {
    attach: function (context, settings) {
      $('#edit-reset', context).click(function () {
      // any other DOM elements to remove .
      this.form.reset();
        return true;
      });
    }
  };
})(jQuery, Drupal);
```


