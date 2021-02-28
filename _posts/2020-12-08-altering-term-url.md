---
layout: post
title: "Alter default Taxonomy Term URL in Drupal 8"
date: 2020-12-08
---
In this post we will see how we can alter the default taxonomy term url. Here we will preprocess the taxonomy term field in the theme file using the `hook_preprocess_field` function and pass our custom `URL` object.

```php
use Drupal\Core\Url;
/**
 * Implements hook_preprocess_field().
 */
function ohchr_preprocess_field(&$variables) {
$element = $variables['element'];
 if ($element['#field_name'] == 'field_taxonomy_term') {
      foreach ($variables['items'] as $index => $item) {
        $variables['items'][$index]['content']['#url'] = Url::fromUri('internal:/<path>');
;
      }
    }
}
```
