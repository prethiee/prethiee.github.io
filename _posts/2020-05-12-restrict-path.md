---
layout: post
title: "Restricting the translations path using hook_node_access in Drupal 8"
date: 2020-05-12
---
The [hook_node_acess](https://api.drupal.org/api/drupal/core%21modules%21node%21node.api.php/function/hook_node_access/8.2.x) function can be used to control access to perform a given operation on a node for a specific user.

The administrative account (user ID #1) always passes any access check, so this hook is not called in that case. Users with the "bypass node access" permission may always view and edit content through the administrative interface.

```php

use Drupal\node\NodeInterface;
use Drupal\Core\Session\AccountInterface;
use Drupal\Core\Access\AccessResult;
use Drupal\user\Entity\User;

/**
 * Implements hook_node_access().
 */
function mymodule_access_node_access(NodeInterface $node, $op, AccountInterface $account) {
  $user = User::load(\Drupal::currentUser()->id());
  // Checking if the logged in user has permission to translate the content type, and whether they are the author of the node. 
  if ($account->hasPermission('translate ' . $node->getType() . ' node') && ($node->getOwner()->id() != \Drupal::currentUser()->id()) {
  // checking if the current path has "translations" string.
    return AccessResult::forbiddenIf(strpos(\Drupal::service('path.current')->getPath(), '/translations')); 
  }
  return AccessResult::neutral();
}
```
Here we are restricting the translations page of the node if the author of the node is not the currently logged in user.
