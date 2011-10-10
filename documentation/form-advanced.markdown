---
layout: documentation
title: Forms avanced configuration
---

# Forms avanced configuration

## Choose your types

You'll probably dream it, changing your forms aspect without writing php. I'm also a dreamer. I've do it for us. 

First of all, i'll show you some samples.

### Change years range of a date field

Configure your field in the section `params.fields` or `params.edit.fields` if you wan't to change the value only for edit.

{% highlight yaml %}
params:
  fields:
    release_date:
      formType: birthday
      addFormOptions:
        format: "Y-m-d"
        years:
          .range:
            from: <?php echo date("Y"); ?>

            to: 1950
            step: 1
{% endhighlight %}

Like you can see here, i use the `addFormOptions` to add more options to my form parameters. I could also use `formOptions` to remove all calculated options and set my own only.

>**Did you see the magic?**<br />The `.` means that you wan't to call a php function will return an array or a string to be sets as options. <br />Note: parameters must be keeped in the good order of the called function

### Use a text input for your date field

{% highlight yaml %}
params:
  fields:
    release_date:
      addFormOptions:
        widget: single_text
{% endhighlight %}

### Use a collection type 

By default collections are represented by a double list selector but sometimes, you'll wan't to create a collection type.

{% highlight yaml %}
params:
  fields:
    actors:
      formType: collection
      addFormOptions:
        type: \Admingenerator\PropelDemoBundle\Form\Type\ActorType
{% endhighlight %}

And of course create your ActorType 

{% highlight php %}
<?php
namespace Admingenerator\PropelDemoBundle\Form\Type;

use Symfony\Component\Form\AbstractType;
use Symfony\Component\Form\FormBuilder;

class ActorType extends AbstractType
{
    public function buildForm(FormBuilder $builder, array $options)
    {
        $builder->add('name');
    }
    
    public function getName()
    {
        return 'propel_embed_actor';
    }
    
    public function getDefaultOptions(array $options)
    {
        return array(
            'data_class' => 'Admingenerator\PropelDemoBundle\Model\Actor',
        );
    }
}
{% endhighlight %}

## Attach a dbType to a virtual field

If you wan't to use a virtual field and determine you want to show a date, a text input or a collection, you have to overwriter the dbType

{% highlight yaml %}
params:
  fields:
    vitrual_actors:
      formType: collection
      dbType: collection
      addFormOptions:
        type: \Admingenerator\PropelDemoBundle\Form\Type\ActorType
{% endhighlight %}

Like that the method called will not be `setActors` but `setVirtualActors`

