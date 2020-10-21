---
layout: post
title: "Drupal 8 Node Entity CRUD operations Cheat Sheet"
date: 2020-07-07
---
##### Node creation using static call
```php
$node = Node::create(['type' => 'page']);
$node->set('title', 'My Title');
$node->save();
```
##### Node creation using Entity Manager
```php
$info = ['type' => 'page', 'title' => 'My title'];
$node = \Drupal::entityTypeManager()->getStorage('node')->create($info);
$node->save();
```
##### Loading a Node procedurally
```php
$node = entity_load('node',1);
$nodes = entity_load_multiple('node', [1,2,3]);
```
##### Loading node with static calls
```php
$nid = 1;
$node = Node::loadMultiple($nids);
```
##### Loading node using Entity Manager
```php
$storage = \Drupal::entityManager()->getStorage('node');
$node = $storage->load(1);
$nodes = $storage->loadMultiple([1,2,3]);
```
##### Saving a node procedurally
```php
$node = entity_load_single('node',1);
$node->save();
```
##### Saving a node static calls
```php
$nid = 1;
$node = Node::load($nid);
$node->set('title', 'My title');
$node->set('field_my_field', 'My field');
$node->save();
```
##### Saving a node using Entity Manager
```php
$storage = \Drupal::entityManager()->getStorage('node');
$node = $storage->load(123);
$node->set('field_my_field', 'value');
$node->save();
```
##### Deleting a node procedurally
```php
entity_delete_multiple('node',[1]);
```
##### Deleting a node statically
```php
$nid = 1;
$node = Node::load($nid);
$node->delete();
```
##### Deleting a node using Entity Manager
```php
$storage = \Drupal::entityManager()->getStorage('node');
$node = $storage->load(123);
$node->delete();
```

