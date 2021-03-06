---
layout: post
title: "Adding entity autocomplete form field in Drupal 8"
date: 2020-11-24
---
In this post we will see how we can use the 'entity_autocomplete' Form API element in creating a autocomplete field for the entity types.

```php
$form['my_element'] = [
  '#type' => 'entity_autocomplete',
  '#target_type' => 'node',
  '#default_value' => $entity, // The #default_value can be either an entity object or an array of entity objects.
  '#selection_handler' => 'default', // Optional. The default selection handler is pre-populated to 'default'.
];
```
Here `#target_type` can be any entity including `user`,`taxonomy_term` etc.

Incase if we want to restrict the suggestions to specific content type we can use `target_bundles` selection setting

```php
$form['my_element'] = [
  '#type' => 'entity_autocomplete',
  '#target_type' => 'node',
  '#selection_settings' => [
    'target_bundles' => ['article', 'page'],
  ],
];
```
