---
layout: documentation
title: Check credentials
---

# Security: Check credentials ?

## For actions

I don't know for you but for me the `credentials` option in the symfony 1 is just an incomprehensible thing to write, it was something like [ A, [[ B, C ]]].

So because i don't understand what means this `[` and i understand words in the admingenerator new generation, write only a string

{% highlight yaml %}
builders:
  edit:
    params:
      credentials: "ROLE_A or (ROLE_B and ROLE_C)"
{% endhighlight %}

With this sample, you'll secure your **edit** action, so if i go on the url edit without the authorization it will throw an AccessDeniedException.

And of course you'll ask him about the link to this action ! By default do noting and the test will be the same as the action. 
But if you want to make another tests :

{% highlight yaml %}
builders:
  list:
    params:
      object_actions:
        credentials: "ROLE_Z"
{% endhighlight %}

But i don't see good example to not let the generetor do the magic with the same test !

## For columns and forms

The idea is the same as actions, only the parameter key change, we are now on `fields`

{% highlight yaml %}
params:
  fields:
    fieldName:
      credentials: "ROLE_A or (ROLE_B and ROLE_C)"
{% endhighlight %}