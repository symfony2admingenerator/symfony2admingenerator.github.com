---
layout: documentation
title: Forms configuration
---

# New / Edit form configuration 

## Overview
This section describes how new and edit forms are produced from parameters defined in the builders.     
The parameters include: title, fields, display and list.  Here is an example for the edit form:

{% highlight yaml %}
 edit:
    params:
      title: You're editing the movie "{{ Movie.title }}"
      fields:
        actors:
          formType: collection
          dbType: collection
          addFormOptions:
            type: \Admingenerator\PropelDemoBundle\Form\Type\ActorType
      display:
        "NONE": [ title, release_date ]
        "Other informations": [[ is_published ], [producer, actors ]]
      actions:
        list: ~
{% endhighlight %}  

This simple definition:

*   Sets the edit page title, including **twig display** of any field from the model
*   Allows fields to be defined that links this edit form to the underlying model.  Note the definition for actors and how this pulls in the subform ActorType
*   full control of the display and layout of the fields.  This form contains 2 layout sections, showing visual separation of fields between them.
*   define additional **actions** - e.g. navigation links/buttons can be placed on the form that link back to the list, delete or new forms.
    
##Title
The example above shows a simple title string including the Twig inclusion of the field movie.actor. 

For more control of the title section, when your changes are too extensive for this single line, you can override the Twig Block named form_**title**:

Edit your local bundle file (NOT the one in cache)  : YourBundle/Resources/views/(Edit|New)/index.html

and overwrite the Twig Block named form_**title** with your own as follows:  

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

>**Tip**<br />This field will be parsed by twig so you could use all the power of filters...

## Fields
This section is [a large topic refer to](/documentation/fields-for-list.html) as well.
Fields allow tight integration between your model and the forms, by using the full power and flexibility of the symfony form components. This is where you setup:

*     subforms that are related in your model 
*     field formatting of form labels 
*     Form options: formating (e.g. format: "Y-m-d") of fields,   
*     PHP snippets directly in the form, for example to define a field with a date range. 
*     Virtual Fields using getters that tie your model directly into the form, thereby allowing even complex relationships to be included

## Display

###Layout

####Defining columns and rows for your form

*    Multiple rows of **fields** [firstname,lastname].  This show  one column  on two separate rows.  
*    Single **row** of fileds[[firstname,lastname]] will show the fields with two columns on a single row.
*    And [[firstname, initial, lastname],[Address],[city, state],[Country]] shows that the form can contain multiple rows of varying number of columns per row. 

Note: at the Current time you cannot mix fields and rows together.  i.e [[firstname, lastname],Address,city,state] is not allowed. 
Use  4 rows [[firstname, lastname],[Address],[city],[state]]

### Single Layout Section
For a simple display.
{% highlight yaml %}
new:
  display: [ [firstname, lastname],[Address,City,state] ]
{% endhighlight %}

###Multiple layout sections
A form can be broken down into several layout sections with the use of fieldsets.  For example a registration form may contain a layout section for the username, email and password, 
another for the address and a third section for the credit card details. Each grouped separately.
Basically a layout section is defined by: a top legand and a fieldsets to put in the section.  This example shows two layout sections, each with a legand and a fieldset.


{% highlight yaml %}
edit:
  display: 
    NONE: [ title, name ]
    "Where is it ?": [ location ]
{% endhighlight %}

>**Tip**<br />Like in symfony 1, you do not need to define a top legand just set this to NONE. 

#### And the killer feature is : Show more than one field per rows

{% highlight yaml %}
edit:
  display: 
    NONE: [ title, name ]
    "Where is it ?": [[ location_id], [ zipcode, country ]]
{% endhighlight %}

Note: When you use sections each has to be properly defined on their own **separate** line:

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
    
    <div class="tabbertab" title="Or ">
    
{% highlight yaml %}
new:
  display: 
    NONE: [ title, [ name, firstname ] ]
{% endhighlight %}

    </div>
</div>

## Tabs

If you want to display tabs wich contains fieldsets use

{% highlight yaml %}
builders:
  list:
    params:
      tabs: 
        "My First Tab title":
          "MyFieldset": [ field1, [ field2, field3 ]]
          "MyFieldset2": # ....
        "My Second tab":
          "MyFieldset2": # ...
{% endhighlight %}

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

##Actions

Like for lis you can configure actions 

{% highlight yaml %}
 edit:
   actions:
     myActionName: 
       route: MyRoute
{% endhighlight %}

But when you are in the edit view you want probably to keep some context to build your route 

{% highlight yaml %}
   actions:
     myActionName: 
       route: MyRoute
       params:
         pk: "{{ MyModel.id }}"
         locale: fr
{% endhighlight %}
