---
layout: documentation
title: How to use scope filtering ?
---

# Configure scopes

## Propel

{% highlight yaml %}
builders:
  list:
    params:
      scopes:
        group_1: 
          All: ~
          Published: 
            default: true
            filters: 
              filterByIsPublished: true
          "Not Published": 
            filters: 
              filterByIsPublished: false
        group_2:
          "With actors":
             filters: [ withActors ]
          "Without actors":
             filters: [ withoutActors ]
{% endhighlight %}

### Create groups

Like you see on the previous sample, you have to group your scopes. In a group scopes are exculsives between each other. And you can combine scope between groups.

### Determine filters methods

You can chain filter method of your query object in the option `filters` of your scope.

You can also pass an argument to be passed to the filter (eg the publication boolean for the filter is published)

### Determine default scope to apply

You can choose the default scope to apply with the `default: true` on the scope.

>**Tip**<br />Like for filter form the user choice is memorized after in the user session.

## Doctrine

{% highlight yaml %}
builders:
  list:
    params:
      scopes:
        group_1: 
          All: ~
          Published: 
            default: true
            filters: 
              is_published: true
          "Not Published": 
            filters: 
              is_published: false
        group_2:
          "With actors":
             filters: [ withActors ]
          "Without actors":
             filters: [ withoutActors ]
{% endhighlight %}

### Create groups

Like you see on the previous sample, you have to group your scopes. In a group scopes are exculsives between each other. And you can combine scope between groups.

### Add a filter to the query

You can chain filter query parameters to add on the main query.

The key is your column name and the parameter the value to pass. The value have to complete an equal verification.

### Use you own method filtering

You'll probably wan't to make complex filters by writing your own.

To do this, pass an array of method and write in the `ListController.php` the corresponding method : scope

{% highlight php %}
<?php

protected function scopeYouFilter($queryFilter)
{
    $queryFilter->addBooleanFilter(...);
    $queryFilter->getQuery()->addWhere();
}
{% endhighlight %}

You will get the argument $queryFilter wich is the current instance of `Doctrine(ORM|ODM)QueryFilter`

### Determine default scope to apply

You can choose the default scope to apply with the `default: true` on the scope.

>**Tip**<br />Like for filter form the user choice is memorized after in the user session.

