---
layout: post
title: "Plugin derivatives in Drupal 8"
date: 2020-08-04
---

##### Plugins

Drupal 8 follows the Plugin design pattern, and gives the advantage of extending a module or a service, using one of the four discovery methods

1. StaticDiscovery - These are used for test code.
2. HookDiscovery - D7 carry over hook system, still used in many places.
3. AnnotatedClassDiscovery - used in blocks, views, rules, Queue API, and more.
4. YamlDiscovery - used in menus, routes, and services

##### Plugin Derivatives

Derivatives provide a simple way to expand a single plugin so that it can represent itself as multiple plugins in the user interface.
Examples: To contruct the routes dynamically for a menu link, or for generating multiple block instance of a specific node type.

Some articles to check on this Example:
* [Drupal 8 Custom Plugins are addictive](https://spinningcode.org/2017/01/drupal-8-plugins-are-addictive/)
* [Tutorial on Using Drupal 8 Plugin Derivatives Effectively](https://www.sitepoint.com/tutorial-on-using-drupal-8-plugin-derivatives-effectively/)
* [Dynamic menu links in Drupal 8 with plugin derivatives](https://www.webomelette.com/dynamic-menu-links-drupal-8-plugin-derivatives)
