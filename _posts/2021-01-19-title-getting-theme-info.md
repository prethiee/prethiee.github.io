---
layout: post
title: "Getting theme info in Drupal 8"
date: 2021-01-19
---
In this post we will see few helper functions to get the theme setting in the site. </ br>

**Getting the active theme name**
```php
$active_theme_name = \Drupal::theme()->getActiveTheme()->getName();
```
</ br>

**Getting admin theme name**
```php
$admin_theme = \Drupal::config('system.theme')->get('admin');
$admin_theme_name = \Drupal::service('theme_handler')->getName($admin_theme);
```
</ br>

**Getting the admin theme name using Drush**
```yaml
drush cget system.theme admin
```

