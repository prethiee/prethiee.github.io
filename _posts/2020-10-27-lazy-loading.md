---
layout: post
title: "Lazy loading of blocks in Drupal 8"
date: 2020-10-27
---
The response for any page request is sent when all the placeholders are being replaced.This is done in Drupal 8 using the Singe flush strategy. On top of that the `BigPipe` module which has been included in Drupal 8 core, that allows us to flush the initial page first, and then stream the replacements for the placeholders.

In instances when the page has a lot of dynamic content it can drastically reduce the performance and the site becomes slow. To improve the performance Drupal 8 uses rendering and caching system which provides us a way to cache static part of the page and the dynamic one to be uncached. This is done by the render array using the `#lazy_builder` key and `#create_placeholder => TRUE` key.

Example callback on a custom block
```php
public function build() {
return [
  '#theme' => 'custom_theme',
  '#variables' => [
    '#lazy_builder' => [static::class . '::lazyBuilder', []],
    '#create_placeholder' => TRUE,
  ],
];
}

public static function lazyBuilder() {
    sleep(3); 
    return[
      '#markup' => $var->getTitle()
    ];
 }
 ```
 Another way to render the `title`
```php
'title' => ['#plain_text' => $var->getTitle()]
```
Give this [article](https://drupalize.me/tutorial/use-lazy-builders-and-placeholders?p=2766) a read for a more detailed explanation, and different callback formats.
