---
layout: post
title: "Block helper functions to get config info in Drupal 8"
date: 2021-01-05
---
In this post we will see few helper functions to help us get the values of a block.

<br/>
**Getting the UUID of the config block**<br/>

The function `uuid()` can be used to get the uuid of the block. To get the uuid of the associated content block function `getDependencies()` can be used. The function gives the array of values having the info about the content block.

```php
$block->getDependencies()['content'][0]
```
The above string returns a string having `block-type:block-name:block-uuid`, which can be extracted by<br/>

```php
$block_uuid = explode(':', $block->getDependencies()['content'][0])[2];
```
<br/>
**Getting external module settings on a block**

```php
$block->setThirdPartySetting('module_name', 'module_setting_name', 'setting_value');
```

