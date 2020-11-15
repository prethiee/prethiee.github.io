---
layout: post
title: "Lock service in Drupal 8"
date: 2020-09-15
---

The [lock](https://api.drupal.org/api/drupal/core%21core.services.yml/service/lock/9.2.x) service in drupal 8 can be used in instances to acquire lock on a particular function which will allow only one process to execute a piece of code at a time and then allow other process and so fort,.so that the code does not run in parallel.

* A function can acquire a lock using `$lock->acquire()`, and it should always release its lock by using `$lock->release()`.
* If a function fails to acquire a lock it may either immediately return, or it can call `lock_wait()`. 
* After `lock_wait()` returns, the function may again attempt to acquire the lock, or may simply allow the page request to proceed on the assumption that a parallel request completed the operation.

The Extending class [DatabaseLockBackend](https://api.drupal.org/api/drupal/core%21lib%21Drupal%21Core%21Lock%21DatabaseLockBackend.php/class/DatabaseLockBackend/9.2.x) for reference.
