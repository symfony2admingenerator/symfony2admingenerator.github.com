---
layout: documentation
title: How to configure the list controller ?
---

# How to configure the list controller ?

## Title

This parameter allow you to configure the title displayed on the page. 

{% highlight yaml %}
builders:
  list:
    params:
      title: List of all movies
{% endhighlight %}

>**Tip**<br />This field will be parsed by twig so you could use all the power of filters...

## Display

You can choose the columns to show in your list in your yaml

{% highlight yaml %}
builders:
  list:
    params:
      display: [ id, title, is_published, producer, release_date ]
{% endhighlight %}

The display parameter accept the name of the columns from your model.

You can also add columns from one to many relations, for example the producer of the movie.
In this case, we try to call `__toString` method else if you [parameter the field getter](/documentation/fields-for-list.html#getter)

## Paginate

You can define the number of elements you want to display per page, the default value is 10.

{% highlight yaml %}
builders:
  list:
    params:
      max_per_page: 5
{% endhighlight %}

## Overwrite the rendering of a field

Edit the file : YourBundle/Resources/views/List/index.html

And for the column title overwrite the Twig Block named list_td_column_**title**

{% highlight html+django %}
{{ "{%" }} extends_admingenerated "NamespaceYourBundle:List:index.html.twig" %}
{{ "{%" }} block list_td_column_title %}
    <span style="font-weight:bold">{{ "{{" }} Movie.title }}</span>
{{ "{%" }} endblock %}
{% endhighlight %}

## Default sort

You can define the default sort options with the key sort :

{% highlight yaml %}
builders:
  list:
    params:
      sort: [ producer.name, DESC ]
{% endhighlight %}

With the first argument, the column to sort and the second one optional the sorting order ASC or DESC (default: ASC)

## Object actions

You can set actions for rows. This action will call the defined controller, giving the id of the rows

{% highlight yaml %}
builders:
  list:
    params:
      object_actions: 
        edit: ~
{% endhighlight %}

Will go to the edit link.

{% highlight yaml %}
builders:
  list:
    params:
      object_actions: 
        delete: 
          confirm: Are you sure to delete {{ Movie.title }} ?
{% endhighlight %}

Will process the delete action if you click ok on the confirm box message, and like you can see in this sample you can use twig power in your confirm message

The default route for an object action is  **namespace_prefix** _ **bundle_name** _ **action_name**

You can change it passing the option route to your action :

{% highlight yaml %}
builders:
  list:
    params:
      object_actions: 
        delete: 
          route: my_custom_route
{% endhighlight %}

## Actions

You can set action on the List page. The action will not take params.


{% highlight yaml %}
builders:
  list:
    params:
      actions:
        new: ~
{% endhighlight %}

The default route for an object action is  **namespace_prefix** _ **bundle_name** _ **action_name**

{% highlight yaml %}
builders:
  list:
    params:
      actions: 
        new: 
          route: my_custom_route
{% endhighlight %}

You can add a confirm message like of the [Object actions](/documentation/list.html#object-actions)

The default label is the name of the action, [translated in your language](https://github.com/symfony2admingenerator/AdmingeneratorGeneratorBundle/tree/master/Resources/translations) by the catalog Admingenerator

You can edit it with the `label` option

{% highlight yaml %}
builders:
  list:
    params:
      actions: 
        new: 
          label: Create a movie
{% endhighlight %}

And of course, you can translate it using the same translation catalog.

## Edit query

Because the generated class is extended by a class in your bundle, thanks to generation mecanisme, you can easy open the query in cache and see wich method to overwrite.
And if you want to add a filter on your query the good method is `getQuery`

Eg :

<div class="tabber">
    <div class="tabbertab" title="Propel">

The default method is :

{% highlight php %}
<?php
protected function getQuery()
{
    $query = MovieQuery::create();
    
    $this->processSort($query);
    $this->processFilters($query);

    return $query;
}
{% endhighlight %}

and you can edit to set :

{% highlight php %}
<?php
protected function getQuery()
{
    $query = MovieQuery::create()
                ->filterByPublished(true);
    
    $this->processSort($query);
    $this->processFilters($query);

    return $query;
}
{% endhighlight %}

    </div>
    
    <div class="tabbertab" title="Doctrine ORM">

The default method is :

{% highlight php %}
<?php
protected function getQuery()
{
    $query = $this->getDoctrine()
                ->getEntityManager()
                ->createQueryBuilder()
                ->select('q')
                ->from('Namespace\\Movie', 'q');
    
    $this->processSort($query);
    $this->processFilters($query);

    return $query->getQuery();
}
{% endhighlight %}

and you can edit to set :

{% highlight php %}
<?php
protected function getQuery()
{
    $query = $this->getDoctrine()
                ->getEntityManager()
                ->createQueryBuilder()
                ->select('q')
                ->from('Namespace\\Movie', 'q')
                ->addWhere('q.is_published = :is_published')
                ->setParameter(':is_published', true);
    
    $this->processSort($query);
    $this->processFilters($query);

    return $query->getQuery();
}
{% endhighlight %}

    </div>
    
    <div class="tabbertab" title="Doctrine ODM">

The default method is :

{% highlight php %}
<?php
protected function getQuery()
{
    $query = $this->getDocumentManager()
                  ->createQueryBuilder('Namespace\\Movie');
    
    $this->processSort($query);
    $this->processFilters($query);

    return $query->getQuery();
}
{% endhighlight %}

and you can edit to set :

{% highlight php %}
<?php
protected function getQuery()
{
    $query = $this->getDocumentManager()
                  ->createQueryBuilder('Namespace\\Movie')
                  ->field('is_published')
                  ->equals(true);
                  
    $this->processSort($query);
    $this->processFilters($query);

    return $query->getQuery();
}
{% endhighlight %}

    </div>
</div>

If you want to have by default all the movies published only. 

## Configuration

### Date format

You can use two different options for date field in list.

For example:

<pre>
11/09/2012
</pre>
or
<pre>
dimanche 9 novembre 2012 23:54:47 GMT+00:00
</pre>

For use second option you must set parameter use_localized_date:

{% highlight yaml %}
admingenerator_generator:
  twig:
    use_localized_date: true
{% endhighlight %}

For field with type date Admingenerator use twig filter date.
The date filter format a date to a given format:

{% highlight html+django %}
{{ "{{" }}  post.published_at|date('Y-m-d') }}
{% endhighlight %}
 
Default Admingenerator date format is 'Y-m-d'. This default can be easily changed in your config.yml:

{% highlight yaml %}
admingenerator_generator:
  twig:
    date_format: 'm/d/Y'
{% endhighlight %}

For field with type datetime Admingenerator use twig filter date.
The date filter format a date to a given format:

{% highlight html+django %}
{{ "{{" }}  post.published_at|date('Y-m-d H:i:s') }}
{% endhighlight %}
 
Default Admingenerator datetime format is 'Y-m-d H:i:s'. This default can be easily changed in your config.yml:

{% highlight yaml %}
admingenerator_generator:
  twig:
    date_format: 'm/d/Y H:i'
{% endhighlight %}

For field with type date and use localized format Admingenerator use twig filter localizeddate.
The localizeddate filter format a date to a given format:

{% highlight html+django %}
{{ "{{" }} post.published_at|localizeddate("medium", "none") }}
{% endhighlight %}

For field with type datetime and use localized format Admingenerator use twig filter localizeddate.
The localizeddate filter format a date to a given format:

{% highlight html+django %}
{{ "{{" }}  post.published_at|localizeddate("medium", "medium") }}
{% endhighlight %}
 
In your config.yml you can specify format for localizeddate filter:

{% highlight yaml %}
admingenerator_generator:
  twig:
    localized_date_format: 'full'
    localized_datetime_format: 'full'
{% endhighlight %}

[More about intldateformatter](http://php.net/manual/en/class.intldateformatter.php)

### Number format

For field with type decimal Admingenerator use twig filter number_format.
The number_format filter format a number to a given format:

{% highlight html+django %}
{{ "{{" }} 200.35|number_format }}
{% endhighlight %}

If no formatting options are provided then Admingenerator will use the default formatting options of:
* 0 decimal places.
* . as the decimal point.
* , as the thousands separator.

This default can be easily changed in your config.yml:

{% highlight yaml %}
admingenerator_generator:
  twig:
    number_format:
      decimal: 2
      decimal_point: ','
      thousand_separator: ' '
{% endhighlight %}
