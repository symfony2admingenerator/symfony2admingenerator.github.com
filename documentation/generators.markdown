---
layout: documentation
title: Generators
---

# Choose your generator

Each orm/odm have is generator service. 
And because it's a service you can easylly change to use your own and why not generate other things wich is not an admin.

## Propel

Enable propel services in your `config.yml` :

{% highlight yaml %}
admingenerator_generator:
    use_propel: true
{% endhighlight %}
 
And in your generator.yml :
    
{% highlight yaml %}
generator: admingenerator.generator.propel
{% endhighlight %}

## Doctrine ORM

Enable doctrine orm services in your `config.yml` :

{% highlight yaml %}
admingenerator_generator:
    use_doctrine_orm: true
{% endhighlight %}
 
And in your generator.yml :

{% highlight yaml %}
generator: admingenerator.generator.doctrine
{% endhighlight %}

## Doctrine ODM mongo

Enable doctrine odm services in your `config.yml` :

{% highlight yaml %}
admingenerator_generator:
    use_doctrine_odm: true
{% endhighlight %}
 
And in your generator.yml :

{% highlight yaml %}
generator: admingenerator.generator.doctrine_odm
{% endhighlight %}