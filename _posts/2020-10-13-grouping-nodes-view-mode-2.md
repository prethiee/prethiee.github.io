---
layout: post
title: "Group nodes based on a taxonomy term while using display modes in views Part-2"
date: 2020-10-13
---
In the previous post, we saw how we can group nodes by taxonomy term, given the cardinality of that was one, we were able to achieve this from config alone. In this post, we will see, how we can achieve the same when the cardinality is multiple and had to cater to a multilingual site.

Here since the nodes are grouped and visible under a term name, let's add the term name relationship.
![term-relationship](/blog-13-oct/[blog-13-oct]1.png)


with the Vocabulary used on that field
![term-vocabulary](/blog-13-oct/[blog-13-oct]2.png)

Now, under the fields section add the field Name
![name-field](/blog-13-oct/[blog-13-oct]3.png)

with the relationship term
![name-term-relation](/blog-13-oct/[blog-13-oct]4.png)

Next, Under Format >> Settings, Add the grouping field on Name
![group-field](/blog-13-oct/[blog-13-oct]5.png)

and add the sort criteria on the field Name
![sort-field](/blog-13-oct/[blog-13-oct]6.png)

For a multilingual site, add the Translation criteria for Content type
![content](/blog-13-oct/[blog-13-oct]10.png)

and configure for the language selected on page. This filter will also avoid duplicate nodes being displayed.
![content-lang](/blog-13-oct/[blog-13-oct]11.png)

Add the Translation filtter for the Taxonomy type
![taxonomy](/blog-13-oct/[blog-13-oct]12.png)

and configure for the language selected on page
![taxonomy-lang](/blog-13-oct/[blog-13-oct]13.png)




