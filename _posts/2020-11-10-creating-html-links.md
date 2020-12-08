---
layout: post
title: "Creating HTML links in Drupal 8"
date: 2020-11-10
---
In the below example we can see how we can add HTML tag to a link created with a url from route
```php
<?php
    use Drupal\Core\Url;
    use Drupal\Core\Render\Markup;
    
    
    $link_text = '<span>Link Text containig tags<span>';
    $url = Url::fromRoute('my_module.my_route');
    $form['link_field'] = [
      '#type' => 'link',
      '#title' => Markup::create(
        $link_text
      ), '#url' => $url,
    ];
 ```
 When using an external url
```php
$url = Url::fromUri('http://www.example.com');   
```
When it has to be returned as a renderable array
```php
$link_markup = Markup::create($link_text);
$link = Link::fromTextAndUrl($link_markup, $url);
$link = $link->toRenderable();
```

  
    
