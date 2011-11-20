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

