---
layout: post
title: "Examples of InvokeCommand from AJAX API in Drupal 8"
date: 2020-05-26
---
With the list of functions the [AJAX API](https://api.drupal.org/api/drupal/core%21core.api.php/group/ajax/8.2.x) had to offer in Drupal 8, we will see the different ways in which the InvokeCommand can be used for a ajax response object.

##### InvokeCommand
It is a AJAX command for invoking an arbitrary jQuery method. 

##### AJAX response object
```php
$response = new AjaxResponse();
```
##### The class import use statement
```php
use Drupal\Core\Ajax\InvokeCommand;
```
##### Resetting a drop-down
```php
$response->addCommand(new InvokeCommand('#drop-down', 'prop', ['selectedIndex', '0']));
```
##### Resetting a text box value
```php
$response->addCommand(new InvokeCommand('#test-box', 'val', [""]));
```
##### Triggering a button click event
```php
$response->addCommand(new InvokeCommand('button', 'trigger', ['mousedown']));
```

Check out this response from [StackOverFlow](https://drupal.stackexchange.com/questions/211690/how-to-have-custom-ajax-commands-on-element-using-invokecommand) for some more examples.
