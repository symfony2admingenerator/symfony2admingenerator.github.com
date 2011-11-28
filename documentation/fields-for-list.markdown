---
layout: documentation
title: Fields configuration for list
---

# Fields configuration for list

## Overview
This page shows how flexible the Admin generator is in configuring your list page, that allows tight integration between your model and the list.
Main features in configuring the list include: 

*     Options can be set either at the general params level or at the list level.
*     Flexible sorting, including related tables - one to many left joints 
*     Field formatting of form labels 
*     Form options: formating (e.g. format: "Y-m-d"), 
*     PHP snippets directly in the form, for example to define a date range. 
*     Virtual Fields using getters that tie your model directly into the list; thereby allowing even complex relationships to be included

## Label

The default label is the column name, but you can specify it directly:

{% highlight yaml %}
params:
  fields:
    params:
      producer:
        label: Producer name
{% endhighlight %}

## Sort

The sorting of a list is very flexible: 

*    sort on any of the columns in the table, or 
*    a column in a related table. For a **left join** Use table.field name. For example 'producer'.'name' (see example below), or 
*    sort on a "virtual column". This is a calculated value in your model and accessed by a getter function. It need not be a table column.
You can set option sort_on or sortOn (option are camelized at reading time) 

{% highlight yaml %}
params:
  fields:
    params:
      producer:
        sort_on: producer.name
{% endhighlight %}

If your column contains "." the system understand to add a leftJoin on `producer` and to sort on the joined object on column named `name`

## Getter

The default getter is get*Field*, you can edit it with the `getter` option

{% highlight yaml %}
params:
  fields:
    params:
      producer:
        getter: MyOwn
{% endhighlight %}

Will make call `$movie->getMyOwn()` to render your `producer` column

And of course you can chain getter to make `$movie->getMyOwn()->getLabel()`

{% highlight yaml %}
params:
  fields:
    params:
      producer:
        getter: MyOwn.Label
{% endhighlight %}