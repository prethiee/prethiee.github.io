---
layout: post
title: "Managing String Translations in Drupal 8"
date: 2020-06-09
---
The translations for a string can be accessed using the [StringStorageInterface](https://api.drupal.org/api/drupal/core%21modules%21locale%21src%21StringStorageInterface.php/interface/StringStorageInterface/8.2.x) in Drupal 8.

##### Loading the service through ContainerInterface
```php

  /**
   * Constructs a new class object.
   *
   * @param \Drupal\locale\StringStorageInterface $locale_storage
   *   The locale storage.
   */
  public function __construct(StringStorageInterface $locale_storage) {
  $this->localeStorage = $locale_storage;  
  }
  
  /**
   * {@inheritdoc}
   */
  public static function create(ContainerInterface $container) {
    return new static(
      $container->get('locale.storage')
   }
  
 ```
##### Loading the service statically
```php
 $storage = \Drupal::service('locale.storage');
 ```
##### Getting the source string object
```php
use \Drupal\locale\SourceString;

function get_source_string_object($source_string) {
$storage = \Drupal::service('locale.storage');
    $string_obj = $storage->findString(
      [
        'source' => $source_string,
      ]);
    // If the the string object is empty, it is a new source string.  
    if (is_null($string_obj)) {
      $string_obj = new SourceString();
      $string_obj->setString($source_string);
      $string_obj->setStorage($storage);
      $string_obj->save();
    }
    return $string_obj;
  }
 ```
 ##### Getting previous translations
 ```php
 function get_previous_translation($string_obj, $lang_code) {
 $storage = \Drupal::service('locale.storage');
    return $storage->findTranslation([
      'lid' => $string_obj->lid,
      'language' => $lang_code,
    ])->translation ?? '';
  }
 ```
 ##### Saving the string translation 
 ```php
 function save_translation($string_obj, $translation, $lang_code) {
 $storage = \Drupal::service('locale.storage');
    $storage->createTranslation([
      'lid' => $string_obj->lid,
      'language' => $lang_code,
      'translation' => $translation,
    ])->save();
  }
 ```
 
  
