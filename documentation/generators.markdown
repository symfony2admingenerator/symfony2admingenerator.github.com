---
layout: documentation
title: Generators
---

# Choose your generator

Each orm/odm can provide their own generator service that can replace the admingenerator.
 
Thereby greatly increasing the scope and flexibility including things which are not strictly for an admin site.

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