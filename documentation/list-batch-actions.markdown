---
layout: documentation
title: Batch actions
---

# Batch actions

## Configure generator.yml

Configure myCustomAction in generator.yml:

{% highlight yaml %}
builders:
  list:
    batch_actions:
	  delete: ~ # Pre coded action
	  myCustomAction:
	    label: Do custom
		confirm: Please confirm you want to do that	  
{% endhighlight %}

## How to code your custom action

In your `ListController` add method :

{% highlight php %}
<?php

protected function doBatchMyCustomAction(array $ids)
{
    if (2 == (1+1)) {
		$this->get('session')->setFlash('success', 'Hourri') );
		return;
	}
	
	$this->get('session')->setFlash('error', 'Cruel world!') );	
}
{% endhighlight %}

After the execution of your method `doBatchMyCustomAction` the controller will be redirected to the list.
