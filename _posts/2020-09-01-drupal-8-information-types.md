---
layout: post
title: "Information types in Drupal 8"
date: 2020-09-01
---
**Information Types:**</br>
In Drupal-8 information types are the different ways in which the information can be stored and retrieved with each having its own method.

**Types**
* Content
* Session
* State
* Configuration

**Content**</br>
Innformation of the type Content is stored and accessed using [entities](https://api.drupal.org/api/drupal/core%21lib%21Drupal%21Core%21Entity%21entity.api.php/group/entity_api/9.0.x). These types generally are the information from content types, image files, custom block, taxonomy terms, custo menus, and etc.

**Session**</br>
This type has the informatioin sbout individual's site interaction. It is optimized in order to minimize the impact of anonymous sessions on caching proxies. A session is only started if necessary and the session cookie is removed from the browser as soon as the session has no data. 

**State**</br>
This type has the information about the current state of the site. It is stored in the database and it's not meant to be exported. It is specific to an environment and all the data will be lost if the database is reset.

**Configuration**</br>
Information that is generally user edited relatively considered to be permanent, and not a content.The information(configuration) is considered to be active ,that is currently in use in the site.The storage used for the active configuration is configurable: it could be in the database, in files in a particular directory, or in other storage backends; the default storage is in the database.
