---
layout: post
title: "Creating a Dynamic Block programatically in Drupal 8"
date: 2021-02-02
---
In this post we will see how we can create a Dynamic block plugin.
```php
<?php

namespace Drupal\test_module\Plugin\Block;

use Drupal\Core\Block\BlockBase;

/**
 * Provides an example block.
 *
 * @Block(
 *   id = "test_module_example",
 *   admin_label = @Translation("Example"),
 *   category = @Translation("test-module")
 * )
 */
class ExampleBlock extends BlockBase {

  /**
   * {@inheritdoc}
   */
  public function build() {
    $build['cache']['disabled'] = TRUE;
    $build['content'] = [
      '#markup' => $this->t('Example Block'),
    ];
    return $build;

  }

}
```
Here setting the value of ` $build['cache']['disabled'] = TRUE;` would disable the caching for this block and displays the content dynamically.
