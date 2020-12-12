---
layout: post
title: "Adding entity autocomplete form field in Drupal 8"
date: 2020-11-24
---
In post we will see how we can use the 'entity_autocomplete' Form API element in creating a autocmplete field for the entity types.

```php
$form['my_element'] = [
  '#type' => 'entity_autocomplete',
  '#target_type' => 'node',
  '#default_value' => $entity, // The #default_value can be either an entity object or an array of entity objects.
  '#selection_handler' => 'default', // Optional. The default selection handler is pre-populated to 'default'.
];
```
Here `#target_type` can be any entity including `user`,`taxonomy_term` etc.

Incase if we wanted to restrict the suggestions to specific content types we can use `target_bundles` selection setting

```php
$form['my_element'] = array(
  '#type' => 'entity_autocomplete',
  '#target_type' => 'node',
  '#selection_settings' => array(
    'target_bundles' => array('article', 'page'),
  ),
);
```
