---
layout: post
title: "Group nodes based on a taxonomy term in Drupal 8 even while using display modes in views."
date: 2020-09-29
---
In this tutorial, I will show you technique on how we can group the nodes based on the taxonomy term, even when we were using a content format instead of fields for individual rows. In other words, you can maintain your custom display mode as the output format for the rows but use the value of a field on your content type to group the rows around it and even display this value as a heading for the groups.

Click on settings under unformatted list

![view-settings](/blog-29-sep/view-setting-1.png)

and check **Force using fields** and save the settings

![force-using-fields](/blog-29-sep/view-setting-2.png)

Now, again click on settings under unformatted list. It shows the option to group by fields. Select the respective field by which the nodes should be 
grouped, aand apply the changes.

![group-field](/blog-29-sep/view-setting-3.png)

The result now shows the nodes grouped by a taxonomy term.

![group-result](/blog-29-sep/view-setting-4.png)

In the next installment of the post, we will see how to group the nodes by a taxonomy term field with multiple cardinality for a multilingual site.
