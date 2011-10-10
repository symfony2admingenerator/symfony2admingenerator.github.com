---
layout: documentation
title: Forms configuration
---

# New / Edit form configuration 

## Display

Of course the basic display will not be so diferent of list. But you'll probably want to do more !

### Basic usage

{% highlight yaml %}
new:
  display: [ title, name ]
{% endhighlight %}

### With fieldsets

{% highlight yaml %}
edit:
  display: 
    NONE: [ title, name ]
    "Where is it ?": [ location ]
{% endhighlight %}

>**Tip**<br />Like in symfony 1, the none key allow you to set a fieldset without legend else the key is the legend

### And the killer feature is : Show more than one field per rows

{% highlight yaml %}
edit:
  display: 
    NONE: [ title, name ]
    "Where is it ?": [ location_id, [ zipcode, country ]]
{% endhighlight %}

Note: You have to be under a fieldset. that's means you can't use multiple fields per rows with the basic display :

<div class="tabber">
    <div class="tabbertab" title="You can't do">
    
{% highlight yaml %}
new:
  display: [ title, [ name, firstname ] ]
{% endhighlight %}

    </div>
    
    <div class="tabbertab" title="You have to do ">
    
{% highlight yaml %}
new:
  display: 
    NONE: [ title, [ name, firstname ] ]
{% endhighlight %}

    </div>
</div>