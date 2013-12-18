---
layout: base
title: Batch actions
---

# Batch actions

## Configure generator.yml

Configure myCustomAction in generator.yml:

~~~yaml
builders:
  list:
    batch_actions:
	  delete: ~ # Pre coded action
	  myCustomAction:
	    label: Do custom
		confirm: Please confirm you want to do that	  
~~~

## How to code your custom action

In your `ListController` add method :

~~~php
<?php

protected function doBatchMyCustomAction(array $ids)
{
    if (2 == (1+1)) {
		$this->get('session')->setFlash('success', 'Hourri') );
		return;
	}
	
	$this->get('session')->setFlash('error', 'Cruel world!') );	
}
~~~

After the execution of your method `doBatchMyCustomAction` the controller will be redirected to the list.
