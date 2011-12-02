---
layout: base
title: Contribute
---

# How To Contribute ? #

Here are the best ways you can contribute to the project.

You just  _fork_ the [Admingenerator project on github](https://github.com/cedriclombardot/AdmingeneratorGeneratorBundle) and then
provide Pull Requests and /or submit issues.

## Submit an issue ##

The ticketing system hosted on Github:

* AdmingeneratorGeneratorBundle: [https://github.com/cedriclombardot/AdmingeneratorGeneratorBundle/issues](https://github.com/cedriclombardot/AdmingeneratorGeneratorBundle/issues)
* AdmingeneratorIpsum: [https://github.com/cedriclombardot/AdmingeneratorIpsum/issues](https://github.com/cedriclombardot/AdmingeneratorIpsum/issues)

## Make a Pull Request ##

The best way to submit a patch is to make a Pull Request on Github. First, create a new branch from  `master` and then from your local project type:

{% highlight bash %}
> git checkout -b master fix-my-patch
{% endhighlight %}

Now make your changes in this branch. Important: Please provide unit tests with your patch. This will expedite the Pull request to prove that the patch actually fixes the bug.

Then when you are done, you need to rebase your branch to provide a clean and safe Pull Request.

{% highlight bash %}
> git checkout master
> git pull --ff-only upstream master
> git checkout fix-my-patch
> git rebase master
{% endhighlight %}

In this example, the `upstream` remote is the official repository.

Once done, you can submit the Pull Request by pushing your branch to your fork:

{% highlight bash %}
> git push origin fix-my-patch
{% endhighlight %}

Go to the www.github.com and press the _Pull Request_ button. Add a short description to this Pull Request and submit it.

## Running Unit Tests ##

We use [PHPUnit](http://www.phpunit.de) to test the build and runtime frameworks.

You can find the unit test classes and support files in the `Tests` directory.

### Install PHPUnit ###

In order to run the tests, you must install PHPUnit:

{% highlight bash %}
> pear channel-discover pear.phpunit.de
> pear install phpunit/PHPUnit
{% endhighlight %}

## Running Functionnal Tests ##

We are starting to build behat tests, which you can run on the AdmingeneratorIpsum project with your fork as vendor

{% highlight bash %}
app/console -e=test behat --init @AdmingeneratorGeneratorBundle
{% endhighlight %}
