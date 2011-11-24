---
layout: documentation
title: Configure the success/error messages
---

# Overwrite the default success / error messages

For the actions new, edit, delete, you can overwrite the default notice message to set your own.

{% highlight yaml %}
edit:
  params:
    messages:
      success: "Your movie is well updated"
      error: "Oops, an error occurred, and we can save this movie."
{% endhighlight %}