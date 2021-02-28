---
layout: post
title: "Updating the visibilty of the config block programatically in Drupal 8"
date: 2020-12-22
---
In this post we will see how we can alter the visibility of the config blocks programatically.

```php
/**
 * Function to update block visibility.
 */
function update_blocks_visibility() {
  $blocks = Block::loadMultiple();
  foreach ($blocks as $block) {
      $block->disable()->save();
      Cache::invalidateTags($block->getCacheTagsToInvalidate());
    }
  }
}
```
The class `Drupal\block\Entity\Block` is used to load all the config blocks, and class `Drupal\block_content\Entity\BlockContent` is used to load all the content blocks.
