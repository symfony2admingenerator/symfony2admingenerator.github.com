---
layout: base
title: Quick start
---

# In 3 steps

## Step 1: Setup your symfony environnement

Of course, you've to [setup the bundle](/installation.html) by forking the [ipsum project](https://github.com/symfony2admingenerator/AdmingeneratorIpsum) or by following the [installation guide](/installation.html)

## Step 2: Generate a bundle

In your symfony project, you've got two ways to init an admin bundle :

### With the SensioGeneratorBundle

In a shell write :

~~~bash
> php app/console generate:bundle
~~~

And after go to *Step 3*.

### With the AdminGeneratorBundle

With this command you'll build a bundle and all controllers in one time.

~~~bash
> php app/console admin:generate-bundle
~~~

## Step 3 : Add a generator.yml on an existing bundle

You can add generator.yml on a bundle wich already exists (created by AdmingeneratorBundle or not)

~~~bash
> php app/console admin:generate-admin
~~~

