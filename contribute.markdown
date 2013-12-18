---
layout: base
title: Contribute
---

# How To Contribute ? #

Here are the best ways you can contribute to the project.

You just  _fork_ the [Admingenerator project on github](https://github.com/symfony2admingenerator/AdmingeneratorGeneratorBundle) and then
provide Pull Requests and /or submit issues.

## Submit an issue ##

The ticketing system hosted on Github:

* AdmingeneratorGeneratorBundle: [https://github.com/symfony2admingenerator/AdmingeneratorGeneratorBundle/issues](https://github.com/symfony2admingenerator/AdmingeneratorGeneratorBundle/issues)
* AdmingeneratorIpsum: [https://github.com/cedriclombardot/symfony2admingenerator/issues](https://github.com/symfony2admingenerator/AdmingeneratorIpsum/issues)

## Make a Pull Request ##

The best way to submit a patch is to make a Pull Request on Github. First, create a new branch from  `master` and then from your local project type:

~~~bash
> git checkout -b fix-my-patch master
~~~

Now make your changes in this branch. Important: Please provide unit tests with your patch. This will expedite the Pull request to prove that the patch actually fixes the bug.

Then when you are done, you need to rebase your branch to provide a clean and safe Pull Request.

~~~bash
> git checkout master
> git pull --ff-only upstream master
> git checkout fix-my-patch
> git rebase master
~~~

In this example, the `upstream` remote is the official repository.

Once done, you can submit the Pull Request by pushing your branch to your fork:

~~~bash
> git push origin fix-my-patch
~~~

Go to the www.github.com and press the _Pull Request_ button. Add a short description to this Pull Request and submit it.

## Running Unit Tests ##

We use [PHPUnit](http://www.phpunit.de) to test the build and runtime frameworks.

You can find the unit test classes and support files in the `Tests` directory.

### Install PHPUnit ###

In order to run the tests, you must install PHPUnit:

~~~bash
> pear channel-discover pear.phpunit.de
> pear install phpunit/PHPUnit
~~~

## Running Functionnal Tests ##

We are starting to build behat tests, which you can run on the AdmingeneratorIpsum project with your fork as vendor

~~~bash
app/console -e=test behat --init @AdmingeneratorGeneratorBundle
~~~
