---
layout: documentation
title: Params section of generator.yml
---

# Params section of generator.yml

## Bundle in Acme/Bundle/TestBundle ?

If you have "non-standard" structure of bundle and your bundles namespaces are Acme/Bundle/TestBundle and not Acme/TestBundle, 
you have to update the generator.yml like that :

{% highlight yaml %}
params:
  model: ......
  namespace_prefix: Acme
  subfolder: Bundle
  bundle_name: TestBundle
{% endhighlight %}

## Custom stylesheets

Sometimes, you'll want to add your own css in the theme. Two way to do that :

### In the config.yml

{% highlight yaml %}
admingenerator_generator:
    stylesheets:
      - { path: bundles/mybundle/css/backend.css }
      - { path: bundles/mybundle/css/print.css, media: print }
{% endhighlight %}

### In the generator.yml

{% highlight yaml %}
params:
  model: ......
  stylesheets:
    - bundles/mybundle/css/backend.css
    - { path: bundles/mybundle/css/tv.css, media: tv }
{% endhighlight %}