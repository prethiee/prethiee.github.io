---
layout: post
title: "Hiding a field and filter based on roles in Drupal 8"
date: 2020-08-18
---
To hide a field or a filter based on roles, we will use `hook_views_pre_view` for this. The hook has to be placed inside the module folder following the convention `module_name_.views_execution.inc`.

**Hiding a field in a view**
```php
function module_name_views_pre_view($view, $display_id) {
  if ($view->id() == 'view_name') {
    $user_roles = \Drupal::currentUser()->getRoles();
    if (!in_array('administrator', $user_roles)) {
    // Hide the field name
      $view->removeHandler($display_id, 'field', 'field_name');      
    }
  }
}
```
**Hiding a filter in a view**
```php
      $view->removeHandler($display_id, 'filter', 'filter_name');  
```
