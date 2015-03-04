---
layout: base
title: "Documentation for AdmingeneratorGeneratorBundle"
---

# Welcome to the AdmingeneratorGeneratorBundle documentation! #

### What? ###

The AdmingeneratorGeneratorBundle is an open source admin-generator for the famous [Symfony2](http://www.symfony.com/) php framework. 

The bundle generates PHP code in the cache directory, that can be easily read and understand. You can create all the functionality of an admin site, including: 

*     **commands** that generate a bundle for an overall site (includes stubs for controllers) and those for creating a bundle within an existing bundle
*     **setting up filters**, 
*     **routing** that is integrated with the Symfony security framework
*     **form generation supporting complete customization**: fields,field sets, labels, help text and validation. Complete form layout including multiple sections on the form,  sub forms and more
*     **Twig Template generation**, and of course
*     **Supports the Model Managers: Doctrine ORM, Doctrine ODM and Propel** 

All this from one simple file. 

Edge cases are pushed far back since **extensibility is at the heart of the architecture**.  All components outlined above can be overridden by using standard inheritance (for controllers, Twig Templates and forms) or using the normal configuration setup in Symfony (routing for example).
  
### Who is this for? ###

#### Developers looking for a rapid development process ####
The primary goal is to simply and rapidly build an entire admin site. But additionally this can:

*	be used in a similar way to the Symfony Interactive generators to **kick start your own development**, 
*	refractor from this start and use the central yaml file to ensure that site components are consistent as you build out the development, and 
*	be used as a simple way to "wire-frame" your application to show proof of concept functionality to other stake holders, and then used to firm up requirements.  

#### Developers new to Symfony who wish to have an easy start  ####
You can create your first web application using the generator *without writing a single line of code*. Then learn Symfony and examine or use the generated code even in a front end application.

#### Used by other Bundle Developers ####
The generator is really an integration component across bundles and Symfony components. It is envisaged that eventually the Symfony community could extend the class generator with the core team to be more universal.  For example integration with a CMS. But *we need your help to get this production ready*. All contributions are very welcome.

#### 

### Sound too good to be true, so how does it work? ###
Simply you create a YAML file and in conjunction with your model metadata (ODM or ORM or Propel) generates: routing, form classes, the controllers and Twig template files.
The rest of the documentation shows just how flexible and easy this is.  Take a look at the YAML file that shows **the creation of an entire site**:

{% highlight yaml %}
generator: admingenerator.generator.doctrine
params:
  model: Admingenerator\DemoBundle\Entity\Movie
  namespace_prefix: Admingenerator
  bundle_name: DemoBundle
  fields: 
    is_published:
      help: If you want to see this content on you website
    actors:
      filterOn: actors.id
    producer:
      label: Producer name
      sort_on: producer.name
      getter: producer.name
      addFormOptions:
        property: name
    release_date:
      formType: birthday 
      addFormOptions:
        years: 
          .range: 
            from: <?php echo date("Y"); ?>

            to: 1950
            step: 1

builders:
  list:
    params:
      title: Here is a beautiful title no  ???
      display: [ id, title, is_published, producer, release_date ]
      max_per_page: 3
      actions:
        new: ~ 
      object_actions:
        edit: ~ 
        delete: ~
  filters: 
    params:
      fields:
        release_date:
          formType: date_range
      display: [ title, is_published, producer, actors, release_date]

  new: 
    params:
      title: You're creating a new movie
      display: [ title, is_published, producer, actors, release_date ]
      actions:
        list: ~
  edit: 
    params:
      title: You're editing the movie "{{ "{{" }} Movie.title }}"
      display: 
        "NONE": [ title, release_date ]
        "Other informations": [ is_published, producer, actors ]
      actions:
        list: ~
  delete: ~
{% endhighlight %}


### In pictures

![Preview of list](https://github.com/symfony2admingenerator/AdmingeneratorOldThemeBundle/raw/master/Resources/doc/list-preview.png)

![Preview of edit](https://github.com/symfony2admingenerator/AdmingeneratorOldThemeBundle/raw/master/Resources/doc/edit-preview.png)
