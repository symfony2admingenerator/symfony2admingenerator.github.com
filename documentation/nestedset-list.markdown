---
layout: documentation
title: Nested set with admingenerator
---

# Nested set with admingenerator (work only with propel)

<img src="http://symfony2admingenerator.org/images/nestedset.png" alt="Symfony2 admingenerator nestedset" />

## Routing configuration

To use nested set you need complementary routes. 

In routing.yml replace `admingenerator` by `admingenerator_nested`

{% highlight yaml %}
Admingenerator_demonested:
    resource: "@AdmingeneratorDemoBundle/Controller/Category/"
    type:     admingenerator_nested
    prefix:   /category
{% endhighlight %}

## Generator configuration

In generator.yml replace `list` by `nested_list`

{% highlight yaml %}
builders:
  nested_list:
    params:
      title: Liste des cat�gories
      display: ~
      actions:
        new: ~
      object_actions:
        edit: ~
        delete: ~
{% endhighlight %}
