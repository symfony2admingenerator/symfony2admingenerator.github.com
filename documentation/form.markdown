---
layout: documentation
title: Forms configuration
---

# New / Edit form configuration 

## Display

Forms are can be **easily customized** in several ways:
***Layout

Notation:
*    Multiple rows of **fields** [firstname,lastname].  This show  two fields on 2 separate rows .  
*    Single **row** of fileds[[firstname,lastname]] will show the fields all on the same row .
*    And [[firstname, initial, lastname],[Address],[city],[state]] shows the first row with three fields, followed by three fields on their own rows, 
Note: at the Current time you cannot mix fields and rows together.  i.e [[firstname, lastname],Address,city,state] is not allowed. 
Use a collection of 4 rows [[firstname, lastname],[Address],[city],[state]]

### Basic usage
Display fields as multiple rows using a single fieldset.
{% highlight yaml %}
new:
  display: [ [firstname, lastname],[Address,City,state] ]
{% endhighlight %}

### With fieldsets
Multiple fieldsets.
{% highlight yaml %}
edit:
  display: 
    NONE: [ title, name ]
    "Where is it ?": [ location ]
{% endhighlight %}

>**Tip**<br />Like in symfony 1, the none key allow you to set a fieldset without a top legend.   Otherwise the key "Where is it? is displayed as the top legend

### And the killer feature is : Show more than one field per rows

{% highlight yaml %}
edit:
  display: 
    NONE: [ title, name ]
    "Where is it ?": [[ location_id], [ zipcode, country ]]
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
    NONE: [ [title], [ name, firstname ] ]
{% endhighlight %}

    </div>
</div>

## Overwrite the rendering of a field

Edit the file : YourBundle/Resources/views/(Edit|New)/index.html

And for the column title overwrite the Twig Block named form_**title**

{% highlight html+django %}
{{ "{%" }} extends_admingenerated "NamespaceYourBundle:(Edit|New):index.html.twig" %}
{{ "{%" }} block form_title %}
    {{ "{{ " }} parent() }}
    <div id="preview_title">
    
    </div>
    <script>
        // Do here your own
    </script>
{{ "{%" }} endblock %}
{% endhighlight %}
