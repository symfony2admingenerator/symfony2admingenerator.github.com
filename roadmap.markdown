---
layout: base
title: Roadmap
---

# Roadmap

I'm happy to present you the roadmap, feel free to propose complete, clicking the button fork and edit at bottom of this page.

## Now to 1.0
The first production release will be 1.0.  

### Core :

* <strike>Use the TwigGenerator as a vendor [#33](https://github.com/cedriclombardot/AdmingeneratorGeneratorBundle/issues/33)</strike>
* <strike>Make a magic installer [#33](https://github.com/cedriclombardot/AdmingeneratorGeneratorBundle/issues/33)</strike>
* <strike>Implement credentials for actions and columns</strike> 
* <strike>Implement non HTML5 validators [#17](https://github.com/cedriclombardot/AdmingeneratorGeneratorBundle/issues/17)</strike> Moved to 1.1
* Fix mongodb types [#31](https://github.com/cedriclombardot/AdmingeneratorGeneratorBundle/issues/31)

### ActiveAdminTheme :

* Continue the integration of forms

### Documentation :

* On how to skin the admin
* On validators
* On TwigGenerator

## 1.0 to 1.1

### Core :

* Remove dependency on SensioGenerator by using the TwigGenerator for command line
* Add ability to export in XML, CSV, XLS
* Implement a show action with chained admin to make easy to edit related objects
* Adding tests and behat tests
* Add batch actions
* Implement the `owner` credential
* Implement non HTML5 validators [#17](https://github.com/cedriclombardot/AdmingeneratorGeneratorBundle/issues/17)

### Menu

* Implement a menu in yaml probably by making a PR to KNP

### Skins ?

* Probaly a mobile theme

### Documentation

* Of course, always documentation

## 1.1 to 1.2

### Core :

* Make spesialized lists (Datagrid, Nested Set, Orderable)
* Add an ajax datagrid ?
* Add a search engine wich allow you to filter into the entire admin objects
* Make a magic dashboard
