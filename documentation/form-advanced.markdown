---
layout: documentation
title: Forms advanced configuration
---

# Forms advanced configuration

## Choose your types

You've probably dreamt about it: Changing the look and feel of forms without writing php code. I'm also a dreamer. I've done it for you.

First of all, I'll show you some samples.

### Change years range of a date field

Configure your field in the `params.fields` section, or in the `params.edit.fields` section if you want to change the value only for edit.

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

As you can see here, I use the `addFormOptions` parameter to add more options to my form parameters. I could also use `formOptions` to remove all calculated opt                                                                                        ions and set only the ones that I want.

>**Did you see the magic?**<br />The `.` means that will call a php function (the `range()` function in this example). The function must return an array or a st                                                                                        ring to be used as the form options. <br />Note: Parameters must be kept in the                                                                                         same order as in the called function.

### Use a text input for your date field

{% highlight yaml %}
params:
  fields:
    release_date:
      addFormOptions:
        widget: single_text
{% endhighlight %}

### Use a collection type

By default collections are represented by a double list selector, but sometimes                                                                                         you'll want to create a collection type.

{% highlight yaml %}
params:
  fields:
    actors:
      formType: collection
      addFormOptions:
        type: \Admingenerator\PropelDemoBundle\Form\Type\ActorType
{% endhighlight %}

And of course create your `ActorType`:

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

If you want to use a virtual field, depending on the type you want to use (e.g. a dateType, a text input, or a collection), you have to overwrite the `dbType`:

{% highlight yaml %}
params:
  fields:
    vitual_actors:
      formType: collection
      dbType: collection
      addFormOptions:
        type: \Admingenerator\PropelDemoBundle\Form\Type\ActorType
{% endhighlight %}

Like that the method called will not be `setActors` but `setVirtualActors`
